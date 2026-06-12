---
title: "strange issue with old raid 5 drives"
date: 2008-05-27
forum: General Help
---

### Post by modulok on 2008-05-27
A few months ago I had an issue with my raid5 setup. (5 320GB SATA drives connected to a SuperMicro SATA II card AOC-SAT2-MV8)

One day one of the drives stopped working with the array. So I moved the data off. I haven't done anything since the weekend where I installed Hardy 64bit. I did everything I could think of/lookup on the forums and google. I even used my Acronis CD and did long wipes on each drive. I recreated the raid5 array, then I would reboot and its not built.

All drives have no partitions setup. I installed mdadm and restarted. On the Ubuntu boot screen, it hangs for 2-3 minutes. I check the hard drives' activity, and every one is going non-stop. Its almost like they are rebuilding, but mdadm shows no activity. 

Below are the log files from the last bootup. I am guessing its at least one of three things:
1. hard drive is bad
2. Sata card is bad
3. Some mdadm info still on the drive and I can't remake an array.

I am open to any suggestions, please help!

```
Messeges Log
May 27 20:51:55 thunder syslogd 1.5.0#1ubuntu1: restart.
May 27 20:51:55 thunder kernel: Inspecting /boot/System.map-2.6.24-16-generic
May 27 20:51:55 thunder kernel: Loaded 28313 symbols from /boot/System.map-2.6.24-16-generic.
May 27 20:51:55 thunder kernel: Symbols match kernel version 2.6.24.
May 27 20:51:55 thunder kernel: Loaded 28168 symbols from 74 modules.
May 27 20:51:55 thunder kernel: [    0.000000] Linux version 2.6.24-16-generic (buildd@yellow) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 12:47:45 UTC 2008 (Ubuntu 2.6.24-16.30-generic)
May 27 20:51:55 thunder kernel: [    0.000000] Command line: root=UUID=39b63fbe-33e1-4bf8-8a80-12e86eb6af72 ro quiet splash
May 27 20:51:55 thunder kernel: [    0.000000] BIOS-provided physical RAM map:
May 27 20:51:55 thunder kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
May 27 20:51:55 thunder kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
May 27 20:51:55 thunder kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
May 27 20:51:55 thunder kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000daff0000 (usable)
May 27 20:51:55 thunder kernel: [    0.000000]  BIOS-e820: 00000000daff0000 - 00000000dafff000 (ACPI data)
May 27 20:51:55 thunder kernel: [    0.000000]  BIOS-e820: 00000000dafff000 - 00000000db000000 (ACPI NVS)
May 27 20:51:55 thunder kernel: [    0.000000]  BIOS-e820: 00000000ff780000 - 0000000100000000 (reserved)
May 27 20:51:55 thunder kernel: [    0.000000] end_pfn_map = 1048576
May 27 20:51:55 thunder kernel: [    0.000000] DMI 2.3 present.
May 27 20:51:55 thunder kernel: [    0.000000] ACPI: RSDP signature @ 0xFFFF8100000F6F20 checksum 0
May 27 20:51:55 thunder kernel: [    0.000000] ACPI: RSDP 000F6F20, 0014 (r0 ACPIAM)
May 27 20:51:55 thunder kernel: [    0.000000] ACPI: RSDT DAFF0000, 0038 (r1 A M I  OEMRSDT   7000626 MSFT       97)
May 27 20:51:55 thunder kernel: [    0.000000] ACPI: FACP DAFF0200, 0081 (r1 A M I  OEMFACP   7000626 MSFT       97)
May 27 20:51:55 thunder kernel: [    0.000000] ACPI: DSDT DAFF0410, 3751 (r1  0AAAA 0AAAA000        0 INTL  2002026)
May 27 20:51:55 thunder kernel: [    0.000000] ACPI: FACS DAFFF000, 0040
May 27 20:51:55 thunder kernel: [    0.000000] ACPI: APIC DAFF0380, 0084 (r1 A M I  OEMAPIC   7000626 MSFT       97)
May 27 20:51:55 thunder kernel: [    0.000000] ACPI: OEMB DAFFF040, 0041 (r1 A M I  OEMBIOS   7000626 MSFT       97)
May 27 20:51:55 thunder kernel: [    0.000000] ACPI: SRAT DAFF3B70, 0110 (r1 A M I  OEMSRAT   7000626 MSFT       97)
May 27 20:51:55 thunder kernel: [    0.000000] ACPI: ASF! DAFF3C80, 0086 (r1 AMIASF AMDSTRET        1 INTL  2002026)
May 27 20:51:55 thunder kernel: [    0.000000] SRAT: PXM 0 -> APIC 0 -> Node 0
May 27 20:51:55 thunder kernel: [    0.000000] SRAT: PXM 1 -> APIC 1 -> Node 1
May 27 20:51:55 thunder kernel: [    0.000000] SRAT: Node 0 PXM 0 100000-80000000
May 27 20:51:55 thunder kernel: [    0.000000] SRAT: Node 1 PXM 1 80000000-db000000
May 27 20:51:55 thunder kernel: [    0.000000] SRAT: Node 1 PXM 1 80000000-100000000
May 27 20:51:55 thunder kernel: [    0.000000] SRAT: Node 0 PXM 0 0-80000000
May 27 20:51:55 thunder kernel: [    0.000000] Bootmem setup node 0 0000000000000000-0000000080000000
May 27 20:51:55 thunder kernel: [    0.000000] Bootmem setup node 1 0000000080000000-00000000daff0000
May 27 20:51:55 thunder kernel: [    0.000000] Zone PFN ranges:
May 27 20:51:55 thunder kernel: [    0.000000]   DMA             0 ->     4096
May 27 20:51:55 thunder kernel: [    0.000000]   DMA32        4096 ->  1048576
May 27 20:51:55 thunder kernel: [    0.000000]   Normal    1048576 ->  1048576
May 27 20:51:55 thunder kernel: [    0.000000] Movable zone start PFN for each node
May 27 20:51:55 thunder kernel: [    0.000000] early_node_map[3] active PFN ranges
May 27 20:51:55 thunder kernel: [    0.000000]     0:        0 ->      159
May 27 20:51:55 thunder kernel: [    0.000000]     0:      256 ->   524288
May 27 20:51:55 thunder kernel: [    0.000000]     1:   524288 ->   897008
May 27 20:51:55 thunder kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
May 27 20:51:55 thunder kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
May 27 20:51:55 thunder kernel: [    0.000000] Processor #0 (Bootup-CPU)
May 27 20:51:55 thunder kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
May 27 20:51:55 thunder kernel: [    0.000000] Processor #1
May 27 20:51:55 thunder kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
May 27 20:51:55 thunder kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
May 27 20:51:55 thunder kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
May 27 20:51:55 thunder kernel: [    0.000000] IOAPIC[0]: apic_id 2, address 0xfec00000, GSI 0-23
May 27 20:51:55 thunder kernel: [    0.000000] ACPI: IOAPIC (id[0x03] address[0xfebff000] gsi_base[24])
May 27 20:51:55 thunder kernel: [    0.000000] IOAPIC[1]: apic_id 3, address 0xfebff000, GSI 24-27
May 27 20:51:55 thunder kernel: [    0.000000] ACPI: IOAPIC (id[0x04] address[0xfebfe000] gsi_base[28])
May 27 20:51:55 thunder kernel: [    0.000000] IOAPIC[2]: apic_id 4, address 0xfebfe000, GSI 28-31
May 27 20:51:55 thunder kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
May 27 20:51:55 thunder kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
May 27 20:51:55 thunder kernel: [    0.000000] Setting APIC routing to flat
May 27 20:51:55 thunder kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
May 27 20:51:55 thunder kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
May 27 20:51:55 thunder kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e0000
May 27 20:51:55 thunder kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 0000000000100000
May 27 20:51:55 thunder kernel: [    0.000000] Allocating PCI resources starting at dc000000 (gap: db000000:24780000)
May 27 20:51:55 thunder kernel: [    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
May 27 20:51:55 thunder kernel: [    0.000000] PERCPU: Allocating 34656 bytes of per cpu data
May 27 20:51:55 thunder kernel: [    0.000000] Built 2 zonelists in Node order, mobility grouping on.  Total pages: 883439
May 27 20:51:55 thunder kernel: [    0.000000] Policy zone: DMA32
May 27 20:51:55 thunder kernel: [    0.000000] Kernel command line: root=UUID=39b63fbe-33e1-4bf8-8a80-12e86eb6af72 ro quiet splash
May 27 20:51:55 thunder kernel: [    0.000000] Initializing CPU#0
May 27 20:51:55 thunder kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
May 27 20:51:55 thunder kernel: [    0.000000] TSC calibrated against PM_TIMER
May 27 20:51:55 thunder kernel: [   38.398079] Marking TSC unstable due to TSCs unsynchronized
May 27 20:51:55 thunder kernel: [   38.398080] time.c: Detected 2590.564 MHz processor.
May 27 20:51:55 thunder kernel: [   38.400498] Console: colour VGA+ 80x25
May 27 20:51:55 thunder kernel: [   38.400501] console [tty0] enabled
May 27 20:51:55 thunder kernel: [   38.400514] Checking aperture...
May 27 20:51:55 thunder kernel: [   38.400516] CPU 0: aperture @ 4180000000 size 32 MB
May 27 20:51:55 thunder kernel: [   38.400517] Aperture too small (32 MB)
May 27 20:51:55 thunder kernel: [   38.407211] No AGP bridge found
May 27 20:51:55 thunder kernel: [   38.437885] Memory: 3525612k/3588032k available (2466k kernel code, 62032k reserved, 1309k data, 316k init)
May 27 20:51:55 thunder kernel: [   38.437915] SLUB: Genslabs=12, HWalign=64, Order=0-1, MinObjects=4, CPUs=4, Nodes=2
May 27 20:51:55 thunder kernel: [   38.516136] Calibrating delay using timer specific routine.. 5224.63 BogoMIPS (lpj=10449273)
May 27 20:51:55 thunder kernel: [   38.516168] Security Framework initialized
May 27 20:51:55 thunder kernel: [   38.516172] SELinux:  Disabled at boot.
May 27 20:51:55 thunder kernel: [   38.516183] AppArmor: AppArmor initialized
May 27 20:51:55 thunder kernel: [   38.516185] Failure registering capabilities with primary security module.
May 27 20:51:55 thunder kernel: [   38.516464] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
May 27 20:51:55 thunder kernel: [   38.519068] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
May 27 20:51:55 thunder kernel: [   38.520281] Mount-cache hash table entries: 256
May 27 20:51:55 thunder kernel: [   38.520486] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
May 27 20:51:55 thunder kernel: [   38.520487] CPU: L2 Cache: 1024K (64 bytes/line)
May 27 20:51:55 thunder kernel: [   38.520489] CPU 0/0 -> Node 0
May 27 20:51:55 thunder kernel: [   38.520506] SMP alternatives: switching to UP code
May 27 20:51:55 thunder kernel: [   38.520946] Early unpacking initramfs... done
May 27 20:51:55 thunder kernel: [   38.770603] ACPI: Core revision 20070126
May 27 20:51:55 thunder kernel: [   38.770639] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
May 27 20:51:55 thunder kernel: [   38.812943] Using local APIC timer interrupts.
May 27 20:51:55 thunder kernel: [   38.851522] Detected 12.454 MHz APIC timer.
May 27 20:51:55 thunder kernel: [   38.851604] SMP alternatives: switching to SMP code
May 27 20:51:55 thunder kernel: [   38.851965] Booting processor 1/2 APIC 0x1
May 27 20:51:55 thunder kernel: [   38.862125] Initializing CPU#1
May 27 20:51:55 thunder kernel: [   38.939472] Calibrating delay using timer specific routine.. 5181.15 BogoMIPS (lpj=10362319)
May 27 20:51:55 thunder kernel: [   38.939478] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
May 27 20:51:55 thunder kernel: [   38.939479] CPU: L2 Cache: 1024K (64 bytes/line)
May 27 20:51:55 thunder kernel: [   38.939482] CPU 1/1 -> Node 1
May 27 20:51:55 thunder kernel: [   38.939589] AMD Opteron(tm) Processor 252 stepping 01
May 27 20:51:55 thunder kernel: [   38.939612] Brought up 2 CPUs
May 27 20:51:55 thunder kernel: [   38.939989] net_namespace: 120 bytes
May 27 20:51:55 thunder kernel: [   38.940340] Time:  0:48:38  Date: 05/28/08
May 27 20:51:55 thunder kernel: [   38.940370] NET: Registered protocol family 16
May 27 20:51:55 thunder kernel: [   38.940547] ACPI: bus type pci registered
May 27 20:51:55 thunder kernel: [   38.940612] PCI: Using configuration type 1
May 27 20:51:55 thunder kernel: [   38.947562] ACPI: Interpreter enabled
May 27 20:51:55 thunder kernel: [   38.947564] ACPI: (supports S0 S1 S4 S5)
May 27 20:51:55 thunder kernel: [   38.947574] ACPI: Using IOAPIC for interrupt routing
May 27 20:51:55 thunder kernel: [   38.951569] ACPI: PCI Root Bridge [PCI0] (0000:00)
May 27 20:51:55 thunder kernel: [   38.954688] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
May 27 20:51:55 thunder kernel: [   38.954770] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
May 27 20:51:55 thunder kernel: [   38.954849] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
May 27 20:51:55 thunder kernel: [   38.954928] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
May 27 20:51:55 thunder kernel: [   38.955032] Linux Plug and Play Support v0.97 (c) Adam Belay
May 27 20:51:55 thunder kernel: [   38.955070] pnp: PnP ACPI init
May 27 20:51:55 thunder kernel: [   38.955075] ACPI: bus type pnp registered
May 27 20:51:55 thunder kernel: [   38.957143] pnp: PnP ACPI: found 12 devices
May 27 20:51:55 thunder kernel: [   38.957144] ACPI: ACPI bus type pnp unregistered
May 27 20:51:55 thunder kernel: [   38.957374] PCI: Using ACPI for IRQ routing
May 27 20:51:55 thunder kernel: [   38.957376] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
May 27 20:51:55 thunder kernel: [   38.983456] NET: Registered protocol family 8
May 27 20:51:55 thunder kernel: [   38.983458] NET: Registered protocol family 20
May 27 20:51:55 thunder kernel: [   38.983577] AppArmor: AppArmor Filesystem Enabled
May 27 20:51:55 thunder kernel: [   38.995474] system 00:07: ioport range 0x680-0x6ff has been reserved
May 27 20:51:55 thunder kernel: [   38.995477] system 00:07: ioport range 0x295-0x296 has been reserved
May 27 20:51:55 thunder kernel: [   38.995483] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
May 27 20:51:55 thunder kernel: [   38.995485] system 00:08: ioport range 0x1000-0x10bf has been reserved
May 27 20:51:55 thunder kernel: [   38.995487] system 00:08: ioport range 0x10e0-0x10ff has been reserved
May 27 20:51:55 thunder kernel: [   38.995489] system 00:08: ioport range 0x10c0-0x10df has been reserved
May 27 20:51:55 thunder kernel: [   38.995492] system 00:08: ioport range 0xde00-0xde7f has been reserved
May 27 20:51:55 thunder kernel: [   38.995494] system 00:08: ioport range 0xde80-0xdeff has been reserved
May 27 20:51:55 thunder kernel: [   38.995498] system 00:0a: ioport range 0xca0-0xcaf has been reserved
May 27 20:51:55 thunder kernel: [   38.995500] system 00:0a: iomem range 0xfec00000-0xfec00fff has been reserved
May 27 20:51:55 thunder kernel: [   38.995503] system 00:0a: iomem range 0xfee00000-0xfee00fff could not be reserved
May 27 20:51:55 thunder kernel: [   38.995505] system 00:0a: iomem range 0xfff80000-0xffffffff could not be reserved
May 27 20:51:55 thunder kernel: [   38.995508] system 00:0a: iomem range 0xff780000-0xff7fffff could not be reserved
May 27 20:51:55 thunder kernel: [   38.995512] system 00:0b: iomem range 0x0-0x9ffff could not be reserved
May 27 20:51:55 thunder kernel: [   38.995514] system 00:0b: iomem range 0xc0000-0xdffff has been reserved
May 27 20:51:55 thunder kernel: [   38.995517] system 00:0b: iomem range 0xe0000-0xfffff could not be reserved
May 27 20:51:55 thunder kernel: [   38.995519] system 00:0b: iomem range 0x100000-0xdaffffff could not be reserved
May 27 20:51:55 thunder kernel: [   38.995521] system 00:0b: iomem range 0x0-0x0 could not be reserved
May 27 20:51:55 thunder kernel: [   38.996006] PCI: Bridge: 0000:00:06.0
May 27 20:51:55 thunder kernel: [   38.996008]   IO window: b000-bfff
May 27 20:51:55 thunder kernel: [   38.996012]   MEM window: fea00000-feafffff
May 27 20:51:55 thunder kernel: [   38.996015]   PREFETCH window: disabled.
May 27 20:51:55 thunder kernel: [   38.996019] PCI: Bridge: 0000:00:0a.0
May 27 20:51:55 thunder kernel: [   38.996020]   IO window: disabled.
May 27 20:51:55 thunder kernel: [   38.996023]   MEM window: fc900000-fe9fffff
May 27 20:51:55 thunder kernel: [   38.996026]   PREFETCH window: db500000-fb5fffff
May 27 20:51:55 thunder kernel: [   38.996029] PCI: Bridge: 0000:00:0b.0
May 27 20:51:55 thunder kernel: [   38.996031]   IO window: a000-afff
May 27 20:51:55 thunder kernel: [   38.996033]   MEM window: fb700000-fc8fffff
May 27 20:51:55 thunder kernel: [   38.996035]   PREFETCH window: db400000-db4fffff
May 27 20:51:55 thunder kernel: [   38.996108] NET: Registered protocol family 2
May 27 20:51:55 thunder kernel: [   38.999431] Time: acpi_pm clocksource has been installed.
May 27 20:51:55 thunder kernel: [   39.031523] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
May 27 20:51:55 thunder kernel: [   39.032696] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
May 27 20:51:55 thunder kernel: [   39.037800] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
May 27 20:51:55 thunder kernel: [   39.038344] TCP: Hash tables configured (established 524288 bind 65536)
May 27 20:51:55 thunder kernel: [   39.038347] TCP reno registered
May 27 20:51:55 thunder kernel: [   39.047531] checking if image is initramfs... it is
May 27 20:51:55 thunder kernel: [   39.529379] Freeing initrd memory: 7782k freed
May 27 20:51:55 thunder kernel: [   39.534309] audit: initializing netlink socket (disabled)
May 27 20:51:55 thunder kernel: [   39.534326] audit(1211935719.104:1): initialized
May 27 20:51:55 thunder kernel: [   39.536336] VFS: Disk quotas dquot_6.5.1
May 27 20:51:55 thunder kernel: [   39.536399] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
May 27 20:51:55 thunder kernel: [   39.536506] io scheduler noop registered
May 27 20:51:55 thunder kernel: [   39.536507] io scheduler anticipatory registered
May 27 20:51:55 thunder kernel: [   39.536509] io scheduler deadline registered
May 27 20:51:55 thunder kernel: [   39.536600] io scheduler cfq registered (default)
May 27 20:51:55 thunder kernel: [   39.536609] PCI: MSI quirk detected. PCI_BUS_FLAGS_NO_MSI set for 0000:00:0a.0 subordinate bus.
May 27 20:51:55 thunder kernel: [   39.536611] AMD8131 rev 12 detected, disabling PCI-X MMRBC
May 27 20:51:55 thunder kernel: [   39.536614] PCI: MSI quirk detected. PCI_BUS_FLAGS_NO_MSI set for 0000:00:0b.0 subordinate bus.
May 27 20:51:55 thunder kernel: [   39.536616] AMD8131 rev 12 detected, disabling PCI-X MMRBC
May 27 20:51:55 thunder kernel: [   39.591173] PCI: Firmware left 0000:03:08.0 e100 interrupts enabled, disabling
May 27 20:51:55 thunder kernel: [   39.617100] Real Time Clock Driver v1.12ac
May 27 20:51:55 thunder kernel: [   39.617184] hpet_acpi_add: no address or irqs in _CRS
May 27 20:51:55 thunder kernel: [   39.617199] Linux agpgart interface v0.102
May 27 20:51:55 thunder kernel: [   39.617201] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
May 27 20:51:55 thunder kernel: [   39.617323] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
May 27 20:51:55 thunder kernel: [   39.617447] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
May 27 20:51:55 thunder kernel: [   39.617843] 00:05: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
May 27 20:51:55 thunder kernel: [   39.618017] 00:06: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
May 27 20:51:55 thunder kernel: [   39.618907] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
May 27 20:51:55 thunder kernel: [   39.618962] input: Macintosh mouse button emulation as /devices/virtual/input/input0
May 27 20:51:55 thunder kernel: [   39.619270] PNP: No PS/2 controller found. Probing ports directly.
May 27 20:51:55 thunder kernel: [   39.621358] serio: i8042 KBD port at 0x60,0x64 irq 1
May 27 20:51:55 thunder kernel: [   39.621365] serio: i8042 AUX port at 0x60,0x64 irq 12
May 27 20:51:55 thunder kernel: [   39.639606] mice: PS/2 mouse device common for all mice
May 27 20:51:55 thunder kernel: [   39.639648] cpuidle: using governor ladder
May 27 20:51:55 thunder kernel: [   39.639650] cpuidle: using governor menu
May 27 20:51:55 thunder kernel: [   39.639807] NET: Registered protocol family 1
May 27 20:51:55 thunder kernel: [   39.639867] registered taskstats version 1
May 27 20:51:55 thunder kernel: [   39.639980]   Magic number: 8:880:810
May 27 20:51:55 thunder kernel: [   39.640065]   hash matches device ptys4
May 27 20:51:55 thunder kernel: [   39.640105] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
May 27 20:51:55 thunder kernel: [   39.640107] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
May 27 20:51:55 thunder kernel: [   39.640109] EDD information not available.
May 27 20:51:55 thunder kernel: [   39.640117] Freeing unused kernel memory: 316k freed
May 27 20:51:55 thunder kernel: [   40.825509] fuse init (API version 7.9)
May 27 20:51:55 thunder kernel: [   40.840124] ACPI: Processor [CPU1] (supports 8 throttling states)
May 27 20:51:55 thunder kernel: [   40.840158] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
May 27 20:51:55 thunder kernel: [   40.840167] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
May 27 20:51:55 thunder kernel: [   40.853953] md: linear personality registered for level -1
May 27 20:51:55 thunder kernel: [   40.857444] md: multipath personality registered for level -4
May 27 20:51:55 thunder kernel: [   40.860704] md: raid0 personality registered for level 0
May 27 20:51:55 thunder kernel: [   40.864301] md: raid1 personality registered for level 1
May 27 20:51:55 thunder kernel: [   40.867347] xor: automatically using best checksumming function: generic_sse
May 27 20:51:55 thunder kernel: [   40.885996]    generic_sse:  8302.000 MB/sec
May 27 20:51:55 thunder kernel: [   40.885998] xor: using function: generic_sse (8302.000 MB/sec)
May 27 20:51:55 thunder kernel: [   40.886507] async_tx: api initialized (async)
May 27 20:51:55 thunder kernel: [   40.953950] raid6: int64x1   2604 MB/s
May 27 20:51:55 thunder kernel: [   41.021909] raid6: int64x2   3208 MB/s
May 27 20:51:55 thunder kernel: [   41.089859] raid6: int64x4   3330 MB/s
May 27 20:51:55 thunder kernel: [   41.157804] raid6: int64x8   2588 MB/s
May 27 20:51:55 thunder kernel: [   41.225754] raid6: sse2x1    3218 MB/s
May 27 20:51:55 thunder kernel: [   41.293694] raid6: sse2x2    4179 MB/s
May 27 20:51:55 thunder kernel: [   41.361650] raid6: sse2x4    4720 MB/s
May 27 20:51:55 thunder kernel: [   41.361652] raid6: using algorithm sse2x4 (4720 MB/s)
May 27 20:51:55 thunder kernel: [   41.361654] md: raid6 personality registered for level 6
May 27 20:51:55 thunder kernel: [   41.361655] md: raid5 personality registered for level 5
May 27 20:51:55 thunder kernel: [   41.361656] md: raid4 personality registered for level 4
May 27 20:51:55 thunder kernel: [   41.381175] md: raid10 personality registered for level 10
May 27 20:51:55 thunder kernel: [   41.519507] SCSI subsystem initialized
May 27 20:51:55 thunder kernel: [   41.537794] scsi0 : pata_amd
May 27 20:51:55 thunder kernel: [   41.537830] scsi1 : pata_amd
May 27 20:51:55 thunder kernel: [   41.538179] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
May 27 20:51:55 thunder kernel: [   41.538181] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
May 27 20:51:55 thunder kernel: [   41.564915] usbcore: registered new interface driver usbfs
May 27 20:51:55 thunder kernel: [   41.564934] usbcore: registered new interface driver hub
May 27 20:51:55 thunder kernel: [   41.564959] usbcore: registered new device driver usb
May 27 20:51:55 thunder kernel: [   41.587090] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k4-NAPI
May 27 20:51:55 thunder kernel: [   41.587093] e100: Copyright(c) 1999-2006 Intel Corporation
May 27 20:51:55 thunder kernel: [   41.857625] ata1.00: ATAPI: TDK DVDRW1280B, T7S4, max UDMA/33
May 27 20:51:55 thunder kernel: [   42.029440] ata1.00: configured for UDMA/33
May 27 20:51:55 thunder kernel: [   42.197126] scsi 0:0:0:0: CD-ROM            TDK      DVDRW1280B       T7S4 PQ: 0 ANSI: 5
May 27 20:51:55 thunder kernel: [   42.197303] ACPI: PCI Interrupt 0000:03:00.0[D] -> GSI 19 (level, low) -> IRQ 19
May 27 20:51:55 thunder kernel: [   42.197572] ohci_hcd 0000:03:00.0: OHCI Host Controller
May 27 20:51:55 thunder kernel: [   42.197785] ohci_hcd 0000:03:00.0: new USB bus registered, assigned bus number 1
May 27 20:51:55 thunder kernel: [   42.197808] ohci_hcd 0000:03:00.0: irq 19, io mem 0xfeafc000
May 27 20:51:55 thunder kernel: [   42.204279] Driver 'sr' needs updating - please use bus_type methods
May 27 20:51:55 thunder kernel: [   42.209501] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
May 27 20:51:55 thunder kernel: [   42.209507] Uniform CD-ROM driver Revision: 3.20
May 27 20:51:55 thunder kernel: [   42.212454] sr 0:0:0:0: Attached scsi generic sg0 type 5
May 27 20:51:55 thunder kernel: [   42.259181] usb usb1: configuration #1 chosen from 1 choice
May 27 20:51:55 thunder kernel: [   42.259202] hub 1-0:1.0: USB hub found
May 27 20:51:55 thunder kernel: [   42.259211] hub 1-0:1.0: 3 ports detected
May 27 20:51:55 thunder kernel: [   42.361020] ACPI: PCI Interrupt 0000:03:00.1[D] -> GSI 19 (level, low) -> IRQ 19
May 27 20:51:55 thunder kernel: [   42.361258] ohci_hcd 0000:03:00.1: OHCI Host Controller
May 27 20:51:55 thunder kernel: [   42.361318] ohci_hcd 0000:03:00.1: new USB bus registered, assigned bus number 2
May 27 20:51:55 thunder kernel: [   42.361334] ohci_hcd 0000:03:00.1: irq 19, io mem 0xfeafd000
May 27 20:51:55 thunder kernel: [   42.419045] usb usb2: configuration #1 chosen from 1 choice
May 27 20:51:55 thunder kernel: [   42.419064] hub 2-0:1.0: USB hub found
May 27 20:51:55 thunder kernel: [   42.419072] hub 2-0:1.0: 3 ports detected
May 27 20:51:55 thunder kernel: [   42.521054] ACPI: PCI Interrupt 0000:03:08.0[A] -> GSI 18 (level, low) -> IRQ 18
May 27 20:51:55 thunder kernel: [   42.600207] e100: eth0: e100_probe: addr 0xfeafb000, irq 18, MAC addr 00:e0:81:30:52:08
May 27 20:51:55 thunder kernel: [   42.600319] tg3.c:v3.86 (November 9, 2007)
May 27 20:51:55 thunder kernel: [   42.600343] ACPI: PCI Interrupt 0000:02:09.0[A] -> GSI 24 (level, low) -> IRQ 24
May 27 20:51:55 thunder kernel: [   42.616818] eth1: Tigon3 [partno(BCM95704A7) rev 2003 PHY(5704)] (PCI:33MHz:64-bit) 10/100/1000Base-T Ethernet 00:e0:81:30:52:38
May 27 20:51:55 thunder kernel: [   42.616824] eth1: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[1] TSOcap[1]
May 27 20:51:55 thunder kernel: [   42.616826] eth1: dma_rwctrl[763f0000] dma_mask[64-bit]
May 27 20:51:55 thunder kernel: [   42.616856] ACPI: PCI Interrupt 0000:02:09.1[B] -> GSI 25 (level, low) -> IRQ 25
May 27 20:51:55 thunder kernel: [   42.643682] eth2: Tigon3 [partno(BCM95704A7) rev 2003 PHY(5704)] (PCI:33MHz:64-bit) 10/100/1000Base-T Ethernet 00:e0:81:30:52:39
May 27 20:51:55 thunder kernel: [   42.643688] eth2: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[1] TSOcap[1]
May 27 20:51:55 thunder kernel: [   42.643689] eth2: dma_rwctrl[763f0000] dma_mask[64-bit]
May 27 20:51:55 thunder kernel: [   42.644535] sata_mv 0000:01:03.0: version 1.01
May 27 20:51:55 thunder kernel: [   42.644599] ACPI: PCI Interrupt 0000:01:03.0[A] -> GSI 28 (level, low) -> IRQ 28
May 27 20:51:55 thunder kernel: [   42.648130] sata_mv 0000:01:03.0: Gen-II 32 slots 8 ports SCSI mode IRQ via INTx
May 27 20:51:55 thunder kernel: [   42.648259] scsi2 : sata_mv
May 27 20:51:55 thunder kernel: [   42.648311] scsi3 : sata_mv
May 27 20:51:55 thunder kernel: [   42.648755] scsi4 : sata_mv
May 27 20:51:55 thunder kernel: [   42.648786] scsi5 : sata_mv
May 27 20:51:55 thunder kernel: [   42.648812] scsi6 : sata_mv
May 27 20:51:55 thunder kernel: [   42.648837] scsi7 : sata_mv
May 27 20:51:55 thunder kernel: [   42.648863] scsi8 : sata_mv
May 27 20:51:55 thunder kernel: [   42.648889] scsi9 : sata_mv
May 27 20:51:55 thunder kernel: [   42.648911] ata3: SATA max UDMA/133 mmio m1048576@0xfc800000 port 0xfc822000 irq 28
May 27 20:51:55 thunder kernel: [   42.648914] ata4: SATA max UDMA/133 mmio m1048576@0xfc800000 port 0xfc824000 irq 28
May 27 20:51:55 thunder kernel: [   42.648916] ata5: SATA max UDMA/133 mmio m1048576@0xfc800000 port 0xfc826000 irq 28
May 27 20:51:55 thunder kernel: [   42.648918] ata6: SATA max UDMA/133 mmio m1048576@0xfc800000 port 0xfc828000 irq 28
May 27 20:51:55 thunder kernel: [   42.648920] ata7: SATA max UDMA/133 mmio m1048576@0xfc800000 port 0xfc832000 irq 28
May 27 20:51:55 thunder kernel: [   42.648922] ata8: SATA max UDMA/133 mmio m1048576@0xfc800000 port 0xfc834000 irq 28
May 27 20:51:55 thunder kernel: [   42.648925] ata9: SATA max UDMA/133 mmio m1048576@0xfc800000 port 0xfc836000 irq 28
May 27 20:51:55 thunder kernel: [   42.648927] ata10: SATA max UDMA/133 mmio m1048576@0xfc800000 port 0xfc838000 irq 28
May 27 20:51:55 thunder kernel: [   42.824638] usb 2-1: new full speed USB device using ohci_hcd and address 2
May 27 20:51:55 thunder kernel: [   43.033539] usb 2-1: configuration #1 chosen from 1 choice
May 27 20:51:55 thunder kernel: [   43.036471] hub 2-1:1.0: USB hub found
May 27 20:51:55 thunder kernel: [   43.039446] hub 2-1:1.0: 3 ports detected
May 27 20:51:55 thunder kernel: [   43.188389] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
May 27 20:51:55 thunder kernel: [   43.200401] ata3.00: ATA-6: WDC WD360GD-00FLC0, 33.08F33, max UDMA/133
May 27 20:51:55 thunder kernel: [   43.200404] ata3.00: 72303840 sectors, multi 0: LBA48 
May 27 20:51:55 thunder kernel: [   43.224388] ata3.00: configured for UDMA/133
May 27 20:51:55 thunder kernel: [   43.460186] usb 2-2: new low speed USB device using ohci_hcd and address 3
May 27 20:51:55 thunder kernel: [   43.673992] usb 2-2: configuration #1 chosen from 1 choice
May 27 20:51:55 thunder kernel: [   43.759985] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
May 27 20:51:55 thunder kernel: [   43.775987] ata4.00: ATA-7: Maxtor 6B300S0, BANC1G10, max UDMA/133
May 27 20:51:55 thunder kernel: [   43.775989] ata4.00: 586114704 sectors, multi 0: LBA48 NCQ (not used)
May 27 20:51:55 thunder kernel: [   43.799972] ata4.00: configured for UDMA/133
May 27 20:51:55 thunder kernel: [   43.889747] usb 2-1.2: new full speed USB device using ohci_hcd and address 4
May 27 20:51:55 thunder kernel: [   44.004729] usb 2-1.2: configuration #1 chosen from 1 choice
May 27 20:51:55 thunder kernel: [   44.221470] usb 2-1.3: new full speed USB device using ohci_hcd and address 5
May 27 20:51:55 thunder kernel: [   44.335568] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
May 27 20:51:55 thunder kernel: [   44.336449] usb 2-1.3: configuration #1 chosen from 1 choice
May 27 20:51:55 thunder kernel: [   44.343395] usbcore: registered new interface driver hiddev
May 27 20:51:55 thunder kernel: [   44.350504] input: Microsoft Microsoft 5-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:06.0/0000:03:00.1/usb2/2-2/2-2:1.0/input/input1
May 27 20:51:55 thunder kernel: [   44.372061] input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft 5-Button Mouse with IntelliEye(TM)] on usb-0000:03:00.1-2
May 27 20:51:55 thunder kernel: [   44.380396] input: Logitech Logitech BT Mini-Receiver as /devices/pci0000:00/0000:00:06.0/0000:03:00.1/usb2/2-1/2-1.2/2-1.2:1.0/input/input2
May 27 20:51:55 thunder kernel: [   44.391548] ata5.00: ATA-7: MAXTOR STM3320620AS, 3.AAE, max UDMA/133
May 27 20:51:55 thunder kernel: [   44.391551] ata5.00: 625142448 sectors, multi 0: LBA48 NCQ (depth 0/32)
May 27 20:51:55 thunder kernel: [   44.404029] input,hidraw1: USB HID v1.11 Keyboard [Logitech Logitech BT Mini-Receiver] on usb-0000:03:00.1-1.2
May 27 20:51:55 thunder kernel: [   44.416382] input: Logitech Logitech BT Mini-Receiver as /devices/pci0000:00/0000:00:06.0/0000:03:00.1/usb2/2-1/2-1.3/2-1.3:1.0/input/input3
May 27 20:51:55 thunder kernel: [   44.444021] input,hiddev96,hidraw2: USB HID v1.11 Mouse [Logitech Logitech BT Mini-Receiver] on usb-0000:03:00.1-1.3
May 27 20:51:55 thunder kernel: [   44.444033] usbcore: registered new interface driver usbhid
May 27 20:51:55 thunder kernel: [   44.444036] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
May 27 20:51:55 thunder kernel: [   44.471512] ata5.00: configured for UDMA/133
May 27 20:51:55 thunder kernel: [   45.007104] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
May 27 20:51:55 thunder kernel: [   45.063083] ata6.00: ATA-7: MAXTOR STM3320620AS, 3.AAE, max UDMA/133
May 27 20:51:55 thunder kernel: [   45.063085] ata6.00: 625142448 sectors, multi 0: LBA48 NCQ (depth 0/32)
May 27 20:51:55 thunder kernel: [   45.127042] ata6.00: configured for UDMA/133
May 27 20:51:55 thunder kernel: [   45.662633] ata7: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
May 27 20:51:55 thunder kernel: [   45.726608] ata7.00: ATA-7: MAXTOR STM3320620AS, 3.AAE, max UDMA/133
May 27 20:51:55 thunder kernel: [   45.726610] ata7.00: 625142448 sectors, multi 0: LBA48 NCQ (depth 0/32)
May 27 20:51:55 thunder kernel: [   45.790562] ata7.00: configured for UDMA/133
May 27 20:51:55 thunder kernel: [   46.326142] ata8: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
May 27 20:51:55 thunder kernel: [   46.382118] ata8.00: ATA-7: MAXTOR STM3320620AS, 3.AAE, max UDMA/133
May 27 20:51:55 thunder kernel: [   46.382120] ata8.00: 625142448 sectors, multi 0: LBA48 NCQ (depth 0/32)
May 27 20:51:55 thunder kernel: [   46.446077] ata8.00: configured for UDMA/133
May 27 20:51:55 thunder kernel: [   46.981664] ata9: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
May 27 20:51:55 thunder kernel: [   47.037639] ata9.00: ATA-7: MAXTOR STM3320620AS, 3.AAE, max UDMA/133
May 27 20:51:55 thunder kernel: [   47.037640] ata9.00: 625142448 sectors, multi 0: LBA48 NCQ (depth 0/32)
May 27 20:51:55 thunder kernel: [   47.101591] ata9.00: configured for UDMA/133
May 27 20:51:55 thunder kernel: [   47.133539] ata10: SATA link down (SStatus 0 SControl 300)
May 27 20:51:55 thunder kernel: [   47.133633] scsi 2:0:0:0: Direct-Access     ATA      WDC WD360GD-00FL 33.0 PQ: 0 ANSI: 5
May 27 20:51:55 thunder kernel: [   47.133709] scsi 2:0:0:0: Attached scsi generic sg1 type 0
May 27 20:51:55 thunder kernel: [   47.133760] scsi 3:0:0:0: Direct-Access     ATA      Maxtor 6B300S0   BANC PQ: 0 ANSI: 5
May 27 20:51:55 thunder kernel: [   47.133804] scsi 3:0:0:0: Attached scsi generic sg2 type 0
May 27 20:51:55 thunder kernel: [   47.133850] scsi 4:0:0:0: Direct-Access     ATA      MAXTOR STM332062 3.AA PQ: 0 ANSI: 5
May 27 20:51:55 thunder kernel: [   47.133890] scsi 4:0:0:0: Attached scsi generic sg3 type 0
May 27 20:51:55 thunder kernel: [   47.133934] scsi 5:0:0:0: Direct-Access     ATA      MAXTOR STM332062 3.AA PQ: 0 ANSI: 5
May 27 20:51:55 thunder kernel: [   47.133975] scsi 5:0:0:0: Attached scsi generic sg4 type 0
May 27 20:51:55 thunder kernel: [   47.134018] scsi 6:0:0:0: Direct-Access     ATA      MAXTOR STM332062 3.AA PQ: 0 ANSI: 5
May 27 20:51:55 thunder kernel: [   47.134065] scsi 6:0:0:0: Attached scsi generic sg5 type 0
May 27 20:51:55 thunder kernel: [   47.134108] scsi 7:0:0:0: Direct-Access     ATA      MAXTOR STM332062 3.AA PQ: 0 ANSI: 5
May 27 20:51:55 thunder kernel: [   47.134147] scsi 7:0:0:0: Attached scsi generic sg6 type 0
May 27 20:51:55 thunder kernel: [   47.134188] scsi 8:0:0:0: Direct-Access     ATA      MAXTOR STM332062 3.AA PQ: 0 ANSI: 5
May 27 20:51:55 thunder kernel: [   47.134227] scsi 8:0:0:0: Attached scsi generic sg7 type 0
May 27 20:51:55 thunder kernel: [   47.139703] Driver 'sd' needs updating - please use bus_type methods
May 27 20:51:55 thunder kernel: [   47.139778] sd 2:0:0:0: [sda] 72303840 512-byte hardware sectors (37020 MB)
May 27 20:51:55 thunder kernel: [   47.139787] sd 2:0:0:0: [sda] Write Protect is off
May 27 20:51:55 thunder kernel: [   47.139801] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May 27 20:51:55 thunder kernel: [   47.139836] sd 2:0:0:0: [sda] 72303840 512-byte hardware sectors (37020 MB)
May 27 20:51:55 thunder kernel: [   47.139842] sd 2:0:0:0: [sda] Write Protect is off
May 27 20:51:55 thunder kernel: [   47.139854] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May 27 20:51:55 thunder kernel: [   47.139856]  sda: sda1 sda2 < sda5 >
May 27 20:51:55 thunder kernel: [   47.160860] sd 2:0:0:0: [sda] Attached SCSI disk
May 27 20:51:55 thunder kernel: [   47.160916] sd 3:0:0:0: [sdb] 586114704 512-byte hardware sectors (300091 MB)
May 27 20:51:55 thunder kernel: [   47.160927] sd 3:0:0:0: [sdb] Write Protect is off
May 27 20:51:55 thunder kernel: [   47.160941] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May 27 20:51:55 thunder kernel: [   47.160976] sd 3:0:0:0: [sdb] 586114704 512-byte hardware sectors (300091 MB)
May 27 20:51:55 thunder kernel: [   47.160983] sd 3:0:0:0: [sdb] Write Protect is off
May 27 20:51:55 thunder kernel: [   47.160995] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May 27 20:51:55 thunder kernel: [   47.160997]  sdb: sdb2 < sdb5 sdb6 >
May 27 20:51:55 thunder kernel: [   47.197154] sd 3:0:0:0: [sdb] Attached SCSI disk
May 27 20:51:55 thunder kernel: [   47.197198] sd 4:0:0:0: [sdc] 625142448 512-byte hardware sectors (320073 MB)
May 27 20:51:55 thunder kernel: [   47.197205] sd 4:0:0:0: [sdc] Write Protect is off
May 27 20:51:55 thunder kernel: [   47.197218] sd 4:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May 27 20:51:55 thunder kernel: [   47.197245] sd 4:0:0:0: [sdc] 625142448 512-byte hardware sectors (320073 MB)
May 27 20:51:55 thunder kernel: [   47.197252] sd 4:0:0:0: [sdc] Write Protect is off
May 27 20:51:55 thunder kernel: [   47.197264] sd 4:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May 27 20:51:55 thunder kernel: [   47.197266]  sdc:
May 27 20:51:55 thunder kernel: [   47.210337] sd 4:0:0:0: [sdc] Attached SCSI disk
May 27 20:51:55 thunder kernel: [   47.210373] sd 5:0:0:0: [sdd] 625142448 512-byte hardware sectors (320073 MB)
May 27 20:51:55 thunder kernel: [   47.210380] sd 5:0:0:0: [sdd] Write Protect is off
May 27 20:51:55 thunder kernel: [   47.210393] sd 5:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May 27 20:51:55 thunder kernel: [   47.210419] sd 5:0:0:0: [sdd] 625142448 512-byte hardware sectors (320073 MB)
May 27 20:51:55 thunder kernel: [   47.210426] sd 5:0:0:0: [sdd] Write Protect is off
May 27 20:51:55 thunder kernel: [   47.210439] sd 5:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May 27 20:51:55 thunder kernel: [   47.210441]  sdd:
May 27 20:51:55 thunder kernel: [   47.228082] sd 5:0:0:0: [sdd] Attached SCSI disk
May 27 20:51:55 thunder kernel: [   47.228114] sd 6:0:0:0: [sde] 625142448 512-byte hardware sectors (320073 MB)
May 27 20:51:55 thunder kernel: [   47.228121] sd 6:0:0:0: [sde] Write Protect is off
May 27 20:51:55 thunder kernel: [   47.228133] sd 6:0:0:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May 27 20:51:55 thunder kernel: [   47.228157] sd 6:0:0:0: [sde] 625142448 512-byte hardware sectors (320073 MB)
May 27 20:51:55 thunder kernel: [   47.228163] sd 6:0:0:0: [sde] Write Protect is off
May 27 20:51:55 thunder kernel: [   47.228176] sd 6:0:0:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May 27 20:51:55 thunder kernel: [   47.228178]  sde:
May 27 20:51:55 thunder kernel: [   47.241079] sd 6:0:0:0: [sde] Attached SCSI disk
May 27 20:51:55 thunder kernel: [   47.241113] sd 7:0:0:0: [sdf] 625142448 512-byte hardware sectors (320073 MB)
May 27 20:51:55 thunder kernel: [   47.241119] sd 7:0:0:0: [sdf] Write Protect is off
May 27 20:51:55 thunder kernel: [   47.241132] sd 7:0:0:0: [sdf] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May 27 20:51:55 thunder kernel: [   47.241156] sd 7:0:0:0: [sdf] 625142448 512-byte hardware sectors (320073 MB)
May 27 20:51:55 thunder kernel: [   47.241163] sd 7:0:0:0: [sdf] Write Protect is off
May 27 20:51:55 thunder kernel: [   47.241175] sd 7:0:0:0: [sdf] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May 27 20:51:55 thunder kernel: [   47.241177]  sdf:
May 27 20:51:55 thunder kernel: [   47.258955] sd 7:0:0:0: [sdf] Attached SCSI disk
May 27 20:51:55 thunder kernel: [   47.258988] sd 8:0:0:0: [sdg] 625142448 512-byte hardware sectors (320073 MB)
May 27 20:51:55 thunder kernel: [   47.258995] sd 8:0:0:0: [sdg] Write Protect is off
May 27 20:51:55 thunder kernel: [   47.259008] sd 8:0:0:0: [sdg] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May 27 20:51:55 thunder kernel: [   47.259031] sd 8:0:0:0: [sdg] 625142448 512-byte hardware sectors (320073 MB)
May 27 20:51:55 thunder kernel: [   47.259038] sd 8:0:0:0: [sdg] Write Protect is off
May 27 20:51:55 thunder kernel: [   47.259050] sd 8:0:0:0: [sdg] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May 27 20:51:55 thunder kernel: [   47.259053]  sdg:
May 27 20:51:55 thunder kernel: [   47.274150] sd 8:0:0:0: [sdg] Attached SCSI disk
May 27 20:51:55 thunder kernel: [   47.427672] md: md0 stopped.
May 27 20:51:55 thunder kernel: [   47.524600] Attempting manual resume
May 27 20:51:55 thunder kernel: [   47.551551] kjournald starting.  Commit interval 5 seconds
May 27 20:51:55 thunder kernel: [   47.551561] EXT3-fs: mounted filesystem with ordered data mode.
May 27 20:51:55 thunder kernel: [   52.702199] md: md0 stopped.
May 27 20:51:55 thunder kernel: [   52.824471] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
May 27 20:51:55 thunder kernel: [   52.858004] shpchp: HPC vendor_id 1022 device_id 7460 ss_vid 0 ss_did 0
May 27 20:51:55 thunder kernel: [   52.858037] shpchp: HPC vendor_id 1022 device_id 7450 ss_vid 0 ss_did 0
May 27 20:51:55 thunder kernel: [   52.858047] shpchp: HPC vendor_id 1022 device_id 7450 ss_vid 0 ss_did 0
May 27 20:51:55 thunder kernel: [   52.858068] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
May 27 20:51:55 thunder kernel: [   52.929641] input: PC Speaker as /devices/platform/pcspkr/input/input4
May 27 20:51:55 thunder kernel: [   52.976422] AMD768 RNG detected
May 27 20:51:55 thunder kernel: [   52.986502] input: Power Button (FF) as /devices/virtual/input/input5
May 27 20:51:55 thunder kernel: [   53.013779] ACPI: Power Button (FF) [PWRF]
May 27 20:51:55 thunder kernel: [   53.013870] input: Power Button (CM) as /devices/virtual/input/input6
May 27 20:51:55 thunder kernel: [   53.041752] ACPI: Power Button (CM) [PWRB]
May 27 20:51:55 thunder kernel: [   53.383071] nvidia: module license 'NVIDIA' taints kernel.
May 27 20:51:55 thunder kernel: [   53.759081] ACPI: PCI Interrupt 0000:02:02.0[A] -> GSI 26 (level, low) -> IRQ 26
May 27 20:51:55 thunder kernel: [   53.759233] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  169.12  Thu Feb 14 17:51:09 PST 2008
May 27 20:51:55 thunder kernel: [  233.143004] lp: driver loaded but no devices found
May 27 20:51:55 thunder kernel: [  233.254625] Adding 1526132k swap on /dev/sda5.  Priority:-1 extents:1 across:1526132k
May 27 20:51:55 thunder kernel: [  233.783061] EXT3 FS on sda1, internal journal
May 27 20:51:55 thunder kernel: [  234.774668] ip_tables: (C) 2000-2006 Netfilter Core Team
May 27 20:51:55 thunder kernel: [  235.025641] No dock devices found.
May 27 20:51:55 thunder kernel: [  235.240111] powernow-k8: Found 2 AMD Opteron(tm) Processor 252 processors (2 cpu cores) (version 2.20.00)
May 27 20:51:55 thunder kernel: [  235.896085] ppdev: user-space parallel port driver
May 27 20:51:55 thunder kernel: [  235.972269] audit(1211935915.908:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5601 profile="/usr/sbin/cupsd" namespace="default"
May 27 20:51:55 thunder dhcdbd: Started up.
May 27 20:51:56 thunder kernel: [  236.991384] Bluetooth: Core ver 2.11
May 27 20:51:56 thunder kernel: [  236.991792] NET: Registered protocol family 31
May 27 20:51:56 thunder kernel: [  236.991794] Bluetooth: HCI device and connection manager initialized
May 27 20:51:56 thunder kernel: [  236.991811] Bluetooth: HCI socket layer initialized
May 27 20:51:56 thunder kernel: [  237.004919] Bluetooth: L2CAP ver 2.9
May 27 20:51:56 thunder kernel: [  237.004924] Bluetooth: L2CAP socket layer initialized
May 27 20:51:57 thunder kernel: [  237.087182] Bluetooth: RFCOMM socket layer initialized
May 27 20:51:57 thunder kernel: [  237.087199] Bluetooth: RFCOMM TTY layer initialized
May 27 20:51:57 thunder kernel: [  237.087201] Bluetooth: RFCOMM ver 1.8
May 27 20:51:57 thunder kernel: [  237.303364] usb 2-1.1: new full speed USB device using ohci_hcd and address 6
May 27 20:51:57 thunder kernel: [  237.418356] usb 2-1.1: configuration #1 chosen from 1 choice
May 27 20:51:57 thunder kernel: [  237.487396] Bluetooth: HCI USB driver ver 2.9
May 27 20:51:57 thunder kernel: [  237.490713] usbcore: registered new interface driver hci_usb
May 27 20:51:58 thunder dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
May 27 20:52:00 thunder kernel: [  240.149590] tg3: eth1: Link is up at 1000 Mbps, full duplex.
May 27 20:52:00 thunder kernel: [  240.149595] tg3: eth1: Flow control is on for TX and on for RX.
May 27 20:52:00 thunder dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
May 27 20:52:02 thunder kernel: [  242.347450] NET: Registered protocol family 17
May 27 20:52:03 thunder dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.host_name
May 27 20:52:03 thunder dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_domain
May 27 20:52:03 thunder dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_servers
May 27 20:52:03 thunder dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.interface_mtu
May 27 20:52:04 thunder kernel: [  244.800991] NET: Registered protocol family 10
May 27 20:52:04 thunder kernel: [  244.801302] lo: Disabled Privacy Extensions
May 27 20:52:04 thunder kernel: [  244.801771] ADDRCONF(NETDEV_UP): eth0: link is not ready
May 27 20:52:04 thunder kernel: [  244.802342] ADDRCONF(NETDEV_UP): eth2: link is not ready
May 27 20:52:13 thunder kernel: [  253.769021] usb 2-1: USB disconnect, address 2
May 27 20:52:13 thunder kernel: [  253.769026] usb 2-1.1: USB disconnect, address 6
May 27 20:52:13 thunder kernel: [  254.025499] usb 2-1.2: USB disconnect, address 4
May 27 20:52:14 thunder kernel: [  254.081348] usb 2-1.3: USB disconnect, address 5
May 27 20:52:14 thunder kernel: [  254.452585] usb 2-1: new full speed USB device using ohci_hcd and address 7
May 27 20:52:14 thunder kernel: [  254.665289] usb 2-1: configuration #1 chosen from 1 choice
May 27 20:52:14 thunder kernel: [  254.668220] hub 2-1:1.0: USB hub found
May 27 20:52:14 thunder kernel: [  254.671191] hub 2-1:1.0: 3 ports detected
May 27 20:52:14 thunder kernel: [  255.000900] usb 2-1.2: new full speed USB device using ohci_hcd and address 8
May 27 20:52:15 thunder kernel: [  255.116878] usb 2-1.2: configuration #1 chosen from 1 choice
May 27 20:52:15 thunder kernel: [  255.132846] input: Logitech Logitech BT Mini-Receiver as /devices/pci0000:00/0000:00:06.0/0000:03:00.1/usb2/2-1/2-1.2/2-1.2:1.0/input/input7
May 27 20:52:15 thunder kernel: [  255.167739] input,hidraw1: USB HID v1.11 Keyboard [Logitech Logitech BT Mini-Receiver] on usb-0000:03:00.1-1.2
May 27 20:52:15 thunder kernel: [  255.380563] usb 2-1.3: new full speed USB device using ohci_hcd and address 9
May 27 20:52:15 thunder kernel: [  255.496556] usb 2-1.3: configuration #1 chosen from 1 choice
May 27 20:52:15 thunder kernel: [  255.517535] input: Logitech Logitech BT Mini-Receiver as /devices/pci0000:00/0000:00:06.0/0000:03:00.1/usb2/2-1/2-1.3/2-1.3:1.0/input/input8
May 27 20:52:15 thunder kernel: [  255.611213] input,hiddev96,hidraw2: USB HID v1.11 Mouse [Logitech Logitech BT Mini-Receiver] on usb-0000:03:00.1-1.3
```

