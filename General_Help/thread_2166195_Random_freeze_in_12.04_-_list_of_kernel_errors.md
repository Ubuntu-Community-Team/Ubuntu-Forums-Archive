---
title: "Random freeze in 12.04 - list of kernel errors"
date: 2013-08-08
forum: General Help
---

### Post by MorrisseyJ on 2013-08-08
Hi, 

I have been having a number of problems with Ubuntu randomly  freezing. The problem appeared to start after i upgraded to 13.04.  After numerous problems with system hanging i downgraded to 12.04, for  the sake of productivity. Previously while on 12.04 - when it was the  latest version of Ubuntu, i don't recall having any problems. Now  however, after downgrading, i get freezes quite regularly: sometimes  once a day, sometimes three times a day. 

I have run memtest-86,  and no errors were found. I have also updated my bios to the latest  version but the problem persists - although my sense is that freezes are  less frequent. 

Syslog shows a bunch of kernel errors, too many  for me to know what is going on. At one point i thought this was all  related to my broadcom wireless chip, but now i don't know. This is all  beyond my abilities to understand. 

Below are the syslog outputs.  If anyone has any ideas of what i can do to get either 12.04 or 13.04  (ideally the latter) working i would really appreciate it as freezing is  crippling my productivity. 

I am running 64 bit ubuntu, a Lenovo x131e (Intel).

The following was produced running the 3.5.0-36-generic kernel, around the time of the freeze.

