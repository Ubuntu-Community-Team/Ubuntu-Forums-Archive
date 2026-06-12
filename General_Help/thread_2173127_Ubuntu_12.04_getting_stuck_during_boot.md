---
title: "Ubuntu 12.04 getting stuck during boot"
date: 2013-09-08
forum: General Help
---

### Post by eliot3 on 2013-09-08
Hello forums,
I have a problem: When I switch on the computer, currently about half of the time gets stuck during booting. The system is running since Sep. 1st, it worked ok in the beginning, but in the last days the hang is getting more frequent. Also, the symptoms keep changing: Sometimes it gets stuck for about a minute, then finishes booting normally, somtimes it gets stuck for good, sometimes it starts wildly throwing endless lines of log onto the screen, stuck in a loop of some sort, and I have to pull the plug. Usually, rebooting normally works then, at worst the third time, but I'm worried it might get worse, and something is breaking - maybe a hardware problem? My likeliest candidate is the system drive, that's a SSD, and it's a replacement already because the first one died spectacularly after a month of use. With the new one smartctl doesn't find any problems, but I'm still suspicious. Or is it something completely different? I'm a Linux noob, so I'm just guessing... Below are two syslogs of the boot attempts, the bit I'm talking about are those where the counter goes from 2.73 to 34 and then up ridiculously (first one), or directly from 6.something to 313 (second one) - where 6 is strange already, the clean boots usually don't count higher than 3 or 4 seconds. Can anyone translate the log into English for me, or tell me what to look for?
My system: ASRock H77 Pro4 with Intel i5, 2x4GB RAM, MSI GeForce GTX660, 120GBSSD (sdc), 2TB hard drive for storage (sdb), old 160GB IDE drive on a SATA-adapter (sda).
/ and home is the SSD (sdc1) (yes, I know that's not ideal), as it says in the title I'm using Ubuntu 12.04.

```
Sep  6 22:43:29 fido kernel: imklog 5.8.6, log source = /proc/kmsg started.
Sep  6 22:43:29 fido rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="951" x-info="http://www.rsyslog.com"] start
Sep  6 22:43:29 fido rsyslogd: rsyslogd's groupid changed to 103
Sep  6 22:43:29 fido rsyslogd: rsyslogd's userid changed to 101
Sep  6 22:43:29 fido rsyslogd-2039: Could not open output pipe '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Sep  6 22:43:29 fido kernel: [    0.000000] Initializing cgroup subsys cpuset
Sep  6 22:43:29 fido kernel: [    0.000000] Initializing cgroup subsys cpu
Sep  6 22:43:29 fido kernel: [    0.000000] Linux version 3.5.0-39-generic (buildd@roseapple) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #60~precise1-Ubuntu SMP Wed Aug 14 15:38:41 UTC 2013 (Ubuntu 3.5.0-39.60~precise1-generic 3.5.7.17)
Sep  6 22:43:29 fido kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-39-generic root=UUID=91fecb0e-d9e8-4f00-9750-79cb66f9feb3 ro
Sep  6 22:43:29 fido kernel: [    0.000000] KERNEL supported cpus:
Sep  6 22:43:29 fido kernel: [    0.000000]   Intel GenuineIntel
Sep  6 22:43:29 fido kernel: [    0.000000]   AMD AuthenticAMD
Sep  6 22:43:29 fido kernel: [    0.000000]   Centaur CentaurHauls
Sep  6 22:43:29 fido kernel: [    0.000000] e820: BIOS-provided physical RAM map:
Sep  6 22:43:29 fido kernel: [    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009d7ff] usable
Sep  6 22:43:29 fido kernel: [    0.000000] BIOS-e820: [mem 0x000000000009d800-0x000000000009ffff] reserved
Sep  6 22:43:29 fido kernel: [    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
Sep  6 22:43:29 fido kernel: [    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000dd5b1fff] usable
Sep  6 22:43:29 fido kernel: [    0.000000] BIOS-e820: [mem 0x00000000dd5b2000-0x00000000de001fff] reserved
Sep  6 22:43:29 fido kernel: [    0.000000] BIOS-e820: [mem 0x00000000de002000-0x00000000de08bfff] usable
Sep  6 22:43:29 fido kernel: [    0.000000] BIOS-e820: [mem 0x00000000de08c000-0x00000000de12bfff] ACPI NVS
Sep  6 22:43:29 fido kernel: [    0.000000] BIOS-e820: [mem 0x00000000de12c000-0x00000000de915fff] reserved
Sep  6 22:43:29 fido kernel: [    0.000000] BIOS-e820: [mem 0x00000000de916000-0x00000000de916fff] usable
Sep  6 22:43:29 fido kernel: [    0.000000] BIOS-e820: [mem 0x00000000de917000-0x00000000de959fff] ACPI NVS
Sep  6 22:43:29 fido kernel: [    0.000000] BIOS-e820: [mem 0x00000000de95a000-0x00000000df3e5fff] usable
Sep  6 22:43:29 fido kernel: [    0.000000] BIOS-e820: [mem 0x00000000df3e6000-0x00000000df7f0fff] reserved
Sep  6 22:43:29 fido kernel: [    0.000000] BIOS-e820: [mem 0x00000000df7f1000-0x00000000df7fffff] usable
Sep  6 22:43:29 fido kernel: [    0.000000] BIOS-e820: [mem 0x00000000f8000000-0x00000000fbffffff] reserved
Sep  6 22:43:29 fido kernel: [    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
Sep  6 22:43:29 fido kernel: [    0.000000] BIOS-e820: [mem 0x00000000fed00000-0x00000000fed03fff] reserved
Sep  6 22:43:29 fido kernel: [    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
Sep  6 22:43:29 fido kernel: [    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
Sep  6 22:43:29 fido kernel: [    0.000000] BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
Sep  6 22:43:29 fido kernel: [    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000021effffff] usable
Sep  6 22:43:29 fido kernel: [    0.000000] NX (Execute Disable) protection: active
Sep  6 22:43:29 fido kernel: [    0.000000] SMBIOS 2.7 present.
Sep  6 22:43:29 fido kernel: [    0.000000] DMI: To Be Filled By O.E.M. To Be Filled By O.E.M./H77 Pro4-M, BIOS P1.60 09/20/2012
Sep  6 22:43:29 fido kernel: [    0.000000] e820: update [mem 0x00000000-0x0000ffff] usable ==> reserved
Sep  6 22:43:29 fido kernel: [    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
Sep  6 22:43:29 fido kernel: [    0.000000] No AGP bridge found
Sep  6 22:43:29 fido kernel: [    0.000000] e820: last_pfn = 0x21f000 max_arch_pfn = 0x400000000
Sep  6 22:43:29 fido kernel: [    0.000000] MTRR default type: uncachable
Sep  6 22:43:29 fido kernel: [    0.000000] MTRR fixed ranges enabled:
Sep  6 22:43:29 fido kernel: [    0.000000]   00000-9FFFF write-back
Sep  6 22:43:29 fido kernel: [    0.000000]   A0000-BFFFF uncachable
Sep  6 22:43:29 fido kernel: [    0.000000]   C0000-CFFFF write-protect
Sep  6 22:43:29 fido kernel: [    0.000000]   D0000-E7FFF uncachable
Sep  6 22:43:29 fido kernel: [    0.000000]   E8000-FFFFF write-protect
Sep  6 22:43:29 fido kernel: [    0.000000] MTRR variable ranges enabled:
Sep  6 22:43:29 fido kernel: [    0.000000]   0 base 000000000 mask E00000000 write-back
Sep  6 22:43:29 fido kernel: [    0.000000]   1 base 200000000 mask FF0000000 write-back
Sep  6 22:43:29 fido kernel: [    0.000000]   2 base 210000000 mask FF8000000 write-back
Sep  6 22:43:29 fido kernel: [    0.000000]   3 base 218000000 mask FFC000000 write-back
Sep  6 22:43:29 fido kernel: [    0.000000]   4 base 21C000000 mask FFE000000 write-back
Sep  6 22:43:29 fido kernel: [    0.000000]   5 base 21E000000 mask FFF000000 write-back
Sep  6 22:43:29 fido kernel: [    0.000000]   6 base 0E0000000 mask FE0000000 uncachable
Sep  6 22:43:29 fido kernel: [    0.000000]   7 disabled
Sep  6 22:43:29 fido kernel: [    0.000000]   8 disabled
Sep  6 22:43:29 fido kernel: [    0.000000]   9 disabled
Sep  6 22:43:29 fido kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Sep  6 22:43:29 fido kernel: [    0.000000] original variable MTRRs
Sep  6 22:43:29 fido kernel: [    0.000000] reg 0, base: 0GB, range: 8GB, type WB
Sep  6 22:43:29 fido kernel: [    0.000000] reg 1, base: 8GB, range: 256MB, type WB
Sep  6 22:43:29 fido kernel: [    0.000000] reg 2, base: 8448MB, range: 128MB, type WB
Sep  6 22:43:29 fido kernel: [    0.000000] reg 3, base: 8576MB, range: 64MB, type WB
Sep  6 22:43:29 fido kernel: [    0.000000] reg 4, base: 8640MB, range: 32MB, type WB
Sep  6 22:43:29 fido kernel: [    0.000000] reg 5, base: 8672MB, range: 16MB, type WB
Sep  6 22:43:29 fido kernel: [    0.000000] reg 6, base: 3584MB, range: 512MB, type UC
Sep  6 22:43:29 fido kernel: [    0.000000] total RAM covered: 8176M
Sep  6 22:43:29 fido kernel: [    0.000000] Found optimal setting for mtrr clean up
Sep  6 22:43:29 fido kernel: [    0.000000]  gran_size: 64K     chunk_size: 32M     num_reg: 6      lose cover RAM: 0G
Sep  6 22:43:29 fido kernel: [    0.000000] New variable MTRRs
Sep  6 22:43:29 fido kernel: [    0.000000] reg 0, base: 0GB, range: 2GB, type WB
Sep  6 22:43:29 fido kernel: [    0.000000] reg 1, base: 2GB, range: 1GB, type WB
Sep  6 22:43:29 fido kernel: [    0.000000] reg 2, base: 3GB, range: 512MB, type WB
Sep  6 22:43:29 fido kernel: [    0.000000] reg 3, base: 4GB, range: 4GB, type WB
Sep  6 22:43:29 fido kernel: [    0.000000] reg 4, base: 8GB, range: 512MB, type WB
Sep  6 22:43:29 fido kernel: [    0.000000] reg 5, base: 8688MB, range: 16MB, type UC
Sep  6 22:43:29 fido kernel: [    0.000000] e820: update [mem 0xe0000000-0xffffffff] usable ==> reserved
Sep  6 22:43:29 fido kernel: [    0.000000] e820: last_pfn = 0xdf800 max_arch_pfn = 0x400000000
Sep  6 22:43:29 fido kernel: [    0.000000] found SMP MP-table at [mem 0x000fd810-0x000fd81f] mapped at [ffff8800000fd810]
Sep  6 22:43:29 fido kernel: [    0.000000] initial memory mapped: [mem 0x00000000-0x1fffffff]
Sep  6 22:43:29 fido kernel: [    0.000000] Base memory trampoline at [ffff880000097000] 97000 size 24576
Sep  6 22:43:29 fido kernel: [    0.000000] init_memory_mapping: [mem 0x00000000-0xdf7fffff]
Sep  6 22:43:29 fido kernel: [    0.000000]  [mem 0x00000000-0xdf7fffff] page 2M
Sep  6 22:43:29 fido kernel: [    0.000000] kernel direct mapping tables up to 0xdf7fffff @ [mem 0x1fffb000-0x1fffffff]
Sep  6 22:43:29 fido kernel: [    0.000000] init_memory_mapping: [mem 0x100000000-0x21effffff]
Sep  6 22:43:29 fido kernel: [    0.000000]  [mem 0x100000000-0x21effffff] page 2M
Sep  6 22:43:29 fido kernel: [    0.000000] kernel direct mapping tables up to 0x21effffff @ [mem 0xdf7fa000-0xdf7fffff]
Sep  6 22:43:29 fido kernel: [    0.000000] RAMDISK: [mem 0x36208000-0x370fbfff]
Sep  6 22:43:29 fido kernel: [    0.000000] ACPI: RSDP 00000000000f0490 00024 (v02 ALASKA)
Sep  6 22:43:29 fido kernel: [    0.000000] ACPI: XSDT 00000000de110080 0007C (v01 ALASKA    A M I 01072009 AMI  00010013)
Sep  6 22:43:29 fido kernel: [    0.000000] ACPI: FACP 00000000de119cf8 0010C (v05 ALASKA    A M I 01072009 AMI  00010013)
Sep  6 22:43:29 fido kernel: [    0.000000] ACPI: DSDT 00000000de110190 09B65 (v02 ALASKA    A M I 00000022 INTL 20051117)
Sep  6 22:43:29 fido kernel: [    0.000000] ACPI: FACS 00000000de12a080 00040
Sep  6 22:43:29 fido kernel: [    0.000000] ACPI: APIC 00000000de119e08 00072 (v03 ALASKA    A M I 01072009 AMI  00010013)
Sep  6 22:43:29 fido kernel: [    0.000000] ACPI: FPDT 00000000de119e80 00044 (v01 ALASKA    A M I 01072009 AMI  00010013)
Sep  6 22:43:29 fido kernel: [    0.000000] ACPI: MCFG 00000000de119ec8 0003C (v01 ALASKA    A M I 01072009 MSFT 00000097)
Sep  6 22:43:29 fido kernel: [    0.000000] ACPI: SSDT 00000000de119f08 007E1 (v01 Intel_ AoacTabl 00001000 INTL 20091112)
Sep  6 22:43:29 fido kernel: [    0.000000] ACPI: AAFT 00000000de11a6f0 00112 (v01 ALASKA OEMAAFT  01072009 MSFT 00000097)
Sep  6 22:43:29 fido kernel: [    0.000000] ACPI: HPET 00000000de11a808 00038 (v01 ALASKA    A M I 01072009 AMI. 00000005)
Sep  6 22:43:29 fido kernel: [    0.000000] ACPI: SSDT 00000000de11a840 0036D (v01 SataRe SataTabl 00001000 INTL 20091112)
Sep  6 22:43:29 fido kernel: [    0.000000] ACPI: SSDT 00000000de11abb0 009AA (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
Sep  6 22:43:29 fido kernel: [    0.000000] ACPI: SSDT 00000000de11b560 00A92 (v01  PmRef    CpuPm 00003000 INTL 20051117)
Sep  6 22:43:29 fido kernel: [    0.000000] ACPI: BGRT 00000000de11bff8 00038 (v00 ALASKA    A M I 01072009 AMI  00010013)
Sep  6 22:43:29 fido kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Sep  6 22:43:29 fido kernel: [    0.000000] No NUMA configuration found
Sep  6 22:43:29 fido kernel: [    0.000000] Faking a node at [mem 0x0000000000000000-0x000000021effffff]
Sep  6 22:43:29 fido kernel: [    0.000000] Initmem setup node 0 [mem 0x00000000-0x21effffff]
Sep  6 22:43:29 fido kernel: [    0.000000]   NODE_DATA [mem 0x21effc000-0x21effffff]
Sep  6 22:43:29 fido kernel: [    0.000000]  [ffffea0000000000-ffffea00087fffff] PMD -> [ffff880216600000-ffff88021e5fffff] on node 0
Sep  6 22:43:29 fido kernel: [    0.000000] Zone ranges:
Sep  6 22:43:29 fido kernel: [    0.000000]   DMA      [mem 0x00010000-0x00ffffff]
Sep  6 22:43:29 fido kernel: [    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
Sep  6 22:43:29 fido kernel: [    0.000000]   Normal   [mem 0x100000000-0x21effffff]
Sep  6 22:43:29 fido kernel: [    0.000000] Movable zone start for each node
Sep  6 22:43:29 fido kernel: [    0.000000] Early memory node ranges
Sep  6 22:43:29 fido kernel: [    0.000000]   node   0: [mem 0x00010000-0x0009cfff]
Sep  6 22:43:29 fido kernel: [    0.000000]   node   0: [mem 0x00100000-0xdd5b1fff]
Sep  6 22:43:29 fido kernel: [    0.000000]   node   0: [mem 0xde002000-0xde08bfff]
Sep  6 22:43:29 fido kernel: [    0.000000]   node   0: [mem 0xde916000-0xde916fff]
Sep  6 22:43:29 fido kernel: [    0.000000]   node   0: [mem 0xde95a000-0xdf3e5fff]
Sep  6 22:43:29 fido kernel: [    0.000000]   node   0: [mem 0xdf7f1000-0xdf7fffff]
Sep  6 22:43:29 fido kernel: [    0.000000]   node   0: [mem 0x100000000-0x21effffff]
Sep  6 22:43:29 fido kernel: [    0.000000] On node 0 totalpages: 2084965
Sep  6 22:43:29 fido kernel: [    0.000000]   DMA zone: 64 pages used for memmap
Sep  6 22:43:29 fido kernel: [    0.000000]   DMA zone: 6 pages reserved
Sep  6 22:43:29 fido kernel: [    0.000000]   DMA zone: 3911 pages, LIFO batch:0
Sep  6 22:43:29 fido kernel: [    0.000000]   DMA32 zone: 16320 pages used for memmap
Sep  6 22:43:29 fido kernel: [    0.000000]   DMA32 zone: 889112 pages, LIFO batch:31
Sep  6 22:43:29 fido kernel: [    0.000000]   Normal zone: 18368 pages used for memmap
Sep  6 22:43:29 fido kernel: [    0.000000]   Normal zone: 1157184 pages, LIFO batch:31
Sep  6 22:43:29 fido kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Sep  6 22:43:29 fido kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Sep  6 22:43:29 fido kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Sep  6 22:43:29 fido kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
Sep  6 22:43:29 fido kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
Sep  6 22:43:29 fido kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x06] enabled)
Sep  6 22:43:29 fido kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
Sep  6 22:43:29 fido kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Sep  6 22:43:29 fido kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Sep  6 22:43:29 fido kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Sep  6 22:43:29 fido kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Sep  6 22:43:29 fido kernel: [    0.000000] ACPI: IRQ0 used by override.
Sep  6 22:43:29 fido kernel: [    0.000000] ACPI: IRQ2 used by override.
Sep  6 22:43:29 fido kernel: [    0.000000] ACPI: IRQ9 used by override.
Sep  6 22:43:29 fido kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Sep  6 22:43:29 fido kernel: [    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
Sep  6 22:43:29 fido kernel: [    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
Sep  6 22:43:29 fido kernel: [    0.000000] nr_irqs_gsi: 40
Sep  6 22:43:29 fido kernel: [    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
Sep  6 22:43:29 fido kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
Sep  6 22:43:29 fido kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep  6 22:43:29 fido kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep  6 22:43:29 fido kernel: [    0.000000] PM: Registered nosave memory: 00000000dd5b2000 - 00000000de002000
Sep  6 22:43:29 fido kernel: [    0.000000] PM: Registered nosave memory: 00000000de08c000 - 00000000de12c000
Sep  6 22:43:29 fido kernel: [    0.000000] PM: Registered nosave memory: 00000000de12c000 - 00000000de916000
Sep  6 22:43:29 fido kernel: [    0.000000] PM: Registered nosave memory: 00000000de917000 - 00000000de95a000
Sep  6 22:43:29 fido kernel: [    0.000000] PM: Registered nosave memory: 00000000df3e6000 - 00000000df7f1000
Sep  6 22:43:29 fido kernel: [    0.000000] PM: Registered nosave memory: 00000000df800000 - 00000000f8000000
Sep  6 22:43:29 fido kernel: [    0.000000] PM: Registered nosave memory: 00000000f8000000 - 00000000fc000000
Sep  6 22:43:29 fido kernel: [    0.000000] PM: Registered nosave memory: 00000000fc000000 - 00000000fec00000
Sep  6 22:43:29 fido kernel: [    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
Sep  6 22:43:29 fido kernel: [    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fed00000
Sep  6 22:43:29 fido kernel: [    0.000000] PM: Registered nosave memory: 00000000fed00000 - 00000000fed04000
Sep  6 22:43:29 fido kernel: [    0.000000] PM: Registered nosave memory: 00000000fed04000 - 00000000fed1c000
Sep  6 22:43:29 fido kernel: [    0.000000] PM: Registered nosave memory: 00000000fed1c000 - 00000000fed20000
Sep  6 22:43:29 fido kernel: [    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fee00000
Sep  6 22:43:29 fido kernel: [    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
Sep  6 22:43:29 fido kernel: [    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ff000000
Sep  6 22:43:29 fido kernel: [    0.000000] PM: Registered nosave memory: 00000000ff000000 - 0000000100000000
Sep  6 22:43:29 fido kernel: [    0.000000] e820: [mem 0xdf800000-0xf7ffffff] available for PCI devices
Sep  6 22:43:29 fido kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Sep  6 22:43:29 fido kernel: [    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
Sep  6 22:43:29 fido kernel: [    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88021ec00000 s83584 r8192 d22912 u524288
Sep  6 22:43:29 fido kernel: [    0.000000] pcpu-alloc: s83584 r8192 d22912 u524288 alloc=1*2097152
Sep  6 22:43:29 fido kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 
Sep  6 22:43:29 fido kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2050207
Sep  6 22:43:29 fido kernel: [    0.000000] Policy zone: Normal
Sep  6 22:43:29 fido kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-39-generic root=UUID=91fecb0e-d9e8-4f00-9750-79cb66f9feb3 ro
Sep  6 22:43:29 fido kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Sep  6 22:43:29 fido kernel: [    0.000000] __ex_table already sorted, skipping sort
Sep  6 22:43:29 fido kernel: [    0.000000] xsave/xrstor: enabled xstate_bv 0x7, cntxt size 0x340
Sep  6 22:43:29 fido kernel: [    0.000000] Checking aperture...
Sep  6 22:43:29 fido kernel: [    0.000000] No AGP bridge found
Sep  6 22:43:29 fido kernel: [    0.000000] Calgary: detecting Calgary via BIOS EBDA area
Sep  6 22:43:29 fido kernel: [    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
Sep  6 22:43:29 fido kernel: [    0.000000] Memory: 8111084k/8896512k available (6825k kernel code, 556652k absent, 228776k reserved, 6343k data, 948k init)
Sep  6 22:43:29 fido kernel: [    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Sep  6 22:43:29 fido kernel: [    0.000000] Hierarchical RCU implementation.
Sep  6 22:43:29 fido kernel: [    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
Sep  6 22:43:29 fido kernel: [    0.000000] NR_IRQS:16640 nr_irqs:712 16
Sep  6 22:43:29 fido kernel: [    0.000000] Extended CMOS year: 2000
Sep  6 22:43:29 fido kernel: [    0.000000] Console: colour VGA+ 80x25
Sep  6 22:43:29 fido kernel: [    0.000000] console [tty0] enabled
Sep  6 22:43:29 fido kernel: [    0.000000] allocated 33554432 bytes of page_cgroup
Sep  6 22:43:29 fido kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Sep  6 22:43:29 fido kernel: [    0.000000] hpet clockevent registered
Sep  6 22:43:29 fido kernel: [    0.000000] Fast TSC calibration using PIT
Sep  6 22:43:29 fido kernel: [    0.004000] Detected 3193.037 MHz processor.
Sep  6 22:43:29 fido kernel: [    0.000002] Calibrating delay loop (skipped), value calculated using timer frequency.. 6386.07 BogoMIPS (lpj=12772148)
Sep  6 22:43:29 fido kernel: [    0.000097] pid_max: default: 32768 minimum: 301
Sep  6 22:43:29 fido kernel: [    0.000157] Security Framework initialized
Sep  6 22:43:29 fido kernel: [    0.000210] AppArmor: AppArmor initialized
Sep  6 22:43:29 fido kernel: [    0.000256] Yama: becoming mindful.
Sep  6 22:43:29 fido kernel: [    0.000672] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
Sep  6 22:43:29 fido kernel: [    0.002236] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
Sep  6 22:43:29 fido kernel: [    0.002952] Mount-cache hash table entries: 256
Sep  6 22:43:29 fido kernel: [    0.003110] Initializing cgroup subsys cpuacct
Sep  6 22:43:29 fido kernel: [    0.003157] Initializing cgroup subsys memory
Sep  6 22:43:29 fido kernel: [    0.003207] Initializing cgroup subsys devices
Sep  6 22:43:29 fido kernel: [    0.003254] Initializing cgroup subsys freezer
Sep  6 22:43:29 fido kernel: [    0.003300] Initializing cgroup subsys blkio
Sep  6 22:43:29 fido kernel: [    0.003346] Initializing cgroup subsys perf_event
Sep  6 22:43:29 fido kernel: [    0.003410] CPU: Physical Processor ID: 0
Sep  6 22:43:29 fido kernel: [    0.003455] CPU: Processor Core ID: 0
Sep  6 22:43:29 fido kernel: [    0.003503] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
Sep  6 22:43:29 fido kernel: [    0.003503] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
Sep  6 22:43:29 fido kernel: [    0.003849] mce: CPU supports 9 MCE banks
Sep  6 22:43:29 fido kernel: [    0.003904] CPU0: Thermal monitoring enabled (TM1)
Sep  6 22:43:29 fido kernel: [    0.003956] using mwait in idle threads.
Sep  6 22:43:29 fido kernel: [    0.005605] ACPI: Core revision 20120320
Sep  6 22:43:29 fido kernel: [    0.011761] ftrace: allocating 27634 entries in 108 pages
Sep  6 22:43:29 fido kernel: [    0.022120] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Sep  6 22:43:29 fido kernel: [    0.061765] CPU0: Intel(R) Core(TM) i5-3470 CPU @ 3.20GHz stepping 09
Sep  6 22:43:29 fido kernel: [    0.167895] Performance Events: PEBS fmt1+, 16-deep LBR, SandyBridge events, Intel PMU driver.
Sep  6 22:43:29 fido kernel: [    0.168072] ... version:                3
Sep  6 22:43:29 fido kernel: [    0.168117] ... bit width:              48
Sep  6 22:43:29 fido kernel: [    0.168162] ... generic registers:      8
Sep  6 22:43:29 fido kernel: [    0.168207] ... value mask:             0000ffffffffffff
Sep  6 22:43:29 fido kernel: [    0.168255] ... max period:             000000007fffffff
Sep  6 22:43:29 fido kernel: [    0.168302] ... fixed-purpose events:   3
Sep  6 22:43:29 fido kernel: [    0.168347] ... event mask:             00000007000000ff
Sep  6 22:43:29 fido kernel: [    0.168480] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
Sep  6 22:43:29 fido kernel: [    0.168591] Booting Node   0, Processors  #1 #2 #3 Ok.
Sep  6 22:43:29 fido kernel: [    0.209075] Brought up 4 CPUs
Sep  6 22:43:29 fido kernel: [    0.209122] Total of 4 processors activated (25544.29 BogoMIPS).
Sep  6 22:43:29 fido kernel: [    0.211908] devtmpfs: initialized
Sep  6 22:43:29 fido kernel: [    0.212705] EVM: security.selinux
Sep  6 22:43:29 fido kernel: [    0.212750] EVM: security.SMACK64
Sep  6 22:43:29 fido kernel: [    0.212795] EVM: security.capability
Sep  6 22:43:29 fido kernel: [    0.212860] PM: Registering ACPI NVS region [mem 0xde08c000-0xde12bfff] (655360 bytes)
Sep  6 22:43:29 fido kernel: [    0.212930] PM: Registering ACPI NVS region [mem 0xde917000-0xde959fff] (274432 bytes)
Sep  6 22:43:29 fido kernel: [    0.218695] dummy: 
Sep  6 22:43:29 fido kernel: [    0.218764] RTC time: 20:42:53, date: 09/06/13
Sep  6 22:43:29 fido kernel: [    0.218830] NET: Registered protocol family 16
Sep  6 22:43:29 fido kernel: [    0.218933] Trying to unpack rootfs image as initramfs...
Sep  6 22:43:29 fido kernel: [    0.218999] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
Sep  6 22:43:29 fido kernel: [    0.219062] ACPI: bus type pci registered
Sep  6 22:43:29 fido kernel: [    0.219139] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
Sep  6 22:43:29 fido kernel: [    0.219204] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
Sep  6 22:43:29 fido kernel: [    0.224263] PCI: Using configuration type 1 for base access
Sep  6 22:43:29 fido kernel: [    0.224863] bio: create slab <bio-0> at 0
Sep  6 22:43:29 fido kernel: [    0.224952] ACPI: Added _OSI(Module Device)
Sep  6 22:43:29 fido kernel: [    0.224997] ACPI: Added _OSI(Processor Device)
Sep  6 22:43:29 fido kernel: [    0.225042] ACPI: Added _OSI(3.0 _SCP Extensions)
Sep  6 22:43:29 fido kernel: [    0.225088] ACPI: Added _OSI(Processor Aggregator Device)
Sep  6 22:43:29 fido kernel: [    0.226122] ACPI: EC: Look up EC in DSDT
Sep  6 22:43:29 fido kernel: [    0.227250] ACPI: Executed 1 blocks of module-level executable AML code
Sep  6 22:43:29 fido kernel: [    0.271962] ACPI: SSDT 00000000ddfaf018 0083B (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
Sep  6 22:43:29 fido kernel: [    0.272328] ACPI: Dynamic OEM Table Load:
Sep  6 22:43:29 fido kernel: [    0.272428] ACPI: SSDT           (null) 0083B (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
Sep  6 22:43:29 fido kernel: [    0.307732] ACPI: SSDT 00000000ddfb0a98 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
Sep  6 22:43:29 fido kernel: [    0.308117] ACPI: Dynamic OEM Table Load:
Sep  6 22:43:29 fido kernel: [    0.308218] ACPI: SSDT           (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
Sep  6 22:43:29 fido kernel: [    0.327590] ACPI: SSDT 00000000ddfb1c18 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
Sep  6 22:43:29 fido kernel: [    0.327955] ACPI: Dynamic OEM Table Load:
Sep  6 22:43:29 fido kernel: [    0.328055] ACPI: SSDT           (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
Sep  6 22:43:29 fido kernel: [    0.355872] ACPI: Interpreter enabled
Sep  6 22:43:29 fido kernel: [    0.355919] ACPI: (supports S0 S3 S4 S5)
Sep  6 22:43:29 fido kernel: [    0.356086] ACPI: Using IOAPIC for interrupt routing
Sep  6 22:43:29 fido kernel: [    0.359974] ACPI: No dock devices found.
Sep  6 22:43:29 fido kernel: [    0.360022] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Sep  6 22:43:29 fido kernel: [    0.360294] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
Sep  6 22:43:29 fido kernel: [    0.360617] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
Sep  6 22:43:29 fido kernel: [    0.360667] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
Sep  6 22:43:29 fido kernel: [    0.360716] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
Sep  6 22:43:29 fido kernel: [    0.360778] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000d3fff]
Sep  6 22:43:29 fido kernel: [    0.360839] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff]
Sep  6 22:43:29 fido kernel: [    0.360901] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff]
Sep  6 22:43:29 fido kernel: [    0.360963] pci_root PNP0A08:00: host bridge window [mem 0x000dc000-0x000dffff]
Sep  6 22:43:29 fido kernel: [    0.361024] pci_root PNP0A08:00: host bridge window [mem 0x000e0000-0x000e3fff]
Sep  6 22:43:29 fido kernel: [    0.361086] pci_root PNP0A08:00: host bridge window [mem 0x000e4000-0x000e7fff]
Sep  6 22:43:29 fido kernel: [    0.361148] pci_root PNP0A08:00: host bridge window [mem 0xe0000000-0xfeafffff]
Sep  6 22:43:29 fido kernel: [    0.361227] PCI host bridge to bus 0000:00
Sep  6 22:43:29 fido kernel: [    0.361273] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
Sep  6 22:43:29 fido kernel: [    0.361321] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
Sep  6 22:43:29 fido kernel: [    0.361369] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
Sep  6 22:43:29 fido kernel: [    0.361419] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000d3fff]
Sep  6 22:43:29 fido kernel: [    0.361468] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff]
Sep  6 22:43:29 fido kernel: [    0.361517] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff]
Sep  6 22:43:29 fido kernel: [    0.361566] pci_bus 0000:00: root bus resource [mem 0x000dc000-0x000dffff]
Sep  6 22:43:29 fido kernel: [    0.361615] pci_bus 0000:00: root bus resource [mem 0x000e0000-0x000e3fff]
Sep  6 22:43:29 fido kernel: [    0.361664] pci_bus 0000:00: root bus resource [mem 0x000e4000-0x000e7fff]
Sep  6 22:43:29 fido kernel: [    0.361714] pci_bus 0000:00: root bus resource [mem 0xe0000000-0xfeafffff]
Sep  6 22:43:29 fido kernel: [    0.361768] pci 0000:00:00.0: [8086:0150] type 00 class 0x060000
Sep  6 22:43:29 fido kernel: [    0.361795] pci 0000:00:01.0: [8086:0151] type 01 class 0x060400
Sep  6 22:43:29 fido kernel: [    0.361818] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
Sep  6 22:43:29 fido kernel: [    0.361854] pci 0000:00:14.0: [8086:1e31] type 00 class 0x0c0330
Sep  6 22:43:29 fido kernel: [    0.361875] pci 0000:00:14.0: reg 10: [mem 0xf7200000-0xf720ffff 64bit]
Sep  6 22:43:29 fido kernel: [    0.361942] pci 0000:00:14.0: PME# supported from D3hot D3cold
Sep  6 22:43:29 fido kernel: [    0.361963] pci 0000:00:16.0: [8086:1e3a] type 00 class 0x078000
Sep  6 22:43:29 fido kernel: [    0.361984] pci 0000:00:16.0: reg 10: [mem 0xf721a000-0xf721a00f 64bit]
Sep  6 22:43:29 fido kernel: [    0.362053] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
Sep  6 22:43:29 fido kernel: [    0.362083] pci 0000:00:1a.0: [8086:1e2d] type 00 class 0x0c0320
Sep  6 22:43:29 fido kernel: [    0.362102] pci 0000:00:1a.0: reg 10: [mem 0xf7218000-0xf72183ff]
Sep  6 22:43:29 fido kernel: [    0.362186] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
Sep  6 22:43:29 fido kernel: [    0.362209] pci 0000:00:1b.0: [8086:1e20] type 00 class 0x040300
Sep  6 22:43:29 fido kernel: [    0.362222] pci 0000:00:1b.0: reg 10: [mem 0xf7210000-0xf7213fff 64bit]
Sep  6 22:43:29 fido kernel: [    0.362285] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Sep  6 22:43:29 fido kernel: [    0.362309] pci 0000:00:1c.0: [8086:1e10] type 01 class 0x060400
Sep  6 22:43:29 fido kernel: [    0.362438] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Sep  6 22:43:29 fido kernel: [    0.362472] pci 0000:00:1c.5: [8086:1e1a] type 01 class 0x060400
Sep  6 22:43:29 fido kernel: [    0.362545] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
Sep  6 22:43:29 fido kernel: [    0.362569] pci 0000:00:1c.7: [8086:1e1e] type 01 class 0x060400
Sep  6 22:43:29 fido kernel: [    0.362643] pci 0000:00:1c.7: PME# supported from D0 D3hot D3cold
Sep  6 22:43:29 fido kernel: [    0.362668] pci 0000:00:1d.0: [8086:1e26] type 00 class 0x0c0320
Sep  6 22:43:29 fido kernel: [    0.362687] pci 0000:00:1d.0: reg 10: [mem 0xf7217000-0xf72173ff]
Sep  6 22:43:29 fido kernel: [    0.362772] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
Sep  6 22:43:29 fido kernel: [    0.362794] pci 0000:00:1f.0: [8086:1e4a] type 00 class 0x060100
Sep  6 22:43:29 fido kernel: [    0.362910] pci 0000:00:1f.2: [8086:1e02] type 00 class 0x010601
Sep  6 22:43:29 fido kernel: [    0.362926] pci 0000:00:1f.2: reg 10: [io  0xf070-0xf077]
Sep  6 22:43:29 fido kernel: [    0.362933] pci 0000:00:1f.2: reg 14: [io  0xf060-0xf063]
Sep  6 22:43:29 fido kernel: [    0.362940] pci 0000:00:1f.2: reg 18: [io  0xf050-0xf057]
Sep  6 22:43:29 fido kernel: [    0.362946] pci 0000:00:1f.2: reg 1c: [io  0xf040-0xf043]
Sep  6 22:43:29 fido kernel: [    0.362953] pci 0000:00:1f.2: reg 20: [io  0xf020-0xf03f]
Sep  6 22:43:29 fido kernel: [    0.362960] pci 0000:00:1f.2: reg 24: [mem 0xf7216000-0xf72167ff]
Sep  6 22:43:29 fido kernel: [    0.363000] pci 0000:00:1f.2: PME# supported from D3hot
Sep  6 22:43:29 fido kernel: [    0.363015] pci 0000:00:1f.3: [8086:1e22] type 00 class 0x0c0500
Sep  6 22:43:29 fido kernel: [    0.363028] pci 0000:00:1f.3: reg 10: [mem 0xf7215000-0xf72150ff 64bit]
Sep  6 22:43:29 fido kernel: [    0.363047] pci 0000:00:1f.3: reg 20: [io  0xf000-0xf01f]
Sep  6 22:43:29 fido kernel: [    0.363093] pci 0000:01:00.0: [10de:11c0] type 00 class 0x030000
Sep  6 22:43:29 fido kernel: [    0.363101] pci 0000:01:00.0: reg 10: [mem 0xf6000000-0xf6ffffff]
Sep  6 22:43:29 fido kernel: [    0.363110] pci 0000:01:00.0: reg 14: [mem 0xe8000000-0xefffffff 64bit pref]
Sep  6 22:43:29 fido kernel: [    0.363118] pci 0000:01:00.0: reg 1c: [mem 0xf0000000-0xf1ffffff 64bit pref]
Sep  6 22:43:29 fido kernel: [    0.363124] pci 0000:01:00.0: reg 24: [io  0xe000-0xe07f]
Sep  6 22:43:29 fido kernel: [    0.363130] pci 0000:01:00.0: reg 30: [mem 0xf7000000-0xf707ffff pref]
Sep  6 22:43:29 fido kernel: [    0.363178] pci 0000:01:00.1: [10de:0e0b] type 00 class 0x040300
Sep  6 22:43:29 fido kernel: [    0.363185] pci 0000:01:00.1: reg 10: [mem 0xf7080000-0xf7083fff]
Sep  6 22:43:29 fido kernel: [    0.367442] pci 0000:00:01.0: PCI bridge to [bus 01-01]
Sep  6 22:43:29 fido kernel: [    0.367490] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
Sep  6 22:43:29 fido kernel: [    0.367492] pci 0000:00:01.0:   bridge window [mem 0xf6000000-0xf70fffff]
Sep  6 22:43:29 fido kernel: [    0.367494] pci 0000:00:01.0:   bridge window [mem 0xe8000000-0xf1ffffff 64bit pref]
Sep  6 22:43:29 fido kernel: [    0.367563] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
Sep  6 22:43:29 fido kernel: [    0.367684] pci 0000:03:00.0: [10ec:8168] type 00 class 0x020000
Sep  6 22:43:29 fido kernel: [    0.367703] pci 0000:03:00.0: reg 10: [io  0xd000-0xd0ff]
Sep  6 22:43:29 fido kernel: [    0.367736] pci 0000:03:00.0: reg 18: [mem 0xf2104000-0xf2104fff 64bit pref]
Sep  6 22:43:29 fido kernel: [    0.367756] pci 0000:03:00.0: reg 20: [mem 0xf2100000-0xf2103fff 64bit pref]
Sep  6 22:43:29 fido kernel: [    0.367846] pci 0000:03:00.0: supports D1 D2
Sep  6 22:43:29 fido kernel: [    0.367847] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Sep  6 22:43:29 fido kernel: [    0.375428] pci 0000:00:1c.5: PCI bridge to [bus 03-03]
Sep  6 22:43:29 fido kernel: [    0.375477] pci 0000:00:1c.5:   bridge window [io  0xd000-0xdfff]
Sep  6 22:43:29 fido kernel: [    0.375484] pci 0000:00:1c.5:   bridge window [mem 0xf2100000-0xf21fffff 64bit pref]
Sep  6 22:43:29 fido kernel: [    0.375544] pci 0000:04:00.0: [1b21:0612] type 00 class 0x010601
Sep  6 22:43:29 fido kernel: [    0.375562] pci 0000:04:00.0: reg 10: [io  0xc050-0xc057]
Sep  6 22:43:29 fido kernel: [    0.375574] pci 0000:04:00.0: reg 14: [io  0xc040-0xc043]
Sep  6 22:43:29 fido kernel: [    0.375587] pci 0000:04:00.0: reg 18: [io  0xc030-0xc037]
Sep  6 22:43:29 fido kernel: [    0.375599] pci 0000:04:00.0: reg 1c: [io  0xc020-0xc023]
Sep  6 22:43:29 fido kernel: [    0.375612] pci 0000:04:00.0: reg 20: [io  0xc000-0xc01f]
Sep  6 22:43:29 fido kernel: [    0.375625] pci 0000:04:00.0: reg 24: [mem 0xf7100000-0xf71001ff]
Sep  6 22:43:29 fido kernel: [    0.383406] pci 0000:00:1c.7: PCI bridge to [bus 04-04]
Sep  6 22:43:29 fido kernel: [    0.383456] pci 0000:00:1c.7:   bridge window [io  0xc000-0xcfff]
Sep  6 22:43:29 fido kernel: [    0.383459] pci 0000:00:1c.7:   bridge window [mem 0xf7100000-0xf71fffff]
Sep  6 22:43:29 fido kernel: [    0.383482] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Sep  6 22:43:29 fido kernel: [    0.383569] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
Sep  6 22:43:29 fido kernel: [    0.383592] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
Sep  6 22:43:29 fido kernel: [    0.383612] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP08._PRT]
Sep  6 22:43:29 fido kernel: [    0.383630] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEG0._PRT]
Sep  6 22:43:29 fido kernel: [    0.383718]  pci0000:00: Requesting ACPI _OSC control (0x1d)
Sep  6 22:43:29 fido kernel: [    0.383901]  pci0000:00: ACPI _OSC control (0x18) granted
Sep  6 22:43:29 fido kernel: [    0.386397] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 10 *11 12 14 15)
Sep  6 22:43:29 fido kernel: [    0.386773] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 *10 11 12 14 15)
Sep  6 22:43:29 fido kernel: [    0.387145] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 10 11 12 14 15)
Sep  6 22:43:29 fido kernel: [    0.387523] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 6 10 11 12 14 15)
Sep  6 22:43:29 fido kernel: [    0.387896] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
Sep  6 22:43:29 fido kernel: [    0.388334] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
Sep  6 22:43:29 fido kernel: [    0.388772] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 10 *11 12 14 15)
Sep  6 22:43:29 fido kernel: [    0.389143] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 *10 11 12 14 15)
Sep  6 22:43:29 fido kernel: [    0.389547] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
Sep  6 22:43:29 fido kernel: [    0.389611] vgaarb: loaded
Sep  6 22:43:29 fido kernel: [    0.389654] vgaarb: bridge control possible 0000:01:00.0
Sep  6 22:43:29 fido kernel: [    0.389794] SCSI subsystem initialized
Sep  6 22:43:29 fido kernel: [    0.389864] libata version 3.00 loaded.
Sep  6 22:43:29 fido kernel: [    0.389876] ACPI: bus type usb registered
Sep  6 22:43:29 fido kernel: [    0.389932] usbcore: registered new interface driver usbfs
Sep  6 22:43:29 fido kernel: [    0.389983] usbcore: registered new interface driver hub
Sep  6 22:43:29 fido kernel: [    0.390039] usbcore: registered new device driver usb
Sep  6 22:43:29 fido kernel: [    0.390124] PCI: Using ACPI for IRQ routing
Sep  6 22:43:29 fido kernel: [    0.391358] Freeing initrd memory: 15312k freed
Sep  6 22:43:29 fido kernel: [    0.391640] PCI: pci_cache_line_size set to 64 bytes
Sep  6 22:43:29 fido kernel: [    0.391693] e820: reserve RAM buffer [mem 0x0009d800-0x0009ffff]
Sep  6 22:43:29 fido kernel: [    0.391695] e820: reserve RAM buffer [mem 0xdd5b2000-0xdfffffff]
Sep  6 22:43:29 fido kernel: [    0.391696] e820: reserve RAM buffer [mem 0xde08c000-0xdfffffff]
Sep  6 22:43:29 fido kernel: [    0.391697] e820: reserve RAM buffer [mem 0xde917000-0xdfffffff]
Sep  6 22:43:29 fido kernel: [    0.391698] e820: reserve RAM buffer [mem 0xdf3e6000-0xdfffffff]
Sep  6 22:43:29 fido kernel: [    0.391699] e820: reserve RAM buffer [mem 0xdf800000-0xdfffffff]
Sep  6 22:43:29 fido kernel: [    0.391700] e820: reserve RAM buffer [mem 0x21f000000-0x21fffffff]
Sep  6 22:43:29 fido kernel: [    0.391767] NetLabel: Initializing
Sep  6 22:43:29 fido kernel: [    0.391811] NetLabel:  domain hash size = 128
Sep  6 22:43:29 fido kernel: [    0.391856] NetLabel:  protocols = UNLABELED CIPSOv4
Sep  6 22:43:29 fido kernel: [    0.391909] NetLabel:  unlabeled traffic allowed by default
Sep  6 22:43:29 fido kernel: [    0.391993] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
Sep  6 22:43:29 fido kernel: [    0.392289] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
Sep  6 22:43:29 fido kernel: [    0.394341] Switching to clocksource hpet
Sep  6 22:43:29 fido kernel: [    0.398034] AppArmor: AppArmor Filesystem Enabled
Sep  6 22:43:29 fido kernel: [    0.398093] pnp: PnP ACPI init
Sep  6 22:43:29 fido kernel: [    0.398144] ACPI: bus type pnp registered
Sep  6 22:43:29 fido kernel: [    0.398361] pnp 00:00: [bus 00-3e]
Sep  6 22:43:29 fido kernel: [    0.398363] pnp 00:00: [io  0x0000-0x0cf7 window]
Sep  6 22:43:29 fido kernel: [    0.398372] pnp 00:00: [io  0x0cf8-0x0cff]
Sep  6 22:43:29 fido kernel: [    0.398373] pnp 00:00: [io  0x0d00-0xffff window]
Sep  6 22:43:29 fido kernel: [    0.398375] pnp 00:00: [mem 0x000a0000-0x000bffff window]
Sep  6 22:43:29 fido kernel: [    0.398376] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
Sep  6 22:43:29 fido kernel: [    0.398377] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
Sep  6 22:43:29 fido kernel: [    0.398378] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
Sep  6 22:43:29 fido kernel: [    0.398379] pnp 00:00: [mem 0x000cc000-0x000cffff window]
Sep  6 22:43:29 fido kernel: [    0.398380] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
Sep  6 22:43:29 fido kernel: [    0.398382] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
Sep  6 22:43:29 fido kernel: [    0.398383] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
Sep  6 22:43:29 fido kernel: [    0.398385] pnp 00:00: [mem 0x000dc000-0x000dffff window]
Sep  6 22:43:29 fido kernel: [    0.398386] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
Sep  6 22:43:29 fido kernel: [    0.398387] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
Sep  6 22:43:29 fido kernel: [    0.398388] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
Sep  6 22:43:29 fido kernel: [    0.398390] pnp 00:00: [mem 0x000ec000-0x000effff window]
Sep  6 22:43:29 fido kernel: [    0.398391] pnp 00:00: [mem 0x000f0000-0x000fffff window]
Sep  6 22:43:29 fido kernel: [    0.398392] pnp 00:00: [mem 0xe0000000-0xfeafffff window]
Sep  6 22:43:29 fido kernel: [    0.398393] pnp 00:00: [mem 0x00010000-0x0001ffff window]
Sep  6 22:43:29 fido kernel: [    0.398431] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
Sep  6 22:43:29 fido kernel: [    0.398447] pnp 00:01: [mem 0xfed40000-0xfed44fff]
Sep  6 22:43:29 fido kernel: [    0.398469] system 00:01: [mem 0xfed40000-0xfed44fff] has been reserved
Sep  6 22:43:29 fido kernel: [    0.398519] system 00:01: Plug and Play ACPI device, IDs PNP0c01 (active)
Sep  6 22:43:29 fido kernel: [    0.398527] pnp 00:02: [io  0x0000-0x001f]
Sep  6 22:43:29 fido kernel: [    0.398528] pnp 00:02: [io  0x0081-0x0091]
Sep  6 22:43:29 fido kernel: [    0.398529] pnp 00:02: [io  0x0093-0x009f]
Sep  6 22:43:29 fido kernel: [    0.398530] pnp 00:02: [io  0x00c0-0x00df]
Sep  6 22:43:29 fido kernel: [    0.398532] pnp 00:02: [dma 4]
Sep  6 22:43:29 fido kernel: [    0.398542] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
Sep  6 22:43:29 fido kernel: [    0.398546] pnp 00:03: [mem 0xff000000-0xffffffff]
Sep  6 22:43:29 fido kernel: [    0.398557] pnp 00:03: Plug and Play ACPI device, IDs INT0800 (active)
Sep  6 22:43:29 fido kernel: [    0.398607] pnp 00:04: [mem 0xfed00000-0xfed003ff]
Sep  6 22:43:29 fido kernel: [    0.398618] pnp 00:04: Plug and Play ACPI device, IDs PNP0103 (active)
Sep  6 22:43:29 fido kernel: [    0.398625] pnp 00:05: [io  0x002e-0x002f]
Sep  6 22:43:29 fido kernel: [    0.398626] pnp 00:05: [io  0x004e-0x004f]
Sep  6 22:43:29 fido kernel: [    0.398627] pnp 00:05: [io  0x0061]
Sep  6 22:43:29 fido kernel: [    0.398628] pnp 00:05: [io  0x0063]
Sep  6 22:43:29 fido kernel: [    0.398629] pnp 00:05: [io  0x0065]
Sep  6 22:43:29 fido kernel: [    0.398630] pnp 00:05: [io  0x0067]
Sep  6 22:43:29 fido kernel: [    0.398631] pnp 00:05: [io  0x0070]
Sep  6 22:43:29 fido kernel: [    0.398632] pnp 00:05: [io  0x0080]
Sep  6 22:43:29 fido kernel: [    0.398633] pnp 00:05: [io  0x0092]
Sep  6 22:43:29 fido kernel: [    0.398634] pnp 00:05: [io  0x00b2-0x00b3]
Sep  6 22:43:29 fido kernel: [    0.398635] pnp 00:05: [io  0x0680-0x069f]
Sep  6 22:43:29 fido kernel: [    0.398636] pnp 00:05: [io  0x1000-0x100f]
Sep  6 22:43:29 fido kernel: [    0.398637] pnp 00:05: [io  0xffff]
Sep  6 22:43:29 fido kernel: [    0.398638] pnp 00:05: [io  0xffff]
Sep  6 22:43:29 fido kernel: [    0.398639] pnp 00:05: [io  0x0400-0x0453]
Sep  6 22:43:29 fido kernel: [    0.398640] pnp 00:05: [io  0x0458-0x047f]
Sep  6 22:43:29 fido kernel: [    0.398641] pnp 00:05: [io  0x0500-0x057f]
Sep  6 22:43:29 fido kernel: [    0.398642] pnp 00:05: [io  0x164e-0x164f]
Sep  6 22:43:29 fido kernel: [    0.398666] system 00:05: [io  0x0680-0x069f] has been reserved
Sep  6 22:43:29 fido kernel: [    0.398715] system 00:05: [io  0x1000-0x100f] has been reserved
Sep  6 22:43:29 fido kernel: [    0.398763] system 00:05: [io  0xffff] has been reserved
Sep  6 22:43:29 fido kernel: [    0.398810] system 00:05: [io  0xffff] has been reserved
Sep  6 22:43:29 fido kernel: [    0.398857] system 00:05: [io  0x0400-0x0453] has been reserved
Sep  6 22:43:29 fido kernel: [    0.398905] system 00:05: [io  0x0458-0x047f] has been reserved
Sep  6 22:43:29 fido kernel: [    0.398953] system 00:05: [io  0x0500-0x057f] has been reserved
Sep  6 22:43:29 fido kernel: [    0.399001] system 00:05: [io  0x164e-0x164f] has been reserved
Sep  6 22:43:29 fido kernel: [    0.399049] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
Sep  6 22:43:29 fido kernel: [    0.399054] pnp 00:06: [io  0x0070-0x0077]
Sep  6 22:43:29 fido kernel: [    0.399061] pnp 00:06: [irq 8]
Sep  6 22:43:29 fido kernel: [    0.399073] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
Sep  6 22:43:29 fido kernel: [    0.399089] pnp 00:07: [io  0x0454-0x0457]
Sep  6 22:43:29 fido kernel: [    0.399108] system 00:07: [io  0x0454-0x0457] has been reserved
Sep  6 22:43:29 fido kernel: [    0.399157] system 00:07: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
Sep  6 22:43:29 fido kernel: [    0.399191] pnp 00:08: [io  0x0000-0xffffffffffffffff disabled]
Sep  6 22:43:29 fido kernel: [    0.399192] pnp 00:08: [io  0x0290-0x029f]
Sep  6 22:43:29 fido kernel: [    0.399193] pnp 00:08: [io  0x0000-0xffffffffffffffff disabled]
Sep  6 22:43:29 fido kernel: [    0.399212] system 00:08: [io  0x0290-0x029f] has been reserved
Sep  6 22:43:29 fido kernel: [    0.399261] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
Sep  6 22:43:29 fido kernel: [    0.399463] pnp 00:09: [io  0x0378-0x037f]
Sep  6 22:43:29 fido kernel: [    0.399465] pnp 00:09: [io  0x0778-0x077f]
Sep  6 22:43:29 fido kernel: [    0.399470] pnp 00:09: [irq 5]
Sep  6 22:43:29 fido kernel: [    0.399471] pnp 00:09: [dma 3]
Sep  6 22:43:29 fido kernel: [    0.399543] pnp 00:09: Plug and Play ACPI device, IDs PNP0401 (active)
Sep  6 22:43:29 fido kernel: [    0.399660] pnp 00:0a: [io  0x0010-0x001f]
Sep  6 22:43:29 fido kernel: [    0.399661] pnp 00:0a: [io  0x0022-0x003f]
Sep  6 22:43:29 fido kernel: [    0.399662] pnp 00:0a: [io  0x0044-0x005f]
Sep  6 22:43:29 fido kernel: [    0.399663] pnp 00:0a: [io  0x0062-0x0063]
Sep  6 22:43:29 fido kernel: [    0.399664] pnp 00:0a: [io  0x0065-0x006f]
Sep  6 22:43:29 fido kernel: [    0.399665] pnp 00:0a: [io  0x0072-0x007f]
Sep  6 22:43:29 fido kernel: [    0.399666] pnp 00:0a: [io  0x0080]
Sep  6 22:43:29 fido kernel: [    0.399667] pnp 00:0a: [io  0x0084-0x0086]
Sep  6 22:43:29 fido kernel: [    0.399668] pnp 00:0a: [io  0x0088]
Sep  6 22:43:29 fido kernel: [    0.399669] pnp 00:0a: [io  0x008c-0x008e]
Sep  6 22:43:29 fido kernel: [    0.399670] pnp 00:0a: [io  0x0090-0x009f]
Sep  6 22:43:29 fido kernel: [    0.399671] pnp 00:0a: [io  0x00a2-0x00bf]
Sep  6 22:43:29 fido kernel: [    0.399672] pnp 00:0a: [io  0x00e0-0x00ef]
Sep  6 22:43:29 fido kernel: [    0.399673] pnp 00:0a: [io  0x04d0-0x04d1]
Sep  6 22:43:29 fido kernel: [    0.399696] system 00:0a: [io  0x04d0-0x04d1] has been reserved
Sep  6 22:43:29 fido kernel: [    0.399746] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
Sep  6 22:43:29 fido kernel: [    0.399750] pnp 00:0b: [io  0x00f0-0x00ff]
Sep  6 22:43:29 fido kernel: [    0.399754] pnp 00:0b: [irq 13]
Sep  6 22:43:29 fido kernel: [    0.399767] pnp 00:0b: Plug and Play ACPI device, IDs PNP0c04 (active)
Sep  6 22:43:29 fido kernel: [    0.399779] pnp 00:0c: [io  0x0060]
Sep  6 22:43:29 fido kernel: [    0.399781] pnp 00:0c: [io  0x0064]
Sep  6 22:43:29 fido kernel: [    0.399784] pnp 00:0c: [irq 1]
Sep  6 22:43:29 fido kernel: [    0.399800] pnp 00:0c: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
Sep  6 22:43:29 fido kernel: [    0.399892] pnp 00:0d: [io  0x03f8-0x03ff]
Sep  6 22:43:29 fido kernel: [    0.399896] pnp 00:0d: [irq 4]
Sep  6 22:43:29 fido kernel: [    0.399897] pnp 00:0d: [dma 0 disabled]
Sep  6 22:43:29 fido kernel: [    0.399929] pnp 00:0d: Plug and Play ACPI device, IDs PNP0501 (active)
Sep  6 22:43:29 fido kernel: [    0.400063] pnp 00:0e: [mem 0xfed1c000-0xfed1ffff]
Sep  6 22:43:29 fido kernel: [    0.400065] pnp 00:0e: [mem 0xfed10000-0xfed17fff]
Sep  6 22:43:29 fido kernel: [    0.400066] pnp 00:0e: [mem 0xfed18000-0xfed18fff]
Sep  6 22:43:29 fido kernel: [    0.400067] pnp 00:0e: [mem 0xfed19000-0xfed19fff]
Sep  6 22:43:29 fido kernel: [    0.400068] pnp 00:0e: [mem 0xf8000000-0xfbffffff]
Sep  6 22:43:29 fido kernel: [    0.400069] pnp 00:0e: [mem 0xfed20000-0xfed3ffff]
Sep  6 22:43:29 fido kernel: [    0.400070] pnp 00:0e: [mem 0xfed90000-0xfed93fff]
Sep  6 22:43:29 fido kernel: [    0.400071] pnp 00:0e: [mem 0xfed45000-0xfed8ffff]
Sep  6 22:43:29 fido kernel: [    0.400072] pnp 00:0e: [mem 0xff000000-0xffffffff]
Sep  6 22:43:29 fido kernel: [    0.400073] pnp 00:0e: [mem 0xfee00000-0xfeefffff]
Sep  6 22:43:29 fido kernel: [    0.400074] pnp 00:0e: [mem 0xe0000000-0xe0000fff]
Sep  6 22:43:29 fido kernel: [    0.400106] system 00:0e: [mem 0xfed1c000-0xfed1ffff] has been reserved
Sep  6 22:43:29 fido kernel: [    0.400155] system 00:0e: [mem 0xfed10000-0xfed17fff] has been reserved
Sep  6 22:43:29 fido kernel: [    0.400205] system 00:0e: [mem 0xfed18000-0xfed18fff] has been reserved
Sep  6 22:43:29 fido kernel: [    0.400254] system 00:0e: [mem 0xfed19000-0xfed19fff] has been reserved
Sep  6 22:43:29 fido kernel: [    0.400303] system 00:0e: [mem 0xf8000000-0xfbffffff] has been reserved
Sep  6 22:43:29 fido kernel: [    0.400352] system 00:0e: [mem 0xfed20000-0xfed3ffff] has been reserved
Sep  6 22:43:29 fido kernel: [    0.400401] system 00:0e: [mem 0xfed90000-0xfed93fff] has been reserved
Sep  6 22:43:29 fido kernel: [    0.400450] system 00:0e: [mem 0xfed45000-0xfed8ffff] has been reserved
Sep  6 22:43:29 fido kernel: [    0.400499] system 00:0e: [mem 0xff000000-0xffffffff] has been reserved
Sep  6 22:43:29 fido kernel: [    0.400548] system 00:0e: [mem 0xfee00000-0xfeefffff] could not be reserved
Sep  6 22:43:29 fido kernel: [    0.400597] system 00:0e: [mem 0xe0000000-0xe0000fff] has been reserved
Sep  6 22:43:29 fido kernel: [    0.400647] system 00:0e: Plug and Play ACPI device, IDs PNP0c02 (active)
Sep  6 22:43:29 fido kernel: [    0.400737] pnp: PnP ACPI: found 15 devices
Sep  6 22:43:29 fido kernel: [    0.400782] ACPI: ACPI bus type pnp unregistered
Sep  6 22:43:29 fido kernel: [    0.406442] pci 0000:00:01.0: PCI bridge to [bus 01-01]
Sep  6 22:43:29 fido kernel: [    0.406490] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
Sep  6 22:43:29 fido kernel: [    0.406539] pci 0000:00:01.0:   bridge window [mem 0xf6000000-0xf70fffff]
Sep  6 22:43:29 fido kernel: [    0.406589] pci 0000:00:01.0:   bridge window [mem 0xe8000000-0xf1ffffff 64bit pref]
Sep  6 22:43:29 fido kernel: [    0.406653] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
Sep  6 22:43:29 fido kernel: [    0.406715] pci 0000:00:1c.5: PCI bridge to [bus 03-03]
Sep  6 22:43:29 fido kernel: [    0.406763] pci 0000:00:1c.5:   bridge window [io  0xd000-0xdfff]
Sep  6 22:43:29 fido kernel: [    0.406816] pci 0000:00:1c.5:   bridge window [mem 0xf2100000-0xf21fffff 64bit pref]
Sep  6 22:43:29 fido kernel: [    0.406883] pci 0000:00:1c.7: PCI bridge to [bus 04-04]
Sep  6 22:43:29 fido kernel: [    0.406930] pci 0000:00:1c.7:   bridge window [io  0xc000-0xcfff]
Sep  6 22:43:29 fido kernel: [    0.406981] pci 0000:00:1c.7:   bridge window [mem 0xf7100000-0xf71fffff]
Sep  6 22:43:29 fido kernel: [    0.407059] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
Sep  6 22:43:29 fido kernel: [    0.407061] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
Sep  6 22:43:29 fido kernel: [    0.407062] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
Sep  6 22:43:29 fido kernel: [    0.407063] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000d3fff]
Sep  6 22:43:29 fido kernel: [    0.407064] pci_bus 0000:00: resource 8 [mem 0x000d4000-0x000d7fff]
Sep  6 22:43:29 fido kernel: [    0.407066] pci_bus 0000:00: resource 9 [mem 0x000d8000-0x000dbfff]
Sep  6 22:43:29 fido kernel: [    0.407067] pci_bus 0000:00: resource 10 [mem 0x000dc000-0x000dffff]
Sep  6 22:43:29 fido kernel: [    0.407068] pci_bus 0000:00: resource 11 [mem 0x000e0000-0x000e3fff]
Sep  6 22:43:29 fido kernel: [    0.407069] pci_bus 0000:00: resource 12 [mem 0x000e4000-0x000e7fff]
Sep  6 22:43:29 fido kernel: [    0.407070] pci_bus 0000:00: resource 13 [mem 0xe0000000-0xfeafffff]
Sep  6 22:43:29 fido kernel: [    0.407072] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
Sep  6 22:43:29 fido kernel: [    0.407073] pci_bus 0000:01: resource 1 [mem 0xf6000000-0xf70fffff]
Sep  6 22:43:29 fido kernel: [    0.407074] pci_bus 0000:01: resource 2 [mem 0xe8000000-0xf1ffffff 64bit pref]
Sep  6 22:43:29 fido kernel: [    0.407076] pci_bus 0000:03: resource 0 [io  0xd000-0xdfff]
Sep  6 22:43:29 fido kernel: [    0.407077] pci_bus 0000:03: resource 2 [mem 0xf2100000-0xf21fffff 64bit pref]
Sep  6 22:43:29 fido kernel: [    0.407078] pci_bus 0000:04: resource 0 [io  0xc000-0xcfff]
Sep  6 22:43:29 fido kernel: [    0.407079] pci_bus 0000:04: resource 1 [mem 0xf7100000-0xf71fffff]
Sep  6 22:43:29 fido kernel: [    0.407098] NET: Registered protocol family 2
Sep  6 22:43:29 fido kernel: [    0.407250] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
Sep  6 22:43:29 fido kernel: [    0.407762] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
Sep  6 22:43:29 fido kernel: [    0.408746] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Sep  6 22:43:29 fido kernel: [    0.408904] TCP: Hash tables configured (established 524288 bind 65536)
Sep  6 22:43:29 fido kernel: [    0.408953] TCP: reno registered
Sep  6 22:43:29 fido kernel: [    0.409006] UDP hash table entries: 4096 (order: 5, 131072 bytes)
Sep  6 22:43:29 fido kernel: [    0.409074] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
Sep  6 22:43:29 fido kernel: [    0.409171] NET: Registered protocol family 1
Sep  6 22:43:29 fido kernel: [    0.446298] pci 0000:01:00.0: Boot video device
Sep  6 22:43:29 fido kernel: [    0.446318] PCI: CLS 64 bytes, default 64
Sep  6 22:43:29 fido kernel: [    0.446320] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
Sep  6 22:43:29 fido kernel: [    0.446380] software IO TLB [mem 0xd95b2000-0xdd5b1fff] (64MB) mapped at [ffff8800d95b2000-ffff8800dd5b1fff]
Sep  6 22:43:29 fido kernel: [    0.446728] audit: initializing netlink socket (disabled)
Sep  6 22:43:29 fido kernel: [    0.446779] type=2000 audit(1378500173.336:1): initialized
Sep  6 22:43:29 fido kernel: [    0.463961] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Sep  6 22:43:29 fido kernel: [    0.465102] VFS: Disk quotas dquot_6.5.2
Sep  6 22:43:29 fido kernel: [    0.465169] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Sep  6 22:43:29 fido kernel: [    0.465465] fuse init (API version 7.19)
Sep  6 22:43:29 fido kernel: [    0.465551] msgmni has been set to 15871
Sep  6 22:43:29 fido kernel: [    0.465797] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
Sep  6 22:43:29 fido kernel: [    0.465874] io scheduler noop registered
Sep  6 22:43:29 fido kernel: [    0.465919] io scheduler deadline registered (default)
Sep  6 22:43:29 fido kernel: [    0.465978] io scheduler cfq registered
Sep  6 22:43:29 fido kernel: [    0.466082] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
Sep  6 22:43:29 fido kernel: [    0.466275] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Sep  6 22:43:29 fido kernel: [    0.466330] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Sep  6 22:43:29 fido kernel: [    0.466403] intel_idle: MWAIT substates: 0x1120
Sep  6 22:43:29 fido kernel: [    0.466404] intel_idle: v0.4 model 0x3A
Sep  6 22:43:29 fido kernel: [    0.466405] intel_idle: lapic_timer_reliable_states 0xffffffff
Sep  6 22:43:29 fido kernel: [    0.466457] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
Sep  6 22:43:29 fido kernel: [    0.466522] ACPI: Power Button [PWRB]
Sep  6 22:43:29 fido kernel: [    0.466586] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Sep  6 22:43:29 fido kernel: [    0.466648] ACPI: Power Button [PWRF]
Sep  6 22:43:29 fido kernel: [    0.466750] ACPI: Requesting acpi_cpufreq
Sep  6 22:43:29 fido kernel: [    0.469244] GHES: HEST is not enabled!
Sep  6 22:43:29 fido kernel: [    0.474255] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Sep  6 22:43:29 fido kernel: [    0.494660] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Sep  6 22:43:29 fido kernel: [    0.515655] 00:0d: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Sep  6 22:43:29 fido kernel: [    0.515856] Linux agpgart interface v0.103
Sep  6 22:43:29 fido kernel: [    0.516579] brd: module loaded
Sep  6 22:43:29 fido kernel: [    0.516972] loop: module loaded
Sep  6 22:43:29 fido kernel: [    0.517190] Fixed MDIO Bus: probed
Sep  6 22:43:29 fido kernel: [    0.517254] tun: Universal TUN/TAP device driver, 1.6
Sep  6 22:43:29 fido kernel: [    0.517300] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Sep  6 22:43:29 fido kernel: [    0.517368] PPP generic driver version 2.4.2
Sep  6 22:43:29 fido kernel: [    0.517441] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Sep  6 22:43:29 fido kernel: [    0.517514] ehci_hcd 0000:00:1a.0: setting latency timer to 64
Sep  6 22:43:29 fido kernel: [    0.517516] ehci_hcd 0000:00:1a.0: EHCI Host Controller
Sep  6 22:43:29 fido kernel: [    0.517566] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
Sep  6 22:43:29 fido kernel: [    0.517646] ehci_hcd 0000:00:1a.0: debug port 2
Sep  6 22:43:29 fido kernel: [    0.521553] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
Sep  6 22:43:29 fido kernel: [    0.521564] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xf7218000
Sep  6 22:43:29 fido kernel: [    0.530080] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
Sep  6 22:43:29 fido kernel: [    0.530151] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
Sep  6 22:43:29 fido kernel: [    0.530211] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Sep  6 22:43:29 fido kernel: [    0.530272] usb usb1: Product: EHCI Host Controller
Sep  6 22:43:29 fido kernel: [    0.530318] usb usb1: Manufacturer: Linux 3.5.0-39-generic ehci_hcd
Sep  6 22:43:29 fido kernel: [    0.530367] usb usb1: SerialNumber: 0000:00:1a.0
Sep  6 22:43:29 fido kernel: [    0.530473] hub 1-0:1.0: USB hub found
Sep  6 22:43:29 fido kernel: [    0.530519] hub 1-0:1.0: 2 ports detected
Sep  6 22:43:29 fido kernel: [    0.530603] ehci_hcd 0000:00:1d.0: setting latency timer to 64
Sep  6 22:43:29 fido kernel: [    0.530605] ehci_hcd 0000:00:1d.0: EHCI Host Controller
Sep  6 22:43:29 fido kernel: [    0.530654] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
Sep  6 22:43:29 fido kernel: [    0.530731] ehci_hcd 0000:00:1d.0: debug port 2
Sep  6 22:43:29 fido kernel: [    0.534646] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
Sep  6 22:43:29 fido kernel: [    0.534655] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xf7217000
Sep  6 22:43:29 fido kernel: [    0.546045] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
Sep  6 22:43:29 fido kernel: [    0.546111] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
Sep  6 22:43:29 fido kernel: [    0.546171] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Sep  6 22:43:29 fido kernel: [    0.546232] usb usb2: Product: EHCI Host Controller
Sep  6 22:43:29 fido kernel: [    0.546279] usb usb2: Manufacturer: Linux 3.5.0-39-generic ehci_hcd
Sep  6 22:43:29 fido kernel: [    0.546327] usb usb2: SerialNumber: 0000:00:1d.0
Sep  6 22:43:29 fido kernel: [    0.546426] hub 2-0:1.0: USB hub found
Sep  6 22:43:29 fido kernel: [    0.546471] hub 2-0:1.0: 2 ports detected
Sep  6 22:43:29 fido kernel: [    0.546544] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Sep  6 22:43:29 fido kernel: [    0.546599] uhci_hcd: USB Universal Host Controller Interface driver
Sep  6 22:43:29 fido kernel: [    0.546672] xhci_hcd 0000:00:14.0: setting latency timer to 64
Sep  6 22:43:29 fido kernel: [    0.546675] xhci_hcd 0000:00:14.0: xHCI Host Controller
Sep  6 22:43:29 fido kernel: [    0.546723] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 3
Sep  6 22:43:29 fido kernel: [    0.546855] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
Sep  6 22:43:29 fido kernel: [    0.546891] xhci_hcd 0000:00:14.0: irq 41 for MSI/MSI-X
Sep  6 22:43:29 fido kernel: [    0.546927] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
Sep  6 22:43:29 fido kernel: [    0.546977] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Sep  6 22:43:29 fido kernel: [    0.547039] usb usb3: Product: xHCI Host Controller
Sep  6 22:43:29 fido kernel: [    0.547085] usb usb3: Manufacturer: Linux 3.5.0-39-generic xhci_hcd
Sep  6 22:43:29 fido kernel: [    0.547134] usb usb3: SerialNumber: 0000:00:14.0
Sep  6 22:43:29 fido kernel: [    0.547224] xHCI xhci_add_endpoint called for root hub
Sep  6 22:43:29 fido kernel: [    0.547225] xHCI xhci_check_bandwidth called for root hub
Sep  6 22:43:29 fido kernel: [    0.547237] hub 3-0:1.0: USB hub found
Sep  6 22:43:29 fido kernel: [    0.547286] hub 3-0:1.0: 4 ports detected
Sep  6 22:43:29 fido kernel: [    0.547363] xhci_hcd 0000:00:14.0: xHCI Host Controller
Sep  6 22:43:29 fido kernel: [    0.547411] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 4
Sep  6 22:43:29 fido kernel: [    0.547485] usb usb4: New USB device found, idVendor=1d6b, idProduct=0003
Sep  6 22:43:29 fido kernel: [    0.547534] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Sep  6 22:43:29 fido kernel: [    0.547595] usb usb4: Product: xHCI Host Controller
Sep  6 22:43:29 fido kernel: [    0.547641] usb usb4: Manufacturer: Linux 3.5.0-39-generic xhci_hcd
Sep  6 22:43:29 fido kernel: [    0.547690] usb usb4: SerialNumber: 0000:00:14.0
Sep  6 22:43:29 fido kernel: [    0.547771] xHCI xhci_add_endpoint called for root hub
Sep  6 22:43:29 fido kernel: [    0.547772] xHCI xhci_check_bandwidth called for root hub
Sep  6 22:43:29 fido kernel: [    0.547783] hub 4-0:1.0: USB hub found
Sep  6 22:43:29 fido kernel: [    0.547831] hub 4-0:1.0: 4 ports detected
Sep  6 22:43:29 fido kernel: [    0.547951] usbcore: registered new interface driver libusual
Sep  6 22:43:29 fido kernel: [    0.548020] i8042: PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
Sep  6 22:43:29 fido kernel: [    0.548069] i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
Sep  6 22:43:29 fido kernel: [    0.548714] serio: i8042 KBD port at 0x60,0x64 irq 1
Sep  6 22:43:29 fido kernel: [    0.548822] mousedev: PS/2 mouse device common for all mice
Sep  6 22:43:29 fido kernel: [    0.548948] rtc_cmos 00:06: RTC can wake from S4
Sep  6 22:43:29 fido kernel: [    0.549093] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
Sep  6 22:43:29 fido kernel: [    0.549165] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
Sep  6 22:43:29 fido kernel: [    0.549250] device-mapper: uevent: version 1.0.3
Sep  6 22:43:29 fido kernel: [    0.549327] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
Sep  6 22:43:29 fido kernel: [    0.549434] cpuidle: using governor ladder
Sep  6 22:43:29 fido kernel: [    0.549524] cpuidle: using governor menu
Sep  6 22:43:29 fido kernel: [    0.549569] EFI Variables Facility v0.08 2004-May-17
Sep  6 22:43:29 fido kernel: [    0.549742] ashmem: initialized
Sep  6 22:43:29 fido kernel: [    0.549849] TCP: cubic registered
Sep  6 22:43:29 fido kernel: [    0.549941] NET: Registered protocol family 10
Sep  6 22:43:29 fido kernel: [    0.550099] NET: Registered protocol family 17
Sep  6 22:43:29 fido kernel: [    0.550151] Key type dns_resolver registered
Sep  6 22:43:29 fido kernel: [    0.550372] PM: Hibernation image not present or could not be loaded.
Sep  6 22:43:29 fido kernel: [    0.550378] registered taskstats version 1
Sep  6 22:43:29 fido kernel: [    0.552296] Key type trusted registered
Sep  6 22:43:29 fido kernel: [    0.553779] Key type encrypted registered
Sep  6 22:43:29 fido kernel: [    0.555775]   Magic number: 13:275:750
Sep  6 22:43:29 fido kernel: [    0.555837] tty ttyS1: hash matches
Sep  6 22:43:29 fido kernel: [    0.555973] rtc_cmos 00:06: setting system clock to 2013-09-06 20:42:54 UTC (1378500174)
Sep  6 22:43:29 fido kernel: [    0.556536] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Sep  6 22:43:29 fido kernel: [    0.556584] EDD information not available.
Sep  6 22:43:29 fido kernel: [    0.557607] Freeing unused kernel memory: 948k freed
Sep  6 22:43:29 fido kernel: [    0.557727] Write protecting the kernel read-only data: 12288k
Sep  6 22:43:29 fido kernel: [    0.560069] Freeing unused kernel memory: 1356k freed
Sep  6 22:43:29 fido kernel: [    0.561972] Freeing unused kernel memory: 1060k freed
Sep  6 22:43:29 fido kernel: [    0.567808] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
Sep  6 22:43:29 fido kernel: [    0.582571] ahci 0000:00:1f.2: version 3.0
Sep  6 22:43:29 fido kernel: [    0.582616] ahci 0000:00:1f.2: irq 42 for MSI/MSI-X
Sep  6 22:43:29 fido kernel: [    0.583172] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Sep  6 22:43:29 fido kernel: [    0.583339] r8169 0000:03:00.0: irq 43 for MSI/MSI-X
Sep  6 22:43:29 fido kernel: [    0.583467] r8169 0000:03:00.0: eth0: RTL8168evl/8111evl at 0xffffc90005792000, bc:5f:f4:77:66:52, XID 0c900800 IRQ 43
Sep  6 22:43:29 fido kernel: [    0.583536] r8169 0000:03:00.0: eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
Sep  6 22:43:29 fido kernel: [    0.598035] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x3f impl SATA mode
Sep  6 22:43:29 fido kernel: [    0.598102] ahci 0000:00:1f.2: flags: 64bit ncq led clo pio slum part ems apst 
Sep  6 22:43:29 fido kernel: [    0.598167] ahci 0000:00:1f.2: setting latency timer to 64
Sep  6 22:43:29 fido kernel: [    0.638221] scsi0 : ahci
Sep  6 22:43:29 fido kernel: [    0.638397] scsi1 : ahci
Sep  6 22:43:29 fido kernel: [    0.638552] scsi2 : ahci
Sep  6 22:43:29 fido kernel: [    0.638697] scsi3 : ahci
Sep  6 22:43:29 fido kernel: [    0.638859] scsi4 : ahci
Sep  6 22:43:29 fido kernel: [    0.639001] scsi5 : ahci
Sep  6 22:43:29 fido kernel: [    0.639226] ata1: SATA max UDMA/133 abar m2048@0xf7216000 port 0xf7216100 irq 42
Sep  6 22:43:29 fido kernel: [    0.639297] ata2: SATA max UDMA/133 abar m2048@0xf7216000 port 0xf7216180 irq 42
Sep  6 22:43:29 fido kernel: [    0.639359] ata3: SATA max UDMA/133 abar m2048@0xf7216000 port 0xf7216200 irq 42
Sep  6 22:43:29 fido kernel: [    0.639421] ata4: SATA max UDMA/133 abar m2048@0xf7216000 port 0xf7216280 irq 42
Sep  6 22:43:29 fido kernel: [    0.639483] ata5: SATA max UDMA/133 abar m2048@0xf7216000 port 0xf7216300 irq 42
Sep  6 22:43:29 fido kernel: [    0.639545] ata6: SATA max UDMA/133 abar m2048@0xf7216000 port 0xf7216380 irq 42
Sep  6 22:43:29 fido kernel: [    0.639711] ahci 0000:04:00.0: irq 44 for MSI/MSI-X
Sep  6 22:43:29 fido kernel: [    0.639738] ahci: SSS flag set, parallel bus scan disabled
Sep  6 22:43:29 fido kernel: [    0.639869] ahci 0000:04:00.0: AHCI 0001.0200 32 slots 2 ports 6 Gbps 0x3 impl SATA mode
Sep  6 22:43:29 fido kernel: [    0.639953] ahci 0000:04:00.0: flags: 64bit ncq sntf stag led clo pmp pio slum part ccc sxs 
Sep  6 22:43:29 fido kernel: [    0.640228] scsi6 : ahci
Sep  6 22:43:29 fido kernel: [    0.640350] scsi7 : ahci
Sep  6 22:43:29 fido kernel: [    0.640425] ata7: SATA max UDMA/133 abar m512@0xf7100000 port 0xf7100100 irq 44
Sep  6 22:43:29 fido kernel: [    0.640490] ata8: SATA max UDMA/133 abar m512@0xf7100000 port 0xf7100180 irq 44
Sep  6 22:43:29 fido kernel: [    0.841391] usb 1-1: new high-speed USB device number 2 using ehci_hcd
Sep  6 22:43:29 fido kernel: [    0.957139] ata1: SATA link down (SStatus 0 SControl 300)
Sep  6 22:43:29 fido kernel: [    0.957221] ata5: SATA link down (SStatus 0 SControl 300)
Sep  6 22:43:29 fido kernel: [    0.957306] ata4: SATA link down (SStatus 0 SControl 300)
Sep  6 22:43:29 fido kernel: [    0.957378] ata3: SATA link down (SStatus 0 SControl 300)
Sep  6 22:43:29 fido kernel: [    0.957467] ata2: SATA link down (SStatus 0 SControl 300)
Sep  6 22:43:29 fido kernel: [    0.973535] usb 1-1: New USB device found, idVendor=8087, idProduct=0024
Sep  6 22:43:29 fido kernel: [    0.973592] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
Sep  6 22:43:29 fido kernel: [    0.973939] hub 1-1:1.0: USB hub found
Sep  6 22:43:29 fido kernel: [    0.974123] hub 1-1:1.0: 6 ports detected
Sep  6 22:43:29 fido kernel: [    1.084842] usb 2-1: new high-speed USB device number 2 using ehci_hcd
Sep  6 22:43:29 fido kernel: [    1.128747] ata7: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
Sep  6 22:43:29 fido kernel: [    1.129866] ata7.00: ATA-8: Hitachi HDS5C3020BLE630, MZ4OAAB0, max UDMA/133
Sep  6 22:43:29 fido kernel: [    1.129923] ata7.00: 3907029168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
Sep  6 22:43:29 fido kernel: [    1.131130] ata7.00: configured for UDMA/133
Sep  6 22:43:29 fido kernel: [    1.216981] usb 2-1: New USB device found, idVendor=8087, idProduct=0024
Sep  6 22:43:29 fido kernel: [    1.217038] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
Sep  6 22:43:29 fido kernel: [    1.217368] hub 2-1:1.0: USB hub found
Sep  6 22:43:29 fido kernel: [    1.217587] hub 2-1:1.0: 8 ports detected
Sep  6 22:43:29 fido kernel: [    1.236498] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Sep  6 22:43:29 fido kernel: [    1.243713] ata6.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) rejected by device (Stat=0x51 Err=0x04)
Sep  6 22:43:29 fido kernel: [    1.243787] ata6.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
Sep  6 22:43:29 fido kernel: [    1.243860] ata6.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
Sep  6 22:43:29 fido kernel: [    1.245201] ata6.00: ATA-6: WDC WD1600BB-00GUC0, 08.02D08, max UDMA/100
Sep  6 22:43:29 fido kernel: [    1.245258] ata6.00: 312581808 sectors, multi 16: LBA48 
Sep  6 22:43:29 fido kernel: [    1.245316] ata6.00: applying bridge limits
Sep  6 22:43:29 fido kernel: [    1.253773] ata6.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) rejected by device (Stat=0x51 Err=0x04)
Sep  6 22:43:29 fido kernel: [    1.253848] ata6.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
Sep  6 22:43:29 fido kernel: [    1.253920] ata6.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
Sep  6 22:43:29 fido kernel: [    1.255266] ata6.00: configured for UDMA/100
Sep  6 22:43:29 fido kernel: [    1.255526] scsi 5:0:0:0: Direct-Access     ATA      WDC WD1600BB-00G 08.0 PQ: 0 ANSI: 5
Sep  6 22:43:29 fido kernel: [    1.260590] sd 5:0:0:0: Attached scsi generic sg0 type 0
Sep  6 22:43:29 fido kernel: [    1.260602] sd 5:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
Sep  6 22:43:29 fido kernel: [    1.260834] sd 5:0:0:0: [sda] Write Protect is off
Sep  6 22:43:29 fido kernel: [    1.260891] sd 5:0:0:0: [sda] Mode Sense: 00 3a 00 00
Sep  6 22:43:29 fido kernel: [    1.260973] sd 5:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep  6 22:43:29 fido kernel: [    1.276638]  sda: sda1
Sep  6 22:43:29 fido kernel: [    1.277277] sd 5:0:0:0: [sda] Attached SCSI disk
Sep  6 22:43:29 fido kernel: [    1.277500] scsi 6:0:0:0: Direct-Access     ATA      Hitachi HDS5C302 MZ4O PQ: 0 ANSI: 5
Sep  6 22:43:29 fido kernel: [    1.277667] sd 6:0:0:0: [sdb] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
Sep  6 22:43:29 fido kernel: [    1.277670] sd 6:0:0:0: Attached scsi generic sg1 type 0
Sep  6 22:43:29 fido kernel: [    1.277827] sd 6:0:0:0: [sdb] 4096-byte physical blocks
Sep  6 22:43:29 fido kernel: [    1.277983] sd 6:0:0:0: [sdb] Write Protect is off
Sep  6 22:43:29 fido kernel: [    1.278065] sd 6:0:0:0: [sdb] Mode Sense: 00 3a 00 00
Sep  6 22:43:29 fido kernel: [    1.278077] sd 6:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep  6 22:43:29 fido kernel: [    1.288566] usb 1-1.5: new full-speed USB device number 3 using ehci_hcd
Sep  6 22:43:29 fido kernel: [    1.299985]  sdb: sdb1
Sep  6 22:43:29 fido kernel: [    1.300400] sd 6:0:0:0: [sdb] Attached SCSI disk
Sep  6 22:43:29 fido kernel: [    1.381817] usb 1-1.5: New USB device found, idVendor=041e, idProduct=4034
Sep  6 22:43:29 fido kernel: [    1.381877] usb 1-1.5: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Sep  6 22:43:29 fido kernel: [    1.381941] usb 1-1.5: Product: WebCam Instant 
Sep  6 22:43:29 fido kernel: [    1.381995] usb 1-1.5: Manufacturer: Creative Labs  
Sep  6 22:43:29 fido kernel: [    1.444024] Refined TSC clocksource calibration: 3192.747 MHz.
Sep  6 22:43:29 fido kernel: [    1.444086] Switching to clocksource tsc
Sep  6 22:43:29 fido kernel: [    1.488111] usb 2-1.5: new low-speed USB device number 3 using ehci_hcd
Sep  6 22:43:29 fido kernel: [    1.600855] usb 2-1.5: New USB device found, idVendor=040b, idProduct=2011
Sep  6 22:43:29 fido kernel: [    1.600912] usb 2-1.5: New USB device strings: Mfr=0, Product=1, SerialNumber=0
Sep  6 22:43:29 fido kernel: [    1.600985] usb 2-1.5: Product: GiGa HiD
Sep  6 22:43:29 fido kernel: [    1.671692] usb 2-1.7: new full-speed USB device number 4 using ehci_hcd
Sep  6 22:43:29 fido kernel: [    1.767291] ata8: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
Sep  6 22:43:29 fido kernel: [    1.767724] usb 2-1.7: New USB device found, idVendor=0aec, idProduct=3050
Sep  6 22:43:29 fido kernel: [    1.767782] usb 2-1.7: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Sep  6 22:43:29 fido kernel: [    1.767854] usb 2-1.7: Product: USB Storage Device
Sep  6 22:43:29 fido kernel: [    1.767900] usb 2-1.7: Manufacturer: Generic 
Sep  6 22:43:29 fido kernel: [    1.767945] usb 2-1.7: SerialNumber: 0AEC305000001A000
Sep  6 22:43:29 fido kernel: [    1.769313] Initializing USB Mass Storage driver...
Sep  6 22:43:29 fido kernel: [    1.769566] scsi8 : usb-storage 2-1.7:1.0
Sep  6 22:43:29 fido kernel: [    1.769653] usbcore: registered new interface driver usb-storage
Sep  6 22:43:29 fido kernel: [    1.769702] USB Mass Storage support registered.
Sep  6 22:43:29 fido kernel: [    1.779077] ata8.00: ATA-8: MKNSSDCR120GB, 507ABBF0, max UDMA/133
Sep  6 22:43:29 fido kernel: [    1.779133] ata8.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
Sep  6 22:43:29 fido kernel: [    1.788939] ata8.00: configured for UDMA/133
Sep  6 22:43:29 fido kernel: [    1.789094] scsi 7:0:0:0: Direct-Access     ATA      MKNSSDCR120GB    507A PQ: 0 ANSI: 5
Sep  6 22:43:29 fido kernel: [    1.789244] sd 7:0:0:0: Attached scsi generic sg2 type 0
Sep  6 22:43:29 fido kernel: [    1.789252] sd 7:0:0:0: [sdc] 234441648 512-byte logical blocks: (120 GB/111 GiB)
Sep  6 22:43:29 fido kernel: [    1.789377] sd 7:0:0:0: [sdc] Write Protect is off
Sep  6 22:43:29 fido kernel: [    1.789378] sd 7:0:0:0: [sdc] Mode Sense: 00 3a 00 00
Sep  6 22:43:29 fido kernel: [    1.789459] sd 7:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep  6 22:43:29 fido kernel: [    1.790402]  sdc: sdc1
Sep  6 22:43:29 fido kernel: [    1.790858] sd 7:0:0:0: [sdc] Attached SCSI disk
Sep  6 22:43:29 fido kernel: [    1.799031] usbcore: registered new interface driver usbhid
Sep  6 22:43:29 fido kernel: [    1.799080] usbhid: USB HID core driver
Sep  6 22:43:29 fido kernel: [    1.800280] input: GiGa HiD as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.0/input/input3
Sep  6 22:43:29 fido kernel: [    1.800525] hid-generic 0003:040B:2011.0001: input,hiddev0,hidraw0: USB HID v1.10 Mouse [GiGa HiD] on usb-0000:00:1d.0-1.5/input0
Sep  6 22:43:29 fido kernel: [    1.820561] EXT4-fs (sdc1): mounted filesystem without journal. Opts: (null)
Sep  6 22:43:29 fido kernel: [    2.766550] scsi 8:0:0:0: Direct-Access     Generic  USB Storage-SMC  500A PQ: 0 ANSI: 0 CCS
Sep  6 22:43:29 fido kernel: [    2.767671] scsi 8:0:0:1: Direct-Access     Generic  USB Storage-CFC  500A PQ: 0 ANSI: 0 CCS
Sep  6 22:43:29 fido kernel: [    2.768792] scsi 8:0:0:2: Direct-Access     Generic  USB Storage-MMC  500A PQ: 0 ANSI: 0 CCS
Sep  6 22:43:29 fido kernel: [    2.769916] scsi 8:0:0:3: Direct-Access     Generic  USB Storage-MSC  500A PQ: 0 ANSI: 0 CCS
Sep  6 22:43:29 fido kernel: [    2.770394] sd 8:0:0:0: Attached scsi generic sg3 type 0
Sep  6 22:43:29 fido kernel: [    2.770549] sd 8:0:0:1: Attached scsi generic sg4 type 0
Sep  6 22:43:29 fido kernel: [    2.770674] sd 8:0:0:2: Attached scsi generic sg5 type 0
Sep  6 22:43:29 fido kernel: [    2.770801] sd 8:0:0:3: Attached scsi generic sg6 type 0
Sep  6 22:43:29 fido kernel: [    2.782880] sd 8:0:0:0: [sdd] Attached SCSI removable disk
Sep  6 22:43:29 fido kernel: [    2.784149] sd 8:0:0:1: [sde] Attached SCSI removable disk
Sep  6 22:43:29 fido kernel: [    2.785501] sd 8:0:0:2: [sdf] Attached SCSI removable disk
Sep  6 22:43:29 fido kernel: [    2.786873] sd 8:0:0:3: [sdg] Attached SCSI removable disk
Sep  6 22:43:29 fido kernel: [   33.918243] ata8.00: exception Emask 0x10 SAct 0x7fffffff SErr 0x280100 action 0x6 frozen
Sep  6 22:43:29 fido kernel: [   33.918324] ata8: SError: { UnrecovData 10B8B BadCRC }
Sep  6 22:43:29 fido kernel: [   33.918371] ata8.00: failed command: READ FPDMA QUEUED
Sep  6 22:43:29 fido kernel: [   33.918419] ata8.00: cmd 60/88:00:48:84:08/00:00:04:00:00/40 tag 0 ncq 69632 in
Sep  6 22:43:29 fido kernel: [   33.918419]          res 40/00:01:00:00:00/00:00:00:00:00/e0 Emask 0x14 (ATA bus error)
Sep  6 22:43:29 fido kernel: [   33.918515] ata8.00: status: { DRDY }
Sep  6 22:43:29 fido kernel: [   33.918559] ata8.00: failed command: READ FPDMA QUEUED
Sep  6 22:43:29 fido kernel: [   33.918607] ata8.00: cmd 60/50:08:c0:a4:08/01:00:04:00:00/40 tag 1 ncq 172032 in
Sep  6 22:43:29 fido kernel: [   33.918607]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x14 (ATA bus error)
Sep  6 22:43:29 fido kernel: [   33.918703] ata8.00: status: { DRDY }
Sep  6 22:43:29 fido kernel: [   33.918747] ata8.00: failed command: READ FPDMA QUEUED
Sep  6 22:43:29 fido kernel: [   33.918794] ata8.00: cmd 60/a8:10:90:b0:08/03:00:04:00:00/40 tag 2 ncq 479232 in
Sep  6 22:43:29 fido kernel: [   33.918794]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x14 (ATA bus error)
Sep  6 22:43:29 fido kernel: [   33.918891] ata8.00: status: { DRDY }
Sep  6 22:43:29 fido kernel: [   33.918935] ata8.00: failed command: READ FPDMA QUEUED
Sep  6 22:43:29 fido kernel: [   33.918982] ata8.00: cmd 60/c0:18:c0:c2:08/02:00:04:00:00/40 tag 3 ncq 360448 in
Sep  6 22:43:29 fido kernel: [   33.918982]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x14 (ATA bus error)
Sep  6 22:43:29 fido kernel: [   33.919079] ata8.00: status: { DRDY }
Sep  6 22:43:29 fido kernel: [   33.919122] ata8.00: failed command: READ FPDMA QUEUED
Sep  6 22:43:29 fido kernel: [   33.919170] ata8.00: cmd 60/08:20:28:19:09/00:00:04:00:00/40 tag 4 ncq 4096 in
Sep  6 22:43:29 fido kernel: [   33.919170]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x14 (ATA bus error)
Sep  6 22:43:29 fido kernel: [   33.919266] ata8.00: status: { DRDY }
Sep  6 22:43:29 fido kernel: [   33.919310] ata8.00: failed command: READ FPDMA QUEUED
Sep  6 22:43:29 fido kernel: [   33.919357] ata8.00: cmd 60/08:28:80:19:09/00:00:04:00:00/40 tag 5 ncq 4096 in
Sep  6 22:43:29 fido kernel: [   33.919357]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x14 (ATA bus error)
Sep  6 22:43:29 fido kernel: [   33.919453] ata8.00: status: { DRDY }
Sep  6 22:43:29 fido kernel: [   33.919497] ata8.00: failed command: READ FPDMA QUEUED
Sep  6 22:43:29 fido kernel: [   33.919545] ata8.00: cmd 60/f0:30:70:d1:08/00:00:04:00:00/40 tag 6 ncq 122880 in
Sep  6 22:43:29 fido kernel: [   33.919545]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x14 (ATA bus error)
Sep  6 22:43:29 fido kernel: [   33.919641] ata8.00: status: { DRDY }
Sep  6 22:43:29 fido kernel: [   33.919685] ata8.00: failed command: READ FPDMA QUEUED
Sep  6 22:43:29 fido kernel: [   33.919732] ata8.00: cmd 60/10:38:38:16:09/00:00:04:00:00/40 tag 7 ncq 8192 in
Sep  6 22:43:29 fido kernel: [   33.919732]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x14 (ATA bus error)
Sep  6 22:43:29 fido kernel: [   33.919829] ata8.00: status: { DRDY }
Sep  6 22:43:29 fido kernel: [   33.919873] ata8.00: failed command: READ FPDMA QUEUED
Sep  6 22:43:29 fido kernel: [   33.919920] ata8.00: cmd 60/38:40:b0:dd:08/01:00:04:00:00/40 tag 8 ncq 159744 in
Sep  6 22:43:29 fido kernel: [   33.919920]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x14 (ATA bus error)
Sep  6 22:43:29 fido kernel: [   33.920016] ata8.00: status: { DRDY }
Sep  6 22:43:29 fido kernel: [   33.920060] ata8.00: failed command: READ FPDMA QUEUED
Sep  6 22:43:29 fido kernel: [   33.920107] ata8.00: cmd 60/68:48:48:c6:45/00:00:04:00:00/40 tag 9 ncq 53248 in
Sep  6 22:43:29 fido kernel: [   33.920107]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x14 (ATA bus error)
Sep  6 22:43:29 fido kernel: [   33.920204] ata8.00: status: { DRDY }
Sep  6 22:43:29 fido kernel: [   33.920248] ata8.00: failed command: READ FPDMA QUEUED
Sep  6 22:43:29 fido kernel: [   33.920295] ata8.00: cmd 60/10:50:80:1a:09/00:00:04:00:00/40 tag 10 ncq 8192 in
Sep  6 22:43:29 fido kernel: [   33.920295]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x14 (ATA bus error)
Sep  6 22:43:29 fido kernel: [   33.920391] ata8.00: status: { DRDY }
Sep  6 22:43:29 fido kernel: [   33.920435] ata8.00: failed command: READ FPDMA QUEUED
Sep  6 22:43:29 fido kernel: [   33.920483] ata8.00: cmd 60/c8:58:80:c5:08/03:00:04:00:00/40 tag 11 ncq 495616 in
Sep  6 22:43:29 fido kernel: [   33.920483]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x14 (ATA bus error)
Sep  6 22:43:29 fido kernel: [   33.920579] ata8.00: status: { DRDY }
Sep  6 22:43:29 fido kernel: [   33.920623] ata8.00: failed command: READ FPDMA QUEUED
Sep  6 22:43:29 fido kernel: [   33.920670] ata8.00: cmd 60/58:60:00:18:0a/00:00:04:00:00/40 tag 12 ncq 45056 in
Sep  6 22:43:29 fido kernel: [   33.920670]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x14 (ATA bus error)
Sep  6 22:43:29 fido kernel: [   33.920767] ata8.00: status: { DRDY }
Sep  6 22:43:29 fido kernel: [   33.920811] ata8.00: failed command: READ FPDMA QUEUED
Sep  6 22:43:29 fido kernel: [   33.920858] ata8.00: cmd 60/78:68:50:df:08/01:00:04:00:00/40 tag 13 ncq 192512 in
Sep  6 22:43:29 fido kernel: [   33.920858]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x14 (ATA bus error)
Sep  6 22:43:29 fido kernel: [   33.920955] ata8.00: status: { DRDY }
Sep  6 22:43:29 fido kernel: [   33.920999] ata8.00: failed command: READ FPDMA QUEUED
Sep  6 22:43:29 fido kernel: [   33.921046] ata8.00: cmd 60/70:70:d0:16:09/00:00:04:00:00/40 tag 14 ncq 57344 in
Sep  6 22:43:29 fido kernel: [   33.921046]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x14 (ATA bus error)
Sep  6 22:43:29 fido kernel: [   33.921142] ata8.00: status: { DRDY }
Sep  6 22:43:29 fido kernel: [   33.921186] ata8.00: failed command: READ FPDMA QUEUED
Sep  6 22:43:29 fido kernel: [   33.921234] ata8.00: cmd 60/f0:78:00:15:09/00:00:04:00:00/40 tag 15 ncq 122880 in
Sep  6 22:43:29 fido kernel: [   33.921234]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x14 (ATA bus error)
Sep  6 22:43:29 fido kernel: [   33.926227] ata8.00: status: { DRDY }
Sep  6 22:43:29 fido kernel: [   33.926271] ata8.00: failed command: READ FPDMA QUEUED
Sep  6 22:43:29 fido kernel: [   33.926318] ata8.00: cmd 60/08:80:20:16:09/00:00:04:00:00/40 tag 16 ncq 4096 in
Sep  6 22:43:29 fido kernel: [   33.926318]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x14 (ATA bus error)
Sep  6 22:43:29 fido kernel: [   33.926414] ata8.00: status: { DRDY }
Sep  6 22:43:29 fido kernel: [   33.926458] ata8.00: failed command: READ FPDMA QUEUED
Sep  6 22:43:29 fido kernel: [   33.926505] ata8.00: cmd 60/08:88:58:17:09/00:00:04:00:00/40 tag 17 ncq 4096 in
Sep  6 22:43:29 fido kernel: [   33.926505]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x14 (ATA bus error)
Sep  6 22:43:29 fido kernel: [   33.926602] ata8.00: status: { DRDY }
Sep  6 22:43:29 fido kernel: [   33.926646] ata8.00: failed command: READ FPDMA QUEUED
Sep  6 22:43:29 fido kernel: [   33.926693] ata8.00: cmd 60/e8:90:a8:c9:08/01:00:04:00:00/40 tag 18 ncq 249856 in
Sep  6 22:43:29 fido kernel: [   33.926693]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x14 (ATA bus error)
Sep  6 22:43:29 fido kernel: [   33.926790] ata8.00: status: { DRDY }
Sep  6 22:43:29 fido kernel: [   33.926834] ata8.00: failed command: READ FPDMA QUEUED
Sep  6 22:43:29 fido kernel: [   33.926881] ata8.00: cmd 60/88:98:b8:17:09/00:00:04:00:00/40 tag 19 ncq 69632 in
Sep  6 22:43:29 fido kernel: [   33.926881]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x14 (ATA bus error)
Sep  6 22:43:29 fido kernel: [   33.926977] ata8.00: status: { DRDY }
Sep  6 22:43:29 fido kernel: [   33.927021] ata8.00: failed command: READ FPDMA QUEUED
Sep  6 22:43:29 fido kernel: [   33.927068] ata8.00: cmd 60/a0:a0:e8:cb:08/01:00:04:00:00/40 tag 20 ncq 212992 in
Sep  6 22:43:29 fido kernel: [   33.927068]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x14 (ATA bus error)
Sep  6 22:43:29 fido kernel: [   33.927165] ata8.00: status: { DRDY }
Sep  6 22:43:29 fido kernel: [   33.927209] ata8.00: failed command: READ FPDMA QUEUED
Sep  6 22:43:29 fido kernel: [   33.927256] ata8.00: cmd 60/08:a8:88:18:09/00:00:04:00:00/40 tag 21 ncq 4096 in
Sep  6 22:43:29 fido kernel: [   33.927256]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x14 (ATA bus error)
Sep  6 22:43:29 fido kernel: [   33.927353] ata8.00: status: { DRDY }
Sep  6 22:43:29 fido kernel: [   33.927397] ata8.00: failed command: READ FPDMA QUEUED
Sep  6 22:43:29 fido kernel: [   33.927444] ata8.00: cmd 60/18:b0:10:5f:0a/00:00:04:00:00/40 tag 22 ncq 12288 in
Sep  6 22:43:29 fido kernel: [   33.927444]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x14 (ATA bus error)
Sep  6 22:43:29 fido kernel: [   33.927540] ata8.00: status: { DRDY }
Sep  6 22:43:29 fido kernel: [   33.927584] ata8.00: failed command: READ FPDMA QUEUED
Sep  6 22:43:29 fido kernel: [   33.927632] ata8.00: cmd 60/08:b8:30:c1:45/00:00:04:00:00/40 tag 23 ncq 4096 in
Sep  6 22:43:29 fido kernel: [   33.927632]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x14 (ATA bus error)
Sep  6 22:43:29 fido kernel: [   33.927728] ata8.00: status: { DRDY }
Sep  6 22:43:29 fido kernel: [   33.927772] ata8.00: failed command: READ FPDMA QUEUED
Sep  6 22:43:29 fido kernel: [   33.927819] ata8.00: cmd 60/10:c0:18:c4:45/00:00:04:00:00/40 tag 24 ncq 8192 in
Sep  6 22:43:29 fido kernel: [   33.927819]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x14 (ATA bus error)
Sep  6 22:43:29 fido kernel: [   33.927915] ata8.00: status: { DRDY }
Sep  6 22:43:29 fido kernel: [   33.927959] ata8.00: failed command: READ FPDMA QUEUED
Sep  6 22:43:29 fido kernel: [   33.928007] ata8.00: cmd 60/20:c8:f0:1c:0a/00:00:04:00:00/40 tag 25 ncq 16384 in
Sep  6 22:43:29 fido kernel: [   33.928007]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x14 (ATA bus error)
Sep  6 22:43:29 fido kernel: [   33.928103] ata8.00: status: { DRDY }
Sep  6 22:43:29 fido kernel: [   33.928147] ata8.00: failed command: READ FPDMA QUEUED
Sep  6 22:43:29 fido kernel: [   33.928194] ata8.00: cmd 60/30:d0:18:bc:08/01:00:04:00:00/40 tag 26 ncq 155648 in
Sep  6 22:43:29 fido kernel: [   33.928194]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x14 (ATA bus error)
Sep  6 22:43:29 fido kernel: [   33.928291] ata8.00: status: { DRDY }
Sep  6 22:43:29 fido kernel: [   33.928335] ata8.00: failed command: READ FPDMA QUEUED
Sep  6 22:43:29 fido kernel: [   33.928382] ata8.00: cmd 60/10:d8:30:c4:45/00:00:04:00:00/40 tag 27 ncq 8192 in
Sep  6 22:43:29 fido kernel: [   33.928382]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x14 (ATA bus error)
Sep  6 22:43:29 fido kernel: [   33.928478] ata8.00: status: { DRDY }
Sep  6 22:43:29 fido kernel: [   33.928522] ata8.00: failed command: READ FPDMA QUEUED
Sep  6 22:43:29 fido kernel: [   33.928570] ata8.00: cmd 60/08:e0:48:c4:45/00:00:04:00:00/40 tag 28 ncq 4096 in
Sep  6 22:43:29 fido kernel: [   33.928570]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x14 (ATA bus error)
Sep  6 22:43:29 fido kernel: [   33.928666] ata8.00: status: { DRDY }
Sep  6 22:43:29 fido kernel: [   33.928710] ata8.00: failed command: READ FPDMA QUEUED
Sep  6 22:43:29 fido kernel: [   33.928757] ata8.00: cmd 60/08:e8:98:ce:08/02:00:04:00:00/40 tag 29 ncq 266240 in
Sep  6 22:43:29 fido kernel: [   33.928757]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x14 (ATA bus error)
Sep  6 22:43:29 fido kernel: [   33.928854] ata8.00: status: { DRDY }
Sep  6 22:43:29 fido kernel: [   33.928898] ata8.00: failed command: READ FPDMA QUEUED
Sep  6 22:43:29 fido kernel: [   33.928945] ata8.00: cmd 60/08:f0:d8:c6:45/00:00:04:00:00/40 tag 30 ncq 4096 in
Sep  6 22:43:29 fido kernel: [   33.928945]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x14 (ATA bus error)
Sep  6 22:43:29 fido kernel: [   33.929041] ata8.00: status: { DRDY }
Sep  6 22:43:29 fido kernel: [   33.929087] ata8: hard resetting link
Sep  6 22:43:29 fido kernel: [   34.417118] ata8: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
Sep  6 22:43:29 fido kernel: [   34.439062] ata8.00: configured for UDMA/133
Sep  6 22:43:29 fido kernel: [   34.439118] ata8.00: device reported invalid CHS sector 0
Sep  6 22:43:29 fido kernel: [   34.439175] ata8.00: device reported invalid CHS sector 0
Sep  6 22:43:29 fido kernel: [   34.439222] ata8.00: device reported invalid CHS sector 0
Sep  6 22:43:29 fido kernel: [   34.439268] ata8.00: device reported invalid CHS sector 0
Sep  6 22:43:29 fido kernel: [   34.439315] ata8.00: device reported invalid CHS sector 0
Sep  6 22:43:29 fido kernel: [   34.439361] ata8.00: device reported invalid CHS sector 0
Sep  6 22:43:29 fido kernel: [   34.439408] ata8.00: device reported invalid CHS sector 0
Sep  6 22:43:29 fido kernel: [   34.439454] ata8.00: device reported invalid CHS sector 0
Sep  6 22:43:29 fido kernel: [   34.439501] ata8.00: device reported invalid CHS sector 0
Sep  6 22:43:29 fido kernel: [   34.439547] ata8.00: device reported invalid CHS sector 0
Sep  6 22:43:29 fido kernel: [   34.439593] ata8.00: device reported invalid CHS sector 0
Sep  6 22:43:29 fido kernel: [   34.439640] ata8.00: device reported invalid CHS sector 0
Sep  6 22:43:29 fido kernel: [   34.439686] ata8.00: device reported invalid CHS sector 0
Sep  6 22:43:29 fido kernel: [   34.439733] ata8.00: device reported invalid CHS sector 0
Sep  6 22:43:29 fido kernel: [   34.439779] ata8.00: device reported invalid CHS sector 0
Sep  6 22:43:29 fido kernel: [   34.439825] ata8.00: device reported invalid CHS sector 0
Sep  6 22:43:29 fido kernel: [   34.439872] ata8.00: device reported invalid CHS sector 0
Sep  6 22:43:29 fido kernel: [   34.439918] ata8.00: device reported invalid CHS sector 0
Sep  6 22:43:29 fido kernel: [   34.439965] ata8.00: device reported invalid CHS sector 0
Sep  6 22:43:29 fido kernel: [   34.440011] ata8.00: device reported invalid CHS sector 0
Sep  6 22:43:29 fido kernel: [   34.440057] ata8.00: device reported invalid CHS sector 0
Sep  6 22:43:29 fido kernel: [   34.440104] ata8.00: device reported invalid CHS sector 0
Sep  6 22:43:29 fido kernel: [   34.440150] ata8.00: device reported invalid CHS sector 0
Sep  6 22:43:29 fido kernel: [   34.440197] ata8.00: device reported invalid CHS sector 0
Sep  6 22:43:29 fido kernel: [   34.440243] ata8.00: device reported invalid CHS sector 0
Sep  6 22:43:29 fido kernel: [   34.440289] ata8.00: device reported invalid CHS sector 0
Sep  6 22:43:29 fido kernel: [   34.440336] ata8.00: device reported invalid CHS sector 0
Sep  6 22:43:29 fido kernel: [   34.440382] ata8.00: device reported invalid CHS sector 0
Sep  6 22:43:29 fido kernel: [   34.440429] ata8.00: device reported invalid CHS sector 0
Sep  6 22:43:29 fido kernel: [   34.440475] ata8.00: device reported invalid CHS sector 0
Sep  6 22:43:29 fido kernel: [   34.440521] ata8.00: device reported invalid CHS sector 0
Sep  6 22:43:29 fido kernel: [   34.440573] ata8: EH complete
Sep  6 22:43:29 fido kernel: [   34.519473] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Sep  6 22:43:29 fido kernel: [   34.529093] lp: driver loaded but no devices found
Sep  6 22:43:29 fido kernel: [   34.551901] mei 0000:00:16.0: setting latency timer to 64
Sep  6 22:43:29 fido kernel: [   34.551949] mei 0000:00:16.0: irq 45 for MSI/MSI-X
Sep  6 22:43:29 fido kernel: [   34.557635] nvidia: module license 'NVIDIA' taints kernel.
Sep  6 22:43:29 fido kernel: [   34.557639] Disabling lock debugging due to kernel taint
Sep  6 22:43:29 fido kernel: [   34.560366] ACPI Warning: 0x0000000000000460-0x000000000000047f SystemIO conflicts with Region \PMIO 1 (20120320/utaddress-251)
Sep  6 22:43:29 fido kernel: [   34.560374] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Sep  6 22:43:29 fido kernel: [   34.560376] lpc_ich: Resource conflict(s) found affecting iTCO_wdt
Sep  6 22:43:29 fido kernel: [   34.560380] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMIO 1 (20120320/utaddress-251)
Sep  6 22:43:29 fido kernel: [   34.560382] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Sep  6 22:43:29 fido kernel: [   34.560385] ACPI Warning: 0x0000000000000500-0x000000000000053f SystemIO conflicts with Region \GPR2 1 (20120320/utaddress-251)
Sep  6 22:43:29 fido kernel: [   34.560387] ACPI Warning: 0x0000000000000500-0x000000000000053f SystemIO conflicts with Region \GPIO 2 (20120320/utaddress-251)
Sep  6 22:43:29 fido kernel: [   34.560389] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Sep  6 22:43:29 fido kernel: [   34.560391] lpc_ich: Resource conflict(s) found affecting gpio_ich
Sep  6 22:43:29 fido kernel: [   34.561445] mei 0000:00:16.0: wd: failed to find the client
Sep  6 22:43:29 fido kernel: [   34.569407] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
Sep  6 22:43:29 fido kernel: [   34.569537] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  304.88  Wed Mar 27 14:26:46 PDT 2013
Sep  6 22:43:29 fido kernel: [   34.577103] type=1400 audit(1378500208.595:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=562 comm="apparmor_parser"
Sep  6 22:43:29 fido kernel: [   34.577354] type=1400 audit(1378500208.595:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=562 comm="apparmor_parser"
Sep  6 22:43:29 fido kernel: [   34.577495] type=1400 audit(1378500208.595:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=562 comm="apparmor_parser"
Sep  6 22:43:29 fido kernel: [   34.584623] parport_pc 00:09: reported by Plug and Play ACPI
Sep  6 22:43:29 fido kernel: [   34.584679] parport0: PC-style at 0x378 (0x778), irq 5, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
Sep  6 22:43:29 fido kernel: [   34.605743] snd_hda_intel 0000:00:1b.0: irq 46 for MSI/MSI-X
Sep  6 22:43:29 fido kernel: [   34.606414] Linux video capture interface: v2.00
Sep  6 22:43:29 fido kernel: [   34.606653] gspca_main: v2.14.0 registered
Sep  6 22:43:29 fido kernel: [   34.607100] gspca_main: gspca_zc3xx-2.14.0 probing 041e:4034
Sep  6 22:43:29 fido kernel: [   34.611765] microcode: CPU0 sig=0x306a9, pf=0x2, revision=0x12
Sep  6 22:43:29 fido kernel: [   34.665666] input: HDA Intel PCH Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input4
Sep  6 22:43:29 fido kernel: [   34.665686] ppdev: user-space parallel port driver
Sep  6 22:43:29 fido kernel: [   34.665955] input: HDA Intel PCH Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input5
Sep  6 22:43:29 fido kernel: [   34.665991] input: HDA Intel PCH Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
Sep  6 22:43:29 fido kernel: [   34.666024] input: HDA Intel PCH Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
Sep  6 22:43:29 fido kernel: [   34.666054] input: HDA Intel PCH Line Out CLFE as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
Sep  6 22:43:29 fido kernel: [   34.666083] input: HDA Intel PCH Line Out Surround as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
Sep  6 22:43:29 fido kernel: [   34.666115] input: HDA Intel PCH Line Out Front as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
Sep  6 22:43:29 fido kernel: [   34.666325] hda_intel: Disabling MSI
Sep  6 22:43:29 fido kernel: [   34.666331] hda-intel: 0000:01:00.1: Handle VGA-switcheroo audio client
Sep  6 22:43:29 fido kernel: [   34.668480] microcode: CPU1 sig=0x306a9, pf=0x2, revision=0x12
Sep  6 22:43:29 fido kernel: [   34.671843] microcode: CPU2 sig=0x306a9, pf=0x2, revision=0x12
Sep  6 22:43:29 fido kernel: [   34.673728] microcode: CPU3 sig=0x306a9, pf=0x2, revision=0x12
Sep  6 22:43:29 fido kernel: [   34.674460] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
Sep  6 22:43:29 fido kernel: [   34.680735] lp0: using parport0 (interrupt-driven).
Sep  6 22:43:29 fido kernel: [   34.796241] EXT4-fs (sdc1): Remounting file system with no journal so ignoring journalled data option
Sep  6 22:43:29 fido kernel: [   34.796438] EXT4-fs (sdc1): re-mounted. Opts: discard,data=writeback,errors=remount-ro
Sep  6 22:43:29 fido kernel: [   34.813591] input: gspca_zc3xx as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/input/input11
Sep  6 22:43:29 fido kernel: [   34.813739] usbcore: registered new interface driver gspca_zc3xx
Sep  6 22:43:29 fido kernel: [   34.886723] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
Sep  6 22:43:29 fido modem-manager[970]: <info>  ModemManager (version 0.5.2.0) starting...
Sep  6 22:43:29 fido bluetoothd[974]: Bluetooth daemon 4.98
Sep  6 22:43:29 fido modem-manager[970]: <info>  Loaded plugin X22X
Sep  6 22:43:29 fido modem-manager[970]: <info>  Loaded plugin Huawei
Sep  6 22:43:29 fido modem-manager[970]: <info>  Loaded plugin Ericsson MBM
Sep  6 22:43:29 fido modem-manager[970]: <info>  Loaded plugin Option High-Speed
Sep  6 22:43:29 fido bluetoothd[974]: Starting SDP server
Sep  6 22:43:29 fido modem-manager[970]: <info>  Loaded plugin Sierra
Sep  6 22:43:29 fido modem-manager[970]: <info>  Loaded plugin ZTE
Sep  6 22:43:29 fido modem-manager[970]: <info>  Loaded plugin MotoC
Sep  6 22:43:29 fido modem-manager[970]: <info>  Loaded plugin Longcheer
Sep  6 22:43:29 fido modem-manager[970]: <info>  Loaded plugin SimTech
Sep  6 22:43:29 fido modem-manager[970]: <info>  Loaded plugin Wavecom
Sep  6 22:43:29 fido modem-manager[970]: <info>  Loaded plugin Samsung
Sep  6 22:43:29 fido modem-manager[970]: <info>  Loaded plugin Gobi
Sep  6 22:43:29 fido modem-manager[970]: <info>  Loaded plugin Option
Sep  6 22:43:29 fido modem-manager[970]: <info>  Loaded plugin Generic
Sep  6 22:43:29 fido modem-manager[970]: <info>  Loaded plugin Linktop
Sep  6 22:43:29 fido modem-manager[970]: <info>  Loaded plugin Nokia
Sep  6 22:43:29 fido modem-manager[970]: <info>  Loaded plugin AnyData
Sep  6 22:43:29 fido modem-manager[970]: <info>  Loaded plugin Novatel
Sep  6 22:43:29 fido bluetoothd[974]: Failed to init alert plugin
Sep  6 22:43:29 fido bluetoothd[974]: Failed to init time plugin
Sep  6 22:43:29 fido bluetoothd[974]: Failed to init proximity plugin
Sep  6 22:43:29 fido kernel: [   35.187370] Bluetooth: Core ver 2.16
Sep  6 22:43:29 fido kernel: [   35.187399] NET: Registered protocol family 31
Sep  6 22:43:29 fido kernel: [   35.187400] Bluetooth: HCI device and connection manager initialized
Sep  6 22:43:29 fido kernel: [   35.187401] Bluetooth: HCI socket layer initialized
Sep  6 22:43:29 fido kernel: [   35.187402] Bluetooth: L2CAP socket layer initialized
Sep  6 22:43:29 fido kernel: [   35.187404] Bluetooth: SCO socket layer initialized
Sep  6 22:43:29 fido bluetoothd[974]: Failed to init gatt_example plugin
Sep  6 22:43:29 fido kernel: [   35.191641] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Sep  6 22:43:29 fido kernel: [   35.191643] Bluetooth: BNEP filters: protocol multicast
Sep  6 22:43:29 fido kernel: [   35.194052] Bluetooth: RFCOMM TTY layer initialized
Sep  6 22:43:29 fido kernel: [   35.194055] Bluetooth: RFCOMM socket layer initialized
Sep  6 22:43:29 fido kernel: [   35.194056] Bluetooth: RFCOMM ver 1.11
Sep  6 22:43:29 fido NetworkManager[992]: <info> NetworkManager (version 0.9.4.0) is starting...
Sep  6 22:43:29 fido NetworkManager[992]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
Sep  6 22:43:29 fido NetworkManager[992]: <info> VPN: loaded org.freedesktop.NetworkManager.pptp
Sep  6 22:43:29 fido NetworkManager[992]: <info> DNS: loaded plugin dnsmasq
Sep  6 22:43:29 fido kernel: [   35.200894] type=1400 audit(1378500209.219:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=993 comm="apparmor_parser"
Sep  6 22:43:29 fido kernel: [   35.201188] type=1400 audit(1378500209.219:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=993 comm="apparmor_parser"
Sep  6 22:43:29 fido kernel: [   35.204490] type=1400 audit(1378500209.223:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=1023 comm="apparmor_parser"
Sep  6 22:43:29 fido kernel: [   35.204694] type=1400 audit(1378500209.223:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper//chromium_browser" pid=1023 comm="apparmor_parser"
Sep  6 22:43:29 fido dbus[952]: [system] Activating service name='org.freedesktop.PolicyKit1' (using servicehelper)
Sep  6 22:43:29 fido avahi-daemon[1031]: Found user 'avahi' (UID 107) and group 'avahi' (GID 118).
Sep  6 22:43:29 fido avahi-daemon[1031]: Successfully dropped root privileges.
Sep  6 22:43:29 fido avahi-daemon[1031]: avahi-daemon 0.6.30 starting up.
Sep  6 22:43:29 fido avahi-daemon[1031]: Successfully called chroot().
Sep  6 22:43:29 fido avahi-daemon[1031]: Successfully dropped remaining capabilities.
Sep  6 22:43:29 fido avahi-daemon[1031]: Loading service file /services/udisks.service.
Sep  6 22:43:29 fido dbus[952]: [system] Activating service name='org.freedesktop.ColorManager' (using servicehelper)
Sep  6 22:43:29 fido avahi-daemon[1031]: Network interface enumeration completed.
Sep  6 22:43:29 fido avahi-daemon[1031]: Registering HINFO record with values 'X86_64'/'LINUX'.
Sep  6 22:43:29 fido avahi-daemon[1031]: Server startup complete. Host name is fido.local. Local service cookie is 674850280.
Sep  6 22:43:29 fido avahi-daemon[1031]: Service "fido" (/services/udisks.service) successfully established.
Sep  6 22:43:29 fido kernel: [   35.207821] type=1400 audit(1378500209.227:9): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1024 comm="apparmor_parser"
Sep  6 22:43:29 fido kernel: [   35.208079] type=1400 audit(1378500209.227:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1024 comm="apparmor_parser"
Sep  6 22:43:29 fido kernel: [   35.208220] type=1400 audit(1378500209.227:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1024 comm="apparmor_parser"
Sep  6 22:43:29 fido polkitd[1030]: started daemon version 0.104 using authority implementation `local' version `0.104'
Sep  6 22:43:29 fido dbus[952]: [system] Successfully activated service 'org.freedesktop.PolicyKit1'
Sep  6 22:43:29 fido NetworkManager[992]:    SCPlugin-Ifupdown: init!
Sep  6 22:43:29 fido NetworkManager[992]:    SCPlugin-Ifupdown: update_system_hostname
Sep  6 22:43:29 fido NetworkManager[992]:    SCPluginIfupdown: management mode: unmanaged
Sep  6 22:43:29 fido dbus[952]: [system] Successfully activated service 'org.freedesktop.ColorManager'
Sep  6 22:43:29 fido NetworkManager[992]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.5/0000:03:00.0/net/eth0, iface: eth0)
Sep  6 22:43:29 fido NetworkManager[992]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.5/0000:03:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Sep  6 22:43:29 fido NetworkManager[992]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Sep  6 22:43:29 fido NetworkManager[992]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Sep  6 22:43:29 fido NetworkManager[992]:    SCPlugin-Ifupdown: end _init.
Sep  6 22:43:29 fido NetworkManager[992]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Sep  6 22:43:29 fido NetworkManager[992]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Sep  6 22:43:29 fido NetworkManager[992]:    Ifupdown: get unmanaged devices count: 0
Sep  6 22:43:29 fido NetworkManager[992]:    SCPlugin-Ifupdown: (15989552) ... get_connections.
Sep  6 22:43:29 fido NetworkManager[992]:    SCPlugin-Ifupdown: (15989552) ... get_connections (managed=false): return empty list.
Sep  6 22:43:29 fido NetworkManager[992]:    Ifupdown: get unmanaged devices count: 0
Sep  6 22:43:29 fido NetworkManager[992]: <info> modem-manager is now available
Sep  6 22:43:29 fido NetworkManager[992]: <info> monitoring kernel firmware directory '/lib/firmware'.
Sep  6 22:43:29 fido NetworkManager[992]: <info> WiFi enabled by radio killswitch; enabled by state file
Sep  6 22:43:29 fido NetworkManager[992]: <info> WWAN enabled by radio killswitch; enabled by state file
Sep  6 22:43:29 fido NetworkManager[992]: <info> WiMAX enabled by radio killswitch; enabled by state file
Sep  6 22:43:29 fido NetworkManager[992]: <info> Networking is enabled by state file
Sep  6 22:43:29 fido NetworkManager[992]: <warn> failed to allocate link cache: (-10) Operation not supported
Sep  6 22:43:29 fido NetworkManager[992]: <info> (eth0): carrier is OFF
Sep  6 22:43:29 fido NetworkManager[992]: <info> (eth0): new Ethernet device (driver: 'r8169' ifindex: 2)
Sep  6 22:43:29 fido NetworkManager[992]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Sep  6 22:43:29 fido NetworkManager[992]: <info> (eth0): now managed
Sep  6 22:43:29 fido NetworkManager[992]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Sep  6 22:43:29 fido NetworkManager[992]: <info> (eth0): bringing up device.
Sep  6 22:43:29 fido anacron[1094]: Anacron 2.3 started on 2013-09-06
Sep  6 22:43:29 fido acpid: starting up with proc fs
Sep  6 22:43:29 fido acpid: 35 rules loaded
Sep  6 22:43:29 fido acpid: waiting for events: event logging is off
Sep  6 22:43:29 fido anacron[1094]: Normal exit (0 jobs run)
Sep  6 22:43:29 fido cron[1075]: (CRON) INFO (pidfile fd = 3)
Sep  6 22:43:29 fido cron[1103]: (CRON) STARTUP (fork ok)
Sep  6 22:43:29 fido cron[1103]: (CRON) INFO (Running @reboot jobs)
Sep  6 22:43:29 fido kernel: [   35.267250] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input12
Sep  6 22:43:29 fido kernel: [   35.271229] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input13
Sep  6 22:43:29 fido kernel: [   35.271302] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input14
Sep  6 22:43:29 fido kernel: [   35.271367] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input15
Sep  6 22:43:29 fido NetworkManager[992]: <info> (eth0): preparing device.
Sep  6 22:43:29 fido NetworkManager[992]: <info> (eth0): deactivating device (reason 'managed') [2]
Sep  6 22:43:29 fido NetworkManager[992]: <info> Added default wired connection 'Wired connection 1' for /sys/devices/pci0000:00/0000:00:1c.5/0000:03:00.0/net/eth0
Sep  6 22:43:29 fido kernel: [   35.296056] r8169 0000:03:00.0: eth0: link down
Sep  6 22:43:29 fido kernel: [   35.296075] r8169 0000:03:00.0: eth0: link down
Sep  6 22:43:29 fido kernel: [   35.296485] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Sep  6 22:43:29 fido kernel: [   35.296671] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Sep  6 22:43:29 fido acpid: client connected from 1207[0:0]
Sep  6 22:43:29 fido acpid: 1 client rule loaded
Sep  6 22:43:29 fido anacron[1237]: Anacron 2.3 started on 2013-09-06
Sep  6 22:43:29 fido anacron[1237]: Normal exit (0 jobs run)
Sep  6 22:43:30 fido acpid: client connected from 1207[0:0]
Sep  6 22:43:30 fido acpid: 1 client rule loaded
Sep  6 22:43:30 fido dbus[952]: [system] Activating service name='org.freedesktop.Accounts' (using servicehelper)
Sep  6 22:43:30 fido dbus[952]: [system] Successfully activated service 'org.freedesktop.Accounts'
Sep  6 22:43:30 fido accounts-daemon[1339]: started daemon version 0.6.15
Sep  6 22:43:30 fido dbus[952]: [system] Activating service name='org.freedesktop.ConsoleKit' (using servicehelper)
Sep  6 22:43:30 fido dbus[952]: [system] Successfully activated service 'org.freedesktop.ConsoleKit'
Sep  6 22:43:30 fido dbus[952]: [system] Activating service name='org.freedesktop.UPower' (using servicehelper)
Sep  6 22:43:30 fido dbus[952]: [system] Successfully activated service 'org.freedesktop.UPower'
Sep  6 22:43:30 fido anacron[1557]: Anacron 2.3 started on 2013-09-06
Sep  6 22:43:30 fido anacron[1557]: Normal exit (0 jobs run)
Sep  6 22:43:30 fido dbus[952]: [system] Activating service name='org.freedesktop.RealtimeKit1' (using servicehelper)
Sep  6 22:43:30 fido dbus[952]: [system] Successfully activated service 'org.freedesktop.RealtimeKit1'
Sep  6 22:43:30 fido rtkit-daemon[1690]: Successfully called chroot.
Sep  6 22:43:30 fido rtkit-daemon[1690]: Successfully dropped privileges.
Sep  6 22:43:30 fido rtkit-daemon[1690]: Successfully limited resources.
Sep  6 22:43:30 fido rtkit-daemon[1690]: Running.
Sep  6 22:43:30 fido rtkit-daemon[1690]: Watchdog thread running.
Sep  6 22:43:30 fido rtkit-daemon[1690]: Canary thread running.
Sep  6 22:43:30 fido rtkit-daemon[1690]: Successfully made thread 1688 of process 1688 (n/a) owned by '104' high priority at nice level -11.
Sep  6 22:43:30 fido rtkit-daemon[1690]: Supervising 1 threads of 1 processes of 1 users.
Sep  6 22:43:30 fido rtkit-daemon[1690]: Successfully made thread 1702 of process 1688 (n/a) owned by '104' RT at priority 5.
Sep  6 22:43:30 fido rtkit-daemon[1690]: Supervising 2 threads of 1 processes of 1 users.
Sep  6 22:43:30 fido NetworkManager[992]: <info> (eth0): carrier now ON (device state 20)
Sep  6 22:43:30 fido NetworkManager[992]: <info> (eth0): device state change: unavailable -> disconnected (reason 'carrier-changed') [20 30 40]
Sep  6 22:43:30 fido NetworkManager[992]: <info> Auto-activating connection 'Wired connection 1'.
Sep  6 22:43:30 fido NetworkManager[992]: <info> Activation (eth0) starting connection 'Wired connection 1'
Sep  6 22:43:30 fido NetworkManager[992]: <info> (eth0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Sep  6 22:43:30 fido NetworkManager[992]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Sep  6 22:43:30 fido NetworkManager[992]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Sep  6 22:43:30 fido NetworkManager[992]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Sep  6 22:43:30 fido NetworkManager[992]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Sep  6 22:43:30 fido NetworkManager[992]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Sep  6 22:43:30 fido NetworkManager[992]: <info> (eth0): device state change: prepare -> config (reason 'none') [40 50 0]
Sep  6 22:43:30 fido NetworkManager[992]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Sep  6 22:43:30 fido NetworkManager[992]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Sep  6 22:43:30 fido NetworkManager[992]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Sep  6 22:43:30 fido NetworkManager[992]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Sep  6 22:43:30 fido NetworkManager[992]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
Sep  6 22:43:30 fido NetworkManager[992]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Sep  6 22:43:30 fido NetworkManager[992]: <info> dhclient started with pid 1703
Sep  6 22:43:30 fido kernel: [   36.837069] r8169 0000:03:00.0: eth0: link up
Sep  6 22:43:30 fido kernel: [   36.837429] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Sep  6 22:43:30 fido NetworkManager[992]: <info> Activation (eth0) Beginning IP6 addrconf.
Sep  6 22:43:30 fido dhclient: Internet Systems Consortium DHCP Client 4.1-ESV-R4
Sep  6 22:43:30 fido dhclient: Copyright 2004-2011 Internet Systems Consortium.
Sep  6 22:43:30 fido dhclient: All rights reserved.
Sep  6 22:43:30 fido dhclient: For info, please visit https://www.isc.org/software/dhcp/
Sep  6 22:43:30 fido dhclient: 
Sep  6 22:43:30 fido NetworkManager[992]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Sep  6 22:43:30 fido NetworkManager[992]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Sep  6 22:43:30 fido dhclient: Listening on LPF/eth0/bc:5f:f4:77:66:52
Sep  6 22:43:30 fido dhclient: Sending on   LPF/eth0/bc:5f:f4:77:66:52
Sep  6 22:43:30 fido dhclient: Sending on   Socket/fallback
Sep  6 22:43:30 fido dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Sep  6 22:43:31 fido rtkit-daemon[1690]: Successfully made thread 1706 of process 1688 (n/a) owned by '104' RT at priority 5.
Sep  6 22:43:31 fido rtkit-daemon[1690]: Supervising 3 threads of 1 processes of 1 users.
Sep  6 22:43:31 fido rtkit-daemon[1690]: Successfully made thread 1707 of process 1688 (n/a) owned by '104' RT at priority 5.
Sep  6 22:43:31 fido rtkit-daemon[1690]: Supervising 4 threads of 1 processes of 1 users.
Sep  6 22:43:31 fido rtkit-daemon[1690]: Successfully made thread 1710 of process 1710 (n/a) owned by '104' high priority at nice level -11.
Sep  6 22:43:31 fido rtkit-daemon[1690]: Supervising 5 threads of 2 processes of 1 users.
Sep  6 22:43:31 fido pulseaudio[1710]: [pulseaudio] pid.c: Daemon already running.
Sep  6 22:43:31 fido udev-configure-printer: add /devices/pnp0/00:09/printer/lp0
Sep  6 22:43:31 fido udev-configure-printer: Failed to get parent
Sep  6 22:43:31 fido udev-configure-printer: add /module/lp
Sep  6 22:43:31 fido udev-configure-printer: Failed to get parent
Sep  6 22:43:31 fido udev-configure-printer: add /module/lpc_ich
Sep  6 22:43:31 fido udev-configure-printer: Failed to get parent
Sep  6 22:43:32 fido avahi-daemon[1031]: Joining mDNS multicast group on interface eth0.IPv6 with address fe80::be5f:f4ff:fe77:6652.
Sep  6 22:43:32 fido avahi-daemon[1031]: New relevant interface eth0.IPv6 for mDNS.
Sep  6 22:43:32 fido avahi-daemon[1031]: Registering new address record for fe80::be5f:f4ff:fe77:6652 on eth0.*.
Sep  6 22:43:33 fido dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Sep  6 22:43:34 fido dhclient: DHCPREQUEST of 192.168.178.30 on eth0 to 255.255.255.255 port 67
Sep  6 22:43:34 fido dhclient: DHCPOFFER of 192.168.178.30 from 192.168.178.1
Sep  6 22:43:35 fido dhclient: DHCPACK of 192.168.178.30 from 192.168.178.1
Sep  6 22:43:35 fido dhclient: bound to 192.168.178.30 -- renewal in 383484 seconds.
Sep  6 22:43:35 fido NetworkManager[992]: <info> (eth0): DHCPv4 state changed preinit -> bound
Sep  6 22:43:35 fido NetworkManager[992]: <info>   address 192.168.178.30
Sep  6 22:43:35 fido NetworkManager[992]: <info>   prefix 24 (255.255.255.0)
Sep  6 22:43:35 fido NetworkManager[992]: <info>   gateway 192.168.178.1
Sep  6 22:43:35 fido NetworkManager[992]: <info>   nameserver '192.168.178.1'
Sep  6 22:43:35 fido NetworkManager[992]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Sep  6 22:43:35 fido NetworkManager[992]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) started...
Sep  6 22:43:35 fido avahi-daemon[1031]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.178.30.
Sep  6 22:43:35 fido avahi-daemon[1031]: New relevant interface eth0.IPv4 for mDNS.
Sep  6 22:43:35 fido avahi-daemon[1031]: Registering new address record for 192.168.178.30 on eth0.IPv4.
Sep  6 22:43:35 fido rtkit-daemon[1690]: Successfully made thread 1868 of process 1868 (n/a) owned by '1000' high priority at nice level -11.
Sep  6 22:43:35 fido rtkit-daemon[1690]: Supervising 5 threads of 2 processes of 2 users.
Sep  6 22:43:35 fido dbus[952]: [system] Activating service name='org.freedesktop.UDisks' (using servicehelper)
Sep  6 22:43:35 fido dbus[952]: [system] Successfully activated service 'org.freedesktop.UDisks'
Sep  6 22:43:36 fido NetworkManager[992]: <info> DNS: starting dnsmasq...
Sep  6 22:43:36 fido NetworkManager[992]: <info> (eth0): writing resolv.conf to /sbin/resolvconf
Sep  6 22:43:36 fido dnsmasq[1895]: started, version 2.59 cache disabled
Sep  6 22:43:36 fido dnsmasq[1895]: compile time options: IPv6 GNU-getopt DBus i18n DHCP TFTP conntrack IDN
Sep  6 22:43:36 fido dnsmasq[1895]: using nameserver 192.168.178.1#53
Sep  6 22:43:36 fido rtkit-daemon[1690]: Successfully made thread 1933 of process 1868 (n/a) owned by '1000' RT at priority 5.
Sep  6 22:43:36 fido rtkit-daemon[1690]: Supervising 6 threads of 2 processes of 2 users.
Sep  6 22:43:36 fido rtkit-daemon[1690]: Successfully made thread 1942 of process 1868 (n/a) owned by '1000' RT at priority 5.
Sep  6 22:43:36 fido rtkit-daemon[1690]: Supervising 7 threads of 2 processes of 2 users.
Sep  6 22:43:36 fido NetworkManager[992]: <info> (eth0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Sep  6 22:43:36 fido rtkit-daemon[1690]: Successfully made thread 1943 of process 1868 (n/a) owned by '1000' RT at priority 5.
Sep  6 22:43:36 fido rtkit-daemon[1690]: Supervising 8 threads of 2 processes of 2 users.
Sep  6 22:43:36 fido NetworkManager[992]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Sep  6 22:43:36 fido NetworkManager[992]: <info> Activation (eth0) successful, device activated.
Sep  6 22:43:36 fido NetworkManager[992]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) complete.
Sep  6 22:43:36 fido dbus[952]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Sep  6 22:43:36 fido dbus[952]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Sep  6 22:43:44 fido ntpdate[1978]: step time server 91.189.94.4 offset -0.577593 sec
Sep  6 22:43:50 fido goa[2292]: goa-daemon version 3.4.0 starting [main.c:112, main()]
Sep  6 22:43:50 fido NetworkManager[992]: <info> (eth0): IP6 addrconf timed out or failed.
Sep  6 22:43:50 fido NetworkManager[992]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Sep  6 22:43:50 fido NetworkManager[992]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Sep  6 22:43:50 fido NetworkManager[992]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Sep  6 22:44:37 fido dbus[952]: [system] Activating service name='org.freedesktop.PackageKit' (using servicehelper)
Sep  6 22:44:37 fido dbus[952]: [system] Activating service name='com.ubuntu.SystemService' (using servicehelper)
Sep  6 22:44:37 fido dbus[952]: [system] Successfully activated service 'com.ubuntu.SystemService'
Sep  6 22:44:37 fido AptDaemon: INFO: Initializing daemon
Sep  6 22:44:37 fido AptDaemon.PackageKit: INFO: Initializing PackageKit compat layer
Sep  6 22:44:37 fido dbus[952]: [system] Successfully activated service 'org.freedesktop.PackageKit'
Sep  6 22:44:37 fido AptDaemon.PackageKit: INFO: Initializing PackageKit transaction
Sep  6 22:44:37 fido AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/f5744abe3d5b44d095f4b0ada7e70ead
Sep  6 22:44:37 fido AptDaemon.Worker: INFO: Processing transaction /org/debian/apt/transaction/f5744abe3d5b44d095f4b0ada7e70ead
Sep  6 22:44:37 fido AptDaemon.PackageKit: INFO: Get updates()
Sep  6 22:44:38 fido AptDaemon.Worker: INFO: Finished transaction /org/debian/apt/transaction/f5744abe3d5b44d095f4b0ada7e70ead
Sep  6 22:48:38 fido kernel: [  343.953183] audit_printk_skb: 39 callbacks suppressed
Sep  6 22:48:38 fido kernel: [  343.953187] type=1400 audit(1378500518.098:25): apparmor="DENIED" operation="capable" parent=1 profile="/usr/sbin/cupsd" pid=1021 comm="cupsd" pid=1021 comm="cupsd" capability=36  capname="block_suspend"
Sep  6 22:50:37 fido AptDaemon: INFO: Quitting due to inactivity
Sep  6 22:50:37 fido AptDaemon: INFO: Quitting was requested
Sep  6 22:57:37 fido kernel: [  881.755413] type=1400 audit(1378501057.118:26): apparmor="DENIED" operation="capable" parent=1 profile="/usr/sbin/cupsd" pid=1021 comm="cupsd" pid=1021 comm="cupsd" capability=36  capname="block_suspend"
Sep  6 22:59:38 fido kernel: Kernel logging (proc) stopped.
Sep  6 22:59:38 fido rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="951" x-info="http://www.rsyslog.com"] exiting on signal 15.
```

```
Sep  7 12:27:36 fido kernel: imklog 5.8.6, log source = /proc/kmsg started.
Sep  7 12:27:36 fido rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="1010" x-info="http://www.rsyslog.com"] start
Sep  7 12:27:36 fido rsyslogd: rsyslogd's groupid changed to 103
Sep  7 12:27:36 fido rsyslogd: rsyslogd's userid changed to 101
Sep  7 12:27:36 fido rsyslogd-2039: Could not open output pipe '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Sep  7 12:27:36 fido kernel: [    0.000000] Initializing cgroup subsys cpuset
Sep  7 12:27:36 fido kernel: [    0.000000] Initializing cgroup subsys cpu
Sep  7 12:27:36 fido kernel: [    0.000000] Linux version 3.5.0-39-generic (buildd@roseapple) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #60~precise1-Ubuntu SMP Wed Aug 14 15:38:41 UTC 2013 (Ubuntu 3.5.0-39.60~precise1-generic 3.5.7.17)
Sep  7 12:27:36 fido kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-39-generic root=UUID=91fecb0e-d9e8-4f00-9750-79cb66f9feb3 ro
Sep  7 12:27:36 fido kernel: [    0.000000] KERNEL supported cpus:
Sep  7 12:27:36 fido kernel: [    0.000000]   Intel GenuineIntel
Sep  7 12:27:36 fido kernel: [    0.000000]   AMD AuthenticAMD
Sep  7 12:27:36 fido kernel: [    0.000000]   Centaur CentaurHauls
Sep  7 12:27:36 fido kernel: [    0.000000] e820: BIOS-provided physical RAM map:
Sep  7 12:27:36 fido kernel: [    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009d7ff] usable
Sep  7 12:27:36 fido kernel: [    0.000000] BIOS-e820: [mem 0x000000000009d800-0x000000000009ffff] reserved
Sep  7 12:27:36 fido kernel: [    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
Sep  7 12:27:36 fido kernel: [    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000dd5b1fff] usable
Sep  7 12:27:36 fido kernel: [    0.000000] BIOS-e820: [mem 0x00000000dd5b2000-0x00000000de001fff] reserved
Sep  7 12:27:36 fido kernel: [    0.000000] BIOS-e820: [mem 0x00000000de002000-0x00000000de08bfff] usable
Sep  7 12:27:36 fido kernel: [    0.000000] BIOS-e820: [mem 0x00000000de08c000-0x00000000de12bfff] ACPI NVS
Sep  7 12:27:36 fido kernel: [    0.000000] BIOS-e820: [mem 0x00000000de12c000-0x00000000de915fff] reserved
Sep  7 12:27:36 fido kernel: [    0.000000] BIOS-e820: [mem 0x00000000de916000-0x00000000de916fff] usable
Sep  7 12:27:36 fido kernel: [    0.000000] BIOS-e820: [mem 0x00000000de917000-0x00000000de959fff] ACPI NVS
Sep  7 12:27:36 fido kernel: [    0.000000] BIOS-e820: [mem 0x00000000de95a000-0x00000000df3e5fff] usable
Sep  7 12:27:36 fido kernel: [    0.000000] BIOS-e820: [mem 0x00000000df3e6000-0x00000000df7f0fff] reserved
Sep  7 12:27:36 fido kernel: [    0.000000] BIOS-e820: [mem 0x00000000df7f1000-0x00000000df7fffff] usable
Sep  7 12:27:36 fido kernel: [    0.000000] BIOS-e820: [mem 0x00000000f8000000-0x00000000fbffffff] reserved
Sep  7 12:27:36 fido kernel: [    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
Sep  7 12:27:36 fido kernel: [    0.000000] BIOS-e820: [mem 0x00000000fed00000-0x00000000fed03fff] reserved
Sep  7 12:27:36 fido kernel: [    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
Sep  7 12:27:36 fido kernel: [    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
Sep  7 12:27:36 fido kernel: [    0.000000] BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
Sep  7 12:27:36 fido kernel: [    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000021effffff] usable
Sep  7 12:27:36 fido kernel: [    0.000000] NX (Execute Disable) protection: active
Sep  7 12:27:36 fido kernel: [    0.000000] SMBIOS 2.7 present.
Sep  7 12:27:36 fido kernel: [    0.000000] DMI: To Be Filled By O.E.M. To Be Filled By O.E.M./H77 Pro4-M, BIOS P1.60 09/20/2012
Sep  7 12:27:36 fido kernel: [    0.000000] e820: update [mem 0x00000000-0x0000ffff] usable ==> reserved
Sep  7 12:27:36 fido kernel: [    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
Sep  7 12:27:36 fido kernel: [    0.000000] No AGP bridge found
Sep  7 12:27:36 fido kernel: [    0.000000] e820: last_pfn = 0x21f000 max_arch_pfn = 0x400000000
Sep  7 12:27:36 fido kernel: [    0.000000] MTRR default type: uncachable
Sep  7 12:27:36 fido kernel: [    0.000000] MTRR fixed ranges enabled:
Sep  7 12:27:36 fido kernel: [    0.000000]   00000-9FFFF write-back
Sep  7 12:27:36 fido kernel: [    0.000000]   A0000-BFFFF uncachable
Sep  7 12:27:36 fido kernel: [    0.000000]   C0000-CFFFF write-protect
Sep  7 12:27:36 fido kernel: [    0.000000]   D0000-E7FFF uncachable
Sep  7 12:27:36 fido kernel: [    0.000000]   E8000-FFFFF write-protect
Sep  7 12:27:36 fido kernel: [    0.000000] MTRR variable ranges enabled:
Sep  7 12:27:36 fido kernel: [    0.000000]   0 base 000000000 mask E00000000 write-back
Sep  7 12:27:36 fido kernel: [    0.000000]   1 base 200000000 mask FF0000000 write-back
Sep  7 12:27:36 fido kernel: [    0.000000]   2 base 210000000 mask FF8000000 write-back
Sep  7 12:27:36 fido kernel: [    0.000000]   3 base 218000000 mask FFC000000 write-back
Sep  7 12:27:36 fido kernel: [    0.000000]   4 base 21C000000 mask FFE000000 write-back
Sep  7 12:27:36 fido kernel: [    0.000000]   5 base 21E000000 mask FFF000000 write-back
Sep  7 12:27:36 fido kernel: [    0.000000]   6 base 0E0000000 mask FE0000000 uncachable
Sep  7 12:27:36 fido kernel: [    0.000000]   7 disabled
Sep  7 12:27:36 fido kernel: [    0.000000]   8 disabled
Sep  7 12:27:36 fido kernel: [    0.000000]   9 disabled
Sep  7 12:27:36 fido kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Sep  7 12:27:36 fido kernel: [    0.000000] original variable MTRRs
Sep  7 12:27:36 fido kernel: [    0.000000] reg 0, base: 0GB, range: 8GB, type WB
Sep  7 12:27:36 fido kernel: [    0.000000] reg 1, base: 8GB, range: 256MB, type WB
Sep  7 12:27:36 fido kernel: [    0.000000] reg 2, base: 8448MB, range: 128MB, type WB
Sep  7 12:27:36 fido kernel: [    0.000000] reg 3, base: 8576MB, range: 64MB, type WB
Sep  7 12:27:36 fido kernel: [    0.000000] reg 4, base: 8640MB, range: 32MB, type WB
Sep  7 12:27:36 fido kernel: [    0.000000] reg 5, base: 8672MB, range: 16MB, type WB
Sep  7 12:27:36 fido kernel: [    0.000000] reg 6, base: 3584MB, range: 512MB, type UC
Sep  7 12:27:36 fido kernel: [    0.000000] total RAM covered: 8176M
Sep  7 12:27:36 fido kernel: [    0.000000] Found optimal setting for mtrr clean up
Sep  7 12:27:36 fido kernel: [    0.000000]  gran_size: 64K     chunk_size: 32M     num_reg: 6      lose cover RAM: 0G
Sep  7 12:27:36 fido kernel: [    0.000000] New variable MTRRs
Sep  7 12:27:36 fido kernel: [    0.000000] reg 0, base: 0GB, range: 2GB, type WB
Sep  7 12:27:36 fido kernel: [    0.000000] reg 1, base: 2GB, range: 1GB, type WB
Sep  7 12:27:36 fido kernel: [    0.000000] reg 2, base: 3GB, range: 512MB, type WB
Sep  7 12:27:36 fido kernel: [    0.000000] reg 3, base: 4GB, range: 4GB, type WB
Sep  7 12:27:36 fido kernel: [    0.000000] reg 4, base: 8GB, range: 512MB, type WB
Sep  7 12:27:36 fido kernel: [    0.000000] reg 5, base: 8688MB, range: 16MB, type UC
Sep  7 12:27:36 fido kernel: [    0.000000] e820: update [mem 0xe0000000-0xffffffff] usable ==> reserved
Sep  7 12:27:36 fido kernel: [    0.000000] e820: last_pfn = 0xdf800 max_arch_pfn = 0x400000000
Sep  7 12:27:36 fido kernel: [    0.000000] found SMP MP-table at [mem 0x000fd810-0x000fd81f] mapped at [ffff8800000fd810]
Sep  7 12:27:36 fido kernel: [    0.000000] initial memory mapped: [mem 0x00000000-0x1fffffff]
Sep  7 12:27:36 fido kernel: [    0.000000] Base memory trampoline at [ffff880000097000] 97000 size 24576
Sep  7 12:27:36 fido kernel: [    0.000000] init_memory_mapping: [mem 0x00000000-0xdf7fffff]
Sep  7 12:27:36 fido kernel: [    0.000000]  [mem 0x00000000-0xdf7fffff] page 2M
Sep  7 12:27:36 fido kernel: [    0.000000] kernel direct mapping tables up to 0xdf7fffff @ [mem 0x1fffb000-0x1fffffff]
Sep  7 12:27:36 fido kernel: [    0.000000] init_memory_mapping: [mem 0x100000000-0x21effffff]
Sep  7 12:27:36 fido kernel: [    0.000000]  [mem 0x100000000-0x21effffff] page 2M
Sep  7 12:27:36 fido kernel: [    0.000000] kernel direct mapping tables up to 0x21effffff @ [mem 0xdf7fa000-0xdf7fffff]
Sep  7 12:27:36 fido kernel: [    0.000000] RAMDISK: [mem 0x36208000-0x370fbfff]
Sep  7 12:27:36 fido kernel: [    0.000000] ACPI: RSDP 00000000000f0490 00024 (v02 ALASKA)
Sep  7 12:27:36 fido kernel: [    0.000000] ACPI: XSDT 00000000de110080 0007C (v01 ALASKA    A M I 01072009 AMI  00010013)
Sep  7 12:27:36 fido kernel: [    0.000000] ACPI: FACP 00000000de119cf8 0010C (v05 ALASKA    A M I 01072009 AMI  00010013)
Sep  7 12:27:36 fido kernel: [    0.000000] ACPI: DSDT 00000000de110190 09B65 (v02 ALASKA    A M I 00000022 INTL 20051117)
Sep  7 12:27:36 fido kernel: [    0.000000] ACPI: FACS 00000000de12a080 00040
Sep  7 12:27:36 fido kernel: [    0.000000] ACPI: APIC 00000000de119e08 00072 (v03 ALASKA    A M I 01072009 AMI  00010013)
Sep  7 12:27:36 fido kernel: [    0.000000] ACPI: FPDT 00000000de119e80 00044 (v01 ALASKA    A M I 01072009 AMI  00010013)
Sep  7 12:27:36 fido kernel: [    0.000000] ACPI: MCFG 00000000de119ec8 0003C (v01 ALASKA    A M I 01072009 MSFT 00000097)
Sep  7 12:27:36 fido kernel: [    0.000000] ACPI: SSDT 00000000de119f08 007E1 (v01 Intel_ AoacTabl 00001000 INTL 20091112)
Sep  7 12:27:36 fido kernel: [    0.000000] ACPI: AAFT 00000000de11a6f0 00112 (v01 ALASKA OEMAAFT  01072009 MSFT 00000097)
Sep  7 12:27:36 fido kernel: [    0.000000] ACPI: HPET 00000000de11a808 00038 (v01 ALASKA    A M I 01072009 AMI. 00000005)
Sep  7 12:27:36 fido kernel: [    0.000000] ACPI: SSDT 00000000de11a840 0036D (v01 SataRe SataTabl 00001000 INTL 20091112)
Sep  7 12:27:36 fido kernel: [    0.000000] ACPI: SSDT 00000000de11abb0 009AA (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
Sep  7 12:27:36 fido kernel: [    0.000000] ACPI: SSDT 00000000de11b560 00A92 (v01  PmRef    CpuPm 00003000 INTL 20051117)
Sep  7 12:27:36 fido kernel: [    0.000000] ACPI: BGRT 00000000de11bff8 00038 (v00 ALASKA    A M I 01072009 AMI  00010013)
Sep  7 12:27:36 fido kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Sep  7 12:27:36 fido kernel: [    0.000000] No NUMA configuration found
Sep  7 12:27:36 fido kernel: [    0.000000] Faking a node at [mem 0x0000000000000000-0x000000021effffff]
Sep  7 12:27:36 fido kernel: [    0.000000] Initmem setup node 0 [mem 0x00000000-0x21effffff]
Sep  7 12:27:36 fido kernel: [    0.000000]   NODE_DATA [mem 0x21effc000-0x21effffff]
Sep  7 12:27:36 fido kernel: [    0.000000]  [ffffea0000000000-ffffea00087fffff] PMD -> [ffff880216600000-ffff88021e5fffff] on node 0
Sep  7 12:27:36 fido kernel: [    0.000000] Zone ranges:
Sep  7 12:27:36 fido kernel: [    0.000000]   DMA      [mem 0x00010000-0x00ffffff]
Sep  7 12:27:36 fido kernel: [    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
Sep  7 12:27:36 fido kernel: [    0.000000]   Normal   [mem 0x100000000-0x21effffff]
Sep  7 12:27:36 fido kernel: [    0.000000] Movable zone start for each node
Sep  7 12:27:36 fido kernel: [    0.000000] Early memory node ranges
Sep  7 12:27:36 fido kernel: [    0.000000]   node   0: [mem 0x00010000-0x0009cfff]
Sep  7 12:27:36 fido kernel: [    0.000000]   node   0: [mem 0x00100000-0xdd5b1fff]
Sep  7 12:27:36 fido kernel: [    0.000000]   node   0: [mem 0xde002000-0xde08bfff]
Sep  7 12:27:36 fido kernel: [    0.000000]   node   0: [mem 0xde916000-0xde916fff]
Sep  7 12:27:36 fido kernel: [    0.000000]   node   0: [mem 0xde95a000-0xdf3e5fff]
Sep  7 12:27:36 fido kernel: [    0.000000]   node   0: [mem 0xdf7f1000-0xdf7fffff]
Sep  7 12:27:36 fido kernel: [    0.000000]   node   0: [mem 0x100000000-0x21effffff]
Sep  7 12:27:36 fido kernel: [    0.000000] On node 0 totalpages: 2084965
Sep  7 12:27:36 fido kernel: [    0.000000]   DMA zone: 64 pages used for memmap
Sep  7 12:27:36 fido kernel: [    0.000000]   DMA zone: 6 pages reserved
Sep  7 12:27:36 fido kernel: [    0.000000]   DMA zone: 3911 pages, LIFO batch:0
Sep  7 12:27:36 fido kernel: [    0.000000]   DMA32 zone: 16320 pages used for memmap
Sep  7 12:27:36 fido kernel: [    0.000000]   DMA32 zone: 889112 pages, LIFO batch:31
Sep  7 12:27:36 fido kernel: [    0.000000]   Normal zone: 18368 pages used for memmap
Sep  7 12:27:36 fido kernel: [    0.000000]   Normal zone: 1157184 pages, LIFO batch:31
Sep  7 12:27:36 fido kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Sep  7 12:27:36 fido kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Sep  7 12:27:36 fido kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Sep  7 12:27:36 fido kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
Sep  7 12:27:36 fido kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
Sep  7 12:27:36 fido kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x06] enabled)
Sep  7 12:27:36 fido kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
Sep  7 12:27:36 fido kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Sep  7 12:27:36 fido kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Sep  7 12:27:36 fido kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Sep  7 12:27:36 fido kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Sep  7 12:27:36 fido kernel: [    0.000000] ACPI: IRQ0 used by override.
Sep  7 12:27:36 fido kernel: [    0.000000] ACPI: IRQ2 used by override.
Sep  7 12:27:36 fido kernel: [    0.000000] ACPI: IRQ9 used by override.
Sep  7 12:27:36 fido kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Sep  7 12:27:36 fido kernel: [    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
Sep  7 12:27:36 fido kernel: [    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
Sep  7 12:27:36 fido kernel: [    0.000000] nr_irqs_gsi: 40
Sep  7 12:27:36 fido kernel: [    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
Sep  7 12:27:36 fido kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
Sep  7 12:27:36 fido kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep  7 12:27:36 fido kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep  7 12:27:36 fido kernel: [    0.000000] PM: Registered nosave memory: 00000000dd5b2000 - 00000000de002000
Sep  7 12:27:36 fido kernel: [    0.000000] PM: Registered nosave memory: 00000000de08c000 - 00000000de12c000
Sep  7 12:27:36 fido kernel: [    0.000000] PM: Registered nosave memory: 00000000de12c000 - 00000000de916000
Sep  7 12:27:36 fido kernel: [    0.000000] PM: Registered nosave memory: 00000000de917000 - 00000000de95a000
Sep  7 12:27:36 fido kernel: [    0.000000] PM: Registered nosave memory: 00000000df3e6000 - 00000000df7f1000
Sep  7 12:27:36 fido kernel: [    0.000000] PM: Registered nosave memory: 00000000df800000 - 00000000f8000000
Sep  7 12:27:36 fido kernel: [    0.000000] PM: Registered nosave memory: 00000000f8000000 - 00000000fc000000
Sep  7 12:27:36 fido kernel: [    0.000000] PM: Registered nosave memory: 00000000fc000000 - 00000000fec00000
Sep  7 12:27:36 fido kernel: [    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
Sep  7 12:27:36 fido kernel: [    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fed00000
Sep  7 12:27:36 fido kernel: [    0.000000] PM: Registered nosave memory: 00000000fed00000 - 00000000fed04000
Sep  7 12:27:36 fido kernel: [    0.000000] PM: Registered nosave memory: 00000000fed04000 - 00000000fed1c000
Sep  7 12:27:36 fido kernel: [    0.000000] PM: Registered nosave memory: 00000000fed1c000 - 00000000fed20000
Sep  7 12:27:36 fido kernel: [    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fee00000
Sep  7 12:27:36 fido kernel: [    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
Sep  7 12:27:36 fido kernel: [    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ff000000
Sep  7 12:27:36 fido kernel: [    0.000000] PM: Registered nosave memory: 00000000ff000000 - 0000000100000000
Sep  7 12:27:36 fido kernel: [    0.000000] e820: [mem 0xdf800000-0xf7ffffff] available for PCI devices
Sep  7 12:27:36 fido kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Sep  7 12:27:36 fido kernel: [    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
Sep  7 12:27:36 fido kernel: [    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88021ec00000 s83584 r8192 d22912 u524288
Sep  7 12:27:36 fido kernel: [    0.000000] pcpu-alloc: s83584 r8192 d22912 u524288 alloc=1*2097152
Sep  7 12:27:36 fido kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3
Sep  7 12:27:36 fido kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2050207
Sep  7 12:27:36 fido kernel: [    0.000000] Policy zone: Normal
Sep  7 12:27:36 fido kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-39-generic root=UUID=91fecb0e-d9e8-4f00-9750-79cb66f9feb3 ro
Sep  7 12:27:36 fido kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Sep  7 12:27:36 fido kernel: [    0.000000] __ex_table already sorted, skipping sort
Sep  7 12:27:36 fido kernel: [    0.000000] xsave/xrstor: enabled xstate_bv 0x7, cntxt size 0x340
Sep  7 12:27:36 fido kernel: [    0.000000] Checking aperture...
Sep  7 12:27:36 fido kernel: [    0.000000] No AGP bridge found
Sep  7 12:27:36 fido kernel: [    0.000000] Calgary: detecting Calgary via BIOS EBDA area
Sep  7 12:27:36 fido kernel: [    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
Sep  7 12:27:36 fido kernel: [    0.000000] Memory: 8111084k/8896512k available (6825k kernel code, 556652k absent, 228776k reserved, 6343k data, 948k init)
Sep  7 12:27:36 fido kernel: [    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Sep  7 12:27:36 fido kernel: [    0.000000] Hierarchical RCU implementation.
Sep  7 12:27:36 fido kernel: [    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
Sep  7 12:27:36 fido kernel: [    0.000000] NR_IRQS:16640 nr_irqs:712 16
Sep  7 12:27:36 fido kernel: [    0.000000] Extended CMOS year: 2000
Sep  7 12:27:36 fido kernel: [    0.000000] Console: colour VGA+ 80x25
Sep  7 12:27:36 fido kernel: [    0.000000] console [tty0] enabled
Sep  7 12:27:36 fido kernel: [    0.000000] allocated 33554432 bytes of page_cgroup
Sep  7 12:27:36 fido kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Sep  7 12:27:36 fido kernel: [    0.000000] hpet clockevent registered
Sep  7 12:27:36 fido kernel: [    0.000000] Fast TSC calibration using PIT
Sep  7 12:27:36 fido kernel: [    0.004000] Detected 3193.045 MHz processor.
Sep  7 12:27:36 fido kernel: [    0.000002] Calibrating delay loop (skipped), value calculated using timer frequency.. 6386.09 BogoMIPS (lpj=12772180)
Sep  7 12:27:36 fido kernel: [    0.000097] pid_max: default: 32768 minimum: 301
Sep  7 12:27:36 fido kernel: [    0.000157] Security Framework initialized
Sep  7 12:27:36 fido kernel: [    0.000210] AppArmor: AppArmor initialized
Sep  7 12:27:36 fido kernel: [    0.000256] Yama: becoming mindful.
Sep  7 12:27:36 fido kernel: [    0.000672] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
Sep  7 12:27:36 fido kernel: [    0.002236] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
Sep  7 12:27:36 fido kernel: [    0.002951] Mount-cache hash table entries: 256
Sep  7 12:27:36 fido kernel: [    0.003108] Initializing cgroup subsys cpuacct
Sep  7 12:27:36 fido kernel: [    0.003155] Initializing cgroup subsys memory
Sep  7 12:27:36 fido kernel: [    0.003205] Initializing cgroup subsys devices
Sep  7 12:27:36 fido kernel: [    0.003252] Initializing cgroup subsys freezer
Sep  7 12:27:36 fido kernel: [    0.003298] Initializing cgroup subsys blkio
Sep  7 12:27:36 fido kernel: [    0.003344] Initializing cgroup subsys perf_event
Sep  7 12:27:36 fido kernel: [    0.003408] CPU: Physical Processor ID: 0
Sep  7 12:27:36 fido kernel: [    0.003453] CPU: Processor Core ID: 0
Sep  7 12:27:36 fido kernel: [    0.003500] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
Sep  7 12:27:36 fido kernel: [    0.003500] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
Sep  7 12:27:36 fido kernel: [    0.003846] mce: CPU supports 9 MCE banks
Sep  7 12:27:36 fido kernel: [    0.003901] CPU0: Thermal monitoring enabled (TM1)
Sep  7 12:27:36 fido kernel: [    0.003954] using mwait in idle threads.
Sep  7 12:27:36 fido kernel: [    0.005603] ACPI: Core revision 20120320
Sep  7 12:27:36 fido kernel: [    0.011759] ftrace: allocating 27634 entries in 108 pages
Sep  7 12:27:36 fido kernel: [    0.022107] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Sep  7 12:27:36 fido kernel: [    0.061752] CPU0: Intel(R) Core(TM) i5-3470 CPU @ 3.20GHz stepping 09
Sep  7 12:27:36 fido kernel: [    0.167895] Performance Events: PEBS fmt1+, 16-deep LBR, SandyBridge events, Intel PMU driver.
Sep  7 12:27:36 fido kernel: [    0.168071] ... version:                3
Sep  7 12:27:36 fido kernel: [    0.168117] ... bit width:              48
Sep  7 12:27:36 fido kernel: [    0.168162] ... generic registers:      8
Sep  7 12:27:36 fido kernel: [    0.168207] ... value mask:             0000ffffffffffff
Sep  7 12:27:36 fido kernel: [    0.168254] ... max period:             000000007fffffff
Sep  7 12:27:36 fido kernel: [    0.168301] ... fixed-purpose events:   3
Sep  7 12:27:36 fido kernel: [    0.168346] ... event mask:             00000007000000ff
Sep  7 12:27:36 fido kernel: [    0.168479] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
Sep  7 12:27:36 fido kernel: [    0.168591] Booting Node   0, Processors  #1 #2 #3 Ok.
Sep  7 12:27:36 fido kernel: [    0.209074] Brought up 4 CPUs
Sep  7 12:27:36 fido kernel: [    0.209121] Total of 4 processors activated (25544.36 BogoMIPS).
Sep  7 12:27:36 fido kernel: [    0.211907] devtmpfs: initialized
Sep  7 12:27:36 fido kernel: [    0.212704] EVM: security.selinux
Sep  7 12:27:36 fido kernel: [    0.212748] EVM: security.SMACK64
Sep  7 12:27:36 fido kernel: [    0.212793] EVM: security.capability
Sep  7 12:27:36 fido kernel: [    0.212859] PM: Registering ACPI NVS region [mem 0xde08c000-0xde12bfff] (655360 bytes)
Sep  7 12:27:36 fido kernel: [    0.212928] PM: Registering ACPI NVS region [mem 0xde917000-0xde959fff] (274432 bytes)
Sep  7 12:27:36 fido kernel: [    0.218678] dummy:
Sep  7 12:27:36 fido kernel: [    0.218746] RTC time: 10:27:31, date: 09/07/13
Sep  7 12:27:36 fido kernel: [    0.218813] NET: Registered protocol family 16
Sep  7 12:27:36 fido kernel: [    0.218915] Trying to unpack rootfs image as initramfs...
Sep  7 12:27:36 fido kernel: [    0.218982] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
Sep  7 12:27:36 fido kernel: [    0.219045] ACPI: bus type pci registered
Sep  7 12:27:36 fido kernel: [    0.219122] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
Sep  7 12:27:36 fido kernel: [    0.219187] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
Sep  7 12:27:36 fido kernel: [    0.224245] PCI: Using configuration type 1 for base access
Sep  7 12:27:36 fido kernel: [    0.224847] bio: create slab <bio-0> at 0
Sep  7 12:27:36 fido kernel: [    0.224935] ACPI: Added _OSI(Module Device)
Sep  7 12:27:36 fido kernel: [    0.224980] ACPI: Added _OSI(Processor Device)
Sep  7 12:27:36 fido kernel: [    0.225025] ACPI: Added _OSI(3.0 _SCP Extensions)
Sep  7 12:27:36 fido kernel: [    0.225071] ACPI: Added _OSI(Processor Aggregator Device)
Sep  7 12:27:36 fido kernel: [    0.226105] ACPI: EC: Look up EC in DSDT
Sep  7 12:27:36 fido kernel: [    0.227233] ACPI: Executed 1 blocks of module-level executable AML code
Sep  7 12:27:36 fido kernel: [    0.271960] ACPI: SSDT 00000000ddfaf018 0083B (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
Sep  7 12:27:36 fido kernel: [    0.272326] ACPI: Dynamic OEM Table Load:
Sep  7 12:27:36 fido kernel: [    0.272426] ACPI: SSDT           (null) 0083B (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
Sep  7 12:27:36 fido kernel: [    0.307733] ACPI: SSDT 00000000ddfb0a98 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
Sep  7 12:27:36 fido kernel: [    0.308118] ACPI: Dynamic OEM Table Load:
Sep  7 12:27:36 fido kernel: [    0.308219] ACPI: SSDT           (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
Sep  7 12:27:36 fido kernel: [    0.327590] ACPI: SSDT 00000000ddfb1c18 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
Sep  7 12:27:36 fido kernel: [    0.327954] ACPI: Dynamic OEM Table Load:
Sep  7 12:27:36 fido kernel: [    0.328054] ACPI: SSDT           (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
Sep  7 12:27:36 fido kernel: [    0.355870] ACPI: Interpreter enabled
Sep  7 12:27:36 fido kernel: [    0.355917] ACPI: (supports S0 S3 S4 S5)
Sep  7 12:27:36 fido kernel: [    0.356085] ACPI: Using IOAPIC for interrupt routing
Sep  7 12:27:36 fido kernel: [    0.359978] ACPI: No dock devices found.
Sep  7 12:27:36 fido kernel: [    0.360026] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Sep  7 12:27:36 fido kernel: [    0.360297] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
Sep  7 12:27:36 fido kernel: [    0.360618] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
Sep  7 12:27:36 fido kernel: [    0.360669] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
Sep  7 12:27:36 fido kernel: [    0.360718] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
Sep  7 12:27:36 fido kernel: [    0.360779] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000d3fff]
Sep  7 12:27:36 fido kernel: [    0.360841] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff]
Sep  7 12:27:36 fido kernel: [    0.360903] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff]
Sep  7 12:27:36 fido kernel: [    0.360964] pci_root PNP0A08:00: host bridge window [mem 0x000dc000-0x000dffff]
Sep  7 12:27:36 fido kernel: [    0.361026] pci_root PNP0A08:00: host bridge window [mem 0x000e0000-0x000e3fff]
Sep  7 12:27:36 fido kernel: [    0.361087] pci_root PNP0A08:00: host bridge window [mem 0x000e4000-0x000e7fff]
Sep  7 12:27:36 fido kernel: [    0.361149] pci_root PNP0A08:00: host bridge window [mem 0xe0000000-0xfeafffff]
Sep  7 12:27:36 fido kernel: [    0.361229] PCI host bridge to bus 0000:00
Sep  7 12:27:36 fido kernel: [    0.361275] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
Sep  7 12:27:36 fido kernel: [    0.361323] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
Sep  7 12:27:36 fido kernel: [    0.361371] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
Sep  7 12:27:36 fido kernel: [    0.361420] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000d3fff]
Sep  7 12:27:36 fido kernel: [    0.361469] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff]
Sep  7 12:27:36 fido kernel: [    0.361519] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff]
Sep  7 12:27:36 fido kernel: [    0.361568] pci_bus 0000:00: root bus resource [mem 0x000dc000-0x000dffff]
Sep  7 12:27:36 fido kernel: [    0.361617] pci_bus 0000:00: root bus resource [mem 0x000e0000-0x000e3fff]
Sep  7 12:27:36 fido kernel: [    0.361666] pci_bus 0000:00: root bus resource [mem 0x000e4000-0x000e7fff]
Sep  7 12:27:36 fido kernel: [    0.361715] pci_bus 0000:00: root bus resource [mem 0xe0000000-0xfeafffff]
Sep  7 12:27:36 fido kernel: [    0.361770] pci 0000:00:00.0: [8086:0150] type 00 class 0x060000
Sep  7 12:27:36 fido kernel: [    0.361797] pci 0000:00:01.0: [8086:0151] type 01 class 0x060400
Sep  7 12:27:36 fido kernel: [    0.361821] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
Sep  7 12:27:36 fido kernel: [    0.361856] pci 0000:00:14.0: [8086:1e31] type 00 class 0x0c0330
Sep  7 12:27:36 fido kernel: [    0.361877] pci 0000:00:14.0: reg 10: [mem 0xf7200000-0xf720ffff 64bit]
Sep  7 12:27:36 fido kernel: [    0.361943] pci 0000:00:14.0: PME# supported from D3hot D3cold
Sep  7 12:27:36 fido kernel: [    0.361964] pci 0000:00:16.0: [8086:1e3a] type 00 class 0x078000
Sep  7 12:27:36 fido kernel: [    0.361985] pci 0000:00:16.0: reg 10: [mem 0xf721a000-0xf721a00f 64bit]
Sep  7 12:27:36 fido kernel: [    0.362055] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
Sep  7 12:27:36 fido kernel: [    0.362085] pci 0000:00:1a.0: [8086:1e2d] type 00 class 0x0c0320
Sep  7 12:27:36 fido kernel: [    0.362104] pci 0000:00:1a.0: reg 10: [mem 0xf7218000-0xf72183ff]
Sep  7 12:27:36 fido kernel: [    0.362189] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
Sep  7 12:27:36 fido kernel: [    0.362211] pci 0000:00:1b.0: [8086:1e20] type 00 class 0x040300
Sep  7 12:27:36 fido kernel: [    0.362225] pci 0000:00:1b.0: reg 10: [mem 0xf7210000-0xf7213fff 64bit]
Sep  7 12:27:36 fido kernel: [    0.362287] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Sep  7 12:27:36 fido kernel: [    0.362311] pci 0000:00:1c.0: [8086:1e10] type 01 class 0x060400
Sep  7 12:27:36 fido kernel: [    0.362439] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Sep  7 12:27:36 fido kernel: [    0.362473] pci 0000:00:1c.5: [8086:1e1a] type 01 class 0x060400
Sep  7 12:27:36 fido kernel: [    0.362548] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
Sep  7 12:27:36 fido kernel: [    0.362571] pci 0000:00:1c.7: [8086:1e1e] type 01 class 0x060400
Sep  7 12:27:36 fido kernel: [    0.362645] pci 0000:00:1c.7: PME# supported from D0 D3hot D3cold
Sep  7 12:27:36 fido kernel: [    0.362670] pci 0000:00:1d.0: [8086:1e26] type 00 class 0x0c0320
Sep  7 12:27:36 fido kernel: [    0.362689] pci 0000:00:1d.0: reg 10: [mem 0xf7217000-0xf72173ff]
Sep  7 12:27:36 fido kernel: [    0.362775] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
Sep  7 12:27:36 fido kernel: [    0.362797] pci 0000:00:1f.0: [8086:1e4a] type 00 class 0x060100
Sep  7 12:27:36 fido kernel: [    0.362914] pci 0000:00:1f.2: [8086:1e02] type 00 class 0x010601
Sep  7 12:27:36 fido kernel: [    0.362930] pci 0000:00:1f.2: reg 10: [io  0xf070-0xf077]
Sep  7 12:27:36 fido kernel: [    0.362937] pci 0000:00:1f.2: reg 14: [io  0xf060-0xf063]
Sep  7 12:27:36 fido kernel: [    0.362944] pci 0000:00:1f.2: reg 18: [io  0xf050-0xf057]
Sep  7 12:27:36 fido kernel: [    0.362950] pci 0000:00:1f.2: reg 1c: [io  0xf040-0xf043]
Sep  7 12:27:36 fido kernel: [    0.362957] pci 0000:00:1f.2: reg 20: [io  0xf020-0xf03f]
Sep  7 12:27:36 fido kernel: [    0.362964] pci 0000:00:1f.2: reg 24: [mem 0xf7216000-0xf72167ff]
Sep  7 12:27:36 fido kernel: [    0.363004] pci 0000:00:1f.2: PME# supported from D3hot
Sep  7 12:27:36 fido kernel: [    0.363019] pci 0000:00:1f.3: [8086:1e22] type 00 class 0x0c0500
Sep  7 12:27:36 fido kernel: [    0.363032] pci 0000:00:1f.3: reg 10: [mem 0xf7215000-0xf72150ff 64bit]
Sep  7 12:27:36 fido kernel: [    0.363051] pci 0000:00:1f.3: reg 20: [io  0xf000-0xf01f]
Sep  7 12:27:36 fido kernel: [    0.363098] pci 0000:01:00.0: [10de:11c0] type 00 class 0x030000
Sep  7 12:27:36 fido kernel: [    0.363106] pci 0000:01:00.0: reg 10: [mem 0xf6000000-0xf6ffffff]
Sep  7 12:27:36 fido kernel: [    0.363114] pci 0000:01:00.0: reg 14: [mem 0xe8000000-0xefffffff 64bit pref]
Sep  7 12:27:36 fido kernel: [    0.363123] pci 0000:01:00.0: reg 1c: [mem 0xf0000000-0xf1ffffff 64bit pref]
Sep  7 12:27:36 fido kernel: [    0.363128] pci 0000:01:00.0: reg 24: [io  0xe000-0xe07f]
Sep  7 12:27:36 fido kernel: [    0.363134] pci 0000:01:00.0: reg 30: [mem 0xf7000000-0xf707ffff pref]
Sep  7 12:27:36 fido kernel: [    0.363181] pci 0000:01:00.1: [10de:0e0b] type 00 class 0x040300
Sep  7 12:27:36 fido kernel: [    0.363189] pci 0000:01:00.1: reg 10: [mem 0xf7080000-0xf7083fff]
Sep  7 12:27:36 fido kernel: [    0.367442] pci 0000:00:01.0: PCI bridge to [bus 01-01]
Sep  7 12:27:36 fido kernel: [    0.367490] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
Sep  7 12:27:36 fido kernel: [    0.367492] pci 0000:00:01.0:   bridge window [mem 0xf6000000-0xf70fffff]
Sep  7 12:27:36 fido kernel: [    0.367494] pci 0000:00:01.0:   bridge window [mem 0xe8000000-0xf1ffffff 64bit pref]
Sep  7 12:27:36 fido kernel: [    0.367563] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
Sep  7 12:27:36 fido kernel: [    0.367684] pci 0000:03:00.0: [10ec:8168] type 00 class 0x020000
Sep  7 12:27:36 fido kernel: [    0.367703] pci 0000:03:00.0: reg 10: [io  0xd000-0xd0ff]
Sep  7 12:27:36 fido kernel: [    0.367736] pci 0000:03:00.0: reg 18: [mem 0xf2104000-0xf2104fff 64bit pref]
Sep  7 12:27:36 fido kernel: [    0.367757] pci 0000:03:00.0: reg 20: [mem 0xf2100000-0xf2103fff 64bit pref]
Sep  7 12:27:36 fido kernel: [    0.367846] pci 0000:03:00.0: supports D1 D2
Sep  7 12:27:36 fido kernel: [    0.367848] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Sep  7 12:27:36 fido kernel: [    0.375427] pci 0000:00:1c.5: PCI bridge to [bus 03-03]
Sep  7 12:27:36 fido kernel: [    0.375476] pci 0000:00:1c.5:   bridge window [io  0xd000-0xdfff]
Sep  7 12:27:36 fido kernel: [    0.375483] pci 0000:00:1c.5:   bridge window [mem 0xf2100000-0xf21fffff 64bit pref]
Sep  7 12:27:36 fido kernel: [    0.375544] pci 0000:04:00.0: [1b21:0612] type 00 class 0x010601
Sep  7 12:27:36 fido kernel: [    0.375561] pci 0000:04:00.0: reg 10: [io  0xc050-0xc057]
Sep  7 12:27:36 fido kernel: [    0.375574] pci 0000:04:00.0: reg 14: [io  0xc040-0xc043]
Sep  7 12:27:36 fido kernel: [    0.375587] pci 0000:04:00.0: reg 18: [io  0xc030-0xc037]
Sep  7 12:27:36 fido kernel: [    0.375599] pci 0000:04:00.0: reg 1c: [io  0xc020-0xc023]
Sep  7 12:27:36 fido kernel: [    0.375612] pci 0000:04:00.0: reg 20: [io  0xc000-0xc01f]
Sep  7 12:27:36 fido kernel: [    0.375625] pci 0000:04:00.0: reg 24: [mem 0xf7100000-0xf71001ff]
Sep  7 12:27:36 fido kernel: [    0.383406] pci 0000:00:1c.7: PCI bridge to [bus 04-04]
Sep  7 12:27:36 fido kernel: [    0.383455] pci 0000:00:1c.7:   bridge window [io  0xc000-0xcfff]
Sep  7 12:27:36 fido kernel: [    0.383458] pci 0000:00:1c.7:   bridge window [mem 0xf7100000-0xf71fffff]
Sep  7 12:27:36 fido kernel: [    0.383481] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Sep  7 12:27:36 fido kernel: [    0.383568] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
Sep  7 12:27:36 fido kernel: [    0.383592] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
Sep  7 12:27:36 fido kernel: [    0.383611] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP08._PRT]
Sep  7 12:27:36 fido kernel: [    0.383629] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEG0._PRT]
Sep  7 12:27:36 fido kernel: [    0.383718]  pci0000:00: Requesting ACPI _OSC control (0x1d)
Sep  7 12:27:36 fido kernel: [    0.383900]  pci0000:00: ACPI _OSC control (0x18) granted
Sep  7 12:27:36 fido kernel: [    0.386394] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 10 *11 12 14 15)
Sep  7 12:27:36 fido kernel: [    0.386770] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 *10 11 12 14 15)
Sep  7 12:27:36 fido kernel: [    0.387141] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 10 11 12 14 15)
Sep  7 12:27:36 fido kernel: [    0.387518] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 6 10 11 12 14 15)
Sep  7 12:27:36 fido kernel: [    0.387891] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
Sep  7 12:27:36 fido kernel: [    0.388329] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
Sep  7 12:27:36 fido kernel: [    0.388766] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 10 *11 12 14 15)
Sep  7 12:27:36 fido kernel: [    0.389137] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 *10 11 12 14 15)
Sep  7 12:27:36 fido kernel: [    0.389541] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
Sep  7 12:27:36 fido kernel: [    0.389604] vgaarb: loaded
Sep  7 12:27:36 fido kernel: [    0.389647] vgaarb: bridge control possible 0000:01:00.0
Sep  7 12:27:36 fido kernel: [    0.389787] SCSI subsystem initialized
Sep  7 12:27:36 fido kernel: [    0.389857] libata version 3.00 loaded.
Sep  7 12:27:36 fido kernel: [    0.389870] ACPI: bus type usb registered
Sep  7 12:27:36 fido kernel: [    0.389926] usbcore: registered new interface driver usbfs
Sep  7 12:27:36 fido kernel: [    0.389977] usbcore: registered new interface driver hub
Sep  7 12:27:36 fido kernel: [    0.390033] usbcore: registered new device driver usb
Sep  7 12:27:36 fido kernel: [    0.390118] PCI: Using ACPI for IRQ routing
Sep  7 12:27:36 fido kernel: [    0.391307] Freeing initrd memory: 15312k freed
Sep  7 12:27:36 fido kernel: [    0.391665] PCI: pci_cache_line_size set to 64 bytes
Sep  7 12:27:36 fido kernel: [    0.391717] e820: reserve RAM buffer [mem 0x0009d800-0x0009ffff]
Sep  7 12:27:36 fido kernel: [    0.391719] e820: reserve RAM buffer [mem 0xdd5b2000-0xdfffffff]
Sep  7 12:27:36 fido kernel: [    0.391720] e820: reserve RAM buffer [mem 0xde08c000-0xdfffffff]
Sep  7 12:27:36 fido kernel: [    0.391721] e820: reserve RAM buffer [mem 0xde917000-0xdfffffff]
Sep  7 12:27:36 fido kernel: [    0.391722] e820: reserve RAM buffer [mem 0xdf3e6000-0xdfffffff]
Sep  7 12:27:36 fido kernel: [    0.391723] e820: reserve RAM buffer [mem 0xdf800000-0xdfffffff]
Sep  7 12:27:36 fido kernel: [    0.391724] e820: reserve RAM buffer [mem 0x21f000000-0x21fffffff]
Sep  7 12:27:36 fido kernel: [    0.391788] NetLabel: Initializing
Sep  7 12:27:36 fido kernel: [    0.391832] NetLabel:  domain hash size = 128
Sep  7 12:27:36 fido kernel: [    0.391877] NetLabel:  protocols = UNLABELED CIPSOv4
Sep  7 12:27:36 fido kernel: [    0.391931] NetLabel:  unlabeled traffic allowed by default
Sep  7 12:27:36 fido kernel: [    0.392015] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
Sep  7 12:27:36 fido kernel: [    0.392309] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
Sep  7 12:27:36 fido kernel: [    0.394362] Switching to clocksource hpet
Sep  7 12:27:36 fido kernel: [    0.398056] AppArmor: AppArmor Filesystem Enabled
Sep  7 12:27:36 fido kernel: [    0.398116] pnp: PnP ACPI init
Sep  7 12:27:36 fido kernel: [    0.398166] ACPI: bus type pnp registered
Sep  7 12:27:36 fido kernel: [    0.398381] pnp 00:00: [bus 00-3e]
Sep  7 12:27:36 fido kernel: [    0.398383] pnp 00:00: [io  0x0000-0x0cf7 window]
Sep  7 12:27:36 fido kernel: [    0.398384] pnp 00:00: [io  0x0cf8-0x0cff]
Sep  7 12:27:36 fido kernel: [    0.398393] pnp 00:00: [io  0x0d00-0xffff window]
Sep  7 12:27:36 fido kernel: [    0.398394] pnp 00:00: [mem 0x000a0000-0x000bffff window]
Sep  7 12:27:36 fido kernel: [    0.398395] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
Sep  7 12:27:36 fido kernel: [    0.398397] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
Sep  7 12:27:36 fido kernel: [    0.398398] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
Sep  7 12:27:36 fido kernel: [    0.398399] pnp 00:00: [mem 0x000cc000-0x000cffff window]
Sep  7 12:27:36 fido kernel: [    0.398400] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
Sep  7 12:27:36 fido kernel: [    0.398401] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
Sep  7 12:27:36 fido kernel: [    0.398402] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
Sep  7 12:27:36 fido kernel: [    0.398405] pnp 00:00: [mem 0x000dc000-0x000dffff window]
Sep  7 12:27:36 fido kernel: [    0.398406] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
Sep  7 12:27:36 fido kernel: [    0.398407] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
Sep  7 12:27:36 fido kernel: [    0.398408] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
Sep  7 12:27:36 fido kernel: [    0.398409] pnp 00:00: [mem 0x000ec000-0x000effff window]
Sep  7 12:27:36 fido kernel: [    0.398410] pnp 00:00: [mem 0x000f0000-0x000fffff window]
Sep  7 12:27:36 fido kernel: [    0.398412] pnp 00:00: [mem 0xe0000000-0xfeafffff window]
Sep  7 12:27:36 fido kernel: [    0.398413] pnp 00:00: [mem 0x00010000-0x0001ffff window]
Sep  7 12:27:36 fido kernel: [    0.398452] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
Sep  7 12:27:36 fido kernel: [    0.398467] pnp 00:01: [mem 0xfed40000-0xfed44fff]
Sep  7 12:27:36 fido kernel: [    0.398490] system 00:01: [mem 0xfed40000-0xfed44fff] has been reserved
Sep  7 12:27:36 fido kernel: [    0.398540] system 00:01: Plug and Play ACPI device, IDs PNP0c01 (active)
Sep  7 12:27:36 fido kernel: [    0.398548] pnp 00:02: [io  0x0000-0x001f]
Sep  7 12:27:36 fido kernel: [    0.398549] pnp 00:02: [io  0x0081-0x0091]
Sep  7 12:27:36 fido kernel: [    0.398550] pnp 00:02: [io  0x0093-0x009f]
Sep  7 12:27:36 fido kernel: [    0.398551] pnp 00:02: [io  0x00c0-0x00df]
Sep  7 12:27:36 fido kernel: [    0.398552] pnp 00:02: [dma 4]
Sep  7 12:27:36 fido kernel: [    0.398563] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
Sep  7 12:27:36 fido kernel: [    0.398567] pnp 00:03: [mem 0xff000000-0xffffffff]
Sep  7 12:27:36 fido kernel: [    0.398578] pnp 00:03: Plug and Play ACPI device, IDs INT0800 (active)
Sep  7 12:27:36 fido kernel: [    0.398628] pnp 00:04: [mem 0xfed00000-0xfed003ff]
Sep  7 12:27:36 fido kernel: [    0.398639] pnp 00:04: Plug and Play ACPI device, IDs PNP0103 (active)
Sep  7 12:27:36 fido kernel: [    0.398646] pnp 00:05: [io  0x002e-0x002f]
Sep  7 12:27:36 fido kernel: [    0.398647] pnp 00:05: [io  0x004e-0x004f]
Sep  7 12:27:36 fido kernel: [    0.398648] pnp 00:05: [io  0x0061]
Sep  7 12:27:36 fido kernel: [    0.398649] pnp 00:05: [io  0x0063]
Sep  7 12:27:36 fido kernel: [    0.398650] pnp 00:05: [io  0x0065]
Sep  7 12:27:36 fido kernel: [    0.398651] pnp 00:05: [io  0x0067]
Sep  7 12:27:36 fido kernel: [    0.398652] pnp 00:05: [io  0x0070]
Sep  7 12:27:36 fido kernel: [    0.398653] pnp 00:05: [io  0x0080]
Sep  7 12:27:36 fido kernel: [    0.398654] pnp 00:05: [io  0x0092]
Sep  7 12:27:36 fido kernel: [    0.398655] pnp 00:05: [io  0x00b2-0x00b3]
Sep  7 12:27:36 fido kernel: [    0.398656] pnp 00:05: [io  0x0680-0x069f]
Sep  7 12:27:36 fido kernel: [    0.398657] pnp 00:05: [io  0x1000-0x100f]
Sep  7 12:27:36 fido kernel: [    0.398658] pnp 00:05: [io  0xffff]
Sep  7 12:27:36 fido kernel: [    0.398659] pnp 00:05: [io  0xffff]
Sep  7 12:27:36 fido kernel: [    0.398660] pnp 00:05: [io  0x0400-0x0453]
Sep  7 12:27:36 fido kernel: [    0.398661] pnp 00:05: [io  0x0458-0x047f]
Sep  7 12:27:36 fido kernel: [    0.398662] pnp 00:05: [io  0x0500-0x057f]
Sep  7 12:27:36 fido kernel: [    0.398663] pnp 00:05: [io  0x164e-0x164f]
Sep  7 12:27:36 fido kernel: [    0.398687] system 00:05: [io  0x0680-0x069f] has been reserved
Sep  7 12:27:36 fido kernel: [    0.398736] system 00:05: [io  0x1000-0x100f] has been reserved
Sep  7 12:27:36 fido kernel: [    0.398784] system 00:05: [io  0xffff] has been reserved
Sep  7 12:27:36 fido kernel: [    0.398831] system 00:05: [io  0xffff] has been reserved
Sep  7 12:27:36 fido kernel: [    0.398879] system 00:05: [io  0x0400-0x0453] has been reserved
Sep  7 12:27:36 fido kernel: [    0.398927] system 00:05: [io  0x0458-0x047f] has been reserved
Sep  7 12:27:36 fido kernel: [    0.398974] system 00:05: [io  0x0500-0x057f] has been reserved
Sep  7 12:27:36 fido kernel: [    0.399022] system 00:05: [io  0x164e-0x164f] has been reserved
Sep  7 12:27:36 fido kernel: [    0.399071] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
Sep  7 12:27:36 fido kernel: [    0.399075] pnp 00:06: [io  0x0070-0x0077]
Sep  7 12:27:36 fido kernel: [    0.399083] pnp 00:06: [irq 8]
Sep  7 12:27:36 fido kernel: [    0.399095] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
Sep  7 12:27:36 fido kernel: [    0.399110] pnp 00:07: [io  0x0454-0x0457]
Sep  7 12:27:36 fido kernel: [    0.399130] system 00:07: [io  0x0454-0x0457] has been reserved
Sep  7 12:27:36 fido kernel: [    0.399178] system 00:07: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
Sep  7 12:27:36 fido kernel: [    0.399211] pnp 00:08: [io  0x0000-0xffffffffffffffff disabled]
Sep  7 12:27:36 fido kernel: [    0.399213] pnp 00:08: [io  0x0290-0x029f]
Sep  7 12:27:36 fido kernel: [    0.399214] pnp 00:08: [io  0x0000-0xffffffffffffffff disabled]
Sep  7 12:27:36 fido kernel: [    0.399233] system 00:08: [io  0x0290-0x029f] has been reserved
Sep  7 12:27:36 fido kernel: [    0.399282] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
Sep  7 12:27:36 fido kernel: [    0.399483] pnp 00:09: [io  0x0378-0x037f]
Sep  7 12:27:36 fido kernel: [    0.399486] pnp 00:09: [io  0x0778-0x077f]
Sep  7 12:27:36 fido kernel: [    0.399490] pnp 00:09: [irq 5]
Sep  7 12:27:36 fido kernel: [    0.399491] pnp 00:09: [dma 3]
Sep  7 12:27:36 fido kernel: [    0.399563] pnp 00:09: Plug and Play ACPI device, IDs PNP0401 (active)
Sep  7 12:27:36 fido kernel: [    0.399680] pnp 00:0a: [io  0x0010-0x001f]
Sep  7 12:27:36 fido kernel: [    0.399681] pnp 00:0a: [io  0x0022-0x003f]
Sep  7 12:27:36 fido kernel: [    0.399682] pnp 00:0a: [io  0x0044-0x005f]
Sep  7 12:27:36 fido kernel: [    0.399683] pnp 00:0a: [io  0x0062-0x0063]
Sep  7 12:27:36 fido kernel: [    0.399684] pnp 00:0a: [io  0x0065-0x006f]
Sep  7 12:27:36 fido kernel: [    0.399685] pnp 00:0a: [io  0x0072-0x007f]
Sep  7 12:27:36 fido kernel: [    0.399686] pnp 00:0a: [io  0x0080]
Sep  7 12:27:36 fido kernel: [    0.399687] pnp 00:0a: [io  0x0084-0x0086]
Sep  7 12:27:36 fido kernel: [    0.399688] pnp 00:0a: [io  0x0088]
Sep  7 12:27:36 fido kernel: [    0.399689] pnp 00:0a: [io  0x008c-0x008e]
Sep  7 12:27:36 fido kernel: [    0.399690] pnp 00:0a: [io  0x0090-0x009f]
Sep  7 12:27:36 fido kernel: [    0.399691] pnp 00:0a: [io  0x00a2-0x00bf]
Sep  7 12:27:36 fido kernel: [    0.399692] pnp 00:0a: [io  0x00e0-0x00ef]
Sep  7 12:27:36 fido kernel: [    0.399693] pnp 00:0a: [io  0x04d0-0x04d1]
Sep  7 12:27:36 fido kernel: [    0.399716] system 00:0a: [io  0x04d0-0x04d1] has been reserved
Sep  7 12:27:36 fido kernel: [    0.399766] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
Sep  7 12:27:36 fido kernel: [    0.399770] pnp 00:0b: [io  0x00f0-0x00ff]
Sep  7 12:27:36 fido kernel: [    0.399774] pnp 00:0b: [irq 13]
Sep  7 12:27:36 fido kernel: [    0.399787] pnp 00:0b: Plug and Play ACPI device, IDs PNP0c04 (active)
Sep  7 12:27:36 fido kernel: [    0.399799] pnp 00:0c: [io  0x0060]
Sep  7 12:27:36 fido kernel: [    0.399800] pnp 00:0c: [io  0x0064]
Sep  7 12:27:36 fido kernel: [    0.399804] pnp 00:0c: [irq 1]
Sep  7 12:27:36 fido kernel: [    0.399820] pnp 00:0c: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
Sep  7 12:27:36 fido kernel: [    0.399911] pnp 00:0d: [io  0x03f8-0x03ff]
Sep  7 12:27:36 fido kernel: [    0.399915] pnp 00:0d: [irq 4]
Sep  7 12:27:36 fido kernel: [    0.399916] pnp 00:0d: [dma 0 disabled]
Sep  7 12:27:36 fido kernel: [    0.399948] pnp 00:0d: Plug and Play ACPI device, IDs PNP0501 (active)
Sep  7 12:27:36 fido kernel: [    0.400083] pnp 00:0e: [mem 0xfed1c000-0xfed1ffff]
Sep  7 12:27:36 fido kernel: [    0.400084] pnp 00:0e: [mem 0xfed10000-0xfed17fff]
Sep  7 12:27:36 fido kernel: [    0.400085] pnp 00:0e: [mem 0xfed18000-0xfed18fff]
Sep  7 12:27:36 fido kernel: [    0.400086] pnp 00:0e: [mem 0xfed19000-0xfed19fff]
Sep  7 12:27:36 fido kernel: [    0.400087] pnp 00:0e: [mem 0xf8000000-0xfbffffff]
Sep  7 12:27:36 fido kernel: [    0.400089] pnp 00:0e: [mem 0xfed20000-0xfed3ffff]
Sep  7 12:27:36 fido kernel: [    0.400090] pnp 00:0e: [mem 0xfed90000-0xfed93fff]
Sep  7 12:27:36 fido kernel: [    0.400091] pnp 00:0e: [mem 0xfed45000-0xfed8ffff]
Sep  7 12:27:36 fido kernel: [    0.400092] pnp 00:0e: [mem 0xff000000-0xffffffff]
Sep  7 12:27:36 fido kernel: [    0.400093] pnp 00:0e: [mem 0xfee00000-0xfeefffff]
Sep  7 12:27:36 fido kernel: [    0.400094] pnp 00:0e: [mem 0xe0000000-0xe0000fff]
Sep  7 12:27:36 fido kernel: [    0.400125] system 00:0e: [mem 0xfed1c000-0xfed1ffff] has been reserved
Sep  7 12:27:36 fido kernel: [    0.400174] system 00:0e: [mem 0xfed10000-0xfed17fff] has been reserved
Sep  7 12:27:36 fido kernel: [    0.400224] system 00:0e: [mem 0xfed18000-0xfed18fff] has been reserved
Sep  7 12:27:36 fido kernel: [    0.400273] system 00:0e: [mem 0xfed19000-0xfed19fff] has been reserved
Sep  7 12:27:36 fido kernel: [    0.400322] system 00:0e: [mem 0xf8000000-0xfbffffff] has been reserved
Sep  7 12:27:36 fido kernel: [    0.400371] system 00:0e: [mem 0xfed20000-0xfed3ffff] has been reserved
Sep  7 12:27:36 fido kernel: [    0.400420] system 00:0e: [mem 0xfed90000-0xfed93fff] has been reserved
Sep  7 12:27:36 fido kernel: [    0.400469] system 00:0e: [mem 0xfed45000-0xfed8ffff] has been reserved
Sep  7 12:27:36 fido kernel: [    0.400518] system 00:0e: [mem 0xff000000-0xffffffff] has been reserved
Sep  7 12:27:36 fido kernel: [    0.400567] system 00:0e: [mem 0xfee00000-0xfeefffff] could not be reserved
Sep  7 12:27:36 fido kernel: [    0.400616] system 00:0e: [mem 0xe0000000-0xe0000fff] has been reserved
Sep  7 12:27:36 fido kernel: [    0.400666] system 00:0e: Plug and Play ACPI device, IDs PNP0c02 (active)
Sep  7 12:27:36 fido kernel: [    0.400757] pnp: PnP ACPI: found 15 devices
Sep  7 12:27:36 fido kernel: [    0.400801] ACPI: ACPI bus type pnp unregistered
Sep  7 12:27:36 fido kernel: [    0.406473] pci 0000:00:01.0: PCI bridge to [bus 01-01]
Sep  7 12:27:36 fido kernel: [    0.406521] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
Sep  7 12:27:36 fido kernel: [    0.406570] pci 0000:00:01.0:   bridge window [mem 0xf6000000-0xf70fffff]
Sep  7 12:27:36 fido kernel: [    0.406620] pci 0000:00:01.0:   bridge window [mem 0xe8000000-0xf1ffffff 64bit pref]
Sep  7 12:27:36 fido kernel: [    0.406684] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
Sep  7 12:27:36 fido kernel: [    0.406746] pci 0000:00:1c.5: PCI bridge to [bus 03-03]
Sep  7 12:27:36 fido kernel: [    0.406793] pci 0000:00:1c.5:   bridge window [io  0xd000-0xdfff]
Sep  7 12:27:36 fido kernel: [    0.406847] pci 0000:00:1c.5:   bridge window [mem 0xf2100000-0xf21fffff 64bit pref]
Sep  7 12:27:36 fido kernel: [    0.406913] pci 0000:00:1c.7: PCI bridge to [bus 04-04]
Sep  7 12:27:36 fido kernel: [    0.406961] pci 0000:00:1c.7:   bridge window [io  0xc000-0xcfff]
Sep  7 12:27:36 fido kernel: [    0.407012] pci 0000:00:1c.7:   bridge window [mem 0xf7100000-0xf71fffff]
Sep  7 12:27:36 fido kernel: [    0.407090] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
Sep  7 12:27:36 fido kernel: [    0.407092] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
Sep  7 12:27:36 fido kernel: [    0.407093] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
Sep  7 12:27:36 fido kernel: [    0.407094] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000d3fff]
Sep  7 12:27:36 fido kernel: [    0.407096] pci_bus 0000:00: resource 8 [mem 0x000d4000-0x000d7fff]
Sep  7 12:27:36 fido kernel: [    0.407097] pci_bus 0000:00: resource 9 [mem 0x000d8000-0x000dbfff]
Sep  7 12:27:36 fido kernel: [    0.407098] pci_bus 0000:00: resource 10 [mem 0x000dc000-0x000dffff]
Sep  7 12:27:36 fido kernel: [    0.407099] pci_bus 0000:00: resource 11 [mem 0x000e0000-0x000e3fff]
Sep  7 12:27:36 fido kernel: [    0.407100] pci_bus 0000:00: resource 12 [mem 0x000e4000-0x000e7fff]
Sep  7 12:27:36 fido kernel: [    0.407102] pci_bus 0000:00: resource 13 [mem 0xe0000000-0xfeafffff]
Sep  7 12:27:36 fido kernel: [    0.407103] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
Sep  7 12:27:36 fido kernel: [    0.407104] pci_bus 0000:01: resource 1 [mem 0xf6000000-0xf70fffff]
Sep  7 12:27:36 fido kernel: [    0.407105] pci_bus 0000:01: resource 2 [mem 0xe8000000-0xf1ffffff 64bit pref]
Sep  7 12:27:36 fido kernel: [    0.407107] pci_bus 0000:03: resource 0 [io  0xd000-0xdfff]
Sep  7 12:27:36 fido kernel: [    0.407108] pci_bus 0000:03: resource 2 [mem 0xf2100000-0xf21fffff 64bit pref]
Sep  7 12:27:36 fido kernel: [    0.407109] pci_bus 0000:04: resource 0 [io  0xc000-0xcfff]
Sep  7 12:27:36 fido kernel: [    0.407110] pci_bus 0000:04: resource 1 [mem 0xf7100000-0xf71fffff]
Sep  7 12:27:36 fido kernel: [    0.407129] NET: Registered protocol family 2
Sep  7 12:27:36 fido kernel: [    0.407280] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
Sep  7 12:27:36 fido kernel: [    0.407792] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
Sep  7 12:27:36 fido kernel: [    0.408776] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Sep  7 12:27:36 fido kernel: [    0.408934] TCP: Hash tables configured (established 524288 bind 65536)
Sep  7 12:27:36 fido kernel: [    0.408984] TCP: reno registered
Sep  7 12:27:36 fido kernel: [    0.409036] UDP hash table entries: 4096 (order: 5, 131072 bytes)
Sep  7 12:27:36 fido kernel: [    0.409103] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
Sep  7 12:27:36 fido kernel: [    0.409201] NET: Registered protocol family 1
Sep  7 12:27:36 fido kernel: [    0.446319] pci 0000:01:00.0: Boot video device
Sep  7 12:27:36 fido kernel: [    0.446339] PCI: CLS 64 bytes, default 64
Sep  7 12:27:36 fido kernel: [    0.446341] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
Sep  7 12:27:36 fido kernel: [    0.446401] software IO TLB [mem 0xd95b2000-0xdd5b1fff] (64MB) mapped at [ffff8800d95b2000-ffff8800dd5b1fff]
Sep  7 12:27:36 fido kernel: [    0.446750] audit: initializing netlink socket (disabled)
Sep  7 12:27:36 fido kernel: [    0.446802] type=2000 audit(1378549650.336:1): initialized
Sep  7 12:27:36 fido kernel: [    0.463971] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Sep  7 12:27:36 fido kernel: [    0.465112] VFS: Disk quotas dquot_6.5.2
Sep  7 12:27:36 fido kernel: [    0.465179] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Sep  7 12:27:36 fido kernel: [    0.465475] fuse init (API version 7.19)
Sep  7 12:27:36 fido kernel: [    0.465561] msgmni has been set to 15871
Sep  7 12:27:36 fido kernel: [    0.465807] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
Sep  7 12:27:36 fido kernel: [    0.465884] io scheduler noop registered
Sep  7 12:27:36 fido kernel: [    0.465929] io scheduler deadline registered (default)
Sep  7 12:27:36 fido kernel: [    0.465988] io scheduler cfq registered
Sep  7 12:27:36 fido kernel: [    0.466092] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
Sep  7 12:27:36 fido kernel: [    0.466285] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Sep  7 12:27:36 fido kernel: [    0.466340] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Sep  7 12:27:36 fido kernel: [    0.466413] intel_idle: MWAIT substates: 0x1120
Sep  7 12:27:36 fido kernel: [    0.466413] intel_idle: v0.4 model 0x3A
Sep  7 12:27:36 fido kernel: [    0.466414] intel_idle: lapic_timer_reliable_states 0xffffffff
Sep  7 12:27:36 fido kernel: [    0.466467] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
Sep  7 12:27:36 fido kernel: [    0.466533] ACPI: Power Button [PWRB]
Sep  7 12:27:36 fido kernel: [    0.466597] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Sep  7 12:27:36 fido kernel: [    0.466659] ACPI: Power Button [PWRF]
Sep  7 12:27:36 fido kernel: [    0.466761] ACPI: Requesting acpi_cpufreq
Sep  7 12:27:36 fido kernel: [    0.469258] GHES: HEST is not enabled!
Sep  7 12:27:36 fido kernel: [    0.474257] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Sep  7 12:27:36 fido kernel: [    0.494658] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Sep  7 12:27:36 fido kernel: [    0.515645] 00:0d: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Sep  7 12:27:36 fido kernel: [    0.515846] Linux agpgart interface v0.103
Sep  7 12:27:36 fido kernel: [    0.516567] brd: module loaded
Sep  7 12:27:36 fido kernel: [    0.516960] loop: module loaded
Sep  7 12:27:36 fido kernel: [    0.517178] Fixed MDIO Bus: probed
Sep  7 12:27:36 fido kernel: [    0.517242] tun: Universal TUN/TAP device driver, 1.6
Sep  7 12:27:36 fido kernel: [    0.517288] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Sep  7 12:27:36 fido kernel: [    0.517355] PPP generic driver version 2.4.2
Sep  7 12:27:36 fido kernel: [    0.517429] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Sep  7 12:27:36 fido kernel: [    0.517501] ehci_hcd 0000:00:1a.0: setting latency timer to 64
Sep  7 12:27:36 fido kernel: [    0.517504] ehci_hcd 0000:00:1a.0: EHCI Host Controller
Sep  7 12:27:36 fido kernel: [    0.517553] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
Sep  7 12:27:36 fido kernel: [    0.517633] ehci_hcd 0000:00:1a.0: debug port 2
Sep  7 12:27:36 fido kernel: [    0.521538] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
Sep  7 12:27:36 fido kernel: [    0.521549] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xf7218000
Sep  7 12:27:36 fido kernel: [    0.530100] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
Sep  7 12:27:36 fido kernel: [    0.530171] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
Sep  7 12:27:36 fido kernel: [    0.530231] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Sep  7 12:27:36 fido kernel: [    0.530292] usb usb1: Product: EHCI Host Controller
Sep  7 12:27:36 fido kernel: [    0.530338] usb usb1: Manufacturer: Linux 3.5.0-39-generic ehci_hcd
Sep  7 12:27:36 fido kernel: [    0.530386] usb usb1: SerialNumber: 0000:00:1a.0
Sep  7 12:27:36 fido kernel: [    0.530493] hub 1-0:1.0: USB hub found
Sep  7 12:27:36 fido kernel: [    0.530539] hub 1-0:1.0: 2 ports detected
Sep  7 12:27:36 fido kernel: [    0.530623] ehci_hcd 0000:00:1d.0: setting latency timer to 64
Sep  7 12:27:36 fido kernel: [    0.530625] ehci_hcd 0000:00:1d.0: EHCI Host Controller
Sep  7 12:27:36 fido kernel: [    0.530674] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
Sep  7 12:27:36 fido kernel: [    0.530751] ehci_hcd 0000:00:1d.0: debug port 2
Sep  7 12:27:36 fido kernel: [    0.534662] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
Sep  7 12:27:36 fido kernel: [    0.534672] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xf7217000
Sep  7 12:27:36 fido kernel: [    0.546066] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
Sep  7 12:27:36 fido kernel: [    0.546132] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
Sep  7 12:27:36 fido kernel: [    0.546192] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Sep  7 12:27:36 fido kernel: [    0.546253] usb usb2: Product: EHCI Host Controller
Sep  7 12:27:36 fido kernel: [    0.546299] usb usb2: Manufacturer: Linux 3.5.0-39-generic ehci_hcd
Sep  7 12:27:36 fido kernel: [    0.546348] usb usb2: SerialNumber: 0000:00:1d.0
Sep  7 12:27:36 fido kernel: [    0.546447] hub 2-0:1.0: USB hub found
Sep  7 12:27:36 fido kernel: [    0.546493] hub 2-0:1.0: 2 ports detected
Sep  7 12:27:36 fido kernel: [    0.546565] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Sep  7 12:27:36 fido kernel: [    0.546620] uhci_hcd: USB Universal Host Controller Interface driver
Sep  7 12:27:36 fido kernel: [    0.546694] xhci_hcd 0000:00:14.0: setting latency timer to 64
Sep  7 12:27:36 fido kernel: [    0.546696] xhci_hcd 0000:00:14.0: xHCI Host Controller
Sep  7 12:27:36 fido kernel: [    0.546744] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 3
Sep  7 12:27:36 fido kernel: [    0.546876] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
Sep  7 12:27:36 fido kernel: [    0.546912] xhci_hcd 0000:00:14.0: irq 41 for MSI/MSI-X
Sep  7 12:27:36 fido kernel: [    0.546948] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
Sep  7 12:27:36 fido kernel: [    0.546998] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Sep  7 12:27:36 fido kernel: [    0.547060] usb usb3: Product: xHCI Host Controller
Sep  7 12:27:36 fido kernel: [    0.547106] usb usb3: Manufacturer: Linux 3.5.0-39-generic xhci_hcd
Sep  7 12:27:36 fido kernel: [    0.547155] usb usb3: SerialNumber: 0000:00:14.0
Sep  7 12:27:36 fido kernel: [    0.547245] xHCI xhci_add_endpoint called for root hub
Sep  7 12:27:36 fido kernel: [    0.547246] xHCI xhci_check_bandwidth called for root hub
Sep  7 12:27:36 fido kernel: [    0.547257] hub 3-0:1.0: USB hub found
Sep  7 12:27:36 fido kernel: [    0.547307] hub 3-0:1.0: 4 ports detected
Sep  7 12:27:36 fido kernel: [    0.547384] xhci_hcd 0000:00:14.0: xHCI Host Controller
Sep  7 12:27:36 fido kernel: [    0.547431] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 4
Sep  7 12:27:36 fido kernel: [    0.547505] usb usb4: New USB device found, idVendor=1d6b, idProduct=0003
Sep  7 12:27:36 fido kernel: [    0.547554] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Sep  7 12:27:36 fido kernel: [    0.547615] usb usb4: Product: xHCI Host Controller
Sep  7 12:27:36 fido kernel: [    0.547661] usb usb4: Manufacturer: Linux 3.5.0-39-generic xhci_hcd
Sep  7 12:27:36 fido kernel: [    0.547709] usb usb4: SerialNumber: 0000:00:14.0
Sep  7 12:27:36 fido kernel: [    0.547792] xHCI xhci_add_endpoint called for root hub
Sep  7 12:27:36 fido kernel: [    0.547793] xHCI xhci_check_bandwidth called for root hub
Sep  7 12:27:36 fido kernel: [    0.547803] hub 4-0:1.0: USB hub found
Sep  7 12:27:36 fido kernel: [    0.547852] hub 4-0:1.0: 4 ports detected
Sep  7 12:27:36 fido kernel: [    0.547971] usbcore: registered new interface driver libusual
Sep  7 12:27:36 fido kernel: [    0.548040] i8042: PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
Sep  7 12:27:36 fido kernel: [    0.548089] i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
Sep  7 12:27:36 fido kernel: [    0.548632] serio: i8042 KBD port at 0x60,0x64 irq 1
Sep  7 12:27:36 fido kernel: [    0.548741] mousedev: PS/2 mouse device common for all mice
Sep  7 12:27:36 fido kernel: [    0.548858] rtc_cmos 00:06: RTC can wake from S4
Sep  7 12:27:36 fido kernel: [    0.549013] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
Sep  7 12:27:36 fido kernel: [    0.549085] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
Sep  7 12:27:36 fido kernel: [    0.549170] device-mapper: uevent: version 1.0.3
Sep  7 12:27:36 fido kernel: [    0.549247] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
Sep  7 12:27:36 fido kernel: [    0.549353] cpuidle: using governor ladder
Sep  7 12:27:36 fido kernel: [    0.549444] cpuidle: using governor menu
Sep  7 12:27:36 fido kernel: [    0.549489] EFI Variables Facility v0.08 2004-May-17
Sep  7 12:27:36 fido kernel: [    0.549660] ashmem: initialized
Sep  7 12:27:36 fido kernel: [    0.549768] TCP: cubic registered
Sep  7 12:27:36 fido kernel: [    0.549859] NET: Registered protocol family 10
Sep  7 12:27:36 fido kernel: [    0.550005] NET: Registered protocol family 17
Sep  7 12:27:36 fido kernel: [    0.550072] Key type dns_resolver registered
Sep  7 12:27:36 fido kernel: [    0.550291] PM: Hibernation image not present or could not be loaded.
Sep  7 12:27:36 fido kernel: [    0.550297] registered taskstats version 1
Sep  7 12:27:36 fido kernel: [    0.552231] Key type trusted registered
Sep  7 12:27:36 fido kernel: [    0.553916] Key type encrypted registered
Sep  7 12:27:36 fido kernel: [    0.555777]   Magic number: 13:528:476
Sep  7 12:27:36 fido kernel: [    0.555924] rtc_cmos 00:06: setting system clock to 2013-09-07 10:27:31 UTC (1378549651)
Sep  7 12:27:36 fido kernel: [    0.556631] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Sep  7 12:27:36 fido kernel: [    0.556679] EDD information not available.
Sep  7 12:27:36 fido kernel: [    0.557856] Freeing unused kernel memory: 948k freed
Sep  7 12:27:36 fido kernel: [    0.557979] Write protecting the kernel read-only data: 12288k
Sep  7 12:27:36 fido kernel: [    0.560425] Freeing unused kernel memory: 1356k freed
Sep  7 12:27:36 fido kernel: [    0.562402] Freeing unused kernel memory: 1060k freed
Sep  7 12:27:36 fido kernel: [    0.567594] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
Sep  7 12:27:36 fido kernel: [    0.585440] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Sep  7 12:27:36 fido kernel: [    0.585624] r8169 0000:03:00.0: irq 42 for MSI/MSI-X
Sep  7 12:27:36 fido kernel: [    0.585757] r8169 0000:03:00.0: eth0: RTL8168evl/8111evl at 0xffffc90005790000, bc:5f:f4:77:66:52, XID 0c900800 IRQ 42
Sep  7 12:27:36 fido kernel: [    0.585827] r8169 0000:03:00.0: eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
Sep  7 12:27:36 fido kernel: [    0.588767] ahci 0000:00:1f.2: version 3.0
Sep  7 12:27:36 fido kernel: [    0.588810] ahci 0000:00:1f.2: irq 43 for MSI/MSI-X
Sep  7 12:27:36 fido kernel: [    0.602036] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x3f impl SATA mode
Sep  7 12:27:36 fido kernel: [    0.602115] ahci 0000:00:1f.2: flags: 64bit ncq led clo pio slum part ems apst
Sep  7 12:27:36 fido kernel: [    0.602179] ahci 0000:00:1f.2: setting latency timer to 64
Sep  7 12:27:36 fido kernel: [    0.642255] scsi0 : ahci
Sep  7 12:27:36 fido kernel: [    0.642401] scsi1 : ahci
Sep  7 12:27:36 fido kernel: [    0.642545] scsi2 : ahci
Sep  7 12:27:36 fido kernel: [    0.642689] scsi3 : ahci
Sep  7 12:27:36 fido kernel: [    0.642834] scsi4 : ahci
Sep  7 12:27:36 fido kernel: [    0.642998] scsi5 : ahci
Sep  7 12:27:36 fido kernel: [    0.643211] ata1: SATA max UDMA/133 abar m2048@0xf7216000 port 0xf7216100 irq 43
Sep  7 12:27:36 fido kernel: [    0.643273] ata2: SATA max UDMA/133 abar m2048@0xf7216000 port 0xf7216180 irq 43
Sep  7 12:27:36 fido kernel: [    0.643335] ata3: SATA max UDMA/133 abar m2048@0xf7216000 port 0xf7216200 irq 43
Sep  7 12:27:36 fido kernel: [    0.643397] ata4: SATA max UDMA/133 abar m2048@0xf7216000 port 0xf7216280 irq 43
Sep  7 12:27:36 fido kernel: [    0.643459] ata5: SATA max UDMA/133 abar m2048@0xf7216000 port 0xf7216300 irq 43
Sep  7 12:27:36 fido kernel: [    0.643520] ata6: SATA max UDMA/133 abar m2048@0xf7216000 port 0xf7216380 irq 43
Sep  7 12:27:36 fido kernel: [    0.643713] ahci 0000:04:00.0: irq 44 for MSI/MSI-X
Sep  7 12:27:36 fido kernel: [    0.643749] ahci: SSS flag set, parallel bus scan disabled
Sep  7 12:27:36 fido kernel: [    0.643876] ahci 0000:04:00.0: AHCI 0001.0200 32 slots 2 ports 6 Gbps 0x3 impl SATA mode
Sep  7 12:27:36 fido kernel: [    0.643951] ahci 0000:04:00.0: flags: 64bit ncq sntf stag led clo pmp pio slum part ccc sxs
Sep  7 12:27:36 fido kernel: [    0.644168] scsi6 : ahci
Sep  7 12:27:36 fido kernel: [    0.644290] scsi7 : ahci
Sep  7 12:27:36 fido kernel: [    0.644366] ata7: SATA max UDMA/133 abar m512@0xf7100000 port 0xf7100100 irq 44
Sep  7 12:27:36 fido kernel: [    0.644430] ata8: SATA max UDMA/133 abar m512@0xf7100000 port 0xf7100180 irq 44
Sep  7 12:27:36 fido kernel: [    0.841411] usb 1-1: new high-speed USB device number 2 using ehci_hcd
Sep  7 12:27:36 fido kernel: [    0.961171] ata2: SATA link down (SStatus 0 SControl 300)
Sep  7 12:27:36 fido kernel: [    0.961248] ata3: SATA link down (SStatus 0 SControl 300)
Sep  7 12:27:36 fido kernel: [    0.961313] ata5: SATA link down (SStatus 0 SControl 300)
Sep  7 12:27:36 fido kernel: [    0.961388] ata4: SATA link down (SStatus 0 SControl 300)
Sep  7 12:27:36 fido kernel: [    0.961479] ata1: SATA link down (SStatus 0 SControl 300)
Sep  7 12:27:36 fido kernel: [    0.973521] usb 1-1: New USB device found, idVendor=8087, idProduct=0024
Sep  7 12:27:36 fido kernel: [    0.973578] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
Sep  7 12:27:36 fido kernel: [    0.973919] hub 1-1:1.0: USB hub found
Sep  7 12:27:36 fido kernel: [    0.974160] hub 1-1:1.0: 6 ports detected
Sep  7 12:27:36 fido kernel: [    1.084862] usb 2-1: new high-speed USB device number 2 using ehci_hcd
Sep  7 12:27:36 fido kernel: [    1.132759] ata7: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
Sep  7 12:27:36 fido kernel: [    1.133891] ata7.00: ATA-8: Hitachi HDS5C3020BLE630, MZ4OAAB0, max UDMA/133
Sep  7 12:27:36 fido kernel: [    1.133948] ata7.00: 3907029168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
Sep  7 12:27:36 fido kernel: [    1.135166] ata7.00: configured for UDMA/133
Sep  7 12:27:36 fido kernel: [    1.216965] usb 2-1: New USB device found, idVendor=8087, idProduct=0024
Sep  7 12:27:36 fido kernel: [    1.217022] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
Sep  7 12:27:36 fido kernel: [    1.217359] hub 2-1:1.0: USB hub found
Sep  7 12:27:36 fido kernel: [    1.217589] hub 2-1:1.0: 8 ports detected
Sep  7 12:27:36 fido kernel: [    1.240508] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Sep  7 12:27:36 fido kernel: [    1.247696] ata6.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) rejected by device (Stat=0x51 Err=0x04)
Sep  7 12:27:36 fido kernel: [    1.247771] ata6.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
Sep  7 12:27:36 fido kernel: [    1.247844] ata6.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
Sep  7 12:27:36 fido kernel: [    1.249186] ata6.00: ATA-6: WDC WD1600BB-00GUC0, 08.02D08, max UDMA/100
Sep  7 12:27:36 fido kernel: [    1.249243] ata6.00: 312581808 sectors, multi 16: LBA48
Sep  7 12:27:36 fido kernel: [    1.249302] ata6.00: applying bridge limits
Sep  7 12:27:36 fido kernel: [    1.257761] ata6.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) rejected by device (Stat=0x51 Err=0x04)
Sep  7 12:27:36 fido kernel: [    1.257835] ata6.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
Sep  7 12:27:36 fido kernel: [    1.257907] ata6.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
Sep  7 12:27:36 fido kernel: [    1.259275] ata6.00: configured for UDMA/100
Sep  7 12:27:36 fido kernel: [    1.259448] scsi 5:0:0:0: Direct-Access     ATA      WDC WD1600BB-00G 08.0 PQ: 0 ANSI: 5
Sep  7 12:27:36 fido kernel: [    1.259600] sd 5:0:0:0: Attached scsi generic sg0 type 0
Sep  7 12:27:36 fido kernel: [    1.259610] sd 5:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
Sep  7 12:27:36 fido kernel: [    1.259649] sd 5:0:0:0: [sda] Write Protect is off
Sep  7 12:27:36 fido kernel: [    1.259651] sd 5:0:0:0: [sda] Mode Sense: 00 3a 00 00
Sep  7 12:27:36 fido kernel: [    1.259660] sd 5:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep  7 12:27:36 fido kernel: [    1.280065]  sda: sda1
Sep  7 12:27:36 fido kernel: [    1.280287] sd 5:0:0:0: [sda] Attached SCSI disk
Sep  7 12:27:36 fido kernel: [    1.280438] scsi 6:0:0:0: Direct-Access     ATA      Hitachi HDS5C302 MZ4O PQ: 0 ANSI: 5
Sep  7 12:27:36 fido kernel: [    1.280588] sd 6:0:0:0: Attached scsi generic sg1 type 0
Sep  7 12:27:36 fido kernel: [    1.280592] sd 6:0:0:0: [sdb] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
Sep  7 12:27:36 fido kernel: [    1.280593] sd 6:0:0:0: [sdb] 4096-byte physical blocks
Sep  7 12:27:36 fido kernel: [    1.280622] sd 6:0:0:0: [sdb] Write Protect is off
Sep  7 12:27:36 fido kernel: [    1.280623] sd 6:0:0:0: [sdb] Mode Sense: 00 3a 00 00
Sep  7 12:27:36 fido kernel: [    1.280635] sd 6:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep  7 12:27:36 fido kernel: [    1.288546] usb 1-1.5: new full-speed USB device number 3 using ehci_hcd
Sep  7 12:27:36 fido kernel: [    1.306073]  sdb: sdb1
Sep  7 12:27:36 fido kernel: [    1.306296] sd 6:0:0:0: [sdb] Attached SCSI disk
Sep  7 12:27:36 fido kernel: [    1.381716] usb 1-1.5: New USB device found, idVendor=041e, idProduct=4034
Sep  7 12:27:36 fido kernel: [    1.381773] usb 1-1.5: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Sep  7 12:27:36 fido kernel: [    1.381845] usb 1-1.5: Product: WebCam Instant
Sep  7 12:27:36 fido kernel: [    1.381890] usb 1-1.5: Manufacturer: Creative Labs  
Sep  7 12:27:36 fido kernel: [    1.444044] Refined TSC clocksource calibration: 3192.746 MHz.
Sep  7 12:27:36 fido kernel: [    1.444101] Switching to clocksource tsc
Sep  7 12:27:36 fido kernel: [    1.488068] usb 2-1.5: new low-speed USB device number 3 using ehci_hcd
Sep  7 12:27:36 fido kernel: [    1.601089] usb 2-1.5: New USB device found, idVendor=040b, idProduct=2011
Sep  7 12:27:36 fido kernel: [    1.601147] usb 2-1.5: New USB device strings: Mfr=0, Product=1, SerialNumber=0
Sep  7 12:27:36 fido kernel: [    1.601219] usb 2-1.5: Product: GiGa HiD
Sep  7 12:27:36 fido kernel: [    1.671677] usb 2-1.7: new full-speed USB device number 4 using ehci_hcd
Sep  7 12:27:36 fido kernel: [    1.767961] usb 2-1.7: New USB device found, idVendor=0aec, idProduct=3050
Sep  7 12:27:36 fido kernel: [    1.768018] usb 2-1.7: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Sep  7 12:27:36 fido kernel: [    1.768090] usb 2-1.7: Product: USB Storage Device
Sep  7 12:27:36 fido kernel: [    1.768136] usb 2-1.7: Manufacturer: Generic
Sep  7 12:27:36 fido kernel: [    1.768181] usb 2-1.7: SerialNumber: 0AEC305000001A000
Sep  7 12:27:36 fido kernel: [    1.769630] Initializing USB Mass Storage driver...
Sep  7 12:27:36 fido kernel: [    1.769873] scsi8 : usb-storage 2-1.7:1.0
Sep  7 12:27:36 fido kernel: [    1.769973] usbcore: registered new interface driver usb-storage
Sep  7 12:27:36 fido kernel: [    1.770038] USB Mass Storage support registered.
Sep  7 12:27:36 fido kernel: [    1.771299] ata8: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
Sep  7 12:27:36 fido kernel: [    1.783443] ata8.00: ATA-8: MKNSSDCR120GB, 507ABBF0, max UDMA/133
Sep  7 12:27:36 fido kernel: [    1.783499] ata8.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
Sep  7 12:27:36 fido kernel: [    1.793243] ata8.00: configured for UDMA/133
Sep  7 12:27:36 fido kernel: [    1.793397] scsi 7:0:0:0: Direct-Access     ATA      MKNSSDCR120GB    507A PQ: 0 ANSI: 5
Sep  7 12:27:36 fido kernel: [    1.793548] sd 7:0:0:0: Attached scsi generic sg2 type 0
Sep  7 12:27:36 fido kernel: [    1.793557] sd 7:0:0:0: [sdc] 234441648 512-byte logical blocks: (120 GB/111 GiB)
Sep  7 12:27:36 fido kernel: [    1.793620] sd 7:0:0:0: [sdc] Write Protect is off
Sep  7 12:27:36 fido kernel: [    1.793621] sd 7:0:0:0: [sdc] Mode Sense: 00 3a 00 00
Sep  7 12:27:36 fido kernel: [    1.793649] sd 7:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep  7 12:27:36 fido kernel: [    1.794013]  sdc: sdc1
Sep  7 12:27:36 fido kernel: [    1.794198] sd 7:0:0:0: [sdc] Attached SCSI disk
Sep  7 12:27:36 fido kernel: [    1.801695] usbcore: registered new interface driver usbhid
Sep  7 12:27:36 fido kernel: [    1.801755] usbhid: USB HID core driver
Sep  7 12:27:36 fido kernel: [    1.802960] input: GiGa HiD as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.0/input/input3
Sep  7 12:27:36 fido kernel: [    1.803161] hid-generic 0003:040B:2011.0001: input,hiddev0,hidraw0: USB HID v1.10 Mouse [GiGa HiD] on usb-0000:00:1d.0-1.5/input0
Sep  7 12:27:36 fido kernel: [    1.823813] EXT4-fs (sdc1): mounted filesystem without journal. Opts: (null)
Sep  7 12:27:36 fido kernel: [    2.766536] scsi 8:0:0:0: Direct-Access     Generic  USB Storage-SMC  500A PQ: 0 ANSI: 0 CCS
Sep  7 12:27:36 fido kernel: [    2.767670] scsi 8:0:0:1: Direct-Access     Generic  USB Storage-CFC  500A PQ: 0 ANSI: 0 CCS
Sep  7 12:27:36 fido kernel: [    2.768792] scsi 8:0:0:2: Direct-Access     Generic  USB Storage-MMC  500A PQ: 0 ANSI: 0 CCS
Sep  7 12:27:36 fido kernel: [    2.769903] scsi 8:0:0:3: Direct-Access     Generic  USB Storage-MSC  500A PQ: 0 ANSI: 0 CCS
Sep  7 12:27:36 fido kernel: [    2.770374] sd 8:0:0:0: Attached scsi generic sg3 type 0
Sep  7 12:27:36 fido kernel: [    2.770516] sd 8:0:0:1: Attached scsi generic sg4 type 0
Sep  7 12:27:36 fido kernel: [    2.770656] sd 8:0:0:2: Attached scsi generic sg5 type 0
Sep  7 12:27:36 fido kernel: [    2.770778] sd 8:0:0:3: Attached scsi generic sg6 type 0
Sep  7 12:27:36 fido kernel: [    2.782866] sd 8:0:0:0: [sdd] Attached SCSI removable disk
Sep  7 12:27:36 fido kernel: [    2.784141] sd 8:0:0:1: [sde] Attached SCSI removable disk
Sep  7 12:27:36 fido kernel: [    2.785488] sd 8:0:0:2: [sdf] Attached SCSI removable disk
Sep  7 12:27:36 fido kernel: [    2.786859] sd 8:0:0:3: [sdg] Attached SCSI removable disk
Sep  7 12:27:36 fido kernel: [    3.026740] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Sep  7 12:27:36 fido kernel: [    3.051378] lp: driver loaded but no devices found
Sep  7 12:27:36 fido kernel: [    3.054629] ACPI Warning: 0x0000000000000460-0x000000000000047f SystemIO conflicts with Region \PMIO 1 (20120320/utaddress-251)
Sep  7 12:27:36 fido kernel: [    3.054634] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Sep  7 12:27:36 fido kernel: [    3.054635] lpc_ich: Resource conflict(s) found affecting iTCO_wdt
Sep  7 12:27:36 fido kernel: [    3.054638] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMIO 1 (20120320/utaddress-251)
Sep  7 12:27:36 fido kernel: [    3.054639] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Sep  7 12:27:36 fido kernel: [    3.054642] ACPI Warning: 0x0000000000000500-0x000000000000053f SystemIO conflicts with Region \GPR2 1 (20120320/utaddress-251)
Sep  7 12:27:36 fido kernel: [    3.054644] ACPI Warning: 0x0000000000000500-0x000000000000053f SystemIO conflicts with Region \GPIO 2 (20120320/utaddress-251)
Sep  7 12:27:36 fido kernel: [    3.054645] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Sep  7 12:27:36 fido kernel: [    3.054646] lpc_ich: Resource conflict(s) found affecting gpio_ich
Sep  7 12:27:36 fido kernel: [    3.072932] type=1400 audit(1378549654.019:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=548 comm="apparmor_parser"
Sep  7 12:27:36 fido kernel: [    3.073180] type=1400 audit(1378549654.019:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=548 comm="apparmor_parser"
Sep  7 12:27:36 fido kernel: [    3.073320] type=1400 audit(1378549654.019:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=548 comm="apparmor_parser"
Sep  7 12:27:36 fido kernel: [    3.075542] mei 0000:00:16.0: setting latency timer to 64
Sep  7 12:27:36 fido kernel: [    3.075590] mei 0000:00:16.0: irq 45 for MSI/MSI-X
Sep  7 12:27:36 fido kernel: [    3.087118] mei 0000:00:16.0: wd: failed to find the client
Sep  7 12:27:36 fido kernel: [    3.105593] microcode: CPU0 sig=0x306a9, pf=0x2, revision=0x12
Sep  7 12:27:36 fido kernel: [    3.108487] nvidia: module license 'NVIDIA' taints kernel.
Sep  7 12:27:36 fido kernel: [    3.108489] Disabling lock debugging due to kernel taint
Sep  7 12:27:36 fido kernel: [    3.117210] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
Sep  7 12:27:36 fido kernel: [    3.117649] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  304.88  Wed Mar 27 14:26:46 PDT 2013
Sep  7 12:27:36 fido kernel: [    3.122716] Linux video capture interface: v2.00
Sep  7 12:27:36 fido kernel: [    3.122901] gspca_main: v2.14.0 registered
Sep  7 12:27:36 fido kernel: [    3.123058] gspca_main: gspca_zc3xx-2.14.0 probing 041e:4034
Sep  7 12:27:36 fido kernel: [    3.146034] snd_hda_intel 0000:00:1b.0: irq 46 for MSI/MSI-X
Sep  7 12:27:36 fido kernel: [    3.158034] parport_pc 00:09: reported by Plug and Play ACPI
Sep  7 12:27:36 fido kernel: [    3.158090] parport0: PC-style at 0x378 (0x778), irq 5, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
Sep  7 12:27:36 fido kernel: [    3.190528] microcode: CPU1 sig=0x306a9, pf=0x2, revision=0x12
Sep  7 12:27:36 fido kernel: [    3.198843] microcode: CPU2 sig=0x306a9, pf=0x2, revision=0x12
Sep  7 12:27:36 fido kernel: [    3.200237] ppdev: user-space parallel port driver
Sep  7 12:27:36 fido kernel: [    3.200923] microcode: CPU3 sig=0x306a9, pf=0x2, revision=0x12
Sep  7 12:27:36 fido kernel: [    3.201809] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
Sep  7 12:27:36 fido kernel: [    3.204118] input: HDA Intel PCH Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input4
Sep  7 12:27:36 fido kernel: [    3.204225] input: HDA Intel PCH Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input5
Sep  7 12:27:36 fido kernel: [    3.204356] input: HDA Intel PCH Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
Sep  7 12:27:36 fido kernel: [    3.204429] input: HDA Intel PCH Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
Sep  7 12:27:36 fido kernel: [    3.204491] input: HDA Intel PCH Line Out CLFE as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
Sep  7 12:27:36 fido kernel: [    3.204573] input: HDA Intel PCH Line Out Surround as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
Sep  7 12:27:36 fido kernel: [    3.204670] input: HDA Intel PCH Line Out Front as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
Sep  7 12:27:36 fido kernel: [    3.204930] hda_intel: Disabling MSI
Sep  7 12:27:36 fido kernel: [    3.204935] hda-intel: 0000:01:00.1: Handle VGA-switcheroo audio client
Sep  7 12:27:36 fido kernel: [    3.252086] lp0: using parport0 (interrupt-driven).
Sep  7 12:27:36 fido kernel: [    3.329064] input: gspca_zc3xx as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/input/input11
Sep  7 12:27:36 fido kernel: [    3.329155] usbcore: registered new interface driver gspca_zc3xx
Sep  7 12:27:36 fido kernel: [    3.802782] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input12
Sep  7 12:27:36 fido kernel: [    3.802845] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input13
Sep  7 12:27:36 fido kernel: [    3.802933] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input14
Sep  7 12:27:36 fido kernel: [    3.802974] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input15
Sep  7 12:27:36 fido kernel: [    4.676799] EXT4-fs (sdc1): Remounting file system with no journal so ignoring journalled data option
Sep  7 12:27:36 fido kernel: [    4.678788] EXT4-fs (sdc1): re-mounted. Opts: discard,data=writeback,errors=remount-ro
Sep  7 12:27:36 fido kernel: [    4.994057] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
Sep  7 12:27:36 fido modem-manager[1027]: <info>  ModemManager (version 0.5.2.0) starting...
Sep  7 12:27:36 fido modem-manager[1027]: <info>  Loaded plugin X22X
Sep  7 12:27:36 fido modem-manager[1027]: <info>  Loaded plugin Huawei
Sep  7 12:27:36 fido modem-manager[1027]: <info>  Loaded plugin Ericsson MBM
Sep  7 12:27:36 fido modem-manager[1027]: <info>  Loaded plugin Option High-Speed
Sep  7 12:27:36 fido modem-manager[1027]: <info>  Loaded plugin Sierra
Sep  7 12:27:36 fido modem-manager[1027]: <info>  Loaded plugin ZTE
Sep  7 12:27:36 fido modem-manager[1027]: <info>  Loaded plugin MotoC
Sep  7 12:27:36 fido modem-manager[1027]: <info>  Loaded plugin Longcheer
Sep  7 12:27:36 fido modem-manager[1027]: <info>  Loaded plugin SimTech
Sep  7 12:27:36 fido modem-manager[1027]: <info>  Loaded plugin Wavecom
Sep  7 12:27:36 fido modem-manager[1027]: <info>  Loaded plugin Samsung
Sep  7 12:27:36 fido modem-manager[1027]: <info>  Loaded plugin Gobi
Sep  7 12:27:36 fido modem-manager[1027]: <info>  Loaded plugin Option
Sep  7 12:27:36 fido modem-manager[1027]: <info>  Loaded plugin Generic
Sep  7 12:27:36 fido modem-manager[1027]: <info>  Loaded plugin Linktop
Sep  7 12:27:36 fido modem-manager[1027]: <info>  Loaded plugin Nokia
Sep  7 12:27:36 fido modem-manager[1027]: <info>  Loaded plugin AnyData
Sep  7 12:27:36 fido modem-manager[1027]: <info>  Loaded plugin Novatel
Sep  7 12:27:36 fido bluetoothd[1029]: Bluetooth daemon 4.98
Sep  7 12:27:36 fido bluetoothd[1029]: Starting SDP server
Sep  7 12:27:36 fido bluetoothd[1029]: Failed to init alert plugin
Sep  7 12:27:36 fido NetworkManager[1040]: <info> NetworkManager (version 0.9.4.0) is starting...
Sep  7 12:27:36 fido bluetoothd[1029]: Failed to init time plugin
Sep  7 12:27:36 fido NetworkManager[1040]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
Sep  7 12:27:36 fido bluetoothd[1029]: Failed to init proximity plugin
Sep  7 12:27:36 fido bluetoothd[1029]: Failed to init gatt_example plugin
Sep  7 12:27:36 fido NetworkManager[1040]: <info> VPN: loaded org.freedesktop.NetworkManager.pptp
Sep  7 12:27:36 fido NetworkManager[1040]: <info> DNS: loaded plugin dnsmasq
Sep  7 12:27:36 fido kernel: [    5.136967] Bluetooth: Core ver 2.16
Sep  7 12:27:36 fido kernel: [    5.136980] NET: Registered protocol family 31
Sep  7 12:27:36 fido kernel: [    5.136981] Bluetooth: HCI device and connection manager initialized
Sep  7 12:27:36 fido kernel: [    5.136982] Bluetooth: HCI socket layer initialized
Sep  7 12:27:36 fido kernel: [    5.136983] Bluetooth: L2CAP socket layer initialized
Sep  7 12:27:36 fido kernel: [    5.136984] Bluetooth: SCO socket layer initialized
Sep  7 12:27:36 fido kernel: [    5.138341] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Sep  7 12:27:36 fido kernel: [    5.138343] Bluetooth: BNEP filters: protocol multicast
Sep  7 12:27:36 fido dbus[1007]: [system] Activating service name='org.freedesktop.PolicyKit1' (using servicehelper)
Sep  7 12:27:36 fido avahi-daemon[1065]: Found user 'avahi' (UID 107) and group 'avahi' (GID 118).
Sep  7 12:27:36 fido avahi-daemon[1065]: Successfully dropped root privileges.
Sep  7 12:27:36 fido avahi-daemon[1065]: avahi-daemon 0.6.30 starting up.
Sep  7 12:27:36 fido avahi-daemon[1065]: Successfully called chroot().
Sep  7 12:27:36 fido avahi-daemon[1065]: Successfully dropped remaining capabilities.
Sep  7 12:27:36 fido avahi-daemon[1065]: Loading service file /services/udisks.service.
Sep  7 12:27:36 fido kernel: [    5.144382] Bluetooth: RFCOMM TTY layer initialized
Sep  7 12:27:36 fido kernel: [    5.144386] Bluetooth: RFCOMM socket layer initialized
Sep  7 12:27:36 fido kernel: [    5.144387] Bluetooth: RFCOMM ver 1.11
Sep  7 12:27:36 fido kernel: [    5.146393] type=1400 audit(1378549656.095:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1060 comm="apparmor_parser"
Sep  7 12:27:36 fido kernel: [    5.146884] type=1400 audit(1378549656.095:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=1060 comm="apparmor_parser"
Sep  7 12:27:36 fido polkitd[1056]: started daemon version 0.104 using authority implementation `local' version `0.104'
Sep  7 12:27:36 fido avahi-daemon[1065]: Network interface enumeration completed.
Sep  7 12:27:36 fido avahi-daemon[1065]: Registering HINFO record with values 'X86_64'/'LINUX'.
Sep  7 12:27:36 fido dbus[1007]: [system] Successfully activated service 'org.freedesktop.PolicyKit1'
Sep  7 12:27:36 fido avahi-daemon[1065]: Server startup complete. Host name is fido.local. Local service cookie is 3683713434.
Sep  7 12:27:36 fido avahi-daemon[1065]: Service "fido" (/services/udisks.service) successfully established.
Sep  7 12:27:36 fido NetworkManager[1040]:    SCPlugin-Ifupdown: init!
Sep  7 12:27:36 fido NetworkManager[1040]:    SCPlugin-Ifupdown: update_system_hostname
Sep  7 12:27:36 fido NetworkManager[1040]:    SCPluginIfupdown: management mode: unmanaged
Sep  7 12:27:36 fido NetworkManager[1040]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.5/0000:03:00.0/net/eth0, iface: eth0)
Sep  7 12:27:36 fido NetworkManager[1040]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.5/0000:03:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Sep  7 12:27:36 fido NetworkManager[1040]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Sep  7 12:27:36 fido NetworkManager[1040]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Sep  7 12:27:36 fido NetworkManager[1040]:    SCPlugin-Ifupdown: end _init.
Sep  7 12:27:36 fido NetworkManager[1040]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Sep  7 12:27:36 fido NetworkManager[1040]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Sep  7 12:27:36 fido NetworkManager[1040]:    Ifupdown: get unmanaged devices count: 0
Sep  7 12:27:36 fido NetworkManager[1040]:    SCPlugin-Ifupdown: (13249328) ... get_connections.
Sep  7 12:27:36 fido NetworkManager[1040]:    SCPlugin-Ifupdown: (13249328) ... get_connections (managed=false): return empty list.
Sep  7 12:27:36 fido NetworkManager[1040]:    Ifupdown: get unmanaged devices count: 0
Sep  7 12:27:36 fido NetworkManager[1040]: <info> modem-manager is now available
Sep  7 12:27:36 fido NetworkManager[1040]: <info> monitoring kernel firmware directory '/lib/firmware'.
Sep  7 12:27:36 fido NetworkManager[1040]: <info> WiFi enabled by radio killswitch; enabled by state file
Sep  7 12:27:36 fido NetworkManager[1040]: <info> WWAN enabled by radio killswitch; enabled by state file
Sep  7 12:27:36 fido NetworkManager[1040]: <info> WiMAX enabled by radio killswitch; enabled by state file
Sep  7 12:27:36 fido NetworkManager[1040]: <info> Networking is enabled by state file
Sep  7 12:27:36 fido NetworkManager[1040]: <warn> failed to allocate link cache: (-10) Operation not supported
Sep  7 12:27:36 fido NetworkManager[1040]: <info> (eth0): carrier is OFF
Sep  7 12:27:36 fido NetworkManager[1040]: <info> (eth0): new Ethernet device (driver: 'r8169' ifindex: 2)
Sep  7 12:27:36 fido NetworkManager[1040]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Sep  7 12:27:36 fido NetworkManager[1040]: <info> (eth0): now managed
Sep  7 12:27:36 fido NetworkManager[1040]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Sep  7 12:27:36 fido NetworkManager[1040]: <info> (eth0): bringing up device.
Sep  7 12:27:36 fido dbus[1007]: [system] Activating service name='org.freedesktop.ColorManager' (using servicehelper)
Sep  7 12:27:36 fido kernel: [    5.153486] type=1400 audit(1378549656.103:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=1087 comm="apparmor_parser"
Sep  7 12:27:36 fido kernel: [    5.153688] type=1400 audit(1378549656.103:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper//chromium_browser" pid=1087 comm="apparmor_parser"
Sep  7 12:27:36 fido kernel: [    5.155081] type=1400 audit(1378549656.103:9): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1088 comm="apparmor_parser"
Sep  7 12:27:36 fido kernel: [    5.155430] type=1400 audit(1378549656.103:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1088 comm="apparmor_parser"
Sep  7 12:27:36 fido dbus[1007]: [system] Successfully activated service 'org.freedesktop.ColorManager'
Sep  7 12:27:36 fido cron[1147]: (CRON) INFO (pidfile fd = 3)
Sep  7 12:27:36 fido anacron[1165]: Anacron 2.3 started on 2013-09-07
Sep  7 12:27:36 fido cron[1164]: (CRON) STARTUP (fork ok)
Sep  7 12:27:36 fido NetworkManager[1040]: <info> (eth0): preparing device.
Sep  7 12:27:36 fido NetworkManager[1040]: <info> (eth0): deactivating device (reason 'managed') [2]
Sep  7 12:27:36 fido cron[1164]: (CRON) INFO (Running @reboot jobs)
Sep  7 12:27:36 fido NetworkManager[1040]: <info> Added default wired connection 'Wired connection 1' for /sys/devices/pci0000:00/0000:00:1c.5/0000:03:00.0/net/eth0
Sep  7 12:27:36 fido anacron[1165]: Will run job `cron.daily' in 5 min.
Sep  7 12:27:36 fido anacron[1165]: Jobs will be executed sequentially
Sep  7 12:27:36 fido kernel: [    5.248532] r8169 0000:03:00.0: eth0: link down
Sep  7 12:27:36 fido kernel: [    5.248954] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Sep  7 12:27:36 fido kernel: [    5.249131] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Sep  7 12:27:36 fido kernel: [    5.250255] r8169 0000:03:00.0: eth0: link down
Sep  7 12:27:36 fido acpid: starting up with proc fs
Sep  7 12:27:36 fido acpid: 35 rules loaded
Sep  7 12:27:36 fido acpid: waiting for events: event logging is off
Sep  7 12:27:36 fido acpid: client connected from 1235[0:0]
Sep  7 12:27:36 fido acpid: 1 client rule loaded
Sep  7 12:27:36 fido acpid: client connected from 1235[0:0]
Sep  7 12:27:36 fido acpid: 1 client rule loaded
Sep  7 12:27:37 fido dbus[1007]: [system] Activating service name='org.freedesktop.Accounts' (using servicehelper)
Sep  7 12:27:37 fido dbus[1007]: [system] Successfully activated service 'org.freedesktop.Accounts'
Sep  7 12:27:37 fido accounts-daemon[1374]: started daemon version 0.6.15
Sep  7 12:27:37 fido dbus[1007]: [system] Activating service name='org.freedesktop.ConsoleKit' (using servicehelper)
Sep  7 12:27:37 fido dbus[1007]: [system] Successfully activated service 'org.freedesktop.ConsoleKit'
Sep  7 12:27:37 fido dbus[1007]: [system] Activating service name='org.freedesktop.UPower' (using servicehelper)
Sep  7 12:27:37 fido dbus[1007]: [system] Successfully activated service 'org.freedesktop.UPower'
Sep  7 12:27:37 fido dbus[1007]: [system] Activating service name='org.freedesktop.RealtimeKit1' (using servicehelper)
Sep  7 12:27:37 fido dbus[1007]: [system] Successfully activated service 'org.freedesktop.RealtimeKit1'
Sep  7 12:27:37 fido rtkit-daemon[1727]: Successfully called chroot.
Sep  7 12:27:37 fido rtkit-daemon[1727]: Successfully dropped privileges.
Sep  7 12:27:37 fido rtkit-daemon[1727]: Successfully limited resources.
Sep  7 12:27:37 fido rtkit-daemon[1727]: Running.
Sep  7 12:27:37 fido rtkit-daemon[1727]: Canary thread running.
Sep  7 12:27:37 fido rtkit-daemon[1727]: Watchdog thread running.
Sep  7 12:27:37 fido rtkit-daemon[1727]: Successfully made thread 1725 of process 1725 (n/a) owned by '104' high priority at nice level -11.
Sep  7 12:27:37 fido rtkit-daemon[1727]: Supervising 1 threads of 1 processes of 1 users.
Sep  7 12:27:37 fido rtkit-daemon[1727]: Successfully made thread 1737 of process 1725 (n/a) owned by '104' RT at priority 5.
Sep  7 12:27:37 fido rtkit-daemon[1727]: Supervising 2 threads of 1 processes of 1 users.
Sep  7 12:27:37 fido NetworkManager[1040]: <info> (eth0): carrier now ON (device state 20)
Sep  7 12:27:37 fido NetworkManager[1040]: <info> (eth0): device state change: unavailable -> disconnected (reason 'carrier-changed') [20 30 40]
Sep  7 12:27:37 fido NetworkManager[1040]: <info> Auto-activating connection 'Wired connection 1'.
Sep  7 12:27:37 fido NetworkManager[1040]: <info> Activation (eth0) starting connection 'Wired connection 1'
Sep  7 12:27:37 fido NetworkManager[1040]: <info> (eth0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Sep  7 12:27:37 fido NetworkManager[1040]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Sep  7 12:27:37 fido NetworkManager[1040]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Sep  7 12:27:37 fido NetworkManager[1040]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Sep  7 12:27:37 fido NetworkManager[1040]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Sep  7 12:27:37 fido NetworkManager[1040]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Sep  7 12:27:37 fido NetworkManager[1040]: <info> (eth0): device state change: prepare -> config (reason 'none') [40 50 0]
Sep  7 12:27:37 fido NetworkManager[1040]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Sep  7 12:27:37 fido NetworkManager[1040]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Sep  7 12:27:37 fido NetworkManager[1040]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Sep  7 12:27:37 fido NetworkManager[1040]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Sep  7 12:27:37 fido NetworkManager[1040]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
Sep  7 12:27:37 fido NetworkManager[1040]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Sep  7 12:27:37 fido NetworkManager[1040]: <info> dhclient started with pid 1738
Sep  7 12:27:37 fido NetworkManager[1040]: <info> Activation (eth0) Beginning IP6 addrconf.
Sep  7 12:27:37 fido dhclient: Internet Systems Consortium DHCP Client 4.1-ESV-R4
Sep  7 12:27:37 fido dhclient: Copyright 2004-2011 Internet Systems Consortium.
Sep  7 12:27:37 fido dhclient: All rights reserved.
Sep  7 12:27:37 fido dhclient: For info, please visit https://www.isc.org/software/dhcp/
Sep  7 12:27:37 fido dhclient:
Sep  7 12:27:37 fido kernel: [    6.788872] r8169 0000:03:00.0: eth0: link up
Sep  7 12:27:37 fido kernel: [    6.789222] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Sep  7 12:27:37 fido NetworkManager[1040]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Sep  7 12:27:37 fido NetworkManager[1040]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Sep  7 12:27:37 fido dhclient: Listening on LPF/eth0/bc:5f:f4:77:66:52
Sep  7 12:27:37 fido dhclient: Sending on   LPF/eth0/bc:5f:f4:77:66:52
Sep  7 12:27:37 fido dhclient: Sending on   Socket/fallback
Sep  7 12:27:37 fido dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Sep  7 12:27:37 fido rtkit-daemon[1727]: Successfully made thread 1741 of process 1725 (n/a) owned by '104' RT at priority 5.
Sep  7 12:27:37 fido rtkit-daemon[1727]: Supervising 3 threads of 1 processes of 1 users.
Sep  7 12:27:37 fido rtkit-daemon[1727]: Successfully made thread 1742 of process 1725 (n/a) owned by '104' RT at priority 5.
Sep  7 12:27:37 fido rtkit-daemon[1727]: Supervising 4 threads of 1 processes of 1 users.
Sep  7 12:27:37 fido rtkit-daemon[1727]: Successfully made thread 1745 of process 1745 (n/a) owned by '104' high priority at nice level -11.
Sep  7 12:27:37 fido rtkit-daemon[1727]: Supervising 5 threads of 2 processes of 1 users.
Sep  7 12:27:37 fido pulseaudio[1745]: [pulseaudio] pid.c: Daemon already running.
Sep  7 12:27:38 fido udev-configure-printer: add /devices/pnp0/00:09/printer/lp0
Sep  7 12:27:38 fido udev-configure-printer: Failed to get parent
Sep  7 12:27:38 fido udev-configure-printer: add /module/lp
Sep  7 12:27:38 fido udev-configure-printer: Failed to get parent
Sep  7 12:27:38 fido udev-configure-printer: add /module/lpc_ich
Sep  7 12:27:38 fido udev-configure-printer: Failed to get parent
Sep  7 12:27:38 fido dhclient: DHCPREQUEST of 192.168.178.30 on eth0 to 255.255.255.255 port 67
Sep  7 12:27:38 fido dhclient: DHCPOFFER of 192.168.178.30 from 192.168.178.1
Sep  7 12:27:38 fido dhclient: DHCPACK of 192.168.178.30 from 192.168.178.1
Sep  7 12:27:38 fido dhclient: bound to 192.168.178.30 -- renewal in 354057 seconds.
Sep  7 12:27:38 fido NetworkManager[1040]: <info> (eth0): DHCPv4 state changed preinit -> bound
Sep  7 12:27:38 fido NetworkManager[1040]: <info>   address 192.168.178.30
Sep  7 12:27:38 fido NetworkManager[1040]: <info>   prefix 24 (255.255.255.0)
Sep  7 12:27:38 fido NetworkManager[1040]: <info>   gateway 192.168.178.1
Sep  7 12:27:38 fido NetworkManager[1040]: <info>   nameserver '192.168.178.1'
Sep  7 12:27:38 fido NetworkManager[1040]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Sep  7 12:27:38 fido NetworkManager[1040]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) started...
Sep  7 12:27:38 fido avahi-daemon[1065]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.178.30.
Sep  7 12:27:38 fido avahi-daemon[1065]: New relevant interface eth0.IPv4 for mDNS.
Sep  7 12:27:38 fido avahi-daemon[1065]: Registering new address record for 192.168.178.30 on eth0.IPv4.
Sep  7 12:27:39 fido avahi-daemon[1065]: Joining mDNS multicast group on interface eth0.IPv6 with address fe80::be5f:f4ff:fe77:6652.
Sep  7 12:27:39 fido avahi-daemon[1065]: New relevant interface eth0.IPv6 for mDNS.
Sep  7 12:27:39 fido avahi-daemon[1065]: Registering new address record for fe80::be5f:f4ff:fe77:6652 on eth0.*.
Sep  7 12:27:39 fido NetworkManager[1040]: <info> DNS: starting dnsmasq...
Sep  7 12:27:39 fido NetworkManager[1040]: <info> (eth0): writing resolv.conf to /sbin/resolvconf
Sep  7 12:27:39 fido dnsmasq[1759]: started, version 2.59 cache disabled
Sep  7 12:27:39 fido dnsmasq[1759]: compile time options: IPv6 GNU-getopt DBus i18n DHCP TFTP conntrack IDN
Sep  7 12:27:39 fido dnsmasq[1759]: using nameserver 192.168.178.1#53
Sep  7 12:27:40 fido NetworkManager[1040]: <info> (eth0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Sep  7 12:27:40 fido NetworkManager[1040]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Sep  7 12:27:40 fido NetworkManager[1040]: <info> Activation (eth0) successful, device activated.
Sep  7 12:27:40 fido NetworkManager[1040]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) complete.
Sep  7 12:27:40 fido dbus[1007]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Sep  7 12:27:40 fido dbus[1007]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Sep  7 12:27:42 fido rtkit-daemon[1727]: Successfully made thread 1974 of process 1974 (n/a) owned by '1000' high priority at nice level -11.
Sep  7 12:27:42 fido rtkit-daemon[1727]: Supervising 5 threads of 2 processes of 2 users.
Sep  7 12:27:42 fido dbus[1007]: [system] Activating service name='org.freedesktop.UDisks' (using servicehelper)
Sep  7 12:27:42 fido dbus[1007]: [system] Successfully activated service 'org.freedesktop.UDisks'
Sep  7 12:27:42 fido rtkit-daemon[1727]: Successfully made thread 2011 of process 1974 (n/a) owned by '1000' RT at priority 5.
Sep  7 12:27:42 fido rtkit-daemon[1727]: Supervising 6 threads of 2 processes of 2 users.
Sep  7 12:27:43 fido rtkit-daemon[1727]: Successfully made thread 2021 of process 1974 (n/a) owned by '1000' RT at priority 5.
Sep  7 12:27:43 fido rtkit-daemon[1727]: Supervising 7 threads of 2 processes of 2 users.
Sep  7 12:27:43 fido rtkit-daemon[1727]: Successfully made thread 2022 of process 1974 (n/a) owned by '1000' RT at priority 5.
Sep  7 12:27:43 fido rtkit-daemon[1727]: Supervising 8 threads of 2 processes of 2 users.
Sep  7 12:27:48 fido ntpdate[1820]: adjust time server 91.189.94.4 offset -0.105528 sec
Sep  7 12:27:57 fido goa[2283]: goa-daemon version 3.4.0 starting [main.c:112, main()]
Sep  7 12:27:58 fido NetworkManager[1040]: <info> (eth0): IP6 addrconf timed out or failed.
Sep  7 12:27:58 fido NetworkManager[1040]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Sep  7 12:27:58 fido NetworkManager[1040]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Sep  7 12:27:58 fido NetworkManager[1040]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Sep  7 12:28:44 fido dbus[1007]: [system] Activating service name='org.freedesktop.PackageKit' (using servicehelper)
Sep  7 12:28:44 fido dbus[1007]: [system] Activating service name='com.ubuntu.SystemService' (using servicehelper)
Sep  7 12:28:44 fido AptDaemon: INFO: Initializing daemon
Sep  7 12:28:44 fido dbus[1007]: [system] Successfully activated service 'com.ubuntu.SystemService'
Sep  7 12:28:44 fido AptDaemon.PackageKit: INFO: Initializing PackageKit compat layer
Sep  7 12:28:44 fido dbus[1007]: [system] Successfully activated service 'org.freedesktop.PackageKit'
Sep  7 12:28:44 fido AptDaemon.PackageKit: INFO: Initializing PackageKit transaction
Sep  7 12:28:44 fido AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/6313d9c623f0473a85ffb231a7b751b7
Sep  7 12:28:44 fido AptDaemon.Worker: INFO: Processing transaction /org/debian/apt/transaction/6313d9c623f0473a85ffb231a7b751b7
Sep  7 12:28:45 fido AptDaemon.PackageKit: INFO: Get updates()
Sep  7 12:28:45 fido AptDaemon.Worker: INFO: Finished transaction /org/debian/apt/transaction/6313d9c623f0473a85ffb231a7b751b7
Sep  7 12:32:36 fido anacron[1165]: Job `cron.daily' started
Sep  7 12:32:36 fido anacron[2570]: Updated timestamp for job `cron.daily' to 2013-09-07
Sep  7 12:32:45 fido kernel: [  313.828539] audit_printk_skb: 42 callbacks suppressed
Sep  7 12:32:45 fido kernel: [  313.828542] type=1400 audit(1378549965.331:25): apparmor="DENIED" operation="capable" parent=1 profile="/usr/sbin/cupsd" pid=1073 comm="cupsd" pid=1073 comm="cupsd" capability=36  capname="block_suspend"
Sep  7 12:34:45 fido AptDaemon: INFO: Quitting due to inactivity
Sep  7 12:34:45 fido AptDaemon: INFO: Quitting was requested
Sep  7 12:41:45 fido kernel: [  852.588482] type=1400 audit(1378550505.305:26): apparmor="DENIED" operation="capable" parent=1 profile="/usr/sbin/cupsd" pid=1073 comm="cupsd" pid=1073 comm="cupsd" capability=36  capname="block_suspend"
Sep  7 12:48:54 fido kernel: [ 1280.475746] type=1400 audit(1378550934.165:27): apparmor="DENIED" operation="capable" parent=1 profile="/usr/sbin/cupsd" pid=1073 comm="cupsd" pid=1073 comm="cupsd" capability=36  capname="block_suspend"
```

---