```
syslog logfile
May 27 20:51:55 thunder syslogd 1.5.0#1ubuntu1: restart.
May 27 20:51:55 thunder kernel: Inspecting /boot/System.map-2.6.24-16-generic
May 27 20:51:55 thunder kernel: Loaded 28313 symbols from /boot/System.map-2.6.24-16-generic.
May 27 20:51:55 thunder kernel: Symbols match kernel version 2.6.24.
May 27 20:51:55 thunder kernel: Loaded 28168 symbols from 74 modules.
May 27 20:51:55 thunder kernel: [    0.000000] Linux version 2.6.24-16-generic (buildd@yellow) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 12:47:45 UTC 2008 (Ubuntu 2.6.24-16.30-generic)
May 27 20:51:55 thunder kernel: [    0.000000] Command line: root=UUID=39b63fbe-33e1-4bf8-8a80-12e86eb6af72 ro quiet splash
May 27 20:51:55 thunder kernel: [    0.000000] BIOS-provided physical RAM map:
May 27 20:51:55 thunder kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
May 27 20:51:55 thunder kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
May 27 20:51:55 thunder kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
May 27 20:51:55 thunder kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000daff0000 (usable)
May 27 20:51:55 thunder kernel: [    0.000000]  BIOS-e820: 00000000daff0000 - 00000000dafff000 (ACPI data)
May 27 20:51:55 thunder kernel: [    0.000000]  BIOS-e820: 00000000dafff000 - 00000000db000000 (ACPI NVS)
May 27 20:51:55 thunder kernel: [    0.000000]  BIOS-e820: 00000000ff780000 - 0000000100000000 (reserved)
May 27 20:51:55 thunder kernel: [    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
May 27 20:51:55 thunder kernel: [    0.000000] Entering add_active_range(0, 256, 897008) 1 entries of 3200 used
May 27 20:51:55 thunder kernel: [    0.000000] end_pfn_map = 1048576
May 27 20:51:55 thunder kernel: [    0.000000] DMI 2.3 present.
May 27 20:51:55 thunder kernel: [    0.000000] ACPI: RSDP signature @ 0xFFFF8100000F6F20 checksum 0
May 27 20:51:55 thunder kernel: [    0.000000] ACPI: RSDP 000F6F20, 0014 (r0 ACPIAM)
May 27 20:51:55 thunder kernel: [    0.000000] ACPI: RSDT DAFF0000, 0038 (r1 A M I  OEMRSDT   7000626 MSFT       97)
May 27 20:51:55 thunder kernel: [    0.000000] ACPI: FACP DAFF0200, 0081 (r1 A M I  OEMFACP   7000626 MSFT       97)
May 27 20:51:55 thunder kernel: [    0.000000] ACPI: DSDT DAFF0410, 3751 (r1  0AAAA 0AAAA000        0 INTL  2002026)
May 27 20:51:55 thunder kernel: [    0.000000] ACPI: FACS DAFFF000, 0040
May 27 20:51:55 thunder kernel: [    0.000000] ACPI: APIC DAFF0380, 0084 (r1 A M I  OEMAPIC   7000626 MSFT       97)
May 27 20:51:55 thunder kernel: [    0.000000] ACPI: OEMB DAFFF040, 0041 (r1 A M I  OEMBIOS   7000626 MSFT       97)
May 27 20:51:55 thunder kernel: [    0.000000] ACPI: SRAT DAFF3B70, 0110 (r1 A M I  OEMSRAT   7000626 MSFT       97)
May 27 20:51:55 thunder kernel: [    0.000000] ACPI: ASF! DAFF3C80, 0086 (r1 AMIASF AMDSTRET        1 INTL  2002026)
May 27 20:51:55 thunder kernel: [    0.000000] SRAT: PXM 0 -> APIC 0 -> Node 0
May 27 20:51:55 thunder kernel: [    0.000000] SRAT: PXM 1 -> APIC 1 -> Node 1
May 27 20:51:55 thunder kernel: [    0.000000] SRAT: Node 0 PXM 0 100000-80000000
May 27 20:51:55 thunder kernel: [    0.000000] Entering add_active_range(0, 256, 524288) 0 entries of 3200 used
May 27 20:51:55 thunder kernel: [    0.000000] SRAT: Node 1 PXM 1 80000000-db000000
May 27 20:51:55 thunder kernel: [    0.000000] Entering add_active_range(1, 524288, 897008) 1 entries of 3200 used
May 27 20:51:55 thunder kernel: [    0.000000] SRAT: Node 1 PXM 1 80000000-100000000
May 27 20:51:55 thunder kernel: [    0.000000] Entering add_active_range(1, 524288, 897008) 2 entries of 3200 used
May 27 20:51:55 thunder kernel: [    0.000000] SRAT: Node 0 PXM 0 0-80000000
May 27 20:51:55 thunder kernel: [    0.000000] Entering add_active_range(0, 0, 159) 2 entries of 3200 used
May 27 20:51:55 thunder kernel: [    0.000000] Entering add_active_range(0, 256, 524288) 3 entries of 3200 used
May 27 20:51:55 thunder kernel: [    0.000000] NUMA: Using 31 for the hash shift.
May 27 20:51:55 thunder kernel: [    0.000000] Bootmem setup node 0 0000000000000000-0000000080000000
May 27 20:51:55 thunder kernel: [    0.000000] Bootmem setup node 1 0000000080000000-00000000daff0000
May 27 20:51:55 thunder kernel: [    0.000000] Zone PFN ranges:
May 27 20:51:55 thunder kernel: [    0.000000]   DMA             0 ->     4096
May 27 20:51:55 thunder kernel: [    0.000000]   DMA32        4096 ->  1048576
May 27 20:51:55 thunder kernel: [    0.000000]   Normal    1048576 ->  1048576
May 27 20:51:55 thunder kernel: [    0.000000] Movable zone start PFN for each node
May 27 20:51:55 thunder kernel: [    0.000000] early_node_map[3] active PFN ranges
May 27 20:51:55 thunder kernel: [    0.000000]     0:        0 ->      159
May 27 20:51:55 thunder kernel: [    0.000000]     0:      256 ->   524288
May 27 20:51:55 thunder kernel: [    0.000000]     1:   524288 ->   897008
May 27 20:51:55 thunder kernel: [    0.000000] On node 0 totalpages: 524191
May 27 20:51:55 thunder kernel: [    0.000000]   DMA zone: 56 pages used for memmap
May 27 20:51:55 thunder kernel: [    0.000000]   DMA zone: 1209 pages reserved
May 27 20:51:55 thunder kernel: [    0.000000]   DMA zone: 2734 pages, LIFO batch:0
May 27 20:51:55 thunder kernel: [    0.000000]   DMA32 zone: 7112 pages used for memmap
May 27 20:51:55 thunder kernel: [    0.000000]   DMA32 zone: 513080 pages, LIFO batch:31
May 27 20:51:55 thunder kernel: [    0.000000]   Normal zone: 0 pages used for memmap
May 27 20:51:55 thunder kernel: [    0.000000]   Movable zone: 0 pages used for memmap
May 27 20:51:55 thunder kernel: [    0.000000] On node 1 totalpages: 372720
May 27 20:51:55 thunder kernel: [    0.000000]   DMA zone: 0 pages used for memmap
May 27 20:51:55 thunder kernel: [    0.000000]   DMA32 zone: 5095 pages used for memmap
May 27 20:51:55 thunder kernel: [    0.000000]   DMA32 zone: 367625 pages, LIFO batch:31
May 27 20:51:55 thunder kernel: [    0.000000]   Normal zone: 0 pages used for memmap
May 27 20:51:55 thunder kernel: [    0.000000]   Movable zone: 0 pages used for memmap
May 27 20:51:55 thunder kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
May 27 20:51:55 thunder kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
May 27 20:51:55 thunder kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
May 27 20:51:55 thunder kernel: [    0.000000] Processor #0 (Bootup-CPU)
May 27 20:51:55 thunder kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
May 27 20:51:55 thunder kernel: [    0.000000] Processor #1
May 27 20:51:55 thunder kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
May 27 20:51:55 thunder kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
May 27 20:51:55 thunder kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
May 27 20:51:55 thunder kernel: [    0.000000] IOAPIC[0]: apic_id 2, address 0xfec00000, GSI 0-23
May 27 20:51:55 thunder kernel: [    0.000000] ACPI: IOAPIC (id[0x03] address[0xfebff000] gsi_base[24])
May 27 20:51:55 thunder kernel: [    0.000000] IOAPIC[1]: apic_id 3, address 0xfebff000, GSI 24-27
May 27 20:51:55 thunder kernel: [    0.000000] ACPI: IOAPIC (id[0x04] address[0xfebfe000] gsi_base[28])
May 27 20:51:55 thunder kernel: [    0.000000] IOAPIC[2]: apic_id 4, address 0xfebfe000, GSI 28-31
May 27 20:51:55 thunder kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
May 27 20:51:55 thunder kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
May 27 20:51:55 thunder kernel: [    0.000000] ACPI: IRQ0 used by override.
May 27 20:51:55 thunder kernel: [    0.000000] ACPI: IRQ2 used by override.
May 27 20:51:55 thunder kernel: [    0.000000] ACPI: IRQ9 used by override.
May 27 20:51:55 thunder kernel: [    0.000000] Setting APIC routing to flat
May 27 20:51:55 thunder kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
May 27 20:51:55 thunder kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
May 27 20:51:55 thunder kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e0000
May 27 20:51:55 thunder kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 0000000000100000
May 27 20:51:55 thunder kernel: [    0.000000] Allocating PCI resources starting at dc000000 (gap: db000000:24780000)
May 27 20:51:55 thunder kernel: [    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
May 27 20:51:55 thunder kernel: [    0.000000] PERCPU: Allocating 34656 bytes of per cpu data
May 27 20:51:55 thunder kernel: [    0.000000] Built 2 zonelists in Node order, mobility grouping on.  Total pages: 883439
May 27 20:51:55 thunder kernel: [    0.000000] Policy zone: DMA32
May 27 20:51:55 thunder kernel: [    0.000000] Kernel command line: root=UUID=39b63fbe-33e1-4bf8-8a80-12e86eb6af72 ro quiet splash
May 27 20:51:55 thunder kernel: [    0.000000] Initializing CPU#0
May 27 20:51:55 thunder kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
May 27 20:51:55 thunder kernel: [    0.000000] TSC calibrated against PM_TIMER
May 27 20:51:55 thunder kernel: [   38.398079] Marking TSC unstable due to TSCs unsynchronized
May 27 20:51:55 thunder kernel: [   38.398080] time.c: Detected 2590.564 MHz processor.
May 27 20:51:55 thunder kernel: [   38.400498] Console: colour VGA+ 80x25
May 27 20:51:55 thunder kernel: [   38.400501] console [tty0] enabled
May 27 20:51:55 thunder kernel: [   38.400514] Checking aperture...
May 27 20:51:55 thunder kernel: [   38.400516] CPU 0: aperture @ 4180000000 size 32 MB
May 27 20:51:55 thunder kernel: [   38.400517] Aperture too small (32 MB)
May 27 20:51:55 thunder kernel: [   38.407211] No AGP bridge found
May 27 20:51:55 thunder kernel: [   38.437885] Memory: 3525612k/3588032k available (2466k kernel code, 62032k reserved, 1309k data, 316k init)
May 27 20:51:55 thunder kernel: [   38.437915] SLUB: Genslabs=12, HWalign=64, Order=0-1, MinObjects=4, CPUs=4, Nodes=2
May 27 20:51:55 thunder kernel: [   38.516136] Calibrating delay using timer specific routine.. 5224.63 BogoMIPS (lpj=10449273)
May 27 20:51:55 thunder kernel: [   38.516168] Security Framework initialized
May 27 20:51:55 thunder kernel: [   38.516172] SELinux:  Disabled at boot.
May 27 20:51:55 thunder kernel: [   38.516183] AppArmor: AppArmor initialized
May 27 20:51:55 thunder kernel: [   38.516185] Failure registering capabilities with primary security module.
May 27 20:51:55 thunder kernel: [   38.516464] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
May 27 20:51:55 thunder kernel: [   38.519068] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
May 27 20:51:55 thunder kernel: [   38.520281] Mount-cache hash table entries: 256
May 27 20:51:55 thunder kernel: [   38.520486] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
May 27 20:51:55 thunder kernel: [   38.520487] CPU: L2 Cache: 1024K (64 bytes/line)
May 27 20:51:55 thunder kernel: [   38.520489] CPU 0/0 -> Node 0
May 27 20:51:55 thunder kernel: [   38.520506] SMP alternatives: switching to UP code
May 27 20:51:55 thunder kernel: [   38.520946] Early unpacking initramfs... done
May 27 20:51:55 thunder kernel: [   38.770603] ACPI: Core revision 20070126
May 27 20:51:55 thunder kernel: [   38.770639] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
May 27 20:51:55 thunder kernel: [   38.812943] Using local APIC timer interrupts.
May 27 20:51:55 thunder kernel: [   38.851521] APIC timer calibration result 12454627
May 27 20:51:55 thunder kernel: [   38.851522] Detected 12.454 MHz APIC timer.
May 27 20:51:55 thunder kernel: [   38.851604] SMP alternatives: switching to SMP code
May 27 20:51:55 thunder kernel: [   38.851965] Booting processor 1/2 APIC 0x1
May 27 20:51:55 thunder kernel: [   38.862125] Initializing CPU#1
May 27 20:51:55 thunder kernel: [   38.939472] Calibrating delay using timer specific routine.. 5181.15 BogoMIPS (lpj=10362319)
May 27 20:51:55 thunder kernel: [   38.939478] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
May 27 20:51:55 thunder kernel: [   38.939479] CPU: L2 Cache: 1024K (64 bytes/line)
May 27 20:51:55 thunder kernel: [   38.939482] CPU 1/1 -> Node 1
May 27 20:51:55 thunder kernel: [   38.939589] AMD Opteron(tm) Processor 252 stepping 01
May 27 20:51:55 thunder kernel: [   38.939612] Brought up 2 CPUs
May 27 20:51:55 thunder kernel: [   38.939738] CPU0 attaching sched-domain:
May 27 20:51:55 thunder kernel: [   38.939740]  domain 0: span 03
May 27 20:51:55 thunder kernel: [   38.939741]   groups: 01 02
May 27 20:51:55 thunder kernel: [   38.939743] CPU1 attaching sched-domain:
May 27 20:51:55 thunder kernel: [   38.939744]  domain 0: span 03
May 27 20:51:55 thunder kernel: [   38.939746]   groups: 02 01
May 27 20:51:55 thunder kernel: [   38.939989] net_namespace: 120 bytes
May 27 20:51:55 thunder kernel: [   38.940340] Time:  0:48:38  Date: 05/28/08
May 27 20:51:55 thunder kernel: [   38.940370] NET: Registered protocol family 16
May 27 20:51:55 thunder kernel: [   38.940547] ACPI: bus type pci registered
May 27 20:51:55 thunder kernel: [   38.940612] PCI: Using configuration type 1
May 27 20:51:55 thunder kernel: [   38.945054] ACPI: EC: Look up EC in DSDT
May 27 20:51:55 thunder kernel: [   38.947562] ACPI: Interpreter enabled
May 27 20:51:55 thunder kernel: [   38.947564] ACPI: (supports S0 S1 S4 S5)
May 27 20:51:55 thunder kernel: [   38.947574] ACPI: Using IOAPIC for interrupt routing
May 27 20:51:55 thunder kernel: [   38.951569] ACPI: PCI Root Bridge [PCI0] (0000:00)
May 27 20:51:55 thunder kernel: [   38.952590] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
May 27 20:51:55 thunder kernel: [   38.952647] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
May 27 20:51:55 thunder kernel: [   38.952715] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.GOLA._PRT]
May 27 20:51:55 thunder kernel: [   38.952798] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.GOLB._PRT]
May 27 20:51:55 thunder kernel: [   38.954688] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
May 27 20:51:55 thunder kernel: [   38.954770] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
May 27 20:51:55 thunder kernel: [   38.954849] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
May 27 20:51:55 thunder kernel: [   38.954928] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
May 27 20:51:55 thunder kernel: [   38.955032] Linux Plug and Play Support v0.97 (c) Adam Belay
May 27 20:51:55 thunder kernel: [   38.955070] pnp: PnP ACPI init
May 27 20:51:55 thunder kernel: [   38.955075] ACPI: bus type pnp registered
May 27 20:51:55 thunder kernel: [   38.957143] pnp: PnP ACPI: found 12 devices
May 27 20:51:55 thunder kernel: [   38.957144] ACPI: ACPI bus type pnp unregistered
May 27 20:51:55 thunder kernel: [   38.957374] PCI: Using ACPI for IRQ routing
May 27 20:51:55 thunder kernel: [   38.957376] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
May 27 20:51:55 thunder kernel: [   38.983456] NET: Registered protocol family 8
May 27 20:51:55 thunder kernel: [   38.983458] NET: Registered protocol family 20
May 27 20:51:55 thunder kernel: [   38.983577] AppArmor: AppArmor Filesystem Enabled
May 27 20:51:55 thunder kernel: [   38.995474] system 00:07: ioport range 0x680-0x6ff has been reserved
May 27 20:51:55 thunder kernel: [   38.995477] system 00:07: ioport range 0x295-0x296 has been reserved
May 27 20:51:55 thunder kernel: [   38.995483] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
May 27 20:51:55 thunder kernel: [   38.995485] system 00:08: ioport range 0x1000-0x10bf has been reserved
May 27 20:51:55 thunder kernel: [   38.995487] system 00:08: ioport range 0x10e0-0x10ff has been reserved
May 27 20:51:55 thunder kernel: [   38.995489] system 00:08: ioport range 0x10c0-0x10df has been reserved
May 27 20:51:55 thunder kernel: [   38.995492] system 00:08: ioport range 0xde00-0xde7f has been reserved
May 27 20:51:55 thunder kernel: [   38.995494] system 00:08: ioport range 0xde80-0xdeff has been reserved
May 27 20:51:55 thunder kernel: [   38.995498] system 00:0a: ioport range 0xca0-0xcaf has been reserved
May 27 20:51:55 thunder kernel: [   38.995500] system 00:0a: iomem range 0xfec00000-0xfec00fff has been reserved
May 27 20:51:55 thunder kernel: [   38.995503] system 00:0a: iomem range 0xfee00000-0xfee00fff could not be reserved
May 27 20:51:55 thunder kernel: [   38.995505] system 00:0a: iomem range 0xfff80000-0xffffffff could not be reserved
May 27 20:51:55 thunder kernel: [   38.995508] system 00:0a: iomem range 0xff780000-0xff7fffff could not be reserved
May 27 20:51:55 thunder kernel: [   38.995512] system 00:0b: iomem range 0x0-0x9ffff could not be reserved
May 27 20:51:55 thunder kernel: [   38.995514] system 00:0b: iomem range 0xc0000-0xdffff has been reserved
May 27 20:51:55 thunder kernel: [   38.995517] system 00:0b: iomem range 0xe0000-0xfffff could not be reserved
May 27 20:51:55 thunder kernel: [   38.995519] system 00:0b: iomem range 0x100000-0xdaffffff could not be reserved
May 27 20:51:55 thunder kernel: [   38.995521] system 00:0b: iomem range 0x0-0x0 could not be reserved
May 27 20:51:55 thunder kernel: [   38.996006] PCI: Bridge: 0000:00:06.0
May 27 20:51:55 thunder kernel: [   38.996008]   IO window: b000-bfff
May 27 20:51:55 thunder kernel: [   38.996012]   MEM window: fea00000-feafffff
May 27 20:51:55 thunder kernel: [   38.996015]   PREFETCH window: disabled.
May 27 20:51:55 thunder kernel: [   38.996019] PCI: Bridge: 0000:00:0a.0
May 27 20:51:55 thunder kernel: [   38.996020]   IO window: disabled.
May 27 20:51:55 thunder kernel: [   38.996023]   MEM window: fc900000-fe9fffff
May 27 20:51:55 thunder kernel: [   38.996026]   PREFETCH window: db500000-fb5fffff
May 27 20:51:55 thunder kernel: [   38.996029] PCI: Bridge: 0000:00:0b.0
May 27 20:51:55 thunder kernel: [   38.996031]   IO window: a000-afff
May 27 20:51:55 thunder kernel: [   38.996033]   MEM window: fb700000-fc8fffff
May 27 20:51:55 thunder kernel: [   38.996035]   PREFETCH window: db400000-db4fffff
May 27 20:51:55 thunder kernel: [   38.996108] NET: Registered protocol family 2
May 27 20:51:55 thunder kernel: [   38.999431] Time: acpi_pm clocksource has been installed.
May 27 20:51:55 thunder kernel: [   38.999443] Switched to high resolution mode on CPU 0
May 27 20:51:55 thunder kernel: [   38.999573] Switched to high resolution mode on CPU 1
May 27 20:51:55 thunder kernel: [   39.031523] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
May 27 20:51:55 thunder kernel: [   39.032696] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
May 27 20:51:55 thunder kernel: [   39.037800] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
May 27 20:51:55 thunder kernel: [   39.038344] TCP: Hash tables configured (established 524288 bind 65536)
May 27 20:51:55 thunder kernel: [   39.038347] TCP reno registered
May 27 20:51:55 thunder kernel: [   39.047531] checking if image is initramfs... it is
May 27 20:51:55 thunder kernel: [   39.529379] Freeing initrd memory: 7782k freed
May 27 20:51:55 thunder kernel: [   39.534309] audit: initializing netlink socket (disabled)
May 27 20:51:55 thunder kernel: [   39.534326] audit(1211935719.104:1): initialized
May 27 20:51:55 thunder kernel: [   39.536336] VFS: Disk quotas dquot_6.5.1
May 27 20:51:55 thunder kernel: [   39.536399] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
May 27 20:51:55 thunder kernel: [   39.536506] io scheduler noop registered
May 27 20:51:55 thunder kernel: [   39.536507] io scheduler anticipatory registered
May 27 20:51:55 thunder kernel: [   39.536509] io scheduler deadline registered
May 27 20:51:55 thunder kernel: [   39.536600] io scheduler cfq registered (default)
May 27 20:51:55 thunder kernel: [   39.536609] PCI: MSI quirk detected. PCI_BUS_FLAGS_NO_MSI set for 0000:00:0a.0 subordinate bus.
May 27 20:51:55 thunder kernel: [   39.536611] AMD8131 rev 12 detected, disabling PCI-X MMRBC
May 27 20:51:55 thunder kernel: [   39.536614] PCI: MSI quirk detected. PCI_BUS_FLAGS_NO_MSI set for 0000:00:0b.0 subordinate bus.
May 27 20:51:55 thunder kernel: [   39.536616] AMD8131 rev 12 detected, disabling PCI-X MMRBC
May 27 20:51:55 thunder kernel: [   39.591173] PCI: Firmware left 0000:03:08.0 e100 interrupts enabled, disabling
May 27 20:51:55 thunder kernel: [   39.591189] Boot video device is 0000:02:02.0
May 27 20:51:55 thunder kernel: [   39.617100] Real Time Clock Driver v1.12ac
May 27 20:51:55 thunder kernel: [   39.617184] hpet_acpi_add: no address or irqs in _CRS
May 27 20:51:55 thunder kernel: [   39.617199] Linux agpgart interface v0.102
May 27 20:51:55 thunder kernel: [   39.617201] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
May 27 20:51:55 thunder kernel: [   39.617323] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
May 27 20:51:55 thunder kernel: [   39.617447] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
May 27 20:51:55 thunder kernel: [   39.617843] 00:05: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
May 27 20:51:55 thunder kernel: [   39.618017] 00:06: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
May 27 20:51:55 thunder kernel: [   39.618907] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
May 27 20:51:55 thunder kernel: [   39.618962] input: Macintosh mouse button emulation as /devices/virtual/input/input0
May 27 20:51:55 thunder kernel: [   39.619270] PNP: No PS/2 controller found. Probing ports directly.
May 27 20:51:55 thunder kernel: [   39.621358] serio: i8042 KBD port at 0x60,0x64 irq 1
May 27 20:51:55 thunder kernel: [   39.621365] serio: i8042 AUX port at 0x60,0x64 irq 12
May 27 20:51:55 thunder kernel: [   39.639606] mice: PS/2 mouse device common for all mice
May 27 20:51:55 thunder kernel: [   39.639648] cpuidle: using governor ladder
May 27 20:51:55 thunder kernel: [   39.639650] cpuidle: using governor menu
May 27 20:51:55 thunder kernel: [   39.639807] NET: Registered protocol family 1
May 27 20:51:55 thunder kernel: [   39.639867] registered taskstats version 1
May 27 20:51:55 thunder kernel: [   39.639980]   Magic number: 8:880:810
May 27 20:51:55 thunder kernel: [   39.640065]   hash matches device ptys4
May 27 20:51:55 thunder kernel: [   39.640105] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
May 27 20:51:55 thunder kernel: [   39.640107] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
May 27 20:51:55 thunder kernel: [   39.640109] EDD information not available.
May 27 20:51:55 thunder kernel: [   39.640117] Freeing unused kernel memory: 316k freed
May 27 20:51:55 thunder kernel: [   40.825509] fuse init (API version 7.9)
May 27 20:51:55 thunder kernel: [   40.840124] ACPI: Processor [CPU1] (supports 8 throttling states)
May 27 20:51:55 thunder kernel: [   40.840158] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
May 27 20:51:55 thunder kernel: [   40.840167] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
May 27 20:51:55 thunder kernel: [   40.853953] md: linear personality registered for level -1
May 27 20:51:55 thunder kernel: [   40.857444] md: multipath personality registered for level -4
May 27 20:51:55 thunder kernel: [   40.860704] md: raid0 personality registered for level 0
May 27 20:51:55 thunder kernel: [   40.864301] md: raid1 personality registered for level 1
May 27 20:51:55 thunder kernel: [   40.867347] xor: automatically using best checksumming function: generic_sse
May 27 20:51:55 thunder kernel: [   40.885996]    generic_sse:  8302.000 MB/sec
May 27 20:51:55 thunder kernel: [   40.885998] xor: using function: generic_sse (8302.000 MB/sec)
May 27 20:51:55 thunder kernel: [   40.886507] async_tx: api initialized (async)
May 27 20:51:55 thunder kernel: [   40.953950] raid6: int64x1   2604 MB/s
May 27 20:51:55 thunder kernel: [   41.021909] raid6: int64x2   3208 MB/s
May 27 20:51:55 thunder kernel: [   41.089859] raid6: int64x4   3330 MB/s
May 27 20:51:55 thunder kernel: [   41.157804] raid6: int64x8   2588 MB/s
May 27 20:51:55 thunder kernel: [   41.225754] raid6: sse2x1    3218 MB/s
May 27 20:51:55 thunder kernel: [   41.293694] raid6: sse2x2    4179 MB/s
May 27 20:51:55 thunder kernel: [   41.361650] raid6: sse2x4    4720 MB/s
May 27 20:51:55 thunder kernel: [   41.361652] raid6: using algorithm sse2x4 (4720 MB/s)
May 27 20:51:55 thunder kernel: [   41.361654] md: raid6 personality registered for level 6
May 27 20:51:55 thunder kernel: [   41.361655] md: raid5 personality registered for level 5
May 27 20:51:55 thunder kernel: [   41.361656] md: raid4 personality registered for level 4
May 27 20:51:55 thunder kernel: [   41.381175] md: raid10 personality registered for level 10
May 27 20:51:55 thunder kernel: [   41.519507] SCSI subsystem initialized
May 27 20:51:55 thunder kernel: [   41.532610] libata version 3.00 loaded.
May 27 20:51:55 thunder kernel: [   41.537410] pata_amd 0000:00:07.1: version 0.3.10
May 27 20:51:55 thunder kernel: [   41.537794] scsi0 : pata_amd
May 27 20:51:55 thunder kernel: [   41.537830] scsi1 : pata_amd
May 27 20:51:55 thunder kernel: [   41.538179] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
May 27 20:51:55 thunder kernel: [   41.538181] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
May 27 20:51:55 thunder kernel: [   41.564915] usbcore: registered new interface driver usbfs
May 27 20:51:55 thunder kernel: [   41.564934] usbcore: registered new interface driver hub
May 27 20:51:55 thunder kernel: [   41.564959] usbcore: registered new device driver usb
May 27 20:51:55 thunder kernel: [   41.565824] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
May 27 20:51:55 thunder kernel: [   41.587090] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k4-NAPI
May 27 20:51:55 thunder kernel: [   41.587093] e100: Copyright(c) 1999-2006 Intel Corporation
May 27 20:51:55 thunder kernel: [   41.857625] ata1.00: ATAPI: TDK DVDRW1280B, T7S4, max UDMA/33
May 27 20:51:55 thunder kernel: [   42.029440] ata1.00: configured for UDMA/33
May 27 20:51:55 thunder kernel: [   42.197126] scsi 0:0:0:0: CD-ROM            TDK      DVDRW1280B       T7S4 PQ: 0 ANSI: 5
May 27 20:51:55 thunder kernel: [   42.197303] ACPI: PCI Interrupt 0000:03:00.0[D] -> GSI 19 (level, low) -> IRQ 19
May 27 20:51:55 thunder kernel: [   42.197572] ohci_hcd 0000:03:00.0: OHCI Host Controller
May 27 20:51:55 thunder kernel: [   42.197785] ohci_hcd 0000:03:00.0: new USB bus registered, assigned bus number 1
May 27 20:51:55 thunder kernel: [   42.197808] ohci_hcd 0000:03:00.0: irq 19, io mem 0xfeafc000
May 27 20:51:55 thunder kernel: [   42.204279] Driver 'sr' needs updating - please use bus_type methods
May 27 20:51:55 thunder kernel: [   42.209501] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
May 27 20:51:55 thunder kernel: [   42.209507] Uniform CD-ROM driver Revision: 3.20
May 27 20:51:55 thunder kernel: [   42.209564] sr 0:0:0:0: Attached scsi CD-ROM sr0
May 27 20:51:55 thunder kernel: [   42.212454] sr 0:0:0:0: Attached scsi generic sg0 type 5
May 27 20:51:55 thunder kernel: [   42.259181] usb usb1: configuration #1 chosen from 1 choice
May 27 20:51:55 thunder kernel: [   42.259202] hub 1-0:1.0: USB hub found
May 27 20:51:55 thunder kernel: [   42.259211] hub 1-0:1.0: 3 ports detected
May 27 20:51:55 thunder kernel: [   42.361020] ACPI: PCI Interrupt 0000:03:00.1[D] -> GSI 19 (level, low) -> IRQ 19
May 27 20:51:55 thunder kernel: [   42.361258] ohci_hcd 0000:03:00.1: OHCI Host Controller
May 27 20:51:55 thunder kernel: [   42.361318] ohci_hcd 0000:03:00.1: new USB bus registered, assigned bus number 2
May 27 20:51:55 thunder kernel: [   42.361334] ohci_hcd 0000:03:00.1: irq 19, io mem 0xfeafd000
May 27 20:51:55 thunder kernel: [   42.419045] usb usb2: configuration #1 chosen from 1 choice
May 27 20:51:55 thunder kernel: [   42.419064] hub 2-0:1.0: USB hub found
May 27 20:51:55 thunder kernel: [   42.419072] hub 2-0:1.0: 3 ports detected
May 27 20:51:55 thunder kernel: [   42.521054] ACPI: PCI Interrupt 0000:03:08.0[A] -> GSI 18 (level, low) -> IRQ 18
May 27 20:51:55 thunder kernel: [   42.600207] e100: eth0: e100_probe: addr 0xfeafb000, irq 18, MAC addr 00:e0:81:30:52:08
May 27 20:51:55 thunder kernel: [   42.600319] tg3.c:v3.86 (November 9, 2007)
May 27 20:51:55 thunder kernel: [   42.600343] ACPI: PCI Interrupt 0000:02:09.0[A] -> GSI 24 (level, low) -> IRQ 24
May 27 20:51:55 thunder kernel: [   42.616818] eth1: Tigon3 [partno(BCM95704A7) rev 2003 PHY(5704)] (PCI:33MHz:64-bit) 10/100/1000Base-T Ethernet 00:e0:81:30:52:38
May 27 20:51:55 thunder kernel: [   42.616824] eth1: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[1] TSOcap[1]
May 27 20:51:55 thunder kernel: [   42.616826] eth1: dma_rwctrl[763f0000] dma_mask[64-bit]
May 27 20:51:55 thunder kernel: [   42.616856] ACPI: PCI Interrupt 0000:02:09.1[B] -> GSI 25 (level, low) -> IRQ 25
May 27 20:51:55 thunder kernel: [   42.643682] eth2: Tigon3 [partno(BCM95704A7) rev 2003 PHY(5704)] (PCI:33MHz:64-bit) 10/100/1000Base-T Ethernet 00:e0:81:30:52:39
May 27 20:51:55 thunder kernel: [   42.643688] eth2: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[1] TSOcap[1]
May 27 20:51:55 thunder kernel: [   42.643689] eth2: dma_rwctrl[763f0000] dma_mask[64-bit]
May 27 20:51:55 thunder kernel: [   42.644535] sata_mv 0000:01:03.0: version 1.01
May 27 20:51:55 thunder kernel: [   42.644599] ACPI: PCI Interrupt 0000:01:03.0[A] -> GSI 28 (level, low) -> IRQ 28
May 27 20:51:55 thunder kernel: [   42.648130] sata_mv 0000:01:03.0: Gen-II 32 slots 8 ports SCSI mode IRQ via INTx
May 27 20:51:55 thunder kernel: [   42.648259] scsi2 : sata_mv
May 27 20:51:55 thunder kernel: [   42.648311] scsi3 : sata_mv
May 27 20:51:55 thunder kernel: [   42.648755] scsi4 : sata_mv
May 27 20:51:55 thunder kernel: [   42.648786] scsi5 : sata_mv
May 27 20:51:55 thunder kernel: [   42.648812] scsi6 : sata_mv
May 27 20:51:55 thunder kernel: [   42.648837] scsi7 : sata_mv
May 27 20:51:55 thunder kernel: [   42.648863] scsi8 : sata_mv
May 27 20:51:55 thunder kernel: [   42.648889] scsi9 : sata_mv
May 27 20:51:55 thunder kernel: [   42.648911] ata3: SATA max UDMA/133 mmio m1048576@0xfc800000 port 0xfc822000 irq 28
May 27 20:51:55 thunder kernel: [   42.648914] ata4: SATA max UDMA/133 mmio m1048576@0xfc800000 port 0xfc824000 irq 28
May 27 20:51:55 thunder kernel: [   42.648916] ata5: SATA max UDMA/133 mmio m1048576@0xfc800000 port 0xfc826000 irq 28
May 27 20:51:55 thunder kernel: [   42.648918] ata6: SATA max UDMA/133 mmio m1048576@0xfc800000 port 0xfc828000 irq 28
May 27 20:51:55 thunder kernel: [   42.648920] ata7: SATA max UDMA/133 mmio m1048576@0xfc800000 port 0xfc832000 irq 28
May 27 20:51:55 thunder kernel: [   42.648922] ata8: SATA max UDMA/133 mmio m1048576@0xfc800000 port 0xfc834000 irq 28
May 27 20:51:55 thunder kernel: [   42.648925] ata9: SATA max UDMA/133 mmio m1048576@0xfc800000 port 0xfc836000 irq 28
May 27 20:51:55 thunder kernel: [   42.648927] ata10: SATA max UDMA/133 mmio m1048576@0xfc800000 port 0xfc838000 irq 28
May 27 20:51:55 thunder kernel: [   42.824638] usb 2-1: new full speed USB device using ohci_hcd and address 2
May 27 20:51:55 thunder kernel: [   43.033539] usb 2-1: configuration #1 chosen from 1 choice
May 27 20:51:55 thunder kernel: [   43.036471] hub 2-1:1.0: USB hub found
May 27 20:51:55 thunder kernel: [   43.039446] hub 2-1:1.0: 3 ports detected
May 27 20:51:55 thunder kernel: [   43.188389] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
May 27 20:51:55 thunder kernel: [   43.200401] ata3.00: ATA-6: WDC WD360GD-00FLC0, 33.08F33, max UDMA/133
May 27 20:51:55 thunder kernel: [   43.200404] ata3.00: 72303840 sectors, multi 0: LBA48 
May 27 20:51:55 thunder kernel: [   43.224388] ata3.00: configured for UDMA/133
May 27 20:51:55 thunder kernel: [   43.460186] usb 2-2: new low speed USB device using ohci_hcd and address 3
May 27 20:51:55 thunder kernel: [   43.673992] usb 2-2: configuration #1 chosen from 1 choice
May 27 20:51:55 thunder kernel: [   43.759985] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
May 27 20:51:55 thunder kernel: [   43.775987] ata4.00: ATA-7: Maxtor 6B300S0, BANC1G10, max UDMA/133
May 27 20:51:55 thunder kernel: [   43.775989] ata4.00: 586114704 sectors, multi 0: LBA48 NCQ (not used)
May 27 20:51:55 thunder kernel: [   43.799972] ata4.00: configured for UDMA/133
May 27 20:51:55 thunder kernel: [   43.889747] usb 2-1.2: new full speed USB device using ohci_hcd and address 4
May 27 20:51:55 thunder kernel: [   44.004729] usb 2-1.2: configuration #1 chosen from 1 choice
May 27 20:51:55 thunder kernel: [   44.221470] usb 2-1.3: new full speed USB device using ohci_hcd and address 5
May 27 20:51:55 thunder kernel: [   44.335568] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
May 27 20:51:55 thunder kernel: [   44.336449] usb 2-1.3: configuration #1 chosen from 1 choice
May 27 20:51:55 thunder kernel: [   44.343395] usbcore: registered new interface driver hiddev
May 27 20:51:55 thunder kernel: [   44.350504] input: Microsoft Microsoft 5-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:06.0/0000:03:00.1/usb2/2-2/2-2:1.0/input/input1
May 27 20:51:55 thunder kernel: [   44.372061] input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft 5-Button Mouse with IntelliEye(TM)] on usb-0000:03:00.1-2
May 27 20:51:55 thunder kernel: [   44.380396] input: Logitech Logitech BT Mini-Receiver as /devices/pci0000:00/0000:00:06.0/0000:03:00.1/usb2/2-1/2-1.2/2-1.2:1.0/input/input2
May 27 20:51:55 thunder kernel: [   44.391548] ata5.00: ATA-7: MAXTOR STM3320620AS, 3.AAE, max UDMA/133
May 27 20:51:55 thunder kernel: [   44.391551] ata5.00: 625142448 sectors, multi 0: LBA48 NCQ (depth 0/32)
May 27 20:51:55 thunder kernel: [   44.404029] input,hidraw1: USB HID v1.11 Keyboard [Logitech Logitech BT Mini-Receiver] on usb-0000:03:00.1-1.2
May 27 20:51:55 thunder kernel: [   44.416382] input: Logitech Logitech BT Mini-Receiver as /devices/pci0000:00/0000:00:06.0/0000:03:00.1/usb2/2-1/2-1.3/2-1.3:1.0/input/input3
May 27 20:51:55 thunder kernel: [   44.444021] input,hiddev96,hidraw2: USB HID v1.11 Mouse [Logitech Logitech BT Mini-Receiver] on usb-0000:03:00.1-1.3
May 27 20:51:55 thunder kernel: [   44.444033] usbcore: registered new interface driver usbhid
May 27 20:51:55 thunder kernel: [   44.444036] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
May 27 20:51:55 thunder kernel: [   44.471512] ata5.00: configured for UDMA/133
May 27 20:51:55 thunder kernel: [   45.007104] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
May 27 20:51:55 thunder kernel: [   45.063083] ata6.00: ATA-7: MAXTOR STM3320620AS, 3.AAE, max UDMA/133
May 27 20:51:55 thunder kernel: [   45.063085] ata6.00: 625142448 sectors, multi 0: LBA48 NCQ (depth 0/32)
May 27 20:51:55 thunder kernel: [   45.127042] ata6.00: configured for UDMA/133
May 27 20:51:55 thunder kernel: [   45.662633] ata7: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
May 27 20:51:55 thunder kernel: [   45.726608] ata7.00: ATA-7: MAXTOR STM3320620AS, 3.AAE, max UDMA/133
May 27 20:51:55 thunder kernel: [   45.726610] ata7.00: 625142448 sectors, multi 0: LBA48 NCQ (depth 0/32)
May 27 20:51:55 thunder kernel: [   45.790562] ata7.00: configured for UDMA/133
May 27 20:51:55 thunder kernel: [   46.326142] ata8: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
May 27 20:51:55 thunder kernel: [   46.382118] ata8.00: ATA-7: MAXTOR STM3320620AS, 3.AAE, max UDMA/133
May 27 20:51:55 thunder kernel: [   46.382120] ata8.00: 625142448 sectors, multi 0: LBA48 NCQ (depth 0/32)
May 27 20:51:55 thunder kernel: [   46.446077] ata8.00: configured for UDMA/133
May 27 20:51:55 thunder kernel: [   46.981664] ata9: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
May 27 20:51:55 thunder kernel: [   47.037639] ata9.00: ATA-7: MAXTOR STM3320620AS, 3.AAE, max UDMA/133
May 27 20:51:55 thunder kernel: [   47.037640] ata9.00: 625142448 sectors, multi 0: LBA48 NCQ (depth 0/32)
May 27 20:51:55 thunder kernel: [   47.101591] ata9.00: configured for UDMA/133
May 27 20:51:55 thunder kernel: [   47.133539] ata10: SATA link down (SStatus 0 SControl 300)
May 27 20:51:55 thunder kernel: [   47.133633] scsi 2:0:0:0: Direct-Access     ATA      WDC WD360GD-00FL 33.0 PQ: 0 ANSI: 5
May 27 20:51:55 thunder kernel: [   47.133709] scsi 2:0:0:0: Attached scsi generic sg1 type 0
May 27 20:51:55 thunder kernel: [   47.133760] scsi 3:0:0:0: Direct-Access     ATA      Maxtor 6B300S0   BANC PQ: 0 ANSI: 5
May 27 20:51:55 thunder kernel: [   47.133804] scsi 3:0:0:0: Attached scsi generic sg2 type 0
May 27 20:51:55 thunder kernel: [   47.133850] scsi 4:0:0:0: Direct-Access     ATA      MAXTOR STM332062 3.AA PQ: 0 ANSI: 5
May 27 20:51:55 thunder kernel: [   47.133890] scsi 4:0:0:0: Attached scsi generic sg3 type 0
May 27 20:51:55 thunder kernel: [   47.133934] scsi 5:0:0:0: Direct-Access     ATA      MAXTOR STM332062 3.AA PQ: 0 ANSI: 5
May 27 20:51:55 thunder kernel: [   47.133975] scsi 5:0:0:0: Attached scsi generic sg4 type 0
May 27 20:51:55 thunder kernel: [   47.134018] scsi 6:0:0:0: Direct-Access     ATA      MAXTOR STM332062 3.AA PQ: 0 ANSI: 5
May 27 20:51:55 thunder kernel: [   47.134065] scsi 6:0:0:0: Attached scsi generic sg5 type 0
May 27 20:51:55 thunder kernel: [   47.134108] scsi 7:0:0:0: Direct-Access     ATA      MAXTOR STM332062 3.AA PQ: 0 ANSI: 5
May 27 20:51:55 thunder kernel: [   47.134147] scsi 7:0:0:0: Attached scsi generic sg6 type 0
May 27 20:51:55 thunder kernel: [   47.134188] scsi 8:0:0:0: Direct-Access     ATA      MAXTOR STM332062 3.AA PQ: 0 ANSI: 5
May 27 20:51:55 thunder kernel: [   47.134227] scsi 8:0:0:0: Attached scsi generic sg7 type 0
May 27 20:51:55 thunder kernel: [   47.139703] Driver 'sd' needs updating - please use bus_type methods
May 27 20:51:55 thunder kernel: [   47.139778] sd 2:0:0:0: [sda] 72303840 512-byte hardware sectors (37020 MB)
May 27 20:51:55 thunder kernel: [   47.139787] sd 2:0:0:0: [sda] Write Protect is off
May 27 20:51:55 thunder kernel: [   47.139789] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
May 27 20:51:55 thunder kernel: [   47.139801] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May 27 20:51:55 thunder kernel: [   47.139836] sd 2:0:0:0: [sda] 72303840 512-byte hardware sectors (37020 MB)
May 27 20:51:55 thunder kernel: [   47.139842] sd 2:0:0:0: [sda] Write Protect is off
May 27 20:51:55 thunder kernel: [   47.139844] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
May 27 20:51:55 thunder kernel: [   47.139854] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May 27 20:51:55 thunder kernel: [   47.139856]  sda: sda1 sda2 < sda5 >
May 27 20:51:55 thunder kernel: [   47.160860] sd 2:0:0:0: [sda] Attached SCSI disk
May 27 20:51:55 thunder kernel: [   47.160916] sd 3:0:0:0: [sdb] 586114704 512-byte hardware sectors (300091 MB)
May 27 20:51:55 thunder kernel: [   47.160927] sd 3:0:0:0: [sdb] Write Protect is off
May 27 20:51:55 thunder kernel: [   47.160929] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
May 27 20:51:55 thunder kernel: [   47.160941] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May 27 20:51:55 thunder kernel: [   47.160976] sd 3:0:0:0: [sdb] 586114704 512-byte hardware sectors (300091 MB)
May 27 20:51:55 thunder kernel: [   47.160983] sd 3:0:0:0: [sdb] Write Protect is off
May 27 20:51:55 thunder kernel: [   47.160984] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
May 27 20:51:55 thunder kernel: [   47.160995] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May 27 20:51:55 thunder kernel: [   47.160997]  sdb: sdb2 < sdb5 sdb6 >
May 27 20:51:55 thunder kernel: [   47.197154] sd 3:0:0:0: [sdb] Attached SCSI disk
May 27 20:51:55 thunder kernel: [   47.197198] sd 4:0:0:0: [sdc] 625142448 512-byte hardware sectors (320073 MB)
May 27 20:51:55 thunder kernel: [   47.197205] sd 4:0:0:0: [sdc] Write Protect is off
May 27 20:51:55 thunder kernel: [   47.197207] sd 4:0:0:0: [sdc] Mode Sense: 00 3a 00 00
May 27 20:51:55 thunder kernel: [   47.197218] sd 4:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May 27 20:51:55 thunder kernel: [   47.197245] sd 4:0:0:0: [sdc] 625142448 512-byte hardware sectors (320073 MB)
May 27 20:51:55 thunder kernel: [   47.197252] sd 4:0:0:0: [sdc] Write Protect is off
May 27 20:51:55 thunder kernel: [   47.197253] sd 4:0:0:0: [sdc] Mode Sense: 00 3a 00 00
May 27 20:51:55 thunder kernel: [   47.197264] sd 4:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May 27 20:51:55 thunder kernel: [   47.197266]  sdc:
May 27 20:51:55 thunder kernel: [   47.210337] sd 4:0:0:0: [sdc] Attached SCSI disk
May 27 20:51:55 thunder kernel: [   47.210373] sd 5:0:0:0: [sdd] 625142448 512-byte hardware sectors (320073 MB)
May 27 20:51:55 thunder kernel: [   47.210380] sd 5:0:0:0: [sdd] Write Protect is off
May 27 20:51:55 thunder kernel: [   47.210382] sd 5:0:0:0: [sdd] Mode Sense: 00 3a 00 00
May 27 20:51:55 thunder kernel: [   47.210393] sd 5:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May 27 20:51:55 thunder kernel: [   47.210419] sd 5:0:0:0: [sdd] 625142448 512-byte hardware sectors (320073 MB)
May 27 20:51:55 thunder kernel: [   47.210426] sd 5:0:0:0: [sdd] Write Protect is off
May 27 20:51:55 thunder kernel: [   47.210428] sd 5:0:0:0: [sdd] Mode Sense: 00 3a 00 00
May 27 20:51:55 thunder kernel: [   47.210439] sd 5:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May 27 20:51:55 thunder kernel: [   47.210441]  sdd:
May 27 20:51:55 thunder kernel: [   47.228082] sd 5:0:0:0: [sdd] Attached SCSI disk
May 27 20:51:55 thunder kernel: [   47.228114] sd 6:0:0:0: [sde] 625142448 512-byte hardware sectors (320073 MB)
May 27 20:51:55 thunder kernel: [   47.228121] sd 6:0:0:0: [sde] Write Protect is off
May 27 20:51:55 thunder kernel: [   47.228122] sd 6:0:0:0: [sde] Mode Sense: 00 3a 00 00
May 27 20:51:55 thunder kernel: [   47.228133] sd 6:0:0:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May 27 20:51:55 thunder kernel: [   47.228157] sd 6:0:0:0: [sde] 625142448 512-byte hardware sectors (320073 MB)
May 27 20:51:55 thunder kernel: [   47.228163] sd 6:0:0:0: [sde] Write Protect is off
May 27 20:51:55 thunder kernel: [   47.228165] sd 6:0:0:0: [sde] Mode Sense: 00 3a 00 00
May 27 20:51:55 thunder kernel: [   47.228176] sd 6:0:0:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May 27 20:51:55 thunder kernel: [   47.228178]  sde:
May 27 20:51:55 thunder kernel: [   47.241079] sd 6:0:0:0: [sde] Attached SCSI disk
May 27 20:51:55 thunder kernel: [   47.241113] sd 7:0:0:0: [sdf] 625142448 512-byte hardware sectors (320073 MB)
May 27 20:51:55 thunder kernel: [   47.241119] sd 7:0:0:0: [sdf] Write Protect is off
May 27 20:51:55 thunder kernel: [   47.241121] sd 7:0:0:0: [sdf] Mode Sense: 00 3a 00 00
May 27 20:51:55 thunder kernel: [   47.241132] sd 7:0:0:0: [sdf] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May 27 20:51:55 thunder kernel: [   47.241156] sd 7:0:0:0: [sdf] 625142448 512-byte hardware sectors (320073 MB)
May 27 20:51:55 thunder kernel: [   47.241163] sd 7:0:0:0: [sdf] Write Protect is off
May 27 20:51:55 thunder kernel: [   47.241164] sd 7:0:0:0: [sdf] Mode Sense: 00 3a 00 00
May 27 20:51:55 thunder kernel: [   47.241175] sd 7:0:0:0: [sdf] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May 27 20:51:55 thunder kernel: [   47.241177]  sdf:
May 27 20:51:55 thunder kernel: [   47.258955] sd 7:0:0:0: [sdf] Attached SCSI disk
May 27 20:51:55 thunder kernel: [   47.258988] sd 8:0:0:0: [sdg] 625142448 512-byte hardware sectors (320073 MB)
May 27 20:51:55 thunder kernel: [   47.258995] sd 8:0:0:0: [sdg] Write Protect is off
May 27 20:51:55 thunder kernel: [   47.258997] sd 8:0:0:0: [sdg] Mode Sense: 00 3a 00 00
May 27 20:51:55 thunder kernel: [   47.259008] sd 8:0:0:0: [sdg] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May 27 20:51:55 thunder kernel: [   47.259031] sd 8:0:0:0: [sdg] 625142448 512-byte hardware sectors (320073 MB)
May 27 20:51:55 thunder kernel: [   47.259038] sd 8:0:0:0: [sdg] Write Protect is off
May 27 20:51:55 thunder kernel: [   47.259039] sd 8:0:0:0: [sdg] Mode Sense: 00 3a 00 00
May 27 20:51:55 thunder kernel: [   47.259050] sd 8:0:0:0: [sdg] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May 27 20:51:55 thunder kernel: [   47.259053]  sdg:
May 27 20:51:55 thunder kernel: [   47.274150] sd 8:0:0:0: [sdg] Attached SCSI disk
May 27 20:51:55 thunder kernel: [   47.427672] md: md0 stopped.
May 27 20:51:55 thunder kernel: [   47.524600] Attempting manual resume
May 27 20:51:55 thunder kernel: [   47.524604] swsusp: Resume From Partition 8:5
May 27 20:51:55 thunder kernel: [   47.524605] PM: Checking swsusp image.
May 27 20:51:55 thunder kernel: [   47.524698] PM: Resume from disk failed.
May 27 20:51:55 thunder kernel: [   47.551551] kjournald starting.  Commit interval 5 seconds
May 27 20:51:55 thunder kernel: [   47.551561] EXT3-fs: mounted filesystem with ordered data mode.
May 27 20:51:55 thunder kernel: [   52.702199] md: md0 stopped.
May 27 20:51:55 thunder kernel: [   52.824471] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
May 27 20:51:55 thunder kernel: [   52.858004] shpchp: HPC vendor_id 1022 device_id 7460 ss_vid 0 ss_did 0
May 27 20:51:55 thunder kernel: [   52.858010] shpchp: shpc_init: cannot reserve MMIO region
May 27 20:51:55 thunder kernel: [   52.858037] shpchp: HPC vendor_id 1022 device_id 7450 ss_vid 0 ss_did 0
May 27 20:51:55 thunder kernel: [   52.858039] shpchp: shpc_init: cannot reserve MMIO region
May 27 20:51:55 thunder kernel: [   52.858047] shpchp: HPC vendor_id 1022 device_id 7450 ss_vid 0 ss_did 0
May 27 20:51:55 thunder kernel: [   52.858049] shpchp: shpc_init: cannot reserve MMIO region
May 27 20:51:55 thunder kernel: [   52.858068] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
May 27 20:51:55 thunder kernel: [   52.929641] input: PC Speaker as /devices/platform/pcspkr/input/input4
May 27 20:51:55 thunder kernel: [   52.976422] AMD768 RNG detected
May 27 20:51:55 thunder kernel: [   52.986502] input: Power Button (FF) as /devices/virtual/input/input5
May 27 20:51:55 thunder kernel: [   53.013779] ACPI: Power Button (FF) [PWRF]
May 27 20:51:55 thunder kernel: [   53.013870] input: Power Button (CM) as /devices/virtual/input/input6
May 27 20:51:55 thunder kernel: [   53.041752] ACPI: Power Button (CM) [PWRB]
May 27 20:51:55 thunder kernel: [   53.383071] nvidia: module license 'NVIDIA' taints kernel.
May 27 20:51:55 thunder kernel: [   53.759081] ACPI: PCI Interrupt 0000:02:02.0[A] -> GSI 26 (level, low) -> IRQ 26
May 27 20:51:55 thunder kernel: [   53.759233] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  169.12  Thu Feb 14 17:51:09 PST 2008
May 27 20:51:55 thunder kernel: [  233.143004] lp: driver loaded but no devices found
May 27 20:51:55 thunder kernel: [  233.254625] Adding 1526132k swap on /dev/sda5.  Priority:-1 extents:1 across:1526132k
May 27 20:51:55 thunder kernel: [  233.783061] EXT3 FS on sda1, internal journal
May 27 20:51:55 thunder kernel: [  234.774668] ip_tables: (C) 2000-2006 Netfilter Core Team
May 27 20:51:55 thunder kernel: [  235.025641] No dock devices found.
May 27 20:51:55 thunder kernel: [  235.240111] powernow-k8: Found 2 AMD Opteron(tm) Processor 252 processors (2 cpu cores) (version 2.20.00)
May 27 20:51:55 thunder kernel: [  235.240130] powernow-k8: MP systems not supported by PSB BIOS structure
May 27 20:51:55 thunder kernel: [  235.240149] powernow-k8: MP systems not supported by PSB BIOS structure
May 27 20:51:55 thunder NetworkManager: <info>  starting... 
May 27 20:51:55 thunder avahi-daemon[5567]: Found user 'avahi' (UID 109) and group 'avahi' (GID 120).
May 27 20:51:55 thunder avahi-daemon[5567]: Successfully dropped root privileges.
May 27 20:51:55 thunder avahi-daemon[5567]: avahi-daemon 0.6.22 starting up.
May 27 20:51:55 thunder avahi-daemon[5567]: Successfully called chroot().
May 27 20:51:55 thunder avahi-daemon[5567]: Successfully dropped remaining capabilities.
May 27 20:51:55 thunder avahi-daemon[5567]: No service file found in /etc/avahi/services.
May 27 20:51:55 thunder avahi-daemon[5567]: Network interface enumeration completed.
May 27 20:51:55 thunder avahi-daemon[5567]: Registering HINFO record with values 'X86_64'/'LINUX'.
May 27 20:51:55 thunder avahi-daemon[5567]: Server startup complete. Host name is thunder.local. Local service cookie is 1077712694.
May 27 20:51:55 thunder kernel: [  235.896085] ppdev: user-space parallel port driver
May 27 20:51:55 thunder kernel: [  235.972269] audit(1211935915.908:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5601 profile="/usr/sbin/cupsd" namespace="default"
May 27 20:51:55 thunder dhcdbd: Started up.
May 27 20:51:56 thunder hcid[5815]: Bluetooth HCI daemon
May 27 20:51:56 thunder kernel: [  236.991384] Bluetooth: Core ver 2.11
May 27 20:51:56 thunder kernel: [  236.991792] NET: Registered protocol family 31
May 27 20:51:56 thunder kernel: [  236.991794] Bluetooth: HCI device and connection manager initialized
May 27 20:51:56 thunder kernel: [  236.991811] Bluetooth: HCI socket layer initialized
May 27 20:51:56 thunder hcid[5815]: Starting SDP server
May 27 20:51:56 thunder hcid[5815]: Created local server at unix:abstract=/var/run/dbus-tbr9IXsIdc,guid=b7ab29496966e7e3bace5b86483cacac
May 27 20:51:56 thunder kernel: [  237.004919] Bluetooth: L2CAP ver 2.9
May 27 20:51:56 thunder kernel: [  237.004924] Bluetooth: L2CAP socket layer initialized
May 27 20:51:56 thunder NetworkManager: <info>  eth2: Device is fully-supported using driver 'tg3'. 
May 27 20:51:56 thunder NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
May 27 20:51:56 thunder NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
May 27 20:51:56 thunder NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth2'. 
May 27 20:51:56 thunder NetworkManager: <info>  Deactivating device eth2. 
May 27 20:51:56 thunder input[5834]: Bluetooth Input daemon
May 27 20:51:56 thunder input[5834]: Registered input manager path:/org/bluez/input
May 27 20:51:56 thunder audio[5832]: Bluetooth Audio daemon
May 27 20:51:56 thunder audio[5832]: Unix socket created: 5
May 27 20:51:56 thunder audio[5832]: audio.conf: Key file does not have key 'Enable'
May 27 20:51:56 thunder audio[5832]: audio.conf: Key file does not have key 'Disable'
May 27 20:51:57 thunder kernel: [  237.087182] Bluetooth: RFCOMM socket layer initialized
May 27 20:51:57 thunder kernel: [  237.087199] Bluetooth: RFCOMM TTY layer initialized
May 27 20:51:57 thunder kernel: [  237.087201] Bluetooth: RFCOMM ver 1.8
May 27 20:51:57 thunder audio[5832]: add_service_record: got record id 0x10000
May 27 20:51:57 thunder audio[5832]: audio.conf: Key file does not have key 'Disable'
May 27 20:51:57 thunder audio[5832]: audio.conf: Key file does not have group 'A2DP'
May 27 20:51:57 thunder last message repeated 3 times
May 27 20:51:57 thunder audio[5832]: SEP 0x62d890 registered: type:0 codec:0 seid:1
May 27 20:51:57 thunder audio[5832]: add_service_record: got record id 0x10001
May 27 20:51:57 thunder audio[5832]: add_service_record: got record id 0x10002
May 27 20:51:57 thunder audio[5832]: add_service_record: got record id 0x10003
May 27 20:51:57 thunder audio[5832]: Registered manager path:/org/bluez/audio
May 27 20:51:57 thunder NetworkManager: <info>  eth1: Device is fully-supported using driver 'tg3'. 
May 27 20:51:57 thunder NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
May 27 20:51:57 thunder NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
May 27 20:51:57 thunder NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth1'. 
May 27 20:51:57 thunder NetworkManager: <info>  Deactivating device eth1. 
May 27 20:51:57 thunder mdadm: DeviceDisappeared event detected on md device /dev/md0
May 27 20:51:57 thunder NetworkManager: <info>  eth0: Device is fully-supported using driver 'e100'. 
May 27 20:51:57 thunder NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
May 27 20:51:57 thunder NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
May 27 20:51:57 thunder NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
May 27 20:51:57 thunder NetworkManager: <info>  Deactivating device eth0. 
May 27 20:51:57 thunder NetworkManager: <info>  Will activate wired connection 'eth2' because it now has a link. 
May 27 20:51:57 thunder NetworkManager: <info>  Will activate wired connection 'eth1' because it now has a link. 
May 27 20:51:57 thunder NetworkManager: <debug> [1211935917.084692] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 
May 27 20:51:57 thunder NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link. 
May 27 20:51:57 thunder NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth1'. 
May 27 20:51:57 thunder kernel: [  237.303364] usb 2-1.1: new full speed USB device using ohci_hcd and address 6
May 27 20:51:57 thunder kernel: [  237.418356] usb 2-1.1: configuration #1 chosen from 1 choice
May 27 20:51:57 thunder kernel: [  237.487396] Bluetooth: HCI USB driver ver 2.9
May 27 20:51:57 thunder hcid[5815]: HCI dev 0 registered
May 27 20:51:57 thunder kernel: [  237.490713] usbcore: registered new interface driver hci_usb
May 27 20:51:57 thunder hcid[5815]: HCI dev 0 up
May 27 20:51:57 thunder hcid[5815]: Device hci0 has been added
May 27 20:51:57 thunder hcid[5815]: Starting security manager 0
May 27 20:51:57 thunder hcid[5815]: Device hci0 has been activated
May 27 20:51:58 thunder dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
May 27 20:51:58 thunder NetworkManager: <info>  Will activate connection 'eth1'. 

May 27 20:51:58 thunder NetworkManager: <info>  Device eth1 activation scheduled... 
May 27 20:51:58 thunder NetworkManager: <debug> [1211935918.084932] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c709_0007617A8651'). 
May 27 20:51:58 thunder NetworkManager: <debug> [1211935918.088944] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c709_0007617A8651_if3'). 
May 27 20:51:58 thunder NetworkManager: <debug> [1211935918.089195] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c709_0007617A8651_if1'). 
May 27 20:51:58 thunder NetworkManager: <debug> [1211935918.089429] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c709_0007617A8651_if0'). 
May 27 20:51:58 thunder NetworkManager: <debug> [1211935918.089741] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c709_0007617A8651_if0_bluetooth_hci_7617a8651'). 
May 27 20:51:58 thunder NetworkManager: <debug> [1211935918.090015] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c709_0007617A8651_if2'). 
May 27 20:51:58 thunder NetworkManager: <info>  Activation (eth1) started... 
May 27 20:51:58 thunder NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
May 27 20:51:58 thunder NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
May 27 20:51:58 thunder NetworkManager: <info>  Activation (eth1) failure scheduled... 
May 27 20:51:58 thunder NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
May 27 20:51:58 thunder NetworkManager: <info>  Activation (eth1) failed. 
May 27 20:51:58 thunder NetworkManager: <info>  Deactivating device eth1. 
May 27 20:51:59 thunder anacron[6042]: Anacron 2.3 started on 2008-05-27
May 27 20:51:59 thunder anacron[6042]: Normal exit (0 jobs run)
May 27 20:51:59 thunder /usr/sbin/cron[6071]: (CRON) INFO (pidfile fd = 3)
May 27 20:51:59 thunder /usr/sbin/cron[6072]: (CRON) STARTUP (fork ok)
May 27 20:51:59 thunder /usr/sbin/cron[6072]: (CRON) INFO (Running @reboot jobs)
May 27 20:52:00 thunder kernel: [  240.149590] tg3: eth1: Link is up at 1000 Mbps, full duplex.
May 27 20:52:00 thunder kernel: [  240.149595] tg3: eth1: Flow control is on for TX and on for RX.
May 27 20:52:00 thunder NetworkManager: <info>  Will activate wired connection 'eth1' because it now has a link. 
May 27 20:52:00 thunder NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth1'. 
May 27 20:52:00 thunder dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
May 27 20:52:00 thunder NetworkManager: <info>  Will activate connection 'eth1'. 
May 27 20:52:00 thunder NetworkManager: <info>  Device eth1 activation scheduled... 
May 27 20:52:00 thunder NetworkManager: <info>  Activation (eth1) started... 
May 27 20:52:00 thunder NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
May 27 20:52:00 thunder NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
May 27 20:52:00 thunder NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
May 27 20:52:00 thunder NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
May 27 20:52:00 thunder NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
May 27 20:52:00 thunder NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) successful. 
May 27 20:52:00 thunder NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
May 27 20:52:00 thunder NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
May 27 20:52:00 thunder NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
May 27 20:52:01 thunder NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction. 
May 27 20:52:01 thunder NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth1 
May 27 20:52:01 thunder NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
May 27 20:52:02 thunder NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth1 
May 27 20:52:02 thunder kernel: [  242.347450] NET: Registered protocol family 17
May 27 20:52:03 thunder dhclient: DHCPREQUEST of 192.168.0.100 on eth1 to 255.255.255.255 port 67
May 27 20:52:03 thunder dhclient: DHCPACK of 192.168.0.100 from 192.168.0.1
May 27 20:52:03 thunder avahi-daemon[5567]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.0.100.
May 27 20:52:03 thunder avahi-daemon[5567]: New relevant interface eth1.IPv4 for mDNS.
May 27 20:52:03 thunder avahi-daemon[5567]: Registering new address record for 192.168.0.100 on eth1.IPv4.
May 27 20:52:03 thunder NetworkManager: <info>  DHCP daemon state is now 4 (reboot) for interface eth1 
May 27 20:52:03 thunder NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) scheduled... 
May 27 20:52:03 thunder NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) started... 
May 27 20:52:03 thunder dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.host_name
May 27 20:52:03 thunder dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_domain
May 27 20:52:03 thunder dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_servers
May 27 20:52:03 thunder NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
May 27 20:52:03 thunder NetworkManager: <info>    address 192.168.0.100 
May 27 20:52:03 thunder NetworkManager: <info>    netmask 255.255.255.0 
May 27 20:52:03 thunder NetworkManager: <info>    broadcast 192.168.0.255 
May 27 20:52:03 thunder NetworkManager: <info>    gateway 192.168.0.1 
May 27 20:52:03 thunder NetworkManager: <info>    nameserver 192.168.0.1 
May 27 20:52:03 thunder NetworkManager: <info>    domain name 'hsd1.nj.comcast.net.' 
May 27 20:52:03 thunder dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.interface_mtu
May 27 20:52:03 thunder NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled... 
May 27 20:52:03 thunder NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) complete. 
May 27 20:52:03 thunder NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) started... 
May 27 20:52:03 thunder dhclient: bound to 192.168.0.100 -- renewal in 33403 seconds.
May 27 20:52:03 thunder avahi-daemon[5567]: Withdrawing address record for 192.168.0.100 on eth1.
May 27 20:52:03 thunder avahi-daemon[5567]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.0.100.
May 27 20:52:03 thunder avahi-daemon[5567]: Interface eth1.IPv4 no longer relevant for mDNS.
May 27 20:52:03 thunder avahi-daemon[5567]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.0.100.
May 27 20:52:03 thunder avahi-daemon[5567]: New relevant interface eth1.IPv4 for mDNS.
May 27 20:52:03 thunder avahi-daemon[5567]: Registering new address record for 192.168.0.100 on eth1.IPv4.
May 27 20:52:04 thunder NetworkManager: <info>  Clearing nscd hosts cache. 
May 27 20:52:04 thunder NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
May 27 20:52:04 thunder NetworkManager: <info>  Activation (eth1) Finish handler scheduled. 
May 27 20:52:04 thunder NetworkManager: <info>  Activation (eth1) successful, device activated. 
May 27 20:52:04 thunder NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete. 
May 27 20:52:04 thunder kernel: [  244.800991] NET: Registered protocol family 10
May 27 20:52:04 thunder kernel: [  244.801302] lo: Disabled Privacy Extensions
May 27 20:52:04 thunder kernel: [  244.801771] ADDRCONF(NETDEV_UP): eth0: link is not ready
May 27 20:52:04 thunder kernel: [  244.802342] ADDRCONF(NETDEV_UP): eth2: link is not ready
May 27 20:52:05 thunder ntpdate[6246]: adjust time server 91.189.94.4 offset 0.025060 sec
May 27 20:52:06 thunder avahi-daemon[5567]: Registering new address record for fe80::2e0:81ff:fe30:5238 on eth1.*.
May 27 20:52:08 thunder NetworkManager: <debug> [1211935928.004386] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_76174a2c0'). 
May 27 20:52:08 thunder input[5834]: Incoming connection on PSM 17
May 27 20:52:13 thunder kernel: [  253.769021] usb 2-1: USB disconnect, address 2
May 27 20:52:13 thunder kernel: [  253.769026] usb 2-1.1: USB disconnect, address 6
May 27 20:52:13 thunder hcid[5815]: HCI dev 0 down
May 27 20:52:13 thunder hcid[5815]: Stopping security manager 0
May 27 20:52:13 thunder hcid[5815]: Device hci0 has been disabled
May 27 20:52:13 thunder NetworkManager: <debug> [1211935933.732869] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_76174a2c0'). 
May 27 20:52:13 thunder NetworkManager: <debug> [1211935933.733248] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c709_0007617A8651_if0_bluetooth_hci_7617a8651'). 
May 27 20:52:13 thunder hcid[5815]: HCI dev 0 unregistered
May 27 20:52:13 thunder hcid[5815]: Unregister path: /org/bluez/hci0
May 27 20:52:13 thunder kernel: [  254.025499] usb 2-1.2: USB disconnect, address 4
May 27 20:52:13 thunder hcid[5815]: Device hci0 has been removed
May 27 20:52:13 thunder NetworkManager: <debug> [1211935933.982968] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c709_0007617A8651_if0'). 
May 27 20:52:13 thunder NetworkManager: <debug> [1211935933.986905] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c709_0007617A8651_if1'). 
May 27 20:52:13 thunder NetworkManager: <debug> [1211935933.988396] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c709_0007617A8651_if2'). 
May 27 20:52:13 thunder NetworkManager: <debug> [1211935933.989399] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c709_0007617A8651_if3'). 
May 27 20:52:13 thunder NetworkManager: <debug> [1211935933.991109] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c709_0007617A8651'). 
May 27 20:52:14 thunder NetworkManager: <debug> [1211935934.006754] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c713_0007617A8651_if0_logicaldev_input'). 
May 27 20:52:14 thunder kernel: [  254.081348] usb 2-1.3: USB disconnect, address 5
May 27 20:52:14 thunder NetworkManager: <debug> [1211935934.039940] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c713_0007617A8651_if0'). 
May 27 20:52:14 thunder NetworkManager: <debug> [1211935934.042034] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c713_0007617A8651'). 
May 27 20:52:14 thunder NetworkManager: <debug> [1211935934.086568] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c714_0007617A8651_if0_logicaldev_input'). 
May 27 20:52:14 thunder NetworkManager: <debug> [1211935934.108910] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c714_0007617A8651_if0'). 
May 27 20:52:14 thunder NetworkManager: <debug> [1211935934.111012] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c714_0007617A8651'). 
May 27 20:52:14 thunder NetworkManager: <debug> [1211935934.113038] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_b04_noserial_if0'). 
May 27 20:52:14 thunder NetworkManager: <debug> [1211935934.114405] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_b04_noserial'). 
May 27 20:52:14 thunder kernel: [  254.452585] usb 2-1: new full speed USB device using ohci_hcd and address 7
May 27 20:52:14 thunder kernel: [  254.665289] usb 2-1: configuration #1 chosen from 1 choice
May 27 20:52:14 thunder kernel: [  254.668220] hub 2-1:1.0: USB hub found
May 27 20:52:14 thunder NetworkManager: <debug> [1211935934.626180] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_b04_noserial'). 
May 27 20:52:14 thunder kernel: [  254.671191] hub 2-1:1.0: 3 ports detected
May 27 20:52:14 thunder NetworkManager: <debug> [1211935934.672528] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial'). 
May 27 20:52:14 thunder kernel: [  255.000900] usb 2-1.2: new full speed USB device using ohci_hcd and address 8
May 27 20:52:15 thunder kernel: [  255.116878] usb 2-1.2: configuration #1 chosen from 1 choice
May 27 20:52:15 thunder NetworkManager: <debug> [1211935935.078514] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c713_0007617A8651'). 
May 27 20:52:15 thunder kernel: [  255.132846] input: Logitech Logitech BT Mini-Receiver as /devices/pci0000:00/0000:00:06.0/0000:03:00.1/usb2/2-1/2-1.2/2-1.2:1.0/input/input7
May 27 20:52:15 thunder kernel: [  255.167739] input,hidraw1: USB HID v1.11 Keyboard [Logitech Logitech BT Mini-Receiver] on usb-0000:03:00.1-1.2
May 27 20:52:15 thunder NetworkManager: <debug> [1211935935.128576] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial_0'). 
May 27 20:52:15 thunder NetworkManager: <debug> [1211935935.189267] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial_0_logicaldev_input'). 
May 27 20:52:15 thunder kernel: [  255.380563] usb 2-1.3: new full speed USB device using ohci_hcd and address 9
May 27 20:52:15 thunder kernel: [  255.496556] usb 2-1.3: configuration #1 chosen from 1 choice
May 27 20:52:15 thunder NetworkManager: <debug> [1211935935.458802] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c714_0007617A8651'). 
May 27 20:52:15 thunder kernel: [  255.517535] input: Logitech Logitech BT Mini-Receiver as /devices/pci0000:00/0000:00:06.0/0000:03:00.1/usb2/2-1/2-1.3/2-1.3:1.0/input/input8
May 27 20:52:15 thunder NetworkManager: <debug> [1211935935.507461] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial_1'). 
May 27 20:52:15 thunder kernel: [  255.611213] input,hiddev96,hidraw2: USB HID v1.11 Mouse [Logitech Logitech BT Mini-Receiver] on usb-0000:03:00.1-1.3
May 27 20:52:15 thunder NetworkManager: <debug> [1211935935.601276] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial_1_logicaldev_input'). 
May 27 20:52:15 thunder kernel: [  255.659046] eth1: no IPv6 routers present
May 27 20:52:33 thunder hcid[5815]: Default passkey agent (:1.20, /org/bluez/passkey) registered
May 27 20:52:33 thunder hcid[5815]: Default authorization agent (:1.20, /org/bluez/auth) registered
May 27 20:52:36 thunder NetworkManager: <info>  Updating allowed wireless network lists. 
May 27 20:52:36 thunder NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
May 27 20:53:30 thunder NetworkManager: <debug> [1211936010.125242] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_part2_size_1024'). 
```