```
12:29:30 james-ThinkPad-X131e kernel: imklog 5.8.6, log source = /proc/kmsg started.
Aug   8 12:29:30 james-ThinkPad-X131e rsyslogd: [origin software="rsyslogd"  swVersion="5.8.6" x-pid="850" x-info="http://www.rsyslog.com"] start
Aug  8 12:29:31 james-ThinkPad-X131e rsyslogd: rsyslogd's groupid changed to 103
Aug  8 12:29:31 james-ThinkPad-X131e rsyslogd: rsyslogd's userid changed to 101
Aug   8 12:29:30 james-ThinkPad-X131e rsyslogd-2039: Could not open output  pipe '/dev/xconsole' [try [http://www.rsyslog.com/e/2039](http://www.rsyslog.com/e/2039) ]
Aug  8 12:29:31 james-ThinkPad-X131e failsafe: Failsafe of 120 seconds reached.
Aug  8 12:29:31 james-ThinkPad-X131e bluetoothd[900]: Bluetooth daemon 4.98
Aug  8 12:29:31 james-ThinkPad-X131e bluetoothd[900]: Starting SDP server
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] Initializing cgroup subsys cpuset
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] Initializing cgroup subsys cpu
Aug  8 12:29:31 james-ThinkPad-X131e bluetoothd[900]: Failed to init alert plugin
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] Linux version  3.5.0-23-generic (buildd@komainu) (gcc version 4.6.3 (Ubuntu/Linaro  4.6.3-1ubuntu5) ) #35~precise1-Ubuntu SMP Fri Jan 25 17:13:26 UTC 2013  (Ubuntu 3.5.0-23.35~precise1-generic 3.5.7.2)
Aug  8 12:29:31  james-ThinkPad-X131e kernel: [    0.000000] Command line:  BOOT_IMAGE=/boot/vmlinuz-3.5.0-23-generic  root=UUID=ab2826b2-ce24-4b17-9fc8-ed2b93bbf32b ro quiet splash  vt.handoff=7
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] KERNEL supported cpus:
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000]   Intel GenuineIntel
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000]   AMD AuthenticAMD
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000]   Centaur CentaurHauls
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] e820: BIOS-provided physical RAM map:
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009d7ff] usable
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] BIOS-e820: [mem 0x000000000009d800-0x000000000009ffff] reserved
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000001fffffff] usable
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] BIOS-e820: [mem 0x0000000020000000-0x00000000201fffff] reserved
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] BIOS-e820: [mem 0x0000000020200000-0x000000003fffffff] usable
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] BIOS-e820: [mem 0x0000000040000000-0x00000000401fffff] reserved
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] BIOS-e820: [mem 0x0000000040200000-0x00000000d069ffff] usable
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] BIOS-e820: [mem 0x00000000d06a0000-0x00000000dae9efff] reserved
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] BIOS-e820: [mem 0x00000000dae9f000-0x00000000daf9efff] ACPI NVS
Aug  8 12:29:31 james-ThinkPad-X131e bluetoothd[900]: Failed to init time plugin
Aug  8 12:29:31 james-ThinkPad-X131e bluetoothd[900]: Failed to init proximity plugin
Aug  8 12:29:31 james-ThinkPad-X131e bluetoothd[900]: Failed to init gatt_example plugin
Aug  8 12:29:31 james-ThinkPad-X131e modem-manager[924]: <info>  ModemManager (version 0.5.2.0) starting...
Aug  8 12:29:31 james-ThinkPad-X131e avahi-daemon[927]: Found user 'avahi' (UID 107) and group 'avahi' (GID 118).
Aug  8 12:29:31 james-ThinkPad-X131e avahi-daemon[927]: Successfully dropped root privileges.
Aug  8 12:29:31 james-ThinkPad-X131e avahi-daemon[927]: avahi-daemon 0.6.30 starting up.
Aug  8 12:29:31 james-ThinkPad-X131e modem-manager[924]: <info>  Loaded plugin AnyData
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] BIOS-e820: [mem 0x00000000daf9f000-0x00000000daffefff] ACPI data
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] BIOS-e820: [mem 0x00000000dafff000-0x00000000df9fffff] reserved
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] BIOS-e820: [mem 0x00000000f8000000-0x00000000fbffffff] reserved
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] BIOS-e820: [mem 0x00000000fed08000-0x00000000fed08fff] reserved
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] BIOS-e820: [mem 0x00000000fed10000-0x00000000fed19fff] reserved
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] BIOS-e820: [mem 0x00000000ffc00000-0x00000000ffffffff] reserved
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000021e5fffff] usable
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] BIOS-e820: [mem 0x000000021e600000-0x000000021e7fffff] reserved
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] NX (Execute Disable) protection: active
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] DMI 2.7 present.
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] DMI: LENOVO 33682NG/33682NG, BIOS G8ET92WW (2.52 ) 04/18/2013
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] e820: update [mem 0x00000000-0x0000ffff] usable ==> reserved
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] No AGP bridge found
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] e820: last_pfn = 0x21e600 max_arch_pfn = 0x400000000
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] MTRR default type: uncachable
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] MTRR fixed ranges enabled:
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000]   00000-9FFFF write-back
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000]   A0000-BFFFF uncachable
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000]   C0000-FFFFF write-protect
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] MTRR variable ranges enabled:
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000]   0 base 0FFC00000 mask FFFC00000 write-protect
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000]   1 base 000000000 mask F80000000 write-back
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000]   2 base 080000000 mask FC0000000 write-back
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000]   3 base 0C0000000 mask FE0000000 write-back
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000]   4 base 0DC000000 mask FFC000000 uncachable
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000]   5 base 0DB000000 mask FFF000000 uncachable
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000]   6 base 100000000 mask F00000000 write-back
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000]   7 base 200000000 mask FE0000000 write-back
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000]   8 base 21F000000 mask FFF000000 uncachable
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000]   9 base 21E800000 mask FFF800000 uncachable
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] e820: last_pfn = 0xd06a0 max_arch_pfn = 0x400000000
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] found SMP  MP-table at [mem 0x000f0100-0x000f010f] mapped at [ffff8800000f0100]
Aug  8 12:29:31 james-ThinkPad-X131e modem-manager[924]: <info>  Loaded plugin Generic
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] initial memory mapped: [mem 0x00000000-0x1fffffff]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] Base memory trampoline at [ffff880000097000] 97000 size 24576
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] init_memory_mapping: [mem 0x00000000-0xd069ffff]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000]  [mem 0x00000000-0xd05fffff] page 2M
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000]  [mem 0xd0600000-0xd069ffff] page 4k
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] kernel direct  mapping tables up to 0xd069ffff @ [mem 0x1fffa000-0x1fffffff]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] init_memory_mapping: [mem 0x100000000-0x21e5fffff]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000]  [mem 0x100000000-0x21e5fffff] page 2M
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] kernel direct  mapping tables up to 0x21e5fffff @ [mem 0xd069a000-0xd069ffff]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] RAMDISK: [mem 0x3624a000-0x3711cfff]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] ACPI: RSDP 00000000000f0120 00024 (v02 LENOVO)
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] ACPI: XSDT  00000000daffe170 0009C (v01 LENOVO TP-G8    00002520 PTL  00000002)
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] ACPI: FACP  00000000dafeb000 0010C (v05 LENOVO TP-G8    00002520 PTL  00000002)
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] ACPI: DSDT  00000000dafed000 0EF64 (v02 LENOVO  IVB-CPT 00000000 INTL 20061109)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] ACPI: FACS 00000000daf67000 00040
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] ACPI: SLIC  00000000daffd000 00176 (v01 LENOVO TP-G8    00002520 PTL  00000001)
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] ACPI: TCPA  00000000daffc000 00032 (v02    PTL   LENOVO 06040000 LNVO 00000001)
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] ACPI: ASF!  00000000dafec000 000A5 (v32 LENOVO TP-G8    00002520 PTL  00000002)
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] ACPI: HPET  00000000dafe9000 00038 (v01 LENOVO TP-G8    00002520 PTL  00000002)
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] ACPI: APIC  00000000dafe8000 00098 (v01 LENOVO TP-G8    00002520 PTL  00000002)
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] ACPI: MCFG  00000000dafe7000 0003C (v01 LENOVO TP-G8    00002520 PTL  00000002)
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] ACPI: FPDT  00000000dafe6000 00064 (v01 LENOVO TP-G8    00002520 PTL  00000002)
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] ACPI: SSDT  00000000dafe5000 0073E (v01  PmRef  Cpu0Ist 00003000 INTL 20061109)
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] ACPI: SSDT  00000000dafe4000 00A7E (v01  PmRef    CpuPm 00003000 INTL 20061109)
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] ACPI: UEFI  00000000dafe3000 0003E (v01 LENOVO TP-G8    00002520 PTL  00000002)
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] ACPI: UEFI  00000000dafe2000 00042 (v01 PTL      COMBUF 00000001 PTL  00000001)
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] ACPI: POAT  00000000dafe1000 00055 (v03 LENOVO TP-G8    00002520 PTL  00000002)
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] ACPI: UEFI  00000000dafe0000 002BA (v01 LENOVO TP-G8    00002520 PTL  00000002)
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] ACPI: DBG2  00000000dafdf000 0006B (v00 LENOVO TP-G8    00002520 PTL  00000002)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] No NUMA configuration found
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] Faking a node at [mem 0x0000000000000000-0x000000021e5fffff]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] Initmem setup node 0 [mem 0x00000000-0x21e5fffff]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000]   NODE_DATA [mem 0x21e5fc000-0x21e5fffff]
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000]   [ffffea0000000000-ffffea00087fffff] PMD ->  [ffff880215e00000-ffff88021dbfffff] on node 0
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] Zone ranges:
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000]   DMA      [mem 0x00010000-0x00ffffff]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000]   Normal   [mem 0x100000000-0x21e5fffff]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] Movable zone start for each node
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] Early memory node ranges
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000]   node   0: [mem 0x00010000-0x0009cfff]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000]   node   0: [mem 0x00100000-0x1fffffff]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000]   node   0: [mem 0x20200000-0x3fffffff]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000]   node   0: [mem 0x40200000-0xd069ffff]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000]   node   0: [mem 0x100000000-0x21e5fffff]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] On node 0 totalpages: 2025517
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000]   DMA zone: 64 pages used for memmap
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000]   DMA zone: 6 pages reserved
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000]   DMA zone: 3911 pages, LIFO batch:0
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000]   DMA32 zone: 16320 pages used for memmap
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000]   DMA32 zone: 832224 pages, LIFO batch:31
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000]   Normal zone: 18328 pages used for memmap
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000]   Normal zone: 1154664 pages, LIFO batch:31
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x00] disabled)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x00] disabled)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x00] disabled)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x00] disabled)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] ACPI: IRQ0 used by override.
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] ACPI: IRQ2 used by override.
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] ACPI: IRQ9 used by override.
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] ACPI: HPET id: 0x8086a301 base: 0xfed00000
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] SMP: Allowing 8 CPUs, 4 hotplug CPUs
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] nr_irqs_gsi: 40
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] PM: Registered nosave memory: 0000000020000000 - 0000000020200000
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] PM: Registered nosave memory: 0000000040000000 - 0000000040200000
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] PM: Registered nosave memory: 00000000d06a0000 - 00000000dae9f000
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] PM: Registered nosave memory: 00000000dae9f000 - 00000000daf9f000
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] PM: Registered nosave memory: 00000000daf9f000 - 00000000dafff000
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] PM: Registered nosave memory: 00000000dafff000 - 00000000dfa00000
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] PM: Registered nosave memory: 00000000dfa00000 - 00000000f8000000
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] PM: Registered nosave memory: 00000000f8000000 - 00000000fc000000
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] PM: Registered nosave memory: 00000000fc000000 - 00000000fec00000
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fed08000
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] PM: Registered nosave memory: 00000000fed08000 - 00000000fed09000
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] PM: Registered nosave memory: 00000000fed09000 - 00000000fed10000
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] PM: Registered nosave memory: 00000000fed10000 - 00000000fed1a000
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] PM: Registered nosave memory: 00000000fed1a000 - 00000000fed1c000
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] PM: Registered nosave memory: 00000000fed1c000 - 00000000fed20000
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fee00000
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffc00000
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] PM: Registered nosave memory: 00000000ffc00000 - 0000000100000000
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] e820: [mem 0xdfa00000-0xf7ffffff] available for PCI devices
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] setup_percpu:  NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
Aug  8  12:29:31 james-ThinkPad-X131e kernel: [    0.000000] PERCPU: Embedded 28  pages/cpu @ffff88021e200000 s83584 r8192 d22912 u262144
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] pcpu-alloc: s83584 r8192 d22912 u262144 alloc=1*2097152
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] Built 1  zonelists in Zone order, mobility grouping on.  Total pages: 1990799
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] Policy zone: Normal
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] Kernel command  line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-23-generic  root=UUID=ab2826b2-ce24-4b17-9fc8-ed2b93bbf32b ro quiet splash  vt.handoff=7
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] __ex_table already sorted, skipping sort
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] xsave/xrstor: enabled xstate_bv 0x7, cntxt size 0x340
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] Checking aperture...
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] No AGP bridge found
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] Calgary: detecting Calgary via BIOS EBDA area
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] Memory:  7875020k/8886272k available (6828k kernel code, 784204k absent, 227048k  reserved, 6342k data, 948k init)
Aug  8 12:29:31 james-ThinkPad-X131e  kernel: [    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3,  MinObjects=0, CPUs=8, Nodes=1
Aug  8 12:29:31 james-ThinkPad-X131e modem-manager[924]: <info>  Loaded plugin Linktop
Aug  8 12:29:31 james-ThinkPad-X131e modem-manager[924]: <info>  Loaded plugin SimTech
Aug  8 12:29:31 james-ThinkPad-X131e modem-manager[924]: <info>  Loaded plugin Wavecom
Aug  8 12:29:31 james-ThinkPad-X131e modem-manager[924]: <info>  Loaded plugin Ericsson MBM
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] Hierarchical RCU implementation.
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] NR_IRQS:16640 nr_irqs:744 16
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] Extended CMOS year: 2000
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] vt handoff: transparent VT on vt#7
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] Console: colour dummy device 80x25
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] console [tty0] enabled
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] allocated 33030144 bytes of page_cgroup
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] please try  'cgroup_disable=memory' option if you don't want memory cgroups
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] hpet clockevent registered
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000000] Fast TSC calibration using PIT
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.004000] Detected 1396.862 MHz processor.
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [    0.000003] Calibrating  delay loop (skipped), value calculated using timer frequency.. 2793.72  BogoMIPS (lpj=5587448)
Aug  8 12:29:31 james-ThinkPad-X131e modem-manager[924]: <info>  Loaded plugin Nokia
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000007] pid_max: default: 32768 minimum: 301
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000038] Security Framework initialized
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000055] AppArmor: AppArmor initialized
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000057] Yama: becoming mindful.
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.000938] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.003721] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.004912] Mount-cache hash table entries: 256
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.005160] Initializing cgroup subsys cpuacct
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.005164] Initializing cgroup subsys memory
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.005174] Initializing cgroup subsys devices
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.005176] Initializing cgroup subsys freezer
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.005178] Initializing cgroup subsys blkio
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.005180] Initializing cgroup subsys perf_event
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.005216] CPU: Physical Processor ID: 0
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.005217] CPU: Processor Core ID: 0
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.005224] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.005224] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.005227] mce: CPU supports 7 MCE banks
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.005241] CPU0: Thermal monitoring handled by SMI
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.005251] using mwait in idle threads.
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.009362] ACPI: Core revision 20120320
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.030491] ftrace: allocating 27653 entries in 109 pages
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.053685] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.093369] CPU0: Intel(R) Core(TM) i3-2367M CPU @ 1.40GHz stepping 07
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [    0.199478] Performance  Events: PEBS fmt1+, 16-deep LBR, SandyBridge events, Intel PMU driver.
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.199486] PEBS disabled due to CPU errata.
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.199489] ... version:                3
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.199491] ... bit width:              48
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.199492] ... generic registers:      4
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.199494] ... value mask:             0000ffffffffffff
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.199496] ... max period:             000000007fffffff
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.199497] ... fixed-purpose events:   3
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.199499] ... event mask:             000000070000000f
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [    0.199720] NMI watchdog:  enabled on all CPUs, permanently consumes one hw-PMU counter.
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.211059] CPU1: Thermal monitoring handled by SMI
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.224324] CPU2: Thermal monitoring handled by SMI
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.237569] CPU3: Thermal monitoring handled by SMI
Aug  8 12:29:31 james-ThinkPad-X131e modem-manager[924]: <info>  Loaded plugin Option High-Speed
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.199852] Booting Node   0, Processors  #1 #2 #3
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.239708] Brought up 4 CPUs
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.239713] Total of 4 processors activated (11174.89 BogoMIPS).
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.245200] devtmpfs: initialized
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.246977] EVM: security.selinux
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.246979] EVM: security.SMACK64
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.246981] EVM: security.capability
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [    0.247041] PM: Registering  ACPI NVS region [mem 0xdae9f000-0xdaf9efff] (1048576 bytes)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.248194] dummy: 
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.248234] RTC time: 12:29:08, date: 08/08/13
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.248283] NET: Registered protocol family 16
Aug  8 12:29:31 james-ThinkPad-X131e modem-manager[924]: <info>  Loaded plugin Gobi
Aug  8 12:29:31 james-ThinkPad-X131e modem-manager[924]: <info>  Loaded plugin Option
Aug  8 12:29:31 james-ThinkPad-X131e modem-manager[924]: <info>  Loaded plugin Samsung
Aug  8 12:29:31 james-ThinkPad-X131e modem-manager[924]: <info>  Loaded plugin Huawei
Aug  8 12:29:31 james-ThinkPad-X131e modem-manager[924]: <info>  Loaded plugin X22X
Aug  8 12:29:31 james-ThinkPad-X131e modem-manager[924]: <info>  Loaded plugin Sierra
Aug  8 12:29:31 james-ThinkPad-X131e modem-manager[924]: <info>  Loaded plugin Longcheer
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.248408] Trying to unpack rootfs image as initramfs...
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.248517] ACPI: bus type pci registered
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [    0.248604] PCI: MMCONFIG  for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base  0xf8000000)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.248607] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.258327] PCI: Using configuration type 1 for base access
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.259797] bio: create slab <bio-0> at 0
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.259913] ACPI: Added _OSI(Module Device)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.259916] ACPI: Added _OSI(Processor Device)
Aug  8 12:29:31 james-ThinkPad-X131e modem-manager[924]: <info>  Loaded plugin MotoC
Aug  8 12:29:31 james-ThinkPad-X131e modem-manager[924]: <info>  Loaded plugin Novatel
Aug  8 12:29:31 james-ThinkPad-X131e modem-manager[924]: <info>  Loaded plugin ZTE
Aug  8 12:29:31 james-ThinkPad-X131e NetworkManager[932]: <info> NetworkManager (version 0.9.4.0) is starting...
Aug  8 12:29:31 james-ThinkPad-X131e NetworkManager[932]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
Aug  8 12:29:31 james-ThinkPad-X131e avahi-daemon[927]: Successfully called chroot().
Aug  8 12:29:31 james-ThinkPad-X131e avahi-daemon[927]: Successfully dropped remaining capabilities.
Aug  8 12:29:31 james-ThinkPad-X131e avahi-daemon[927]: Loading service file /services/udisks.service.
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.259918] ACPI: Added _OSI(3.0 _SCP Extensions)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.259920] ACPI: Added _OSI(Processor Aggregator Device)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.263072] ACPI: EC: Look up EC in DSDT
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.266329] ACPI: Executed 1 blocks of module-level executable AML code
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.271962] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [    0.272650] ACPI: SSDT  00000000dae3e018 0096A (v01  PmRef  Cpu0Cst 00003001 INTL 20061109)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.273466] ACPI: Dynamic OEM Table Load:
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [    0.273470] ACPI:  SSDT           (null) 0096A (v01  PmRef  Cpu0Cst 00003001 INTL 20061109)
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [    0.307870] ACPI: SSDT  00000000dae3fa98 00303 (v01  PmRef    ApIst 00003000 INTL 20061109)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.308732] ACPI: Dynamic OEM Table Load:
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [    0.308736] ACPI:  SSDT           (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20061109)
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [    0.343648] ACPI: SSDT  00000000dae3dd98 00119 (v01  PmRef    ApCst 00003000 INTL 20061109)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.344464] ACPI: Dynamic OEM Table Load:
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [    0.344467] ACPI:  SSDT           (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20061109)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.650670] Freeing initrd memory: 15180k freed
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.807633] ACPI: Interpreter enabled
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.807640] ACPI: (supports S0 S3 S4 S5)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.807683] ACPI: Using IOAPIC for interrupt routing
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.818770] ACPI: EC: GPE = 0x16, I/O: command/status = 0x66, data = 0x62
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.819052] ACPI: No dock devices found.
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [    0.819057] PCI: Using host  bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.819580] \_SB_.PCI0:_OSC invalid UUID
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.819583] _OSC request data:1 8 1f 
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.819589] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.820395] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.820398] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.820401] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.820406] pci_root PNP0A08:00: host bridge window [mem 0xdfa00000-0xfeafffff]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.820409] pci_root PNP0A08:00: host bridge window [mem 0xfed40000-0xfed44fff]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.820448] PCI host bridge to bus 0000:00
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.820452] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.820455] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.820457] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.820460] pci_bus 0000:00: root bus resource [mem 0xdfa00000-0xfeafffff]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.820463] pci_bus 0000:00: root bus resource [mem 0xfed40000-0xfed44fff]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.820476] pci 0000:00:00.0: [8086:0104] type 00 class 0x060000
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.820533] pci 0000:00:02.0: [8086:0116] type 00 class 0x030000
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.820550] pci 0000:00:02.0: reg 10: [mem 0xf0000000-0xf03fffff 64bit]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.820560] pci 0000:00:02.0: reg 18: [mem 0xe0000000-0xefffffff 64bit pref]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.820567] pci 0000:00:02.0: reg 20: [io  0x5000-0x503f]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.820658] pci 0000:00:14.0: [8086:1e31] type 00 class 0x0c0330
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.820698] pci 0000:00:14.0: reg 10: [mem 0xf1700000-0xf170ffff 64bit]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.820829] pci 0000:00:14.0: PME# supported from D3hot D3cold
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.820869] pci 0000:00:16.0: [8086:1e3a] type 00 class 0x078000
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.820909] pci 0000:00:16.0: reg 10: [mem 0xf1715000-0xf171500f 64bit]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.821039] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.821101] pci 0000:00:1a.0: [8086:1e2d] type 00 class 0x0c0320
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.821136] pci 0000:00:1a.0: reg 10: [mem 0xf171a000-0xf171a3ff]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.821287] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.821332] pci 0000:00:1b.0: [8086:1e20] type 00 class 0x040300
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.821358] pci 0000:00:1b.0: reg 10: [mem 0xf1710000-0xf1713fff 64bit]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.821487] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.821528] pci 0000:00:1c.0: [8086:1e10] type 01 class 0x060400
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.821670] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.821706] pci 0000:00:1c.1: [8086:1e12] type 01 class 0x060400
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.821847] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.821886] pci 0000:00:1c.2: [8086:1e14] type 01 class 0x060400
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.822026] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.822069] pci 0000:00:1c.5: [8086:1e1a] type 01 class 0x060400
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.822214] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.822268] pci 0000:00:1d.0: [8086:1e26] type 00 class 0x0c0320
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.822303] pci 0000:00:1d.0: reg 10: [mem 0xf1719000-0xf17193ff]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.822451] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.822490] pci 0000:00:1f.0: [8086:1e57] type 00 class 0x060100
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.822687] pci 0000:00:1f.2: [8086:1e03] type 00 class 0x010601
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.822726] pci 0000:00:1f.2: reg 10: [io  0x5088-0x508f]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.822743] pci 0000:00:1f.2: reg 14: [io  0x5094-0x5097]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.822759] pci 0000:00:1f.2: reg 18: [io  0x5080-0x5087]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.822772] pci 0000:00:1f.2: reg 1c: [io  0x5090-0x5093]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.822787] pci 0000:00:1f.2: reg 20: [io  0x5060-0x507f]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.822804] pci 0000:00:1f.2: reg 24: [mem 0xf1718000-0xf17187ff]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.822898] pci 0000:00:1f.2: PME# supported from D3hot
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.822935] pci 0000:00:1f.3: [8086:1e22] type 00 class 0x0c0500
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.822961] pci 0000:00:1f.3: reg 10: [mem 0xf1714000-0xf17140ff 64bit]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.823002] pci 0000:00:1f.3: reg 20: [io  0xefa0-0xefbf]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.823136] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.823293] pci 0000:03:00.0: [14e4:4359] type 00 class 0x028000
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.823333] pci 0000:03:00.0: reg 10: [mem 0xf1600000-0xf1603fff 64bit]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.823546] pci 0000:03:00.0: supports D1 D2
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.823548] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.831461] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.831473] pci 0000:00:1c.1:   bridge window [mem 0xf1600000-0xf16fffff]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.831590] pci 0000:04:00.0: [10ec:5209] type 00 class 0xff0000
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.831619] pci 0000:04:00.0: reg 10: [mem 0xf0e00000-0xf0e00fff]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.831828] pci 0000:04:00.0: supports D1 D2
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.831830] pci 0000:04:00.0: PME# supported from D1 D2 D3hot
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.839421] pci 0000:00:1c.2: PCI bridge to [bus 04-08]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.839431] pci 0000:00:1c.2:   bridge window [io  0x4000-0x4fff]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.839441] pci 0000:00:1c.2:   bridge window [mem 0xf0e00000-0xf15fffff]
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [    0.839462] pci  0000:00:1c.2:   bridge window [mem 0xf0400000-0xf0bfffff 64bit pref]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.839573] pci 0000:09:00.0: [10ec:8168] type 00 class 0x020000
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.839602] pci 0000:09:00.0: reg 10: [io  0x3000-0x30ff]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.839651] pci 0000:09:00.0: reg 18: [mem 0xf0c04000-0xf0c04fff 64bit pref]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.839682] pci 0000:09:00.0: reg 20: [mem 0xf0c00000-0xf0c03fff 64bit pref]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.839813] pci 0000:09:00.0: supports D1 D2
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.839816] pci 0000:09:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.847420] pci 0000:00:1c.5: PCI bridge to [bus 09-09]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.847430] pci 0000:00:1c.5:   bridge window [io  0x3000-0x3fff]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.847439] pci 0000:00:1c.5:   bridge window [mem 0xf0d00000-0xf0dfffff]
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [    0.847460] pci  0000:00:1c.5:   bridge window [mem 0xf0c00000-0xf0cfffff 64bit pref]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.847498] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.847669] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.847718] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.847765] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.847817] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.847970] \_SB_.PCI0:_OSC invalid UUID
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.847972] _OSC request data:1 1f 1f 
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.847979]  pci0000:00: Requesting ACPI _OSC control (0x1d)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.848044] \_SB_.PCI0:_OSC invalid UUID
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.848046] _OSC request data:1 0 1d 
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [    0.848051]  pci0000:00:  ACPI _OSC request failed (AE_ERROR), returned control mask: 0x1d
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.848053] ACPI _OSC control for PCIe not granted, disabling ASPM
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.852532] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 10 *11 12 14 15)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.852603] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 10 *11 12 14 15)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.852669] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 *10 11 12 14 15)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.852734] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 10 11 12 14 15) *7
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [    0.852799] ACPI: PCI  Interrupt Link [LNKE] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [    0.852865] ACPI: PCI  Interrupt Link [LNKF] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.852930] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 10 11 12 14 15) *7
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.852995] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 *10 11 12 14 15)
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [    0.853125] vgaarb: device  added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.853134] vgaarb: loaded
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.853136] vgaarb: bridge control possible 0000:00:02.0
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.853351] SCSI subsystem initialized
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.853395] libata version 3.00 loaded.
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.853421] ACPI: bus type usb registered
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.853443] usbcore: registered new interface driver usbfs
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.853456] usbcore: registered new interface driver hub
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.853484] usbcore: registered new device driver usb
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.853575] PCI: Using ACPI for IRQ routing
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.857096] PCI: pci_cache_line_size set to 64 bytes
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.857221] e820: reserve RAM buffer [mem 0x0009d800-0x0009ffff]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.857223] e820: reserve RAM buffer [mem 0xd06a0000-0xd3ffffff]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.857225] e820: reserve RAM buffer [mem 0x21e600000-0x21fffffff]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.857342] NetLabel: Initializing
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.857344] NetLabel:  domain hash size = 128
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.857346] NetLabel:  protocols = UNLABELED CIPSOv4
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.857360] NetLabel:  unlabeled traffic allowed by default
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.857440] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.857450] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.859473] Switching to clocksource hpet
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.868063] AppArmor: AppArmor Filesystem Enabled
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.868093] pnp: PnP ACPI init
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.868111] ACPI: bus type pnp registered
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.868583] pnp 00:00: [bus 00-3e]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.868587] pnp 00:00: [io  0x0000-0x0cf7 window]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.868590] pnp 00:00: [io  0x0cf8-0x0cff]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.868593] pnp 00:00: [io  0x0d00-0xffff window]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.868596] pnp 00:00: [mem 0x000a0000-0x000bffff window]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.868599] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.868602] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.868605] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.868607] pnp 00:00: [mem 0x000cc000-0x000cffff window]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.868610] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.868613] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.868616] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.868618] pnp 00:00: [mem 0x000dc000-0x000dffff window]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.868621] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.868624] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.868627] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.868629] pnp 00:00: [mem 0x000ec000-0x000effff window]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.868632] pnp 00:00: [mem 0x000f0000-0x000fffff window]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.868635] pnp 00:00: [mem 0xdfa00000-0xfeafffff window]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.868638] pnp 00:00: [mem 0xfed40000-0xfed44fff window]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.868730] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.868749] pnp 00:01: [io  0x0000-0x001f]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.868752] pnp 00:01: [io  0x0081-0x0091]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.868755] pnp 00:01: [io  0x0093-0x009f]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.868757] pnp 00:01: [io  0x00c0-0x00df]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.868760] pnp 00:01: [dma 4]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.868786] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.868797] pnp 00:02: [mem 0xff000000-0xffffffff]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.868823] pnp 00:02: Plug and Play ACPI device, IDs INT0800 (active)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.868944] pnp 00:03: [mem 0xfed00000-0xfed003ff]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.868971] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.868984] pnp 00:04: [io  0x00f0]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.868996] pnp 00:04: [irq 13]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.869024] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.869040] pnp 00:05: [io  0x002e-0x002f]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.869043] pnp 00:05: [io  0x004e-0x004f]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.869045] pnp 00:05: [io  0x0061]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.869048] pnp 00:05: [io  0x0063]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.869050] pnp 00:05: [io  0x0065]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.869052] pnp 00:05: [io  0x0067]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.869055] pnp 00:05: [io  0x0070]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.869057] pnp 00:05: [io  0x0080]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.869061] pnp 00:05: [io  0x0092]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.869064] pnp 00:05: [io  0x00b2-0x00b3]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.869066] pnp 00:05: [io  0x0680-0x069f]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.869069] pnp 00:05: [io  0x2000-0x2003]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.869071] pnp 00:05: [io  0x0800-0x080f]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.869074] pnp 00:05: [io  0xffff]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.869076] pnp 00:05: [io  0x0400-0x0453]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.869079] pnp 00:05: [io  0x0458-0x047f]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.869081] pnp 00:05: [io  0x0500-0x057f]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.869084] pnp 00:05: [io  0x1600-0x16fe]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.869086] pnp 00:05: [io  0xfe00]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.869088] pnp 00:05: [io  0x0068]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.869091] pnp 00:05: [io  0x006c]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.869093] pnp 00:05: [io  0x0700-0x070f]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.869154] system 00:05: [io  0x0680-0x069f] has been reserved
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.869157] system 00:05: [io  0x2000-0x2003] has been reserved
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.869161] system 00:05: [io  0x0800-0x080f] has been reserved
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.869164] system 00:05: [io  0xffff] has been reserved
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.869167] system 00:05: [io  0x0400-0x0453] has been reserved
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.869170] system 00:05: [io  0x0458-0x047f] has been reserved
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.869172] system 00:05: [io  0x0500-0x057f] has been reserved
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.869175] system 00:05: [io  0x1600-0x16fe] has been reserved
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.869178] system 00:05: [io  0xfe00] has been reserved
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.869182] system 00:05: [io  0x0700-0x070f] has been reserved
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.869186] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.869197] pnp 00:06: [io  0x0070-0x0077]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.869204] pnp 00:06: [irq 8]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.869231] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.869268] pnp 00:07: [io  0x0454-0x0457]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.869312] system 00:07: [io  0x0454-0x0457] has been reserved
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [    0.869316] system 00:07:  Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.869328] pnp 00:08: [io  0x0060]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.869330] pnp 00:08: [io  0x0064]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.869337] pnp 00:08: [irq 1]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.869364] pnp 00:08: Plug and Play ACPI device, IDs PNP0303 (active)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.869379] pnp 00:09: [irq 12]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.869409] pnp 00:09: Plug and Play ACPI device, IDs LEN0026 PNP0f13 (active)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.869456] pnp 00:0a: [mem 0xfed40000-0xfed44fff]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.869486] pnp 00:0a: Plug and Play ACPI device, IDs SMO1200 PNP0c31 (active)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.869649] pnp 00:0b: [mem 0xfed1c000-0xfed1ffff]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.869652] pnp 00:0b: [mem 0xfed10000-0xfed17fff]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.869654] pnp 00:0b: [mem 0xfed18000-0xfed18fff]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.869657] pnp 00:0b: [mem 0xfed19000-0xfed19fff]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.869659] pnp 00:0b: [mem 0xf8000000-0xfbffffff]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.869662] pnp 00:0b: [mem 0xfed20000-0xfed3ffff]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.869664] pnp 00:0b: [mem 0xfed90000-0xfed93fff]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.869667] pnp 00:0b: [mem 0xfed45000-0xfed8ffff]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.869669] pnp 00:0b: [mem 0xff000000-0xffffffff]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.869672] pnp 00:0b: [mem 0xfee00000-0xfeefffff]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.869674] pnp 00:0b: [mem 0xfffff000-0xffffffff]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.869728] system 00:0b: [mem 0xfed1c000-0xfed1ffff] has been reserved
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.869732] system 00:0b: [mem 0xfed10000-0xfed17fff] has been reserved
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.869735] system 00:0b: [mem 0xfed18000-0xfed18fff] has been reserved
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.869738] system 00:0b: [mem 0xfed19000-0xfed19fff] has been reserved
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.869741] system 00:0b: [mem 0xf8000000-0xfbffffff] has been reserved
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.869744] system 00:0b: [mem 0xfed20000-0xfed3ffff] has been reserved
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.869747] system 00:0b: [mem 0xfed90000-0xfed93fff] has been reserved
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.869750] system 00:0b: [mem 0xfed45000-0xfed8ffff] has been reserved
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.869754] system 00:0b: [mem 0xff000000-0xffffffff] could not be reserved
Aug  8 12:29:31 james-ThinkPad-X131e NetworkManager[932]: <info> VPN: loaded org.freedesktop.NetworkManager.openconnect
Aug  8 12:29:31 james-ThinkPad-X131e NetworkManager[932]: <info> VPN: loaded org.freedesktop.NetworkManager.pptp
Aug  8 12:29:31 james-ThinkPad-X131e NetworkManager[932]: <info> DNS: loaded plugin dnsmasq
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.869757] system 00:0b: [mem 0xfee00000-0xfeefffff] could not be reserved
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.869760] system 00:0b: [mem 0xfffff000-0xffffffff] has been reserved
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.869764] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.870096] pnp 00:0c: [mem 0x20000000-0x201fffff]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.870099] pnp 00:0c: [mem 0x40000000-0x401fffff]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.870167] system 00:0c: [mem 0x20000000-0x201fffff] has been reserved
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.870170] system 00:0c: [mem 0x40000000-0x401fffff] has been reserved
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.870174] system 00:0c: Plug and Play ACPI device, IDs PNP0c01 (active)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.870786] pnp: PnP ACPI: found 13 devices
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.870788] ACPI: ACPI bus type pnp unregistered
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.878001] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.878024] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.878033] pci 0000:00:1c.1:   bridge window [mem 0xf1600000-0xf16fffff]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.878047] pci 0000:00:1c.2: PCI bridge to [bus 04-08]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.878052] pci 0000:00:1c.2:   bridge window [io  0x4000-0x4fff]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.878060] pci 0000:00:1c.2:   bridge window [mem 0xf0e00000-0xf15fffff]
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [    0.878067] pci  0000:00:1c.2:   bridge window [mem 0xf0400000-0xf0bfffff 64bit pref]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.878078] pci 0000:00:1c.5: PCI bridge to [bus 09-09]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.878082] pci 0000:00:1c.5:   bridge window [io  0x3000-0x3fff]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.878091] pci 0000:00:1c.5:   bridge window [mem 0xf0d00000-0xf0dfffff]
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [    0.878098] pci  0000:00:1c.5:   bridge window [mem 0xf0c00000-0xf0cfffff 64bit pref]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.878156] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.878159] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.878162] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.878165] pci_bus 0000:00: resource 7 [mem 0xdfa00000-0xfeafffff]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.878168] pci_bus 0000:00: resource 8 [mem 0xfed40000-0xfed44fff]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.878171] pci_bus 0000:03: resource 1 [mem 0xf1600000-0xf16fffff]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.878174] pci_bus 0000:04: resource 0 [io  0x4000-0x4fff]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.878177] pci_bus 0000:04: resource 1 [mem 0xf0e00000-0xf15fffff]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.878180] pci_bus 0000:04: resource 2 [mem 0xf0400000-0xf0bfffff 64bit pref]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.878183] pci_bus 0000:09: resource 0 [io  0x3000-0x3fff]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.878186] pci_bus 0000:09: resource 1 [mem 0xf0d00000-0xf0dfffff]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.878189] pci_bus 0000:09: resource 2 [mem 0xf0c00000-0xf0cfffff 64bit pref]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.878229] NET: Registered protocol family 2
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.878492] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [    0.879646] TCP established  hash table entries: 524288 (order: 11, 8388608 bytes)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.881577] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.881763] TCP: Hash tables configured (established 524288 bind 65536)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.881765] TCP: reno registered
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.881785] UDP hash table entries: 4096 (order: 5, 131072 bytes)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.881838] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.881954] NET: Registered protocol family 1
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.881972] pci 0000:00:02.0: Boot video device
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.882220] PCI: CLS 64 bytes, default 64
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.882223] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [    0.882226] software IO TLB  [mem 0xcc69a000-0xd0699fff] (64MB) mapped at  [ffff8800cc69a000-ffff8800d0699fff]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.882881] audit: initializing netlink socket (disabled)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.882899] type=2000 audit(1375964948.760:1): initialized
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.921511] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.923887] VFS: Disk quotas dquot_6.5.2
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.923943] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.924545] fuse init (API version 7.19)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.924653] msgmni has been set to 15410
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.925142] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.925175] io scheduler noop registered
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.925179] io scheduler deadline registered (default)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.925216] io scheduler cfq registered
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.925627] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.925652] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.925710] intel_idle: MWAIT substates: 0x21120
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.925711] intel_idle: v0.4 model 0x2A
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    0.925713] intel_idle: lapic_timer_reliable_states 0xffffffff
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.127700] ACPI: AC Adapter [ACAD] (off-line)
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [    1.127812] input: Lid  Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.128396] ACPI: Lid Switch [LID]
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [    1.128451] input: Power  Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.128456] ACPI: Power Button [PWRB]
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [    1.128506] input: Sleep  Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.128510] ACPI: Sleep Button [SLPB]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.128552] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.128555] ACPI: Power Button [PWRF]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.128651] ACPI: Requesting acpi_cpufreq
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.139033] thermal LNXTHERM:00: registered as thermal_zone0
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.139037] ACPI: Thermal Zone [TZ00] (48 C)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.139066] ACPI: Battery Slot [BAT1] (battery present)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.139092] GHES: HEST is not enabled!
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.139197] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.140912] Linux agpgart interface v0.103
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.142747] brd: module loaded
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.143746] loop: module loaded
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.143869] ahci 0000:00:1f.2: version 3.0
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.143881] ahci 0000:00:1f.2: power state changed by ACPI to D0
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.143887] ahci 0000:00:1f.2: power state changed by ACPI to D0
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.144081] ahci 0000:00:1f.2: irq 40 for MSI/MSI-X
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [    1.144149] ahci  0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x1 impl SATA mode
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [    1.144154] ahci  0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part ems apst 
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.144161] ahci 0000:00:1f.2: setting latency timer to 64
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.144889] scsi0 : ahci
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.144976] scsi1 : ahci
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.145052] scsi2 : ahci
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.145131] scsi3 : ahci
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.145215] scsi4 : ahci
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.145289] scsi5 : ahci
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.145628] ata1: SATA max UDMA/133 abar m2048@0xf1718000 port 0xf1718100 irq 40
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.145631] ata2: DUMMY
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.145632] ata3: DUMMY
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.145634] ata4: DUMMY
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.145635] ata5: DUMMY
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.145637] ata6: DUMMY
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.146032] Fixed MDIO Bus: probed
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.146082] tun: Universal TUN/TAP device driver, 1.6
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.146084] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.146137] PPP generic driver version 2.4.2
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.146192] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.146235] ehci_hcd 0000:00:1a.0: setting latency timer to 64
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.146240] ehci_hcd 0000:00:1a.0: EHCI Host Controller
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.146247] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.146282] ehci_hcd 0000:00:1a.0: debug port 2
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.150184] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.150206] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xf171a000
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.159423] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.159486] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.159490] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.159493] usb usb1: Product: EHCI Host Controller
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.159495] usb usb1: Manufacturer: Linux 3.5.0-23-generic ehci_hcd
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.159498] usb usb1: SerialNumber: 0000:00:1a.0
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.159634] hub 1-0:1.0: USB hub found
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.159640] hub 1-0:1.0: 3 ports detected
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.159730] ehci_hcd 0000:00:1d.0: setting latency timer to 64
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.159735] ehci_hcd 0000:00:1d.0: EHCI Host Controller
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.159741] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.159771] ehci_hcd 0000:00:1d.0: debug port 2
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.163670] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.163688] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xf1719000
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.175431] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.175477] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.175480] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.175482] usb usb2: Product: EHCI Host Controller
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.175485] usb usb2: Manufacturer: Linux 3.5.0-23-generic ehci_hcd
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.175488] usb usb2: SerialNumber: 0000:00:1d.0
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.175610] hub 2-0:1.0: USB hub found
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.175615] hub 2-0:1.0: 3 ports detected
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.175684] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.175703] uhci_hcd: USB Universal Host Controller Interface driver
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.175762] xhci_hcd 0000:00:14.0: setting latency timer to 64
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.175766] xhci_hcd 0000:00:14.0: xHCI Host Controller
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.175772] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 3
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.175874] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.175892] xhci_hcd 0000:00:14.0: irq 21, io mem 0xf1700000
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.175971] xhci_hcd 0000:00:14.0: irq 41 for MSI/MSI-X
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.176030] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.176034] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.176036] usb usb3: Product: xHCI Host Controller
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.176039] usb usb3: Manufacturer: Linux 3.5.0-23-generic xhci_hcd
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.176042] usb usb3: SerialNumber: 0000:00:14.0
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.176146] xHCI xhci_add_endpoint called for root hub
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.176148] xHCI xhci_check_bandwidth called for root hub
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.176175] hub 3-0:1.0: USB hub found
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.176184] hub 3-0:1.0: 4 ports detected
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.176252] xhci_hcd 0000:00:14.0: xHCI Host Controller
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.176257] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 4
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.176282] usb usb4: New USB device found, idVendor=1d6b, idProduct=0003
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.176285] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.176288] usb usb4: Product: xHCI Host Controller
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.176291] usb usb4: Manufacturer: Linux 3.5.0-23-generic xhci_hcd
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.176293] usb usb4: SerialNumber: 0000:00:14.0
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.176381] xHCI xhci_add_endpoint called for root hub
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.176383] xHCI xhci_check_bandwidth called for root hub
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.176410] hub 4-0:1.0: USB hub found
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.176419] hub 4-0:1.0: 4 ports detected
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.176574] usbcore: registered new interface driver libusual
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [    1.176620] i8042: PNP: PS/2  Controller [PNP0303:PSK2,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.179998] i8042: Detected active multiplexing controller, rev 1.1
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.181718] serio: i8042 KBD port at 0x60,0x64 irq 1
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.181725] serio: i8042 AUX0 port at 0x60,0x64 irq 12
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.181734] serio: i8042 AUX1 port at 0x60,0x64 irq 12
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.181738] serio: i8042 AUX2 port at 0x60,0x64 irq 12
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.181740] serio: i8042 AUX3 port at 0x60,0x64 irq 12
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.181948] mousedev: PS/2 mouse device common for all mice
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.182174] rtc_cmos 00:06: RTC can wake from S4
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.182312] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.182345] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.182431] device-mapper: uevent: version 1.0.3
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [    1.182505] device-mapper:  ioctl: 4.22.0-ioctl (2011-10-19) initialised: [email]dm-devel@redhat.com[/email]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.182612] cpuidle: using governor ladder
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.182752] cpuidle: using governor menu
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.182755] EFI Variables Facility v0.08 2004-May-17
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.183050] ashmem: initialized
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.183227] TCP: cubic registered
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.183351] NET: Registered protocol family 10
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.183627] NET: Registered protocol family 17
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.183640] Key type dns_resolver registered
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.184127] PM: Hibernation image not present or could not be loaded.
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.184144] registered taskstats version 1
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.187573] Key type trusted registered
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.190285] Key type encrypted registered
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.193437]   Magic number: 9:809:480
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [    1.193580] rtc_cmos 00:06:  setting system clock to 2013-08-08 12:29:09 UTC (1375964949)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.194462] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.194464] EDD information not available.
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [    1.225743] input: AT  Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.463490] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.465166] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [    1.465173] ata1.00: ACPI  cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.465177] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.471486] usb 1-1: new high-speed USB device number 2 using ehci_hcd
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.483980] ata1.00: ATA-8: ST320LT007-9ZV142, 0004LVM1, max UDMA/133
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.483986] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.487086] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [    1.487093] ata1.00: ACPI  cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.487097] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.489818] ata1.00: configured for UDMA/133
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [    1.490106] scsi 0:0:0:0:  Direct-Access     ATA      ST320LT007-9ZV14 0004 PQ: 0 ANSI: 5
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.490315] sd 0:0:0:0: Attached scsi generic sg0 type 0
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [    1.490339] sd 0:0:0:0:  [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.490344] sd 0:0:0:0: [sda] 4096-byte physical blocks
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.490471] sd 0:0:0:0: [sda] Write Protect is off
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.490477] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [    1.490658] sd 0:0:0:0:  [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or  FUA
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.570623]  sda: sda1 sda2 sda3 < sda5 sda6 >
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.571377] sd 0:0:0:0: [sda] Attached SCSI disk
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.603984] usb 1-1: New USB device found, idVendor=8087, idProduct=0024
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.603990] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.604441] hub 1-1:1.0: USB hub found
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.604646] hub 1-1:1.0: 6 ports detected
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.702683] ACPI: Battery Slot [BAT1] (battery present)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.704779] Freeing unused kernel memory: 948k freed
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.704942] Write protecting the kernel read-only data: 12288k
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.710783] Freeing unused kernel memory: 1352k freed
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.715388] usb 2-1: new high-speed USB device number 2 using ehci_hcd
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.715488] Freeing unused kernel memory: 1048k freed
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.848150] usb 2-1: New USB device found, idVendor=8087, idProduct=0024
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.848157] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.848676] hub 2-1:1.0: USB hub found
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.848873] hub 2-1:1.0: 8 ports detected
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.875652] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.875852] r8169 0000:09:00.0: irq 42 for MSI/MSI-X
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [    1.876161] r8169  0000:09:00.0: eth0: RTL8168evl/8111evl at 0xffffc90000c72000,  08:9e:01:1a:89:b2, XID 0c900800 IRQ 42
Aug  8 12:29:31  james-ThinkPad-X131e kernel: [    1.876169] r8169 0000:09:00.0: eth0:  jumbo features [frames: 9200 bytes, tx checksumming: ko]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.879368] Refined TSC clocksource calibration: 1396.826 MHz.
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    1.879377] Switching to clocksource tsc
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    2.015342] usb 3-2: new low-speed USB device number 2 using xhci_hcd
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    2.034438] usb 3-2: New USB device found, idVendor=0461, idProduct=4d15
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    2.034448] usb 3-2: New USB device strings: Mfr=0, Product=2, SerialNumber=0
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    2.034453] usb 3-2: Product: USB Optical Mouse
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [    2.034823] usb 3-2: ep 0x81  - rounding interval to 64 microframes, ep desc says 80 microframes
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    2.039952] usbcore: registered new interface driver usbhid
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    2.039956] usbhid: USB HID core driver
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [    2.042588] input: USB  Optical Mouse as  /devices/pci0000:00/0000:00:14.0/usb3/3-2/3-2:1.0/input/input5
Aug  8  12:29:31 james-ThinkPad-X131e kernel: [    2.042749] hid-generic  0003:0461:4D15.0001: input,hidraw0: USB HID v1.11 Mouse [USB Optical  Mouse] on usb-0000:00:14.0-2/input0
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    2.199316] usb 3-4: new high-speed USB device number 3 using xhci_hcd
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    2.226862] usb 3-4: New USB device found, idVendor=5986, idProduct=0299
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    2.226868] usb 3-4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    2.226871] usb 3-4: Product: Integrated Camera
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    2.226874] usb 3-4: Manufacturer: Vimicro corp.
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    2.999726] EXT4-fs (sda5): INFO: recovery required on readonly filesystem
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    2.999731] EXT4-fs (sda5): write access will be enabled during recovery
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    5.896676] EXT4-fs (sda5): orphan cleanup on readonly fs
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [    5.896688] EXT4-fs (sda5):  ext4_orphan_cleanup: deleting unreferenced inode 15731730
Aug  8  12:29:31 james-ThinkPad-X131e kernel: [    5.896791] EXT4-fs (sda5):  ext4_orphan_cleanup: deleting unreferenced inode 15731713
Aug  8  12:29:31 james-ThinkPad-X131e kernel: [    5.896809] EXT4-fs (sda5):  ext4_orphan_cleanup: deleting unreferenced inode 15731293
Aug  8  12:29:31 james-ThinkPad-X131e kernel: [    5.896826] EXT4-fs (sda5):  ext4_orphan_cleanup: deleting unreferenced inode 15731183
Aug  8  12:29:31 james-ThinkPad-X131e kernel: [    5.896872] EXT4-fs (sda5):  ext4_orphan_cleanup: deleting unreferenced inode 15731731
Aug  8  12:29:31 james-ThinkPad-X131e kernel: [    5.896917] EXT4-fs (sda5):  ext4_orphan_cleanup: deleting unreferenced inode 15731729
Aug  8  12:29:31 james-ThinkPad-X131e kernel: [    5.896933] EXT4-fs (sda5):  ext4_orphan_cleanup: deleting unreferenced inode 15731726
Aug  8  12:29:31 james-ThinkPad-X131e kernel: [    5.896999] EXT4-fs (sda5):  ext4_orphan_cleanup: deleting unreferenced inode 15731725
Aug  8  12:29:31 james-ThinkPad-X131e kernel: [    5.941325] EXT4-fs (sda5):  ext4_orphan_cleanup: deleting unreferenced inode 15731534
Aug  8  12:29:31 james-ThinkPad-X131e kernel: [    5.941381] EXT4-fs (sda5):  ext4_orphan_cleanup: deleting unreferenced inode 15731307
Aug  8  12:29:31 james-ThinkPad-X131e kernel: [    5.954849] EXT4-fs (sda5):  ext4_orphan_cleanup: deleting unreferenced inode 15731165
Aug  8  12:29:31 james-ThinkPad-X131e kernel: [    5.954891] EXT4-fs (sda5):  ext4_orphan_cleanup: deleting unreferenced inode 15731710
Aug  8  12:29:31 james-ThinkPad-X131e kernel: [    5.954910] EXT4-fs (sda5):  ext4_orphan_cleanup: deleting unreferenced inode 15731708
Aug  8  12:29:31 james-ThinkPad-X131e kernel: [    5.954925] EXT4-fs (sda5):  ext4_orphan_cleanup: deleting unreferenced inode 15731704
Aug  8  12:29:31 james-ThinkPad-X131e kernel: [    5.954941] EXT4-fs (sda5):  ext4_orphan_cleanup: deleting unreferenced inode 15731640
Aug  8  12:29:31 james-ThinkPad-X131e kernel: [    5.954960] EXT4-fs (sda5):  ext4_orphan_cleanup: deleting unreferenced inode 15731706
Aug  8  12:29:31 james-ThinkPad-X131e kernel: [    5.955011] EXT4-fs (sda5):  ext4_orphan_cleanup: deleting unreferenced inode 15731702
Aug  8  12:29:31 james-ThinkPad-X131e kernel: [    5.955027] EXT4-fs (sda5):  ext4_orphan_cleanup: deleting unreferenced inode 15731306
Aug  8  12:29:31 james-ThinkPad-X131e kernel: [    5.955043] EXT4-fs (sda5):  ext4_orphan_cleanup: deleting unreferenced inode 15731701
Aug  8  12:29:31 james-ThinkPad-X131e kernel: [    5.955058] EXT4-fs (sda5):  ext4_orphan_cleanup: deleting unreferenced inode 15731680
Aug  8  12:29:31 james-ThinkPad-X131e kernel: [    5.955074] EXT4-fs (sda5):  ext4_orphan_cleanup: deleting unreferenced inode 15731669
Aug  8  12:29:31 james-ThinkPad-X131e kernel: [    5.955091] EXT4-fs (sda5):  ext4_orphan_cleanup: deleting unreferenced inode 15731662
Aug  8  12:29:31 james-ThinkPad-X131e kernel: [    5.955107] EXT4-fs (sda5):  ext4_orphan_cleanup: deleting unreferenced inode 15731528
Aug  8  12:29:31 james-ThinkPad-X131e kernel: [    5.955122] EXT4-fs (sda5):  ext4_orphan_cleanup: deleting unreferenced inode 15731308
Aug  8  12:29:31 james-ThinkPad-X131e kernel: [    5.955137] EXT4-fs (sda5):  ext4_orphan_cleanup: deleting unreferenced inode 15731545
Aug  8  12:29:31 james-ThinkPad-X131e kernel: [    5.955154] EXT4-fs (sda5):  ext4_orphan_cleanup: deleting unreferenced inode 15731541
Aug  8  12:29:31 james-ThinkPad-X131e kernel: [    5.955169] EXT4-fs (sda5):  ext4_orphan_cleanup: deleting unreferenced inode 15731533
Aug  8  12:29:31 james-ThinkPad-X131e kernel: [    5.955184] EXT4-fs (sda5):  ext4_orphan_cleanup: deleting unreferenced inode 15731531
Aug  8  12:29:31 james-ThinkPad-X131e kernel: [    5.955200] EXT4-fs (sda5):  ext4_orphan_cleanup: deleting unreferenced inode 15731506
Aug  8  12:29:31 james-ThinkPad-X131e kernel: [    5.955217] EXT4-fs (sda5):  ext4_orphan_cleanup: deleting unreferenced inode 15731447
Aug  8  12:29:31 james-ThinkPad-X131e kernel: [    5.955233] EXT4-fs (sda5):  ext4_orphan_cleanup: deleting unreferenced inode 15731445
Aug  8  12:29:31 james-ThinkPad-X131e kernel: [    5.955248] EXT4-fs (sda5):  ext4_orphan_cleanup: deleting unreferenced inode 15731340
Aug  8  12:29:31 james-ThinkPad-X131e kernel: [    5.955265] EXT4-fs (sda5):  ext4_orphan_cleanup: deleting unreferenced inode 15731323
Aug  8  12:29:31 james-ThinkPad-X131e kernel: [    5.955281] EXT4-fs (sda5):  ext4_orphan_cleanup: deleting unreferenced inode 15731321
Aug  8  12:29:31 james-ThinkPad-X131e kernel: [    5.955296] EXT4-fs (sda5):  ext4_orphan_cleanup: deleting unreferenced inode 15731319
Aug  8  12:29:31 james-ThinkPad-X131e kernel: [    5.955312] EXT4-fs (sda5):  ext4_orphan_cleanup: deleting unreferenced inode 15731317
Aug  8  12:29:31 james-ThinkPad-X131e kernel: [    5.955327] EXT4-fs (sda5):  ext4_orphan_cleanup: deleting unreferenced inode 15731313
Aug  8  12:29:31 james-ThinkPad-X131e kernel: [    5.955342] EXT4-fs (sda5):  ext4_orphan_cleanup: deleting unreferenced inode 15731312
Aug  8  12:29:31 james-ThinkPad-X131e kernel: [    5.955357] EXT4-fs (sda5):  ext4_orphan_cleanup: deleting unreferenced inode 15731311
Aug  8  12:29:31 james-ThinkPad-X131e kernel: [    5.955372] EXT4-fs (sda5):  ext4_orphan_cleanup: deleting unreferenced inode 15731310
Aug  8  12:29:31 james-ThinkPad-X131e kernel: [    5.955386] EXT4-fs (sda5):  ext4_orphan_cleanup: deleting unreferenced inode 15731304
Aug  8  12:29:31 james-ThinkPad-X131e kernel: [    5.955401] EXT4-fs (sda5):  ext4_orphan_cleanup: deleting unreferenced inode 15731301
Aug  8  12:29:31 james-ThinkPad-X131e kernel: [    5.995191] EXT4-fs (sda5):  ext4_orphan_cleanup: deleting unreferenced inode 10355618
Aug  8  12:29:31 james-ThinkPad-X131e kernel: [    6.012702] EXT4-fs (sda5):  ext4_orphan_cleanup: deleting unreferenced inode 10356506
Aug  8  12:29:31 james-ThinkPad-X131e kernel: [    6.012757] EXT4-fs (sda5):  ext4_orphan_cleanup: deleting unreferenced inode 15731300
Aug  8  12:29:31 james-ThinkPad-X131e kernel: [    6.012775] EXT4-fs (sda5):  ext4_orphan_cleanup: deleting unreferenced inode 15731185
Aug  8  12:29:31 james-ThinkPad-X131e kernel: [    6.012792] EXT4-fs (sda5):  ext4_orphan_cleanup: deleting unreferenced inode 15731182
Aug  8  12:29:31 james-ThinkPad-X131e kernel: [    6.012808] EXT4-fs (sda5):  ext4_orphan_cleanup: deleting unreferenced inode 15731179
Aug  8  12:29:31 james-ThinkPad-X131e kernel: [    6.012824] EXT4-fs (sda5):  ext4_orphan_cleanup: deleting unreferenced inode 15731188
Aug  8  12:29:31 james-ThinkPad-X131e kernel: [    6.053859] EXT4-fs (sda5):  ext4_orphan_cleanup: deleting unreferenced inode 8650789
Aug  8  12:29:31 james-ThinkPad-X131e kernel: [    6.053916] EXT4-fs (sda5):  ext4_orphan_cleanup: deleting unreferenced inode 8650788
Aug  8  12:29:31 james-ThinkPad-X131e kernel: [    6.053935] EXT4-fs (sda5):  ext4_orphan_cleanup: deleting unreferenced inode 15731709
Aug  8  12:29:31 james-ThinkPad-X131e kernel: [    6.064485] EXT4-fs (sda5):  ext4_orphan_cleanup: deleting unreferenced inode 15731186
Aug  8  12:29:31 james-ThinkPad-X131e kernel: [    6.064514] EXT4-fs (sda5):  ext4_orphan_cleanup: deleting unreferenced inode 15731171
Aug  8  12:29:31 james-ThinkPad-X131e kernel: [    6.064533] EXT4-fs (sda5):  ext4_orphan_cleanup: deleting unreferenced inode 15731170
Aug  8  12:29:31 james-ThinkPad-X131e kernel: [    6.064552] EXT4-fs (sda5):  ext4_orphan_cleanup: deleting unreferenced inode 15731722
Aug  8  12:29:31 james-ThinkPad-X131e kernel: [    6.064569] EXT4-fs (sda5):  ext4_orphan_cleanup: deleting unreferenced inode 15731343
Aug  8  12:29:31 james-ThinkPad-X131e kernel: [    6.064591] EXT4-fs (sda5):  ext4_orphan_cleanup: deleting unreferenced inode 8650782
Aug  8  12:29:31 james-ThinkPad-X131e kernel: [    6.064602] EXT4-fs (sda5):  ext4_orphan_cleanup: deleting unreferenced inode 8650779
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    6.064618] EXT4-fs (sda5): 59 orphan inodes deleted
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    6.064620] EXT4-fs (sda5): recovery complete
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [    6.250887] EXT4-fs (sda5):  mounted filesystem with ordered data mode. Opts: (null)
Aug  8  12:29:31 james-ThinkPad-X131e kernel: [   21.923970] Adding 8100860k  swap on /dev/sda6.  Priority:-1 extents:1 across:8100860k 
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   21.929750] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.006101] lp: driver loaded but no devices found
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.204539] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.214998] tpm_tis 00:0a: 1.2 TPM (device-id 0x0, rev-id 78)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.215625] Non-volatile memory driver v1.3
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.266843] wmi: Mapper loaded
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.272852] tpm_tis 00:0a: TPM is disabled/deactivated (0x6)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.275293] [drm] Initialized drm 1.1.0 20060810
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.286908] lib80211: common routines for IEEE802.11 drivers
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.286913] lib80211_crypt: registered algorithm 'NULL'
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.297981] cfg80211: Calling CRDA to update world regulatory domain
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.298057] i915 0000:00:02.0: setting latency timer to 64
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.301970] pci 0000:00:00.0: Intel Sandybridge Chipset
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [   22.302118] pci  0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.303812] pci 0000:00:00.0: detected 65536K stolen memory
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.324812] wl: module license 'MIXED/Proprietary' taints kernel.
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.324818] Disabling lock debugging due to kernel taint
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [   22.362593] rts_pstor:  module is from the staging directory, the quality is unknown, you have  been warned.
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.363843] Initializing Realtek PCIE storage driver...
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.389324] Resource length: 0x1000
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.393231] Original address: 0xf0e00000, remapped address: 0xffffc900057ac000
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.393822] pci->irq = 18
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.393828] rtsx_acquire_irq: chip->msi_en = 0, pci->irq = 18
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.394674] thinkpad_acpi: ThinkPad ACPI Extras v0.24
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.394680] thinkpad_acpi: [http://ibm-acpi.sf.net/](http://ibm-acpi.sf.net/)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.394683] thinkpad_acpi: ThinkPad BIOS G8ET92WW (2.52 ), EC unknown
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.394686] thinkpad_acpi: Lenovo ThinkPad X131e, model 33682NG
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [   22.394737] cfg80211:  Updating information on frequency 2412 MHz for a 20 MHz width channel  with regulatory rule:
Aug  8 12:29:31 james-ThinkPad-X131e kernel:  [   22.394742] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600  mBi, 2000 mBm)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    22.394745] cfg80211: Updating information on frequency 2417 MHz for a 20  MHz width channel with regulatory rule:
Aug  8 12:29:31  james-ThinkPad-X131e kernel: [   22.394750] cfg80211: 2402000 KHz -  2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
Aug  8 12:29:31  james-ThinkPad-X131e kernel: [   22.394753] cfg80211: Updating  information on frequency 2422 MHz for a 20 MHz width channel with  regulatory rule:
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    22.394757] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi,  2000 mBm)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.394761]  cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width  channel with regulatory rule:
Aug  8 12:29:31 james-ThinkPad-X131e  kernel: [   22.394766] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz),  (600 mBi, 2000 mBm)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    22.394769] cfg80211: Updating information on frequency 2432 MHz for a  20 MHz width channel with regulatory rule:
Aug  8 12:29:31  james-ThinkPad-X131e kernel: [   22.394773] cfg80211: 2402000 KHz -  2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
Aug  8 12:29:31  james-ThinkPad-X131e kernel: [   22.394777] cfg80211: Updating  information on frequency 2437 MHz for a 20 MHz width channel with  regulatory rule:
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    22.394781] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi,  2000 mBm)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.394784]  cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width  channel with regulatory rule:
Aug  8 12:29:31 james-ThinkPad-X131e  kernel: [   22.394789] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz),  (600 mBi, 2000 mBm)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    22.394793] cfg80211: Updating information on frequency 2447 MHz for a  20 MHz width channel with regulatory rule:
Aug  8 12:29:31  james-ThinkPad-X131e kernel: [   22.394797] cfg80211: 2402000 KHz -  2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
Aug  8 12:29:31  james-ThinkPad-X131e kernel: [   22.394800] cfg80211: Updating  information on frequency 2452 MHz for a 20 MHz width channel with  regulatory rule:
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    22.394804] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi,  2000 mBm)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.394808]  cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width  channel with regulatory rule:
Aug  8 12:29:31 james-ThinkPad-X131e  kernel: [   22.394813] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz),  (600 mBi, 2000 mBm)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    22.394816] cfg80211: Updating information on frequency 2462 MHz for a  20 MHz width channel with regulatory rule:
Aug  8 12:29:31  james-ThinkPad-X131e kernel: [   22.394820] cfg80211: 2402000 KHz -  2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
Aug  8 12:29:31  james-ThinkPad-X131e kernel: [   22.394824] cfg80211: Updating  information on frequency 2467 MHz for a 20 MHz width channel with  regulatory rule:
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    22.394828] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz), (600 mBi,  2000 mBm)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.394832]  cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width  channel with regulatory rule:
Aug  8 12:29:31 james-ThinkPad-X131e  kernel: [   22.394836] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz),  (600 mBi, 2000 mBm)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    22.394839] cfg80211: Updating information on frequency 2484 MHz for a  20 MHz width channel with regulatory rule:
Aug  8 12:29:31  james-ThinkPad-X131e kernel: [   22.394844] cfg80211: 2474000 KHz -  2494000 KHz @ 20000 KHz), (600 mBi, 2000 mBm)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.394847] cfg80211: Disabling freq 5170 MHz
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [   22.394851] cfg80211:  Updating information on frequency 5180 MHz for a 20 MHz width channel  with regulatory rule:
Aug  8 12:29:31 james-ThinkPad-X131e kernel:  [   22.394855] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (600  mBi, 2000 mBm)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    22.394859] cfg80211: Updating information on frequency 5190 MHz for a 20  MHz width channel with regulatory rule:
Aug  8 12:29:31  james-ThinkPad-X131e kernel: [   22.394863] cfg80211: 5170000 KHz -  5250000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
Aug  8 12:29:31  james-ThinkPad-X131e kernel: [   22.394867] cfg80211: Updating  information on frequency 5200 MHz for a 20 MHz width channel with  regulatory rule:
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    22.394871] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (600 mBi,  2000 mBm)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.394874]  cfg80211: Updating information on frequency 5210 MHz for a 20 MHz width  channel with regulatory rule:
Aug  8 12:29:31 james-ThinkPad-X131e  kernel: [   22.394879] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz),  (600 mBi, 2000 mBm)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    22.394882] cfg80211: Updating information on frequency 5220 MHz for a  20 MHz width channel with regulatory rule:
Aug  8 12:29:31  james-ThinkPad-X131e kernel: [   22.394886] cfg80211: 5170000 KHz -  5250000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
Aug  8 12:29:31  james-ThinkPad-X131e kernel: [   22.394890] cfg80211: Updating  information on frequency 5230 MHz for a 20 MHz width channel with  regulatory rule:
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    22.394894] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (600 mBi,  2000 mBm)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.394898]  cfg80211: Updating information on frequency 5240 MHz for a 20 MHz width  channel with regulatory rule:
Aug  8 12:29:31 james-ThinkPad-X131e  kernel: [   22.394902] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz),  (600 mBi, 2000 mBm)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.394905] cfg80211: Disabling freq 5260 MHz
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.394908] cfg80211: Disabling freq 5280 MHz
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.394910] cfg80211: Disabling freq 5300 MHz
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.394913] cfg80211: Disabling freq 5320 MHz
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.394916] cfg80211: Disabling freq 5500 MHz
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.394918] cfg80211: Disabling freq 5520 MHz
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.394921] cfg80211: Disabling freq 5540 MHz
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.394924] cfg80211: Disabling freq 5560 MHz
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.394926] cfg80211: Disabling freq 5580 MHz
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.394929] cfg80211: Disabling freq 5600 MHz
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.394932] cfg80211: Disabling freq 5620 MHz
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.394934] cfg80211: Disabling freq 5640 MHz
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.394936] cfg80211: Disabling freq 5660 MHz
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.394939] cfg80211: Disabling freq 5680 MHz
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.394941] cfg80211: Disabling freq 5700 MHz
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [   22.394945] cfg80211:  Updating information on frequency 5745 MHz for a 20 MHz width channel  with regulatory rule:
Aug  8 12:29:31 james-ThinkPad-X131e kernel:  [   22.394949] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (600  mBi, 2000 mBm)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    22.394952] cfg80211: Updating information on frequency 5765 MHz for a 20  MHz width channel with regulatory rule:
Aug  8 12:29:31  james-ThinkPad-X131e kernel: [   22.394955] cfg80211: 5735000 KHz -  5835000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
Aug  8 12:29:31  james-ThinkPad-X131e kernel: [   22.394959] cfg80211: Updating  information on frequency 5785 MHz for a 20 MHz width channel with  regulatory rule:
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    22.394963] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (600 mBi,  2000 mBm)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.394966]  cfg80211: Updating information on frequency 5805 MHz for a 20 MHz width  channel with regulatory rule:
Aug  8 12:29:31 james-ThinkPad-X131e  kernel: [   22.394969] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz),  (600 mBi, 2000 mBm)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    22.394973] cfg80211: Updating information on frequency 5825 MHz for a  20 MHz width channel with regulatory rule:
Aug  8 12:29:31  james-ThinkPad-X131e kernel: [   22.394977] cfg80211: 5735000 KHz -  5835000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.394980] cfg80211: Disabling freq 5920 MHz
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.394983] cfg80211: Disabling freq 5940 MHz
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.394986] cfg80211: Disabling freq 5960 MHz
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.394989] cfg80211: Disabling freq 5980 MHz
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.394992] cfg80211: Disabling freq 6000 MHz
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.394995] cfg80211: Disabling freq 6020 MHz
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.394997] cfg80211: Disabling freq 6040 MHz
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.395000] cfg80211: Disabling freq 6060 MHz
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.395003] cfg80211: Disabling freq 6080 MHz
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [   22.396027] type=1400  audit(1375957770.700:2): apparmor="STATUS" operation="profile_load"  name="/sbin/dhclient" pid=679 comm="apparmor_parser"
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.396912] INFO @wl_cfg80211_attach : Registered CFG80211 phy
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [   22.398186] type=1400  audit(1375957770.704:3): apparmor="STATUS" operation="profile_load"  name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=679  comm="apparmor_parser"
Aug  8 12:29:31 james-ThinkPad-X131e kernel:  [   22.398590] type=1400 audit(1375957770.704:4): apparmor="STATUS"  operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script"  pid=679 comm="apparmor_parser"
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.399503] lib80211_crypt: registered algorithm 'TKIP'
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.399713] i915 0000:00:02.0: irq 43 for MSI/MSI-X
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.399731] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.399734] [drm] Driver supports precise vblank timestamp query.
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [   22.399796] vgaarb: device  changed decodes:  PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.400516] thinkpad_acpi: detected a 8-level brightness capable ThinkPad
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.400920] microcode: CPU0 sig=0x206a7, pf=0x10, revision=0x28
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.427102] thinkpad_acpi: radio switch found; radios are enabled
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [   22.427129] thinkpad_acpi:  possible tablet mode switch found; ThinkPad in laptop mode
Aug  8  12:29:31 james-ThinkPad-X131e kernel: [   22.427367] thinkpad_acpi: This  ThinkPad has standard ACPI backlight brightness control, supported by  the ACPI video driver
Aug  8 12:29:31 james-ThinkPad-X131e kernel:  [   22.427371] thinkpad_acpi: Disabling thinkpad-acpi brightness events  by default...
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    22.576187] eth1: Broadcom BCM4359 802.11 Hybrid Wireless Controller  6.20.155.1 (r326264)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.585870] thinkpad_acpi: rfkill switch tpacpi_bluetooth_sw: radio is blocked
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.587029] Registered led device: tpacpi::thinklight
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.587094] Registered led device: tpacpi::power
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.587132] Registered led device: tpacpi::standby
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.587173] Registered led device: tpacpi::thinkvantage
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [   22.588990] thinkpad_acpi:  Standard ACPI backlight interface available, not loading native one
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [   22.589140] thinkpad_acpi:  Console audio control enabled, mode: monitor (read only)
Aug  8  12:29:31 james-ThinkPad-X131e kernel: [   22.594156] input: ThinkPad  Extra Buttons as /devices/platform/thinkpad_acpi/input/input6
Aug  8  12:29:31 james-ThinkPad-X131e kernel: [   22.596655] cfg80211: Updating  information on frequency 2412 MHz for a 20 MHz width channel with  regulatory rule:
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    22.596662] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi,  2000 mBm)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.596667]  cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width  channel with regulatory rule:
Aug  8 12:29:31 james-ThinkPad-X131e  kernel: [   22.596671] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz),  (300 mBi, 2000 mBm)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    22.596674] cfg80211: Updating information on frequency 2422 MHz for a  20 MHz width channel with regulatory rule:
Aug  8 12:29:31  james-ThinkPad-X131e kernel: [   22.596679] cfg80211: 2402000 KHz -  2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug  8 12:29:31  james-ThinkPad-X131e kernel: [   22.596683] cfg80211: Updating  information on frequency 2427 MHz for a 20 MHz width channel with  regulatory rule:
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    22.596687] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi,  2000 mBm)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.596691]  cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width  channel with regulatory rule:
Aug  8 12:29:31 james-ThinkPad-X131e  kernel: [   22.596695] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz),  (300 mBi, 2000 mBm)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    22.596698] cfg80211: Updating information on frequency 2437 MHz for a  20 MHz width channel with regulatory rule:
Aug  8 12:29:31  james-ThinkPad-X131e kernel: [   22.596702] cfg80211: 2402000 KHz -  2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug  8 12:29:31  james-ThinkPad-X131e kernel: [   22.596706] cfg80211: Updating  information on frequency 2442 MHz for a 20 MHz width channel with  regulatory rule:
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    22.596711] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi,  2000 mBm)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.596714]  cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width  channel with regulatory rule:
Aug  8 12:29:31 james-ThinkPad-X131e  kernel: [   22.596719] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz),  (300 mBi, 2000 mBm)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    22.596723] cfg80211: Updating information on frequency 2452 MHz for a  20 MHz width channel with regulatory rule:
Aug  8 12:29:31  james-ThinkPad-X131e kernel: [   22.596727] cfg80211: 2402000 KHz -  2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug  8 12:29:31  james-ThinkPad-X131e kernel: [   22.596731] cfg80211: Updating  information on frequency 2457 MHz for a 20 MHz width channel with  regulatory rule:
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    22.596735] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi,  2000 mBm)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.596739]  cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width  channel with regulatory rule:
Aug  8 12:29:31 james-ThinkPad-X131e  kernel: [   22.596743] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz),  (300 mBi, 2000 mBm)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    22.596747] cfg80211: Updating information on frequency 2467 MHz for a  20 MHz width channel with regulatory rule:
Aug  8 12:29:31  james-ThinkPad-X131e kernel: [   22.596751] cfg80211: 2457000 KHz -  2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Aug  8 12:29:31  james-ThinkPad-X131e kernel: [   22.596765] cfg80211: Updating  information on frequency 2472 MHz for a 20 MHz width channel with  regulatory rule:
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    22.596768] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi,  2000 mBm)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.596801]  cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width  channel with regulatory rule:
Aug  8 12:29:31 james-ThinkPad-X131e  kernel: [   22.596805] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz),  (300 mBi, 2000 mBm)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.596808] cfg80211: Disabling freq 5170 MHz
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [   22.596811] cfg80211:  Updating information on frequency 5180 MHz for a 20 MHz width channel  with regulatory rule:
Aug  8 12:29:31 james-ThinkPad-X131e kernel:  [   22.596814] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300  mBi, 2000 mBm)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    22.596817] cfg80211: Updating information on frequency 5190 MHz for a 20  MHz width channel with regulatory rule:
Aug  8 12:29:31  james-ThinkPad-X131e kernel: [   22.596822] cfg80211: 5170000 KHz -  5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug  8 12:29:31  james-ThinkPad-X131e kernel: [   22.596825] cfg80211: Updating  information on frequency 5200 MHz for a 20 MHz width channel with  regulatory rule:
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    22.596829] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi,  2000 mBm)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.596832]  cfg80211: Updating information on frequency 5210 MHz for a 20 MHz width  channel with regulatory rule:
Aug  8 12:29:31 james-ThinkPad-X131e  kernel: [   22.596835] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz),  (300 mBi, 2000 mBm)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    22.596838] cfg80211: Updating information on frequency 5220 MHz for a  20 MHz width channel with regulatory rule:
Aug  8 12:29:31  james-ThinkPad-X131e kernel: [   22.596847] cfg80211: 5170000 KHz -  5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug  8 12:29:31  james-ThinkPad-X131e kernel: [   22.596849] cfg80211: Updating  information on frequency 5230 MHz for a 20 MHz width channel with  regulatory rule:
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    22.596853] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi,  2000 mBm)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.596855]  cfg80211: Updating information on frequency 5240 MHz for a 20 MHz width  channel with regulatory rule:
Aug  8 12:29:31 james-ThinkPad-X131e  kernel: [   22.596858] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz),  (300 mBi, 2000 mBm)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.596860] cfg80211: Disabling freq 5260 MHz
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.596863] cfg80211: Disabling freq 5280 MHz
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.596865] cfg80211: Disabling freq 5300 MHz
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.596867] cfg80211: Disabling freq 5320 MHz
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.596871] cfg80211: Disabling freq 5500 MHz
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.596873] cfg80211: Disabling freq 5520 MHz
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.596874] cfg80211: Disabling freq 5540 MHz
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.596877] cfg80211: Disabling freq 5560 MHz
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.596879] cfg80211: Disabling freq 5580 MHz
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.596882] cfg80211: Disabling freq 5600 MHz
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.596884] cfg80211: Disabling freq 5620 MHz
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.596888] cfg80211: Disabling freq 5640 MHz
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.596891] cfg80211: Disabling freq 5660 MHz
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.596892] cfg80211: Disabling freq 5680 MHz
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.596895] cfg80211: Disabling freq 5700 MHz
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [   22.596898] cfg80211:  Updating information on frequency 5745 MHz for a 20 MHz width channel  with regulatory rule:
Aug  8 12:29:31 james-ThinkPad-X131e kernel:  [   22.596929] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300  mBi, 2000 mBm)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    22.596932] cfg80211: Updating information on frequency 5765 MHz for a 20  MHz width channel with regulatory rule:
Aug  8 12:29:31  james-ThinkPad-X131e kernel: [   22.596964] cfg80211: 5735000 KHz -  5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug  8 12:29:31  james-ThinkPad-X131e kernel: [   22.596967] cfg80211: Updating  information on frequency 5785 MHz for a 20 MHz width channel with  regulatory rule:
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    22.596999] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi,  2000 mBm)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.597001]  cfg80211: Updating information on frequency 5805 MHz for a 20 MHz width  channel with regulatory rule:
Aug  8 12:29:31 james-ThinkPad-X131e  kernel: [   22.597033] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz),  (300 mBi, 2000 mBm)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [    22.597036] cfg80211: Updating information on frequency 5825 MHz for a  20 MHz width channel with regulatory rule:
Aug  8 12:29:31  james-ThinkPad-X131e kernel: [   22.597068] cfg80211: 5735000 KHz -  5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.597070] cfg80211: Disabling freq 5920 MHz
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.597101] cfg80211: Disabling freq 5940 MHz
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.597103] cfg80211: Disabling freq 5960 MHz
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.597104] cfg80211: Disabling freq 5980 MHz
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.597136] cfg80211: Disabling freq 6000 MHz
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.597137] cfg80211: Disabling freq 6020 MHz
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.597144] cfg80211: Disabling freq 6040 MHz
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.597146] cfg80211: Disabling freq 6060 MHz
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.597150] cfg80211: Disabling freq 6080 MHz
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.597159] cfg80211: World regulatory domain updated:
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [   22.597161] cfg80211:    (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [   22.597165] cfg80211:    (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug  8  12:29:31 james-ThinkPad-X131e kernel: [   22.597169] cfg80211:    (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Aug  8  12:29:31 james-ThinkPad-X131e kernel: [   22.597173] cfg80211:    (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Aug  8  12:29:31 james-ThinkPad-X131e kernel: [   22.597175] cfg80211:    (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug  8  12:29:31 james-ThinkPad-X131e kernel: [   22.597180] cfg80211:    (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.598448] scsi6 : SCSI emulation for PCI-Express Mass Storage devices
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.598711] rts_pstor: waiting for device to settle before scanning
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.646143] microcode: CPU1 sig=0x206a7, pf=0x10, revision=0x28
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.648749] microcode: CPU2 sig=0x206a7, pf=0x10, revision=0x28
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.651815] microcode: CPU3 sig=0x206a7, pf=0x10, revision=0x28
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [   22.654422] microcode:  Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>,  Peter Oruba
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.724577] Bluetooth: Core ver 2.16
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.724613] NET: Registered protocol family 31
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.724617] Bluetooth: HCI device and connection manager initialized
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.724620] Bluetooth: HCI socket layer initialized
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.724623] Bluetooth: L2CAP socket layer initialized
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.724631] Bluetooth: SCO socket layer initialized
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.727804] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.727811] Bluetooth: BNEP filters: protocol multicast
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.776525] ppdev: user-space parallel port driver
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [   22.817231] type=1400  audit(1375957771.124:5): apparmor="STATUS" operation="profile_load"  name="/usr/lib/cups/backend/cups-pdf" pid=976 comm="apparmor_parser"
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [   22.818100] type=1400  audit(1375957771.124:6): apparmor="STATUS" operation="profile_load"  name="/usr/sbin/cupsd" pid=976 comm="apparmor_parser"
Aug  8 12:29:31  james-ThinkPad-X131e dbus[874]: [system] Activating service  name='org.freedesktop.PolicyKit1' (using servicehelper)
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.832925] usb 2-1.5: new full-speed USB device number 3 using ehci_hcd
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.843321] Bluetooth: RFCOMM TTY layer initialized
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.843329] Bluetooth: RFCOMM socket layer initialized
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.843332] Bluetooth: RFCOMM ver 1.11
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [   22.852704] type=1400  audit(1375957771.156:7): apparmor="STATUS" operation="profile_load"  name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=1004  comm="apparmor_parser"
Aug  8 12:29:31 james-ThinkPad-X131e kernel:  [   22.853410] type=1400 audit(1375957771.160:8): apparmor="STATUS"  operation="profile_load"  name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper//chromium_browser"  pid=1004 comm="apparmor_parser"
Aug  8 12:29:31 james-ThinkPad-X131e  kernel: [   22.856638] type=1400 audit(1375957771.160:9):  apparmor="STATUS" operation="profile_load"  name="/usr/lib/telepathy/mission-control-5" pid=1008  comm="apparmor_parser"
Aug  8 12:29:31 james-ThinkPad-X131e kernel:  [   22.857511] type=1400 audit(1375957771.164:10): apparmor="STATUS"  operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=1008  comm="apparmor_parser"
Aug  8 12:29:31 james-ThinkPad-X131e kernel:  [   22.859314] type=1400 audit(1375957771.164:11): apparmor="STATUS"  operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf"  pid=1009 comm="apparmor_parser"
Aug  8 12:29:31 james-ThinkPad-X131e  polkitd[981]: started daemon version 0.104 using authority  implementation `local' version `0.104'
Aug  8 12:29:31 james-ThinkPad-X131e dbus[874]: [system] Successfully activated service 'org.freedesktop.PolicyKit1'
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.867116] [drm] Enabling RC6 states: RC6 on, RC6p off, RC6pp off
Aug  8 12:29:31 james-ThinkPad-X131e NetworkManager[932]:    SCPlugin-Ifupdown: init!
Aug  8 12:29:31 james-ThinkPad-X131e NetworkManager[932]:    SCPlugin-Ifupdown: update_system_hostname
Aug  8 12:29:31 james-ThinkPad-X131e NetworkManager[932]:    SCPluginIfupdown: management mode: unmanaged
Aug   8 12:29:31 james-ThinkPad-X131e NetworkManager[932]:     SCPlugin-Ifupdown: devices added (path:  /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/eth2, iface: eth2)
Aug   8 12:29:31 james-ThinkPad-X131e NetworkManager[932]:     SCPlugin-Ifupdown: device added (path:  /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/eth2, iface:  eth2): no ifupdown configuration found.
Aug  8 12:29:31  james-ThinkPad-X131e NetworkManager[932]:    SCPlugin-Ifupdown: devices  added (path: /sys/devices/pci0000:00/0000:00:1c.5/0000:09:00.0/net/eth0,  iface: eth0)
Aug  8 12:29:31 james-ThinkPad-X131e  NetworkManager[932]:    SCPlugin-Ifupdown: device added (path:  /sys/devices/pci0000:00/0000:00:1c.5/0000:09:00.0/net/eth0, iface:  eth0): no ifupdown configuration found.
Aug  8 12:29:31  james-ThinkPad-X131e NetworkManager[932]:    SCPlugin-Ifupdown: devices  added (path: /sys/devices/virtual/net/lo, iface: lo)
Aug  8 12:29:31  james-ThinkPad-X131e NetworkManager[932]:    SCPlugin-Ifupdown: device  added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown  configuration found.
Aug  8 12:29:31 james-ThinkPad-X131e NetworkManager[932]:    SCPlugin-Ifupdown: end _init.
Aug   8 12:29:31 james-ThinkPad-X131e NetworkManager[932]: <info>  Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please  use the NetworkManager mailing list.
Aug  8 12:29:31 james-ThinkPad-X131e avahi-daemon[927]: Network interface enumeration completed.
Aug  8 12:29:31 james-ThinkPad-X131e avahi-daemon[927]: Registering HINFO record with values 'X86_64'/'LINUX'.
Aug   8 12:29:31 james-ThinkPad-X131e avahi-daemon[927]: Server startup  complete. Host name is james-ThinkPad-X131e.local. Local service cookie  is 3027419840.
Aug  8 12:29:31 james-ThinkPad-X131e  avahi-daemon[927]: Service "james-ThinkPad-X131e"  (/services/udisks.service) successfully established.
Aug  8 12:29:31  james-ThinkPad-X131e NetworkManager[932]: <info> Loaded plugin  keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the  NetworkManager mailing list.
Aug  8 12:29:31 james-ThinkPad-X131e NetworkManager[932]:    Ifupdown: get unmanaged devices count: 0
Aug  8 12:29:31 james-ThinkPad-X131e NetworkManager[932]:    SCPlugin-Ifupdown: (15899808) ... get_connections.
Aug   8 12:29:31 james-ThinkPad-X131e NetworkManager[932]:     SCPlugin-Ifupdown: (15899808) ... get_connections (managed=false):  return empty list.
Aug  8 12:29:31 james-ThinkPad-X131e NetworkManager[932]:    keyfile: parsing WoodridgeLake ... 
Aug  8 12:29:31 james-ThinkPad-X131e mtp-probe: checking bus 3, device 2: "/sys/devices/pci0000:00/0000:00:14.0/usb3/3-2"
Aug  8 12:29:31 james-ThinkPad-X131e mtp-probe: checking bus 3, device 3: "/sys/devices/pci0000:00/0000:00:14.0/usb3/3-4"
Aug  8 12:29:31 james-ThinkPad-X131e mtp-probe: bus: 3, device: 2 was not an MTP device
Aug  8 12:29:31 james-ThinkPad-X131e NetworkManager[932]:    keyfile:     read connection 'WoodridgeLake'
Aug  8 12:29:31 james-ThinkPad-X131e NetworkManager[932]:    keyfile: parsing MB855 E0:72:E2 ... 
Aug  8 12:29:31 james-ThinkPad-X131e mtp-probe: bus: 3, device: 3 was not an MTP device
Aug  8 12:29:31 james-ThinkPad-X131e NetworkManager[932]:    keyfile:     read connection 'MB855 E0:72:E2'
Aug  8 12:29:31 james-ThinkPad-X131e NetworkManager[932]:    keyfile: parsing AMAG Library Main ... 
Aug  8 12:29:31 james-ThinkPad-X131e NetworkManager[932]:    keyfile:     read connection 'AMAG Library Main'
Aug  8 12:29:31 james-ThinkPad-X131e NetworkManager[932]:    keyfile: parsing Lox ... 
Aug  8 12:29:31 james-ThinkPad-X131e NetworkManager[932]:    keyfile:     read connection 'Lox'
Aug  8 12:29:31 james-ThinkPad-X131e NetworkManager[932]:    keyfile: parsing NYPL ... 
Aug  8 12:29:31 james-ThinkPad-X131e NetworkManager[932]:    keyfile:     read connection 'NYPL'
Aug  8 12:29:31 james-ThinkPad-X131e NetworkManager[932]:    keyfile: parsing T9DR4 ... 
Aug  8 12:29:31 james-ThinkPad-X131e NetworkManager[932]:    keyfile:     read connection 'T9DR4'
Aug  8 12:29:31 james-ThinkPad-X131e NetworkManager[932]:    keyfile: parsing Oxford ... 
Aug  8 12:29:31 james-ThinkPad-X131e NetworkManager[932]:    keyfile:     read connection 'Oxford'
Aug  8 12:29:31 james-ThinkPad-X131e NetworkManager[932]:    keyfile: parsing Linksys ... 
Aug  8 12:29:31 james-ThinkPad-X131e NetworkManager[932]:    keyfile:     read connection 'Linksys'
Aug  8 12:29:31 james-ThinkPad-X131e NetworkManager[932]:    keyfile: parsing 404F-16a91174-74bb-4719-8b43-ae32f74f2dd9 ... 
Aug  8 12:29:31 james-ThinkPad-X131e NetworkManager[932]:    keyfile:     read connection '404F'
Aug  8 12:29:31 james-ThinkPad-X131e NetworkManager[932]:    keyfile: parsing Morrissey-Net ... 
Aug  8 12:29:31 james-ThinkPad-X131e NetworkManager[932]:    keyfile:     read connection 'Morrissey-Net'
Aug  8 12:29:31 james-ThinkPad-X131e NetworkManager[932]:    keyfile: parsing Columbia University ... 
Aug  8 12:29:31 james-ThinkPad-X131e NetworkManager[932]:    keyfile:     read connection 'Columbia University'
Aug  8 12:29:31 james-ThinkPad-X131e NetworkManager[932]:    keyfile: parsing KOS KAFFE ... 
Aug  8 12:29:31 james-ThinkPad-X131e NetworkManager[932]:    keyfile:     read connection 'KOS KAFFE'
Aug  8 12:29:31 james-ThinkPad-X131e NetworkManager[932]:    keyfile: parsing ARCPC-Wireless ... 
Aug  8 12:29:31 james-ThinkPad-X131e NetworkManager[932]:    keyfile:     read connection 'ARCPC-Wireless'
Aug  8 12:29:31 james-ThinkPad-X131e NetworkManager[932]:    keyfile: parsing 07B408853342 ... 
Aug  8 12:29:31 james-ThinkPad-X131e NetworkManager[932]:    keyfile:     read connection '07B408853342'
Aug  8 12:29:31 james-ThinkPad-X131e NetworkManager[932]:    keyfile: parsing attwifi ... 
Aug  8 12:29:31 james-ThinkPad-X131e NetworkManager[932]:    keyfile:     read connection 'attwifi'
Aug  8 12:29:31 james-ThinkPad-X131e NetworkManager[932]:    Ifupdown: get unmanaged devices count: 0
Aug  8 12:29:31 james-ThinkPad-X131e NetworkManager[932]: <info> modem-manager is now available
Aug  8 12:29:31 james-ThinkPad-X131e NetworkManager[932]: <info> monitoring kernel firmware directory '/lib/firmware'.
Aug   8 12:29:31 james-ThinkPad-X131e NetworkManager[932]: <info> found  WiFi radio killswitch rfkill0 (at  /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/ieee80211/phy0/rfkill0)  (driver (unknown))
Aug  8 12:29:31 james-ThinkPad-X131e  NetworkManager[932]: <info> found WiFi radio killswitch rfkill1  (at /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/eth2/rfkill1)  (driver (unknown))
Aug  8 12:29:31 james-ThinkPad-X131e NetworkManager[932]: <info> WiFi enabled by radio killswitch; enabled by state file
Aug  8 12:29:31 james-ThinkPad-X131e NetworkManager[932]: <info> WWAN enabled by radio killswitch; enabled by state file
Aug  8 12:29:31 james-ThinkPad-X131e NetworkManager[932]: <info> WiMAX enabled by radio killswitch; enabled by state file
Aug  8 12:29:31 james-ThinkPad-X131e NetworkManager[932]: <info> Networking is enabled by state file
Aug  8 12:29:31 james-ThinkPad-X131e NetworkManager[932]: <info> (eth2): using nl80211 for WiFi device control
Aug   8 12:29:31 james-ThinkPad-X131e NetworkManager[932]: <error>  [1375957771.221167] [nm-device-wifi.c:2591]  real_update_permanent_hw_address(): (eth2): unable to read permanent MAC  address (error 0)
Aug  8 12:29:31 james-ThinkPad-X131e NetworkManager[932]: <info> (eth2): new 802.11 WiFi device (driver: 'wl' ifindex: 3)
Aug   8 12:29:31 james-ThinkPad-X131e NetworkManager[932]: <info>  (eth2): exported as /org/freedesktop/NetworkManager/Devices/0
Aug  8 12:29:31 james-ThinkPad-X131e NetworkManager[932]: <info> (eth2): now managed
Aug   8 12:29:31 james-ThinkPad-X131e NetworkManager[932]: <info>  (eth2): device state change: unmanaged -> unavailable (reason  'managed') [10 20 2]
Aug  8 12:29:31 james-ThinkPad-X131e NetworkManager[932]: <info> (eth2): bringing up device.
Aug  8 12:29:31 james-ThinkPad-X131e NetworkManager[932]: <info> (eth2): preparing device.
Aug  8 12:29:31 james-ThinkPad-X131e NetworkManager[932]: <info> (eth2): deactivating device (reason 'managed') [2]
Aug  8 12:29:31 james-ThinkPad-X131e dbus[874]: [system] Activating service name='fi.w1.wpa_supplicant1' (using servicehelper)
Aug   8 12:29:31 james-ThinkPad-X131e NetworkManager[932]: <warn>  failed to allocate link cache: (-10) Operation not supported
Aug  8 12:29:31 james-ThinkPad-X131e NetworkManager[932]: <info> (eth0): carrier is OFF
Aug  8 12:29:31 james-ThinkPad-X131e NetworkManager[932]: <info> (eth0): new Ethernet device (driver: 'r8169' ifindex: 2)
Aug   8 12:29:31 james-ThinkPad-X131e NetworkManager[932]: <info>  (eth0): exported as /org/freedesktop/NetworkManager/Devices/1
Aug  8 12:29:31 james-ThinkPad-X131e NetworkManager[932]: <info> (eth0): now managed
Aug   8 12:29:31 james-ThinkPad-X131e NetworkManager[932]: <info>  (eth0): device state change: unmanaged -> unavailable (reason  'managed') [10 20 2]
Aug  8 12:29:31 james-ThinkPad-X131e NetworkManager[932]: <info> (eth0): bringing up device.
Aug  8 12:29:31 james-ThinkPad-X131e dbus[874]: [system] Successfully activated service 'fi.w1.wpa_supplicant1'
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.934911] usb 2-1.5: New USB device found, idVendor=0a5c, idProduct=21f3
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.934919] usb 2-1.5: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.934924] usb 2-1.5: Product: BCM20702A0
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.934928] usb 2-1.5: Manufacturer: Broadcom Corp
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   22.934933] usb 2-1.5: SerialNumber: E006E6FA7C78
Aug   8 12:29:31 james-ThinkPad-X131e dbus[874]: [system] Activating service  name='org.freedesktop.ColorManager' (using servicehelper)
Aug  8 12:29:31 james-ThinkPad-X131e dbus[874]: [system] Successfully activated service 'org.freedesktop.ColorManager'
Aug  8 12:29:31 james-ThinkPad-X131e NetworkManager[932]: <info> (eth0): preparing device.
Aug  8 12:29:31 james-ThinkPad-X131e NetworkManager[932]: <info> (eth0): deactivating device (reason 'managed') [2]
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   23.021681] r8169 0000:09:00.0: eth0: link down
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   23.022560] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   23.023858] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug   8 12:29:31 james-ThinkPad-X131e NetworkManager[932]: <info> Added  default wired connection 'Wired connection 1' for  /sys/devices/pci0000:00/0000:00:1c.5/0000:09:00.0/net/eth0
Aug  8 12:29:31 james-ThinkPad-X131e NetworkManager[932]: <info> wpa_supplicant started
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   23.030205] fbcon: inteldrmfb (fb0) is primary device
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   23.030367] Console: switching to colour frame buffer device 170x48
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   23.030410] fb0: inteldrmfb frame buffer device
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   23.030412] drm: registered panic notifier
Aug  8 12:29:31 james-ThinkPad-X131e NetworkManager[932]: <info> (eth2): supplicant interface state: starting -> ready
Aug   8 12:29:31 james-ThinkPad-X131e NetworkManager[932]: <info>  (eth2): device state change: unavailable -> disconnected (reason  'supplicant-available') [20 30 42]
Aug  8 12:29:31 james-ThinkPad-X131e NetworkManager[932]: <info> (eth2): supplicant interface state: ready -> inactive
Aug  8 12:29:31 james-ThinkPad-X131e NetworkManager[932]: <warn> Trying to remove a non-existant call id.
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   23.063340] acpi device:3e: registered as cooling_device4
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   23.063725] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [   23.064097] input: Video Bus  as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input7
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   23.064478] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   23.064536] mei 0000:00:16.0: setting latency timer to 64
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   23.064650] mei 0000:00:16.0: irq 44 for MSI/MSI-X
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [   23.081525] ACPI Warning:  0x0000000000000460-0x000000000000047f SystemIO conflicts with Region  \PMIO 1 (20120320/utaddress-251)
Aug  8 12:29:31 james-ThinkPad-X131e  kernel: [   23.081538] ACPI: If an ACPI driver is available for this  device, you should use it instead of the native driver
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   23.081543] lpc_ich: Resource conflict(s) found affecting iTCO_wdt
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [   23.081548] ACPI Warning:  0x0000000000000428-0x000000000000042f SystemIO conflicts with Region  \PMIO 1 (20120320/utaddress-251)
Aug  8 12:29:31 james-ThinkPad-X131e  kernel: [   23.081556] ACPI: If an ACPI driver is available for this  device, you should use it instead of the native driver
Aug  8  12:29:31 james-ThinkPad-X131e kernel: [   23.081561] ACPI Warning:  0x0000000000000500-0x000000000000053f SystemIO conflicts with Region  \GPIO 1 (20120320/utaddress-251)
Aug  8 12:29:31 james-ThinkPad-X131e  kernel: [   23.081569] ACPI: If an ACPI driver is available for this  device, you should use it instead of the native driver
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   23.081572] lpc_ich: Resource conflict(s) found affecting gpio_ich
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   23.081810] snd_hda_intel 0000:00:1b.0: irq 45 for MSI/MSI-X
Aug  8 12:29:31 james-ThinkPad-X131e udev-configure-printer: add /bus/pci/drivers/lpc_ich
Aug  8 12:29:31 james-ThinkPad-X131e udev-configure-printer: Failed to get parent
Aug  8 12:29:31 james-ThinkPad-X131e acpid: starting up with proc fs
Aug  8 12:29:31 james-ThinkPad-X131e cron[1089]: (CRON) INFO (pidfile fd = 3)
Aug  8 12:29:31 james-ThinkPad-X131e acpid: 36 rules loaded
Aug  8 12:29:31 james-ThinkPad-X131e acpid: waiting for events: event logging is off
Aug  8 12:29:31 james-ThinkPad-X131e anacron[1113]: Anacron 2.3 started on 2013-08-08
Aug  8 12:29:31 james-ThinkPad-X131e cron[1120]: (CRON) STARTUP (fork ok)
Aug  8 12:29:31 james-ThinkPad-X131e cron[1120]: (CRON) INFO (Running @reboot jobs)
Aug  8 12:29:31 james-ThinkPad-X131e anacron[1113]: Normal exit (0 jobs run)
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [   23.407032] psmouse serio4:  synaptics: Touchpad model: 1, fw: 8.0, id: 0x1e2b1, caps:  0xd001a3/0x940300/0x123c00
Aug  8 12:29:31 james-ThinkPad-X131e  kernel: [   23.407046] psmouse serio4: synaptics: serio: Synaptics  pass-through port at isa0060/serio4/input0
Aug  8 12:29:31 james-ThinkPad-X131e mtp-probe: checking bus 2, device 3: "/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5"
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   23.414700] Linux video capture interface: v2.00
Aug  8 12:29:31 james-ThinkPad-X131e mtp-probe: bus: 2, device: 3 was not an MTP device
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   23.418356] uvcvideo: Found UVC 1.00 device Integrated Camera (5986:0299)
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [   23.421378] input:  Integrated Camera as  /devices/pci0000:00/0000:00:14.0/usb3/3-4/3-4:1.0/input/input8
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   23.421708] usbcore: registered new interface driver uvcvideo
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   23.421713] USB Video Class driver (1.1.1)
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [   23.449512] input: SynPS/2  Synaptics TouchPad as /devices/platform/i8042/serio4/input/input9
Aug  8 12:29:31 james-ThinkPad-X131e acpid: client connected from 1193[0:0]
Aug  8 12:29:31 james-ThinkPad-X131e acpid: 1 client rule loaded
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   23.596717] rts_pstor: device scan complete
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [   23.596875] scsi 6:0:0:0:  Direct-Access     Generic- xD/SD/M.S.       1.00 PQ: 0 ANSI: 0 CCS
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   23.597123] sd 6:0:0:0: Attached scsi generic sg1 type 0
Aug  8 12:29:31 james-ThinkPad-X131e kernel: [   23.597394] sd 6:0:0:0: [sdb] Attached SCSI removable disk
Aug   8 12:29:31 james-ThinkPad-X131e kernel: [   23.643015] input: HDA Intel  PCH HDMI/DP,pcm=3 as  /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
Aug  8 12:29:31  james-ThinkPad-X131e kernel: [   23.643162] input: HDA Intel PCH Mic as  /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
Aug  8 12:29:31  james-ThinkPad-X131e kernel: [   23.643299] input: HDA Intel PCH  Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
Aug   8 12:29:32 james-ThinkPad-X131e dbus[874]: [system] Activating service  name='org.freedesktop.Accounts' (using servicehelper)
Aug  8 12:29:32 james-ThinkPad-X131e dbus[874]: [system] Successfully activated service 'org.freedesktop.Accounts'
Aug  8 12:29:32 james-ThinkPad-X131e accounts-daemon[1281]: started daemon version 0.6.15
Aug  8 12:29:32 james-ThinkPad-X131e kernel: [   23.916150] thinkpad_ec: thinkpad_ec 0.41 loaded.
Aug  8 12:29:32 james-ThinkPad-X131e kernel: [   23.916676] tp_smapi 0.41 loading...
Aug  8 12:29:32 james-ThinkPad-X131e kernel: [   23.916879] tp_smapi successfully loaded (smapi_port=0xb2).
Aug  8 12:29:32 james-ThinkPad-X131e bluetoothd[900]: HCI dev 0 registered
Aug  8 12:29:32 james-ThinkPad-X131e bluetoothd[900]: Listening for HCI events on hci0
Aug  8 12:29:32 james-ThinkPad-X131e dbus[874]: [system] Activating service name='org.freedesktop.UPower' (using servicehelper)
Aug  8 12:29:32 james-ThinkPad-X131e kernel: [   23.944975] usbcore: registered new interface driver btusb
Aug  8 12:29:32 james-ThinkPad-X131e dbus[874]: [system] Successfully activated service 'org.freedesktop.UPower'
Aug  8 12:29:32 james-ThinkPad-X131e bluetoothd[900]: HCI dev 0 up
Aug  8 12:29:32 james-ThinkPad-X131e bluetoothd[900]: Adapter /org/bluez/900/hci0 has been enabled
Aug  8 12:29:32 james-ThinkPad-X131e kernel: [   23.997467] Bluetooth: can't load firmware, may not work correctly
Aug   8 12:29:32 james-ThinkPad-X131e dbus[874]: [system] Activating service  name='org.freedesktop.ConsoleKit' (using servicehelper)
Aug  8 12:29:32 james-ThinkPad-X131e dbus[874]: [system] Successfully activated service 'org.freedesktop.ConsoleKit'
Aug   8 12:29:33 james-ThinkPad-X131e avahi-daemon[927]: Joining mDNS  multicast group on interface eth2.IPv6 with address  fe80::e206:e6ff:fefa:7c77.
Aug  8 12:29:33 james-ThinkPad-X131e avahi-daemon[927]: New relevant interface eth2.IPv6 for mDNS.
Aug  8 12:29:33 james-ThinkPad-X131e avahi-daemon[927]: Registering new address record for fe80::e206:e6ff:fefa:7c77 on eth2.*.
Aug  8 12:29:33 james-ThinkPad-X131e udev-configure-printer: add /module/lp
Aug  8 12:29:33 james-ThinkPad-X131e udev-configure-printer: Failed to get parent
Aug  8 12:29:33 james-ThinkPad-X131e udev-configure-printer: add /module/lpc_ich
Aug  8 12:29:33 james-ThinkPad-X131e udev-configure-printer: Failed to get parent
Aug   8 12:29:34 james-ThinkPad-X131e dbus[874]: [system] Activating service  name='org.freedesktop.RealtimeKit1' (using servicehelper)
Aug  8 12:29:34 james-ThinkPad-X131e dbus[874]: [system] Successfully activated service 'org.freedesktop.RealtimeKit1'
Aug  8 12:29:34 james-ThinkPad-X131e rtkit-daemon[1709]: Successfully called chroot.
Aug  8 12:29:34 james-ThinkPad-X131e rtkit-daemon[1709]: Successfully dropped privileges.
Aug  8 12:29:34 james-ThinkPad-X131e rtkit-daemon[1709]: Successfully limited resources.
Aug  8 12:29:34 james-ThinkPad-X131e rtkit-daemon[1709]: Running.
Aug  8 12:29:34 james-ThinkPad-X131e rtkit-daemon[1709]: Watchdog thread running.
Aug  8 12:29:34 james-ThinkPad-X131e rtkit-daemon[1709]: Canary thread running.
Aug   8 12:29:34 james-ThinkPad-X131e rtkit-daemon[1709]: Successfully made  thread 1707 of process 1707 (n/a) owned by '104' high priority at nice  level -11.
Aug  8 12:29:34 james-ThinkPad-X131e rtkit-daemon[1709]: Supervising 1 threads of 1 processes of 1 users.
Aug   8 12:29:34 james-ThinkPad-X131e rtkit-daemon[1709]: Successfully made  thread 1720 of process 1707 (n/a) owned by '104' RT at priority 5.
Aug  8 12:29:34 james-ThinkPad-X131e rtkit-daemon[1709]: Supervising 2 threads of 1 processes of 1 users.
Aug   8 12:29:34 james-ThinkPad-X131e rtkit-daemon[1709]: Successfully made  thread 1721 of process 1707 (n/a) owned by '104' RT at priority 5.
Aug  8 12:29:34 james-ThinkPad-X131e rtkit-daemon[1709]: Supervising 3 threads of 1 processes of 1 users.
Aug  8 12:29:34 james-ThinkPad-X131e bluetoothd[900]: Endpoint registered: sender=:1.35 path=/MediaEndpoint/HFPAG
Aug  8 12:29:34 james-ThinkPad-X131e bluetoothd[900]: Endpoint registered: sender=:1.35 path=/MediaEndpoint/A2DPSource
Aug  8 12:29:34 james-ThinkPad-X131e bluetoothd[900]: Endpoint registered: sender=:1.35 path=/MediaEndpoint/A2DPSink
Aug   8 12:29:34 james-ThinkPad-X131e rtkit-daemon[1709]: Successfully made  thread 1724 of process 1724 (n/a) owned by '104' high priority at nice  level -11.
Aug  8 12:29:34 james-ThinkPad-X131e rtkit-daemon[1709]: Supervising 4 threads of 2 processes of 1 users.
Aug  8 12:29:34 james-ThinkPad-X131e pulseaudio[1724]: [pulseaudio] pid.c: Daemon already running.
Aug  8 12:29:34 james-ThinkPad-X131e NetworkManager[932]: <info> Auto-activating connection 'Morrissey-Net'.
Aug  8 12:29:34 james-ThinkPad-X131e NetworkManager[932]: <info> Activation (eth2) starting connection 'Morrissey-Net'
Aug   8 12:29:34 james-ThinkPad-X131e NetworkManager[932]: <info>  (eth2): device state change: disconnected -> prepare (reason 'none')  [30 40 0]
Aug  8 12:29:34 james-ThinkPad-X131e NetworkManager[932]:  <info> Activation (eth2) Stage 1 of 5 (Device Prepare)  scheduled...
Aug  8 12:29:34 james-ThinkPad-X131e  NetworkManager[932]: <info> Activation (eth2) Stage 1 of 5 (Device  Prepare) started...
Aug  8 12:29:34 james-ThinkPad-X131e  NetworkManager[932]: <info> Activation (eth2) Stage 2 of 5 (Device  Configure) scheduled...
Aug  8 12:29:34 james-ThinkPad-X131e NetworkManager[932]: <info> Activation (eth2) Stage 1 of 5 (Device Prepare) complete.
Aug   8 12:29:34 james-ThinkPad-X131e NetworkManager[932]: <info>  Activation (eth2) Stage 2 of 5 (Device Configure) starting...
Aug  8  12:29:34 james-ThinkPad-X131e NetworkManager[932]: <info> (eth2):  device state change: prepare -> config (reason 'none') [40 50 0]
Aug   8 12:29:34 james-ThinkPad-X131e NetworkManager[932]: <info>  Activation (eth2/wireless): connection 'Morrissey-Net' has security, and  secrets exist.  No new secrets needed.
Aug  8 12:29:34 james-ThinkPad-X131e NetworkManager[932]: <info> Config: added 'ssid' value 'Morrissey-Net'
Aug  8 12:29:34 james-ThinkPad-X131e NetworkManager[932]: <info> Config: added 'scan_ssid' value '1'
Aug  8 12:29:34 james-ThinkPad-X131e NetworkManager[932]: <info> Config: added 'key_mgmt' value 'NONE'
Aug  8 12:29:34 james-ThinkPad-X131e NetworkManager[932]: <info> Config: added 'wep_key0' value '<omitted>'
Aug  8 12:29:34 james-ThinkPad-X131e NetworkManager[932]: <info> Config: added 'wep_tx_keyidx' value '0'
Aug   8 12:29:34 james-ThinkPad-X131e NetworkManager[932]: <info>  Activation (eth2) Stage 2 of 5 (Device Configure) complete.
Aug  8 12:29:34 james-ThinkPad-X131e NetworkManager[932]: <info> Config: set interface ap_scan to 1
Aug   8 12:29:34 james-ThinkPad-X131e NetworkManager[932]: <info>  (eth2): supplicant interface state: inactive -> scanning
Aug  8  12:29:35 james-ThinkPad-X131e kernel: [   27.148236] xhci_hcd  0000:00:14.0: WARN Event TRB for slot 2 ep 0 with no TDs queued?
Aug   8 12:29:36 james-ThinkPad-X131e wpa_supplicant[1049]: Trying to  associate with 00:0f:b5:c4:82:76 (SSID='Morrissey-Net' freq=2462 MHz)
Aug   8 12:29:36 james-ThinkPad-X131e NetworkManager[932]: <info>  (eth2): supplicant interface state: scanning -> associating
Aug  8 12:29:36 james-ThinkPad-X131e wpa_supplicant[1049]: Associated with 00:0f:b5:c4:82:76
Aug   8 12:29:36 james-ThinkPad-X131e wpa_supplicant[1049]:  CTRL-EVENT-CONNECTED - Connection to 00:0f:b5:c4:82:76 completed (auth)  [id=0 id_str=]
Aug  8 12:29:36 james-ThinkPad-X131e  NetworkManager[932]: <info> (eth2): supplicant interface state:  associating -> completed
Aug  8 12:29:36 james-ThinkPad-X131e  NetworkManager[932]: <info> Activation (eth2/wireless) Stage 2 of 5  (Device Configure) successful.  Connected to wireless network  'Morrissey-Net'.
Aug  8 12:29:36 james-ThinkPad-X131e  NetworkManager[932]: <info> Activation (eth2) Stage 3 of 5 (IP  Configure Start) scheduled.
Aug  8 12:29:36 james-ThinkPad-X131e  NetworkManager[932]: <info> Activation (eth2) Stage 3 of 5 (IP  Configure Start) started...
Aug  8 12:29:36 james-ThinkPad-X131e  NetworkManager[932]: <info> (eth2): device state change: config  -> ip-config (reason 'none') [50 70 0]
Aug  8 12:29:36  james-ThinkPad-X131e NetworkManager[932]: <info> Activation (eth2)  Beginning DHCPv4 transaction (timeout in 45 seconds)
Aug  8 12:29:36 james-ThinkPad-X131e NetworkManager[932]: <info> dhclient started with pid 1728
Aug  8 12:29:36 james-ThinkPad-X131e NetworkManager[932]: <info> Activation (eth2) Beginning IP6 addrconf.
Aug  8 12:29:36 james-ThinkPad-X131e avahi-daemon[927]: Withdrawing address record for fe80::e206:e6ff:fefa:7c77 on eth2.
Aug   8 12:29:36 james-ThinkPad-X131e avahi-daemon[927]: Leaving mDNS  multicast group on interface eth2.IPv6 with address  fe80::e206:e6ff:fefa:7c77.
Aug  8 12:29:36 james-ThinkPad-X131e avahi-daemon[927]: Interface eth2.IPv6 no longer relevant for mDNS.
Aug  8 12:29:36 james-ThinkPad-X131e dhclient: Internet Systems Consortium DHCP Client 4.1-ESV-R4
Aug  8 12:29:36 james-ThinkPad-X131e dhclient: Copyright 2004-2011 Internet Systems Consortium.
Aug  8 12:29:36 james-ThinkPad-X131e dhclient: All rights reserved.
Aug  8 12:29:36 james-ThinkPad-X131e dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Aug  8 12:29:36 james-ThinkPad-X131e dhclient: 
Aug   8 12:29:36 james-ThinkPad-X131e NetworkManager[932]: <info>  Activation (eth2) Stage 3 of 5 (IP Configure Start) complete.
Aug  8 12:29:36 james-ThinkPad-X131e NetworkManager[932]: <info> (eth2): DHCPv4 state changed nbi -> preinit
Aug  8 12:29:36 james-ThinkPad-X131e dhclient: Listening on LPF/eth2/e0:06:e6:fa:7c:77
Aug  8 12:29:36 james-ThinkPad-X131e dhclient: Sending on   LPF/eth2/e0:06:e6:fa:7c:77
Aug  8 12:29:36 james-ThinkPad-X131e dhclient: Sending on   Socket/fallback
Aug  8 12:29:36 james-ThinkPad-X131e dhclient: DHCPREQUEST of 192.168.0.8 on eth2 to 255.255.255.255 port 67
Aug  8 12:29:36 james-ThinkPad-X131e dhclient: DHCPACK of 192.168.0.8 from 192.168.0.1
Aug  8 12:29:36 james-ThinkPad-X131e dhclient: bound to 192.168.0.8 -- renewal in 41771 seconds.
Aug  8 12:29:36 james-ThinkPad-X131e NetworkManager[932]: <info> (eth2): DHCPv4 state changed preinit -> reboot
Aug  8 12:29:36 james-ThinkPad-X131e NetworkManager[932]: <info>   address 192.168.0.8
Aug  8 12:29:36 james-ThinkPad-X131e NetworkManager[932]: <info>   prefix 24 (255.255.255.0)
Aug  8 12:29:36 james-ThinkPad-X131e NetworkManager[932]: <info>   gateway 192.168.0.1
Aug  8 12:29:36 james-ThinkPad-X131e NetworkManager[932]: <info>   nameserver '192.168.0.1'
Aug   8 12:29:36 james-ThinkPad-X131e NetworkManager[932]: <info>  Activation (eth2) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Aug  8 12:29:36 james-ThinkPad-X131e NetworkManager[932]: <info> Activation (eth2) Stage 5 of 5 (IPv4 Commit) started...
Aug   8 12:29:36 james-ThinkPad-X131e avahi-daemon[927]: Joining mDNS  multicast group on interface eth2.IPv4 with address 192.168.0.8.
Aug  8 12:29:36 james-ThinkPad-X131e avahi-daemon[927]: New relevant interface eth2.IPv4 for mDNS.
Aug  8 12:29:36 james-ThinkPad-X131e avahi-daemon[927]: Registering new address record for 192.168.0.8 on eth2.IPv4.
Aug  8 12:29:37 james-ThinkPad-X131e NetworkManager[932]: <info> DNS: starting dnsmasq...
Aug  8 12:29:37 james-ThinkPad-X131e NetworkManager[932]: <info> (eth2): writing resolv.conf to /sbin/resolvconf
Aug  8 12:29:37 james-ThinkPad-X131e dnsmasq[1746]: started, version 2.59 cache disabled
Aug  8 12:29:37 james-ThinkPad-X131e dnsmasq[1746]: compile time options: IPv6 GNU-getopt DBus i18n DHCP TFTP conntrack IDN
Aug  8 12:29:37 james-ThinkPad-X131e dnsmasq[1746]: using nameserver 192.168.0.1#53
Aug   8 12:29:38 james-ThinkPad-X131e kernel: [   30.256210] psmouse serio5:  trackpoint: IBM TrackPoint firmware: 0x0e, buttons: 3/3
Aug  8  12:29:38 james-ThinkPad-X131e kernel: [   30.492497] input: TPPS/2 IBM  TrackPoint as /devices/platform/i8042/serio4/serio5/input/input13
Aug   8 12:29:38 james-ThinkPad-X131e avahi-daemon[927]: Joining mDNS  multicast group on interface eth2.IPv6 with address  fe80::e206:e6ff:fefa:7c77.
Aug  8 12:29:38 james-ThinkPad-X131e avahi-daemon[927]: New relevant interface eth2.IPv6 for mDNS.
Aug  8 12:29:38 james-ThinkPad-X131e avahi-daemon[927]: Registering new address record for fe80::e206:e6ff:fefa:7c77 on eth2.*.
Aug   8 12:29:39 james-ThinkPad-X131e gnome-session[1808]: WARNING: Failed to  start app: Unable to start application: Failed to execute child process  "/usr/lib/indicator-ubuntuone/" (Permission denied)
Aug  8 12:29:39  james-ThinkPad-X131e rtkit-daemon[1709]: Successfully made thread 1916  of process 1916 (n/a) owned by '1000' high priority at nice level -11.
Aug  8 12:29:39 james-ThinkPad-X131e rtkit-daemon[1709]: Supervising 4 threads of 2 processes of 2 users.
Aug  8 12:29:39 james-ThinkPad-X131e dbus[874]: [system] Activating service name='org.freedesktop.UDisks' (using servicehelper)
Aug  8 12:29:39 james-ThinkPad-X131e dbus[874]: [system] Successfully activated service 'org.freedesktop.UDisks'
Aug   8 12:29:40 james-ThinkPad-X131e rtkit-daemon[1709]: Successfully made  thread 1955 of process 1916 (n/a) owned by '1000' RT at priority 5.
Aug  8 12:29:40 james-ThinkPad-X131e rtkit-daemon[1709]: Supervising 5 threads of 2 processes of 2 users.
Aug   8 12:29:40 james-ThinkPad-X131e rtkit-daemon[1709]: Successfully made  thread 1958 of process 1916 (n/a) owned by '1000' RT at priority 5.
Aug  8 12:29:40 james-ThinkPad-X131e rtkit-daemon[1709]: Supervising 6 threads of 2 processes of 2 users.
Aug  8 12:29:40 james-ThinkPad-X131e bluetoothd[900]: Endpoint registered: sender=:1.53 path=/MediaEndpoint/HFPAG
Aug  8 12:29:40 james-ThinkPad-X131e bluetoothd[900]: Endpoint registered: sender=:1.53 path=/MediaEndpoint/A2DPSource
Aug  8 12:29:40 james-ThinkPad-X131e bluetoothd[900]: Endpoint registered: sender=:1.53 path=/MediaEndpoint/A2DPSink
Aug   8 12:29:40 james-ThinkPad-X131e NetworkManager[932]: <info>  (eth2): device state change: ip-config -> activated (reason 'none')  [70 100 0]
Aug  8 12:29:40 james-ThinkPad-X131e NetworkManager[932]:  <info> Policy set 'Morrissey-Net' (eth2) as default for IPv4  routing and DNS.
Aug  8 12:29:40 james-ThinkPad-X131e NetworkManager[932]: <info> Activation (eth2) successful, device activated.
Aug  8 12:29:40 james-ThinkPad-X131e NetworkManager[932]: <info> Activation (eth2) Stage 5 of 5 (IPv4 Commit) complete.
Aug   8 12:29:40 james-ThinkPad-X131e dbus[874]: [system] Activating service  name='org.freedesktop.nm_dispatcher' (using servicehelper)
Aug  8 12:29:40 james-ThinkPad-X131e dbus[874]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Aug  8 12:29:55 james-ThinkPad-X131e goa[2226]: goa-daemon version 3.4.0 starting [main.c:112, main()]
Aug  8 12:29:57 james-ThinkPad-X131e NetworkManager[932]: <info> (eth2): IP6 addrconf timed out or failed.
Aug   8 12:29:57 james-ThinkPad-X131e NetworkManager[932]: <info>  Activation (eth2) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Aug   8 12:29:57 james-ThinkPad-X131e NetworkManager[932]: <info>  Activation (eth2) Stage 4 of 5 (IPv6 Configure Timeout) started...
Aug   8 12:29:57 james-ThinkPad-X131e NetworkManager[932]: <info>  Activation (eth2) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Aug  8 12:29:57 james-ThinkPad-X131e bluetoothd[900]: Endpoint unregistered: sender=:1.35 path=/MediaEndpoint/HFPAG
Aug  8 12:29:57 james-ThinkPad-X131e bluetoothd[900]: Endpoint unregistered: sender=:1.35 path=/MediaEndpoint/A2DPSource
Aug  8 12:29:57 james-ThinkPad-X131e bluetoothd[900]: Endpoint unregistered: sender=:1.35 path=/MediaEndpoint/A2DPSink
Aug  8 12:30:02 james-ThinkPad-X131e bluetoothd[900]: HCI dev 0 down
Aug  8 12:30:02 james-ThinkPad-X131e bluetoothd[900]: Adapter /org/bluez/900/hci0 has been disabled
Aug  8 12:30:02 james-ThinkPad-X131e bluetoothd[900]: HCI dev 0 unregistered
Aug  8 12:30:02 james-ThinkPad-X131e bluetoothd[900]: Stopping hci0 event socket
Aug  8 12:30:02 james-ThinkPad-X131e bluetoothd[900]: Unregister path: /org/bluez/900/hci0
Aug  8 12:30:02 james-ThinkPad-X131e bluetoothd[900]: Endpoint unregistered: sender=:1.53 path=/MediaEndpoint/A2DPSink
Aug  8 12:30:02 james-ThinkPad-X131e bluetoothd[900]: Endpoint unregistered: sender=:1.53 path=/MediaEndpoint/A2DPSource
Aug  8 12:30:02 james-ThinkPad-X131e bluetoothd[900]: Endpoint unregistered: sender=:1.53 path=/MediaEndpoint/HFPAG
Aug  8 12:30:02 james-ThinkPad-X131e kernel: [   54.429107] usb 2-1.5: USB disconnect, device number 3
Aug  8 12:30:05 james-ThinkPad-X131e ntpdate[2170]: adjust time server 91.189.89.199 offset 0.472568 sec
```

---

### Post by MorrisseyJ on 2013-08-09
Hi all, 

Three more system lock-ups this morning. This is kind of enormously frustrating as there does not seem to be a stable version of Ubuntu available to me.

If anyone has any advice on what i could do to sort this out i would very much appreciate it. 

Thanks, 

j

---

### Post by MorrisseyJ on 2013-08-13
Bump.

Any advice on how i might approach decoding what the problem is here would be greatly appreciated. I don't need an answer, just an avenue to pursue. I'd love to have a working system and would be happy to try and contribute to fixing this problem. I am just not sure where to start with such an amorphous problem and so many kernel errors. 

Thanks, 

j

---

### Post by Boab1993 on 2013-08-13
Hi there morrissey J, 

Freezing generally occurs when a critical component crashes in the OS, usually due to an overload in memory. In your case, given the specs of your computer this is very unlikely to be hardware related.

After a quick read of the kernel log, theres nothing that id say is that disturbing.
The only error is at the top : 
[FONT=arial]"Could not open output  pipe '/dev/xconsole' [try [http://www.rsyslog.com/e/2039](http://www.rsyslog.com/e/2039) ]"

I personally dont know if that would cause a freeze.

In your previous install of ubuntu were you using the x-86 intel image(32-bit)?[/FONT]

---

### Post by MorrisseyJ on 2013-08-13
Hi Boab1993, 

Thanks for looking at this. 

Yes, i doubt issues are memory related as i have 8GB of RAM in the machine. 

In response to your question, i have always been running the 64bit install on this machine.

Its good to hear that you think the other kernel errors are not likely to be disturbing and that its the [FONT=arial]"Could not open output  pipe '/dev/xconsole' [try [http://www.rsyslog.com/e/2039](http://www.rsyslog.com/e/2039) ]"[/FONT] error which is of concern. A quick google of that brings up [https://bugs.launchpad.net/ubuntu/+source/rsyslog/+bug/830046](https://bugs.launchpad.net/ubuntu/+source/rsyslog/+bug/830046). There someone appears to have a fix (posts 4 & 5), and someone else notes that on 12.10 their machine is freezing and generating the same error (post #6).

Someone also suggests this is a duplicate of another bug: [https://bugs.launchpad.net/ubuntu/+source/rsyslog/+bug/459730](https://bugs.launchpad.net/ubuntu/+source/rsyslog/+bug/459730), which it seems to be and there again the issue of freezing is discussed: posts #35, #36, #37. It appears that this is not a problem which causes freezing.

I am happy to try and stick the fix in for this problem to see if it works. Do you have any other advice?

Thanks again,

j

---

### Post by Boab1993 on 2013-08-13
Since you've always been running the x64, tends to suggest its nothing to with incompatability of the software.

I didnt think it would be the problem, ill have to read through the logs properly when i get home. 
You might aswell try the fix, it is a reported bug, even if it is completely unrelated.

Another general fix for this kind of error is try updating your kernel, documentation on that can be found here:

[https://help.ubuntu.com/community/Kernel/Upgrade](https://help.ubuntu.com/community/Kernel/Upgrade)

Ill read through the log and get back to you.

Keep us posted.

---

### Post by MorrisseyJ on 2013-08-13
Thanks i really appreciate it. 

To get rid of the  [FONT=arial]"Could not open output  pipe '/dev/xconsole' [try [http://www.rsyslog.com/e/2039](http://www.rsyslog.com/e/2039) ]" error i have commented out [/FONT]lines referencing /dev/xconsole in the rsyslog configuration file (/etc/rsyslog.d/50-default.conf), as per posts #33 and #36 in [https://bugs.launchpad.net/ubuntu/+source/rsyslog/+bug/459730](https://bugs.launchpad.net/ubuntu/+source/rsyslog/+bug/459730).

I have also previously updated to the latest kernel. On that note, it seems that 3.5.0-34-generic, gives the most stability: about one freeze a day. 

Let me know if you come up with anything. 

Thanks again, 

j

---

### Post by MorrisseyJ on 2013-08-17
Bump

---

### Post by MorrisseyJ on 2013-10-17
The problem here was with the wireless card/driver. The problem only occurred when the machine was on battery power and its a well documented problem on Broadcom BCM43228 cards. The proprietary driver had to be installed via the package bcmwl-kernel-source in order to get the wireless to work. When it was not installed the machine was fine (but i had no wireless) and when it was installed the machine would freeze when on battery. 

I tried a number of things: compiling from source (with patches), turning off the auto-power off option on the card, installing upstream kernels, but nothing worked. Eventually i solved this by buying a whitelisted Intel Centrino card for my machine. This was easy to install, relatively cheap and works great. I am now without freezes and have properly functioning wireless. 

james

---