---

### Post by fjgaude on 2008-05-28
I do believe before you can re-create an array with mdadm you will have to zero the superblocks on each drive:

```
sudo mdadm --zero-superblock /dev/sd[nn]
```

I think that will then let you --create a raid array.

---

### Post by modulok on 2008-05-29
> **fjgaude said:**
> I do believe before you can re-create an array with mdadm you will have to zero the superblocks on each drive:

```
sudo mdadm --zero-superblock /dev/sd[nn]
```

I think that will then let you --create a raid array.


Did that back in January when I first had the issue. Any more suggestions?

---

### Post by fjgaude on 2008-05-29
Can't say for sure, but if you can create the array with mdadm and

```
sudo watch cat /proc/mdstat
```

shows nothing, then you likely have a hardware issue, either controller or drives themselves. Are you sure you zeroed the superblocks and also put the filesystem on after you did the --create command?

Sorry I can't be more specific but you likely know how these things can be.

---

### Post by modulok on 2008-05-29
OK, started from scratch again.

removed mdadm, restarted, installed mdadm.

I did a cfdisk on each drive, making partitions and raid as the type.

mdadm --create /dev/md0 --chunk=64 --level=raid5 --raid-devices=5 /dev/sdc1 /dev/sdd1 /dev/sde1 /dev/sdf1 /dev/sdg1

mdadm: /dev/sdc1 appears to be part of a raid array:
    level=raid5 devices=4 ctime=Tue Jan 15 21:44:53 2008
mdadm: Cannot open /dev/sdd1: Device or resource busy
mdadm: /dev/sde1 appears to be part of a raid array:
    level=raid5 devices=4 ctime=Tue Jan 15 21:44:53 2008
mdadm: /dev/sdf1 appears to be part of a raid array:
    level=raid5 devices=4 ctime=Tue Jan 15 21:44:53 2008
mdadm: /dev/sdg1 appears to be part of a raid array:
    level=raid5 devices=4 ctime=Tue Jan 15 21:44:53 2008
mdadm: create aborted

cat /proc/mdstat 
Personalities : 
md0 : inactive sdd1[1](S)
      312568576 blocks
       
unused devices: <none>

mdadm --zero-superblock /dev/sdc1
mdadm --zero-superblock /dev/sdd1
[COLOR="Red"]mdadm: Couldn't open /dev/sdd1 for write - not zeroing[/COLOR]
mdadm --zero-superblock /dev/sde1
mdadm --zero-superblock /dev/sdf1
mdadm --zero-superblock /dev/sdg1

To me, the part in red makes me think there is a hardware issue. Although I just made the partition ok on that drive. I am going to swap drives and see if I get same result.

---

### Post by modulok on 2008-05-29
Well, after swapping sdd and sdg I create the array again and get the following error:

mdadm: /dev/sdg1 appears to be part of a raid array
continue creating? (I say yes)
mdadm: array /dev/md0 started

Then the whole system locks. No hard disk activity.

I boot back up, see some disk activity on all but sdd (old sdg).

cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : inactive sdd1[1](S)
      312568576 blocks
       
unused devices: <none>

I have no idea why the drives are so active, I can't see anything using them, but my cpu is up to 50% (dual socket opteron 152s)

---

### Post by modulok on 2008-06-06
Well I have the raid5 array working with all drives now.
I am not sure exactly what it was, but after I had a good 4 drive array (about 894GB) I added the drive I thought was causing the problems. I formatted it and added it to the array as a spare. Rebooted and no errors or constant disk activity. I deleted the 4 drive array and created a 5 drive array. About an hour goes by, and its built, I format (about 1.2TB), restart, and no issues!

Now to move everything back onto the array from my 1TB Seagate.

---

### Post by fjgaude on 2008-06-06
I wonder what we have learned from all this? <smile>

---

