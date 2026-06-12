---
title: "ubuntu completely freezes"
date: 2007-08-13
forum: General Help
---

### Post by texmurphy on 2007-08-13
hello i am rather new to linux, and for the last few day's gnome completely locks up, mouse does not move, ctrl-alt-backspace does nothing, and i cannot switch desktops either, the only error i can recognise in my syslog is to do with network manager and it mentions wireless, which i do not have installed, here is a copy of my syslog


Aug 12 21:44:43 craig-desktop NetworkManager: <WARNING>^I nm_dbus_get_networks_cb (): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 

Aug 12 22:04:20 craig-desktop -- MARK --

Aug 12 22:17:01 craig-desktop /USR/SBIN/CRON[13440]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)

Aug 12 22:44:20 craig-desktop -- MARK --

Aug 12 23:02:02 craig-desktop syslogd 1.4.1#20ubuntu4: restart.

Aug 12 23:02:03 craig-desktop kernel: Inspecting /boot/System.map-2.6.20-15-generic

Aug 12 23:02:03 craig-desktop kernel: Loaded 24975 symbols from /boot/System.map-2.6.20-15-generic.

Aug 12 23:02:03 craig-desktop kernel: Symbols match kernel version 2.6.20.

Aug 12 23:02:03 craig-desktop kernel: No module symbols loaded - kernel modules not enabled. 

Aug 12 23:02:03 craig-desktop kernel: [    0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007 (Ubuntu 2.6.20-15.27-generic)

Aug 12 23:02:03 craig-desktop kernel: [    0.000000] BIOS-provided physical RAM map:

Aug 12 23:02:03 craig-desktop kernel: [    0.000000] sanitize start

Aug 12 23:02:03 craig-desktop kernel: [    0.000000] sanitize end

Aug 12 23:02:03 craig-desktop kernel: [    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f400 end: 000000000009f400 type: 1

Aug 12 23:02:03 craig-desktop kernel: [    0.000000] copy_e820_map() type is E820_RAM

Aug 12 23:02:03 craig-desktop kernel: [    0.000000] copy_e820_map() start: 000000000009f400 size: 0000000000000c00 end: 00000000000a0000 type: 2

Aug 12 23:02:03 craig-desktop kernel: [    0.000000] copy_e820_map() start: 00000000000f0000 size: 0000000000010000 end: 0000000000100000 type: 2

Aug 12 23:02:03 craig-desktop kernel: [    0.000000] copy_e820_map() start: 0000000000100000 size: 000000007fef0000 end: 000000007fff0000 type: 1

Aug 12 23:02:03 craig-desktop kernel: [    0.000000] copy_e820_map() type is E820_RAM

Aug 12 23:02:03 craig-desktop kernel: [    0.000000] copy_e820_map() start: 000000007fff0000 size: 0000000000003000 end: 000000007fff3000 type: 4

Aug 12 23:02:03 craig-desktop kernel: [    0.000000] copy_e820_map() start: 000000007fff3000 size: 000000000000d000 end: 0000000080000000 type: 3

Aug 12 23:02:03 craig-desktop kernel: [    0.000000] copy_e820_map() start: 00000000e0000000 size: 0000000010000000 end: 00000000f0000000 type: 2

Aug 12 23:02:03 craig-desktop kernel: [    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000001400000 end: 0000000100000000 type: 2

Aug 12 23:02:03 craig-desktop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)

Aug 12 23:02:03 craig-desktop kernel: [    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)

Aug 12 23:02:03 craig-desktop kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)

Aug 12 23:02:03 craig-desktop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007fff0000 (usable)

Aug 12 23:02:03 craig-desktop kernel: [    0.000000]  BIOS-e820: 000000007fff0000 - 000000007fff3000 (ACPI NVS)

Aug 12 23:02:03 craig-desktop kernel: [    0.000000]  BIOS-e820: 000000007fff3000 - 0000000080000000 (ACPI data)

Aug 12 23:02:03 craig-desktop kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)

Aug 12 23:02:03 craig-desktop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)

Aug 12 23:02:03 craig-desktop kernel: [    0.000000] 1151MB HIGHMEM available.

Aug 12 23:02:03 craig-desktop kernel: [    0.000000] 896MB LOWMEM available.

Aug 12 23:02:03 craig-desktop kernel: [    0.000000] found SMP MP-table at 000f52c0

Aug 12 23:02:03 craig-desktop kernel: [    0.000000] Entering add_active_range(0, 0, 524272) 0 entries of 256 used

Aug 12 23:02:03 craig-desktop kernel: [    0.000000] Zone PFN ranges:

Aug 12 23:02:03 craig-desktop kernel: [    0.000000]   DMA             0 ->     4096

Aug 12 23:02:03 craig-desktop kernel: [    0.000000]   Normal       4096 ->   229376

Aug 12 23:02:03 craig-desktop kernel: [    0.000000]   HighMem    229376 ->   524272

Aug 12 23:02:03 craig-desktop kernel: [    0.000000] early_node_map[1] active PFN ranges

Aug 12 23:02:03 craig-desktop kernel: [    0.000000]     0:        0 ->   524272

Aug 12 23:02:03 craig-desktop kernel: [    0.000000] On node 0 totalpages: 524272

Aug 12 23:02:03 craig-desktop kernel: [    0.000000]   DMA zone: 32 pages used for memmap

Aug 12 23:02:03 craig-desktop kernel: [    0.000000]   DMA zone: 0 pages reserved

Aug 12 23:02:03 craig-desktop kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0

Aug 12 23:02:03 craig-desktop kernel: [    0.000000]   Normal zone: 1760 pages used for memmap

Aug 12 23:02:03 craig-desktop kernel: [    0.000000]   Normal zone: 223520 pages, LIFO batch:31

Aug 12 23:02:03 craig-desktop kernel: [    0.000000]   HighMem zone: 2303 pages used for memmap

Aug 12 23:02:03 craig-desktop kernel: [    0.000000]   HighMem zone: 292593 pages, LIFO batch:31

Aug 12 23:02:03 craig-desktop kernel: [    0.000000] DMI 2.3 present.

Aug 12 23:02:03 craig-desktop kernel: [    0.000000] ACPI: RSDP (v000 Nvidia                                ) @ 0x000f7660

Aug 12 23:02:03 craig-desktop kernel: [    0.000000] ACPI: RSDT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x7fff3040

Aug 12 23:02:03 craig-desktop kernel: [    0.000000] ACPI: FADT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x7fff30c0

Aug 12 23:02:03 craig-desktop kernel: [    0.000000] ACPI: MCFG (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x7fff9cc0

Aug 12 23:02:03 craig-desktop kernel: [    0.000000] ACPI: MADT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x7fff9c00

Aug 12 23:02:03 craig-desktop kernel: [    0.000000] ACPI: DSDT (v001 NVIDIA AWRDACPI 0x00001000 MSFT 0x0100000e) @ 0x00000000

Aug 12 23:02:03 craig-desktop kernel: [    0.000000] Nvidia board detected. Ignoring ACPI timer override.

Aug 12 23:02:03 craig-desktop kernel: [    0.000000] If you got timer trouble try acpi_use_timer_override

Aug 12 23:02:03 craig-desktop kernel: [    0.000000] Nvidia board detected. Ignoring ACPI timer override.

Aug 12 23:02:03 craig-desktop kernel: [    0.000000] If you got timer trouble try acpi_use_timer_override

Aug 12 23:02:03 craig-desktop kernel: [    0.000000] Nvidia board detected. Ignoring ACPI timer override.

Aug 12 23:02:03 craig-desktop kernel: [    0.000000] If you got timer trouble try acpi_use_timer_override

Aug 12 23:02:03 craig-desktop kernel: [    0.000000] Nvidia board detected. Ignoring ACPI timer override.

Aug 12 23:02:03 craig-desktop kernel: [    0.000000] If you got timer trouble try acpi_use_timer_override

Aug 12 23:02:03 craig-desktop kernel: [    0.000000] Nvidia board detected. Ignoring ACPI timer override.

Aug 12 23:02:03 craig-desktop kernel: [    0.000000] If you got timer trouble try acpi_use_timer_override

Aug 12 23:02:03 craig-desktop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x4008

Aug 12 23:02:03 craig-desktop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000

Aug 12 23:02:03 craig-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)

Aug 12 23:02:03 craig-desktop kernel: [    0.000000] Processor #0 15:3 APIC version 16

Aug 12 23:02:03 craig-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)

Aug 12 23:02:03 craig-desktop kernel: [    0.000000] Processor #1 15:3 APIC version 16

Aug 12 23:02:03 craig-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])

Aug 12 23:02:03 craig-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])

Aug 12 23:02:03 craig-desktop kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])

Aug 12 23:02:03 craig-desktop kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23

Aug 12 23:02:03 craig-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)

Aug 12 23:02:03 craig-desktop kernel: [    0.000000] ACPI: BIOS IRQ0 pin2 override ignored.

Aug 12 23:02:03 craig-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)

Aug 12 23:02:03 craig-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)

Aug 12 23:02:03 craig-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)

Aug 12 23:02:03 craig-desktop kernel: [    0.000000] ACPI: IRQ9 used by override.

Aug 12 23:02:03 craig-desktop kernel: [    0.000000] ACPI: IRQ14 used by override.

Aug 12 23:02:03 craig-desktop kernel: [    0.000000] ACPI: IRQ15 used by override.

Aug 12 23:02:03 craig-desktop kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs

Aug 12 23:02:03 craig-desktop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information

Aug 12 23:02:03 craig-desktop kernel: [    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)

Aug 12 23:02:03 craig-desktop kernel: [    0.000000] Detected 2211.355 MHz processor.

Aug 12 23:02:03 craig-desktop kernel: [   34.725605] Built 1 zonelists.  Total pages: 520177

Aug 12 23:02:03 craig-desktop kernel: [   34.725608] Kernel command line: root=UUID=97895fc0-c36a-4ed5-ba4d-2367366fda60 ro quiet splash

Aug 12 23:02:03 craig-desktop kernel: [   34.725721] mapped APIC to ffffd000 (fee00000)

Aug 12 23:02:03 craig-desktop kernel: [   34.725724] mapped IOAPIC to ffffc000 (fec00000)

Aug 12 23:02:03 craig-desktop kernel: [   34.725727] Enabling fast FPU save and restore... done.

Aug 12 23:02:03 craig-desktop kernel: [   34.725729] Enabling unmasked SIMD FPU exception support... done.

Aug 12 23:02:03 craig-desktop kernel: [   34.725736] Initializing CPU#0

Aug 12 23:02:03 craig-desktop kernel: [   34.725771] PID hash table entries: 4096 (order: 12, 16384 bytes)

Aug 12 23:02:03 craig-desktop kernel: [   34.725824] spurious 8259A interrupt: IRQ7.

Aug 12 23:02:03 craig-desktop kernel: [   34.727861] Console: colour VGA+ 80x25

Aug 12 23:02:03 craig-desktop kernel: [   34.728262] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)

Aug 12 23:02:03 craig-desktop kernel: [   34.728631] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)

Aug 12 23:02:03 craig-desktop kernel: [   34.784533] Memory: 2067764k/2097088k available (1992k kernel code, 27936k reserved, 893k data, 328k init, 1179584k highmem)

Aug 12 23:02:03 craig-desktop kernel: [   34.784541] virtual kernel memory layout:

Aug 12 23:02:03 craig-desktop kernel: [   34.784542]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)

Aug 12 23:02:03 craig-desktop kernel: [   34.784543]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)

Aug 12 23:02:03 craig-desktop kernel: [   34.784544]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)

Aug 12 23:02:03 craig-desktop kernel: [   34.784546]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)

Aug 12 23:02:03 craig-desktop kernel: [   34.784547]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB)

Aug 12 23:02:03 craig-desktop kernel: [   34.784548]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB)

Aug 12 23:02:03 craig-desktop kernel: [   34.784549]       .text : 0xc0100000 - 0xc02f2264   (1992 kB)

Aug 12 23:02:03 craig-desktop kernel: [   34.784551] Checking if this processor honours the WP bit even in supervisor mode... Ok.

Aug 12 23:02:03 craig-desktop kernel: [   34.861763] Calibrating delay using timer specific routine.. 4425.44 BogoMIPS (lpj=8850885)

Aug 12 23:02:03 craig-desktop kernel: [   34.861799] Security Framework v1.0.0 initialized

Aug 12 23:02:03 craig-desktop kernel: [   34.861805] SELinux:  Disabled at boot.

Aug 12 23:02:03 craig-desktop kernel: [   34.861818] Mount-cache hash table entries: 512

Aug 12 23:02:03 craig-desktop kernel: [   34.861935] CPU: After generic identify, caps: 178bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000003

Aug 12 23:02:03 craig-desktop kernel: [   34.861942] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)

Aug 12 23:02:03 craig-desktop kernel: [   34.861944] CPU: L2 Cache: 1024K (64 bytes/line)

Aug 12 23:02:03 craig-desktop kernel: [   34.861947] CPU 0(2) -> Core 0

Aug 12 23:02:03 craig-desktop kernel: [   34.861948] CPU: After all inits, caps: 178bfbff e3d3fbff 00000000 00000410 00000001 00000000 00000003

Aug 12 23:02:03 craig-desktop kernel: [   34.861958] Compat vDSO mapped to ffffe000.

Aug 12 23:02:03 craig-desktop kernel: [   34.861962] Remapping vsyscall page to ffffe000

Aug 12 23:02:03 craig-desktop kernel: [   34.861970] Checking 'hlt' instruction... OK.

Aug 12 23:02:03 craig-desktop kernel: [   34.877879] SMP alternatives: switching to UP code

Aug 12 23:02:03 craig-desktop kernel: [   34.878231] Early unpacking initramfs... done

Aug 12 23:02:03 craig-desktop kernel: [   35.138775] ACPI: Core revision 20060707

Aug 12 23:02:03 craig-desktop kernel: [   35.141080] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.

Aug 12 23:02:03 craig-desktop kernel: [   35.145011] CPU0: AMD Athlon(tm) 64 X2 Dual Core Processor 4400+ stepping 02

Aug 12 23:02:03 craig-desktop kernel: [   35.145029] SMP alternatives: switching to SMP code

Aug 12 23:02:03 craig-desktop kernel: [   35.145116] Booting processor 1/1 eip 3000

Aug 12 23:02:03 craig-desktop kernel: [   35.155659] Initializing CPU#1

Aug 12 23:02:03 craig-desktop kernel: [   35.234062] Calibrating delay using timer specific routine.. 4422.99 BogoMIPS (lpj=8845982)

Aug 12 23:02:03 craig-desktop kernel: [   35.234069] CPU: After generic identify, caps: 178bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000003

Aug 12 23:02:03 craig-desktop kernel: [   35.234074] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)

Aug 12 23:02:03 craig-desktop kernel: [   35.234076] CPU: L2 Cache: 1024K (64 bytes/line)

Aug 12 23:02:03 craig-desktop kernel: [   35.234078] CPU 1(2) -> Core 1

Aug 12 23:02:03 craig-desktop kernel: [   35.234080] CPU: After all inits, caps: 178bfbff e3d3fbff 00000000 00000410 00000001 00000000 00000003

Aug 12 23:02:03 craig-desktop kernel: [   35.233969] CPU1: AMD Athlon(tm) 64 X2 Dual Core Processor 4400+ stepping 02

Aug 12 23:02:03 craig-desktop kernel: [   35.233978] Total of 2 processors activated (8848.43 BogoMIPS).

Aug 12 23:02:03 craig-desktop kernel: [   35.234116] ENABLING IO-APIC IRQs

Aug 12 23:02:03 craig-desktop kernel: [   35.234296] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1

Aug 12 23:02:03 craig-desktop kernel: [   35.381717] checking TSC synchronization across 2 CPUs: 

Aug 12 23:02:03 craig-desktop kernel: [    0.000001] CPU#0 had -167 usecs TSC skew, fixed it up.

Aug 12 23:02:03 craig-desktop kernel: [    0.000003] CPU#1 had 167 usecs TSC skew, fixed it up.

Aug 12 23:02:03 craig-desktop kernel: [    0.004000] Brought up 2 CPUs

Aug 12 23:02:03 craig-desktop kernel: [    0.058175] migration_cost=508

Aug 12 23:02:03 craig-desktop kernel: [    0.058392] Booting paravirtualized kernel on bare hardware

Aug 12 23:02:03 craig-desktop kernel: [    0.058443] Time: 23:01:37  Date: 07/12/107

Aug 12 23:02:03 craig-desktop kernel: [    0.058478] NET: Registered protocol family 16

Aug 12 23:02:03 craig-desktop kernel: [    0.058549] EISA bus registered

Aug 12 23:02:03 craig-desktop kernel: [    0.058552] ACPI: bus type pci registered

Aug 12 23:02:03 craig-desktop kernel: [    0.063208] PCI: PCI BIOS revision 3.00 entry at 0xf2560, last bus=5

Aug 12 23:02:03 craig-desktop kernel: [    0.063210] PCI: Using configuration type 1

Aug 12 23:02:03 craig-desktop kernel: [    0.063212] Setting up standard PCI resources

Aug 12 23:02:03 craig-desktop kernel: [    0.074034] ACPI: Interpreter enabled

Aug 12 23:02:03 craig-desktop kernel: [    0.074036] ACPI: Using IOAPIC for interrupt routing

Aug 12 23:02:03 craig-desktop kernel: [    0.074483] ACPI: PCI Root Bridge [PCI0] (0000:00)

Aug 12 23:02:03 craig-desktop kernel: [    0.074487] PCI: Probing PCI hardware (bus 00)

Aug 12 23:02:03 craig-desktop kernel: [    0.074985] PCI: Transparent bridge - 0000:00:09.0

Aug 12 23:02:03 craig-desktop kernel: [    0.075168] Boot video device is 0000:01:00.0

Aug 12 23:02:03 craig-desktop kernel: [    0.075221] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]

Aug 12 23:02:03 craig-desktop kernel: [    0.145231] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]

Aug 12 23:02:03 craig-desktop kernel: [    0.146856] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.

Aug 12 23:02:03 craig-desktop kernel: [    0.147129] ACPI: PCI Interrupt Link [LNK2] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.

Aug 12 23:02:03 craig-desktop kernel: [    0.147400] ACPI: PCI Interrupt Link [LNK3] (IRQs 3 4 *5 7 9 10 11 12 14 15)

Aug 12 23:02:03 craig-desktop kernel: [    0.147671] ACPI: PCI Interrupt Link [LNK4] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.

Aug 12 23:02:03 craig-desktop kernel: [    0.147941] ACPI: PCI Interrupt Link [LNK5] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.

Aug 12 23:02:03 craig-desktop kernel: [    0.148216] ACPI: PCI Interrupt Link [LUBA] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.

Aug 12 23:02:03 craig-desktop kernel: [    0.148490] ACPI: PCI Interrupt Link [LUBB] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.

Aug 12 23:02:03 craig-desktop kernel: [    0.148762] ACPI: PCI Interrupt Link [LMAC] (IRQs 3 4 5 7 9 10 *11 12 14 15)

Aug 12 23:02:03 craig-desktop kernel: [    0.149034] ACPI: PCI Interrupt Link [LACI] (IRQs *3 4 5 7 9 10 11 12 14 15)

Aug 12 23:02:03 craig-desktop kernel: [    0.149304] ACPI: PCI Interrupt Link [LMCI] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.

Aug 12 23:02:03 craig-desktop kernel: [    0.149577] ACPI: PCI Interrupt Link [LSMB] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.

Aug 12 23:02:03 craig-desktop kernel: [    0.149849] ACPI: PCI Interrupt Link [LUB2] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.

Aug 12 23:02:03 craig-desktop kernel: [    0.150120] ACPI: PCI Interrupt Link [LIDE] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.

Aug 12 23:02:03 craig-desktop kernel: [    0.150401] ACPI: PCI Interrupt Link [LSID] (IRQs 3 4 5 7 9 10 *11 12 14 15)

Aug 12 23:02:03 craig-desktop kernel: [    0.150681] ACPI: PCI Interrupt Link [LFID] (IRQs 3 4 *5 7 9 10 11 12 14 15)

Aug 12 23:02:03 craig-desktop kernel: [    0.150962] ACPI: PCI Interrupt Link [LPCA] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.

Aug 12 23:02:03 craig-desktop kernel: [    0.151271] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.

Aug 12 23:02:03 craig-desktop kernel: [    0.151575] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.

Aug 12 23:02:03 craig-desktop kernel: [    0.151882] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.

Aug 12 23:02:03 craig-desktop kernel: [    0.152187] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.

Aug 12 23:02:03 craig-desktop kernel: [    0.152420] ACPI: PCI Interrupt Link [APC5] (IRQs *16), disabled.

Aug 12 23:02:03 craig-desktop kernel: [    0.152736] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0, disabled.

Aug 12 23:02:03 craig-desktop kernel: [    0.153051] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.

Aug 12 23:02:03 craig-desktop kernel: [    0.153367] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0, disabled.

Aug 12 23:02:03 craig-desktop kernel: [    0.153682] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0, disabled.

Aug 12 23:02:03 craig-desktop kernel: [    0.153997] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled.

Aug 12 23:02:03 craig-desktop kernel: [    0.154311] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0, disabled.

Aug 12 23:02:03 craig-desktop kernel: [    0.154630] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0, disabled.

Aug 12 23:02:03 craig-desktop kernel: [    0.154945] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.

Aug 12 23:02:03 craig-desktop kernel: [    0.155269] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0, disabled.

Aug 12 23:02:03 craig-desktop kernel: [    0.155597] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0, disabled.

Aug 12 23:02:03 craig-desktop kernel: [    0.155922] ACPI: PCI Interrupt Link [APCP] (IRQs 20 21 22 23) *0, disabled.

Aug 12 23:02:03 craig-desktop kernel: [    0.158944] Linux Plug and Play Support v0.97 (c) Adam Belay

Aug 12 23:02:03 craig-desktop kernel: [    0.158952] pnp: PnP ACPI init

Aug 12 23:02:03 craig-desktop kernel: [    0.164179] pnp: PnP ACPI: found 14 devices

Aug 12 23:02:03 craig-desktop kernel: [    0.164182] PnPBIOS: Disabled by ACPI PNP

Aug 12 23:02:03 craig-desktop kernel: [    0.164213] PCI: Using ACPI for IRQ routing

Aug 12 23:02:03 craig-desktop kernel: [    0.164217] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report

Aug 12 23:02:03 craig-desktop kernel: [    0.217778] NET: Registered protocol family 8

Aug 12 23:02:03 craig-desktop kernel: [    0.217779] NET: Registered protocol family 20

Aug 12 23:02:03 craig-desktop kernel: [    0.218155] pnp: 00:01: ioport range 0x4000-0x407f could not be reserved

Aug 12 23:02:03 craig-desktop kernel: [    0.218157] pnp: 00:01: ioport range 0x4080-0x40ff has been reserved

Aug 12 23:02:03 craig-desktop kernel: [    0.218160] pnp: 00:01: ioport range 0x4400-0x447f has been reserved

Aug 12 23:02:03 craig-desktop kernel: [    0.218162] pnp: 00:01: ioport range 0x4480-0x44ff could not be reserved

Aug 12 23:02:03 craig-desktop kernel: [    0.218164] pnp: 00:01: ioport range 0x4800-0x487f has been reserved

Aug 12 23:02:03 craig-desktop kernel: [    0.218167] pnp: 00:01: ioport range 0x4880-0x48ff has been reserved

Aug 12 23:02:03 craig-desktop kernel: [    0.218385] PCI: Bridge: 0000:00:09.0

Aug 12 23:02:03 craig-desktop kernel: [    0.218387]   IO window: disabled.

Aug 12 23:02:03 craig-desktop kernel: [    0.218389]   MEM window: disabled.

Aug 12 23:02:03 craig-desktop kernel: [    0.218391]   PREFETCH window: disabled.

Aug 12 23:02:03 craig-desktop kernel: [    0.218393] PCI: Bridge: 0000:00:0b.0

Aug 12 23:02:03 craig-desktop kernel: [    0.218394]   IO window: disabled.

Aug 12 23:02:03 craig-desktop kernel: [    0.218396]   MEM window: disabled.

Aug 12 23:02:03 craig-desktop kernel: [    0.218398]   PREFETCH window: disabled.

Aug 12 23:02:03 craig-desktop kernel: [    0.218400] PCI: Bridge: 0000:00:0c.0

Aug 12 23:02:03 craig-desktop kernel: [    0.218401]   IO window: disabled.

Aug 12 23:02:03 craig-desktop kernel: [    0.218403]   MEM window: disabled.

Aug 12 23:02:03 craig-desktop kernel: [    0.218405]   PREFETCH window: disabled.

Aug 12 23:02:03 craig-desktop kernel: [    0.218407] PCI: Bridge: 0000:00:0d.0

Aug 12 23:02:03 craig-desktop kernel: [    0.218408]   IO window: disabled.

Aug 12 23:02:03 craig-desktop kernel: [    0.218410]   MEM window: disabled.

Aug 12 23:02:03 craig-desktop kernel: [    0.218411]   PREFETCH window: disabled.

Aug 12 23:02:03 craig-desktop kernel: [    0.218414] PCI: Bridge: 0000:00:0e.0

Aug 12 23:02:03 craig-desktop kernel: [    0.218415]   IO window: disabled.

Aug 12 23:02:03 craig-desktop kernel: [    0.218417]   MEM window: d0000000-d2ffffff

Aug 12 23:02:03 craig-desktop kernel: [    0.218420]   PREFETCH window: c0000000-cfffffff

Aug 12 23:02:03 craig-desktop kernel: [    0.218426] PCI: Setting latency timer of device 0000:00:09.0 to 64

Aug 12 23:02:03 craig-desktop kernel: [    0.218432] PCI: Setting latency timer of device 0000:00:0b.0 to 64

Aug 12 23:02:03 craig-desktop kernel: [    0.218437] PCI: Setting latency timer of device 0000:00:0c.0 to 64

Aug 12 23:02:03 craig-desktop kernel: [    0.218441] PCI: Setting latency timer of device 0000:00:0d.0 to 64

Aug 12 23:02:03 craig-desktop kernel: [    0.218446] PCI: Setting latency timer of device 0000:00:0e.0 to 64

Aug 12 23:02:03 craig-desktop kernel: [    0.218477] NET: Registered protocol family 2

Aug 12 23:02:03 craig-desktop kernel: [    0.260025] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)

Aug 12 23:02:03 craig-desktop kernel: [    0.260165] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)

Aug 12 23:02:03 craig-desktop kernel: [    0.260938] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)

Aug 12 23:02:03 craig-desktop kernel: [    0.261324] TCP: Hash tables configured (established 131072 bind 65536)

Aug 12 23:02:03 craig-desktop kernel: [    0.261327] TCP reno registered

Aug 12 23:02:03 craig-desktop kernel: [    0.276089] checking if image is initramfs... it is

Aug 12 23:02:03 craig-desktop kernel: [    0.790863] Freeing initrd memory: 7006k freed

Aug 12 23:02:03 craig-desktop kernel: [    1.344000] audit: initializing netlink socket (disabled)

Aug 12 23:02:03 craig-desktop kernel: [    1.344000] audit(1186959698.528:1): initialized

Aug 12 23:02:03 craig-desktop kernel: [    1.344000] highmem bounce pool size: 64 pages

Aug 12 23:02:03 craig-desktop kernel: [    1.344000] VFS: Disk quotas dquot_6.5.1

Aug 12 23:02:03 craig-desktop kernel: [    1.344000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)

Aug 12 23:02:03 craig-desktop kernel: [    1.344000] io scheduler noop registered

Aug 12 23:02:03 craig-desktop kernel: [    1.344000] io scheduler anticipatory registered

Aug 12 23:02:03 craig-desktop kernel: [    1.344000] io scheduler deadline registered

Aug 12 23:02:03 craig-desktop kernel: [    1.344000] io scheduler cfq registered (default)

Aug 12 23:02:03 craig-desktop kernel: [    1.360000] PCI: Found disabled HT MSI Mapping on 0000:00:0b.0

Aug 12 23:02:03 craig-desktop kernel: [    1.360000] PCI: Found enabled HT MSI Mapping on 0000:00:00.0

Aug 12 23:02:03 craig-desktop kernel: [    1.360000] PCI: Found disabled HT MSI Mapping on 0000:00:0c.0

Aug 12 23:02:03 craig-desktop kernel: [    1.360000] PCI: Found enabled HT MSI Mapping on 0000:00:00.0

Aug 12 23:02:03 craig-desktop kernel: [    1.360000] PCI: Found disabled HT MSI Mapping on 0000:00:0d.0

Aug 12 23:02:03 craig-desktop kernel: [    1.360000] PCI: Found enabled HT MSI Mapping on 0000:00:00.0

Aug 12 23:02:03 craig-desktop kernel: [    1.360000] PCI: Found disabled HT MSI Mapping on 0000:00:0e.0

Aug 12 23:02:03 craig-desktop kernel: [    1.360000] PCI: Found enabled HT MSI Mapping on 0000:00:00.0

Aug 12 23:02:03 craig-desktop kernel: [    1.360000] PCI: Setting latency timer of device 0000:00:0b.0 to 64

Aug 12 23:02:03 craig-desktop kernel: [    1.360000] assign_interrupt_mode Found MSI capability

Aug 12 23:02:03 craig-desktop kernel: [    1.360000] Allocate Port Service[0000:00:0b.0:pcie00]

Aug 12 23:02:03 craig-desktop kernel: [    1.360000] PCI: Setting latency timer of device 0000:00:0c.0 to 64

Aug 12 23:02:03 craig-desktop kernel: [    1.360000] assign_interrupt_mode Found MSI capability

Aug 12 23:02:03 craig-desktop kernel: [    1.360000] Allocate Port Service[0000:00:0c.0:pcie00]

Aug 12 23:02:03 craig-desktop kernel: [    1.360000] PCI: Setting latency timer of device 0000:00:0d.0 to 64

Aug 12 23:02:03 craig-desktop kernel: [    1.360000] assign_interrupt_mode Found MSI capability

Aug 12 23:02:03 craig-desktop kernel: [    1.360000] Allocate Port Service[0000:00:0d.0:pcie00]

Aug 12 23:02:03 craig-desktop kernel: [    1.360000] PCI: Setting latency timer of device 0000:00:0e.0 to 64

Aug 12 23:02:03 craig-desktop kernel: [    1.360000] assign_interrupt_mode Found MSI capability

Aug 12 23:02:03 craig-desktop kernel: [    1.360000] Allocate Port Service[0000:00:0e.0:pcie00]

Aug 12 23:02:03 craig-desktop kernel: [    1.360000] isapnp: Scanning for PnP cards...

Aug 12 23:02:03 craig-desktop kernel: [    1.712000] isapnp: No Plug & Play device found

Aug 12 23:02:03 craig-desktop kernel: [    1.728000] Real Time Clock Driver v1.12ac

Aug 12 23:02:03 craig-desktop kernel: [    1.728000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled

Aug 12 23:02:03 craig-desktop kernel: [    1.728000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A

Aug 12 23:02:03 craig-desktop kernel: [    1.728000] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A

Aug 12 23:02:03 craig-desktop kernel: [    1.728000] mice: PS/2 mouse device common for all mice

Aug 12 23:02:03 craig-desktop kernel: [    1.732000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize

Aug 12 23:02:03 craig-desktop kernel: [    1.732000] input: Macintosh mouse button emulation as /class/input/input0

Aug 12 23:02:03 craig-desktop kernel: [    1.732000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2

Aug 12 23:02:03 craig-desktop kernel: [    1.732000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx

Aug 12 23:02:03 craig-desktop kernel: [    1.732000] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1

Aug 12 23:02:03 craig-desktop kernel: [    1.732000] PNP: PS/2 controller doesn't have AUX irq; using default 12

Aug 12 23:02:03 craig-desktop kernel: [    1.988000] serio: i8042 KBD port at 0x60,0x64 irq 1

Aug 12 23:02:03 craig-desktop kernel: [    1.988000] EISA: Probing bus 0 at eisa.0

Aug 12 23:02:03 craig-desktop kernel: [    1.988000] Cannot allocate resource for EISA slot 4

Aug 12 23:02:03 craig-desktop kernel: [    1.988000] EISA: Detected 0 cards.

Aug 12 23:02:03 craig-desktop kernel: [    2.016000] TCP cubic registered

Aug 12 23:02:03 craig-desktop kernel: [    2.016000] NET: Registered protocol family 1

Aug 12 23:02:03 craig-desktop kernel: [    2.016000] Starting balanced_irq

Aug 12 23:02:03 craig-desktop kernel: [    2.016000] Using IPI No-Shortcut mode

Aug 12 23:02:03 craig-desktop kernel: [    2.016000] input: AT Translated Set 2 keyboard as /class/input/input1

Aug 12 23:02:03 craig-desktop kernel: [    2.016000] ACPI: (supports S0 S1 S3 S4 S5)

Aug 12 23:02:03 craig-desktop kernel: [    2.016000]   Magic number: 3:316:49

Aug 12 23:02:03 craig-desktop kernel: [    2.016000] Freeing unused kernel memory: 328k freed

Aug 12 23:02:03 craig-desktop kernel: [    2.020000] Time: acpi_pm clocksource has been installed.

Aug 12 23:02:03 craig-desktop kernel: [    3.136000] Capability LSM initialized

Aug 12 23:02:03 craig-desktop kernel: [    3.168000] ACPI: Fan [FAN] (on)

Aug 12 23:02:03 craig-desktop kernel: [    3.172000] ACPI: Thermal Zone [THRM] (40 C)

Aug 12 23:02:03 craig-desktop kernel: [    3.532000] SCSI subsystem initialized

Aug 12 23:02:03 craig-desktop kernel: [    3.536000] libata version 2.20 loaded.

Aug 12 23:02:03 craig-desktop kernel: [    3.536000] sata_nv 0000:00:07.0: version 3.3

Aug 12 23:02:03 craig-desktop kernel: [    3.536000] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 23

Aug 12 23:02:03 craig-desktop kernel: [    3.536000] ACPI: PCI Interrupt 0000:00:07.0[A] -> Link [APSI] -> GSI 23 (level, low) -> IRQ 16

Aug 12 23:02:03 craig-desktop kernel: [    3.536000] sata_nv 0000:00:07.0: Using ADMA mode

Aug 12 23:02:03 craig-desktop kernel: [    3.536000] PCI: Setting latency timer of device 0000:00:07.0 to 64

Aug 12 23:02:03 craig-desktop kernel: [    3.536000] ata1: SATA max UDMA/133 cmd 0xf882a480 ctl 0xf882a4a0 bmdma 0x0001d800 irq 16

Aug 12 23:02:03 craig-desktop kernel: [    3.560000] ata2: SATA max UDMA/133 cmd 0xf882a580 ctl 0xf882a5a0 bmdma 0x0001d808 irq 16

Aug 12 23:02:03 craig-desktop kernel: [    3.560000] scsi0 : sata_nv

Aug 12 23:02:03 craig-desktop kernel: [    3.584000] usbcore: registered new interface driver usbfs

Aug 12 23:02:03 craig-desktop kernel: [    3.584000] usbcore: registered new interface driver hub

Aug 12 23:02:03 craig-desktop kernel: [    3.588000] usbcore: registered new device driver usb

Aug 12 23:02:03 craig-desktop kernel: [    3.604000] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.59.

Aug 12 23:02:03 craig-desktop kernel: [    3.608000] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver

Aug 12 23:02:03 craig-desktop kernel: [    3.872000] ata1: SATA link down (SStatus 0 SControl 300)

Aug 12 23:02:03 craig-desktop kernel: [    3.872000] scsi1 : sata_nv

Aug 12 23:02:03 craig-desktop kernel: [    4.348000] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)

Aug 12 23:02:03 craig-desktop kernel: [    4.364000] ata2.00: ata_hpa_resize 1: sectors = 240121728, hpa_sectors = 240121728

Aug 12 23:02:03 craig-desktop kernel: [    4.364000] ata2.00: ATA-7: Maxtor 6Y120M0, YAR51EW0, max UDMA/133

Aug 12 23:02:03 craig-desktop kernel: [    4.364000] ata2.00: 240121728 sectors, multi 1: LBA 

Aug 12 23:02:03 craig-desktop kernel: [    4.376000] ata2.00: ata_hpa_resize 1: sectors = 240121728, hpa_sectors = 240121728

Aug 12 23:02:03 craig-desktop kernel: [    4.376000] ata2.00: configured for UDMA/133

Aug 12 23:02:03 craig-desktop kernel: [    4.376000] scsi 1:0:0:0: Direct-Access     ATA      Maxtor 6Y120M0   YAR5 PQ: 0 ANSI: 5

Aug 12 23:02:03 craig-desktop kernel: [    4.376000] ata2: bounce limit 0xFFFFFFFFFFFFFFFF, segment boundary 0xFFFFFFFF, hw segs 61

Aug 12 23:02:03 craig-desktop kernel: [    4.376000] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 22

Aug 12 23:02:03 craig-desktop kernel: [    4.376000] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [APSJ] -> GSI 22 (level, low) -> IRQ 17

Aug 12 23:02:03 craig-desktop kernel: [    4.376000] sata_nv 0000:00:08.0: Using ADMA mode

Aug 12 23:02:03 craig-desktop kernel: [    4.376000] PCI: Setting latency timer of device 0000:00:08.0 to 64

Aug 12 23:02:03 craig-desktop kernel: [    4.376000] ata3: SATA max UDMA/133 cmd 0xf8868480 ctl 0xf88684a0 bmdma 0x0001c400 irq 17

Aug 12 23:02:03 craig-desktop kernel: [    4.376000] ata4: SATA max UDMA/133 cmd 0xf8868580 ctl 0xf88685a0 bmdma 0x0001c408 irq 17

Aug 12 23:02:03 craig-desktop kernel: [    4.376000] scsi2 : sata_nv

Aug 12 23:02:03 craig-desktop kernel: [    4.688000] ata3: SATA link down (SStatus 0 SControl 300)

Aug 12 23:02:03 craig-desktop kernel: [    4.688000] scsi3 : sata_nv

Aug 12 23:02:03 craig-desktop kernel: [    5.004000] ata4: SATA link down (SStatus 0 SControl 300)

Aug 12 23:02:03 craig-desktop kernel: [    5.008000] NFORCE-CK804: IDE controller at PCI slot 0000:00:06.0

Aug 12 23:02:03 craig-desktop kernel: [    5.008000] NFORCE-CK804: chipset revision 242

Aug 12 23:02:03 craig-desktop kernel: [    5.008000] NFORCE-CK804: not 100%% native mode: will probe irqs later

Aug 12 23:02:03 craig-desktop kernel: [    5.008000] NFORCE-CK804: BIOS didn't set cable bits correctly. Enabling workaround.

Aug 12 23:02:03 craig-desktop kernel: [    5.008000] NFORCE-CK804: 0000:00:06.0 (rev f2) UDMA133 controller

Aug 12 23:02:03 craig-desktop kernel: [    5.008000]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:DMA

Aug 12 23:02:03 craig-desktop kernel: [    5.008000]     ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:DMA, hdd:DMA

Aug 12 23:02:03 craig-desktop kernel: [    5.008000] Probing IDE interface ide0...

Aug 12 23:02:03 craig-desktop kernel: [    5.300000] hda: ST3320620A, ATA DISK drive

Aug 12 23:02:03 craig-desktop kernel: [    5.976000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14

Aug 12 23:02:03 craig-desktop kernel: [    5.976000] Probing IDE interface ide1...

Aug 12 23:02:03 craig-desktop kernel: [    6.716000] hdc: PIONEER DVD-RW DVR-112D, ATAPI CD/DVD-ROM drive

Aug 12 23:02:03 craig-desktop kernel: [    7.000000] hdd: HDS722512VLAT20, ATA DISK drive

Aug 12 23:02:03 craig-desktop kernel: [    7.060000] ide1 at 0x170-0x177,0x376 on irq 15

Aug 12 23:02:03 craig-desktop kernel: [    7.068000] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 21

Aug 12 23:02:03 craig-desktop kernel: [    7.068000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [APCF] -> GSI 21 (level, low) -> IRQ 18

Aug 12 23:02:03 craig-desktop kernel: [    7.068000] PCI: Setting latency timer of device 0000:00:02.0 to 64

Aug 12 23:02:03 craig-desktop kernel: [    7.068000] ohci_hcd 0000:00:02.0: OHCI Host Controller

Aug 12 23:02:03 craig-desktop kernel: [    7.068000] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1

Aug 12 23:02:03 craig-desktop kernel: [    7.068000] ohci_hcd 0000:00:02.0: irq 18, io mem 0xd3004000

Aug 12 23:02:03 craig-desktop kernel: [    7.128000] usb usb1: configuration #1 chosen from 1 choice

Aug 12 23:02:03 craig-desktop kernel: [    7.128000] hub 1-0:1.0: USB hub found

Aug 12 23:02:03 craig-desktop kernel: [    7.128000] hub 1-0:1.0: 10 ports detected

Aug 12 23:02:03 craig-desktop kernel: [    7.236000] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 20

Aug 12 23:02:03 craig-desktop kernel: [    7.236000] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [APCL] -> GSI 20 (level, low) -> IRQ 19

Aug 12 23:02:03 craig-desktop kernel: [    7.236000] PCI: Setting latency timer of device 0000:00:02.1 to 64

Aug 12 23:02:03 craig-desktop kernel: [    7.236000] ehci_hcd 0000:00:02.1: EHCI Host Controller

Aug 12 23:02:03 craig-desktop kernel: [    7.236000] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2

Aug 12 23:02:03 craig-desktop kernel: [    7.236000] ehci_hcd 0000:00:02.1: debug port 1

Aug 12 23:02:03 craig-desktop kernel: [    7.236000] PCI: cache line size of 64 is not supported by device 0000:00:02.1

Aug 12 23:02:03 craig-desktop kernel: [    7.236000] ehci_hcd 0000:00:02.1: irq 19, io mem 0xfeb00000

Aug 12 23:02:03 craig-desktop kernel: [    7.236000] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004

Aug 12 23:02:03 craig-desktop kernel: [    7.236000] usb usb2: configuration #1 chosen from 1 choice

Aug 12 23:02:03 craig-desktop kernel: [    7.236000] hub 2-0:1.0: USB hub found

Aug 12 23:02:03 craig-desktop kernel: [    7.236000] hub 2-0:1.0: 10 ports detected

Aug 12 23:02:03 craig-desktop kernel: [    7.344000] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 23

Aug 12 23:02:03 craig-desktop kernel: [    7.344000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [APCH] -> GSI 23 (level, low) -> IRQ 16

Aug 12 23:02:03 craig-desktop kernel: [    7.344000] PCI: Setting latency timer of device 0000:00:0a.0 to 64

Aug 12 23:02:03 craig-desktop kernel: [    7.344000] forcedeth: using HIGHDMA

Aug 12 23:02:03 craig-desktop kernel: [    7.868000] eth0: forcedeth.c: subsystem: 01043:8141 bound to 0000:00:0a.0

Aug 12 23:02:03 craig-desktop kernel: [    7.876000] SCSI device sda: 240121728 512-byte hdwr sectors (122942 MB)

Aug 12 23:02:03 craig-desktop kernel: [    7.876000] sda: Write Protect is off

Aug 12 23:02:03 craig-desktop kernel: [    7.876000] sda: Mode Sense: 00 3a 00 00

Aug 12 23:02:03 craig-desktop kernel: [    7.876000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA

Aug 12 23:02:03 craig-desktop kernel: [    7.876000] SCSI device sda: 240121728 512-byte hdwr sectors (122942 MB)

Aug 12 23:02:03 craig-desktop kernel: [    7.876000] sda: Write Protect is off

Aug 12 23:02:03 craig-desktop kernel: [    7.876000] sda: Mode Sense: 00 3a 00 00

Aug 12 23:02:03 craig-desktop kernel: [    7.876000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA

Aug 12 23:02:03 craig-desktop kernel: [    7.876000]  sda: sda1

Aug 12 23:02:03 craig-desktop kernel: [    7.876000] sd 1:0:0:0: Attached scsi disk sda

Aug 12 23:02:03 craig-desktop kernel: [    7.880000] hda: max request size: 512KiB

Aug 12 23:02:03 craig-desktop kernel: [    7.884000] sd 1:0:0:0: Attached scsi generic sg0 type 0

Aug 12 23:02:03 craig-desktop kernel: [    7.884000] usb 1-4: new low speed USB device using ohci_hcd and address 2

Aug 12 23:02:03 craig-desktop kernel: [    7.924000] hda: 625142448 sectors (320072 MB) w/16384KiB Cache, CHS=38913/255/63, UDMA(100)

Aug 12 23:02:03 craig-desktop kernel: [    7.948000] hda: cache flushes supported

Aug 12 23:02:03 craig-desktop kernel: [    7.948000]  hda: hda1 hda2 hda3 hda4 < hda5 >

Aug 12 23:02:03 craig-desktop kernel: [    7.988000] hdd: max request size: 512KiB

Aug 12 23:02:03 craig-desktop kernel: [    7.988000] hdd: 241254720 sectors (123522 MB) w/1794KiB Cache, CHS=16383/255/63, UDMA(100)

Aug 12 23:02:03 craig-desktop kernel: [    7.988000] hdd: cache flushes supported

Aug 12 23:02:03 craig-desktop kernel: [    7.988000]  hdd: hdd1

Aug 12 23:02:03 craig-desktop kernel: [    8.000000] hdc: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 2000kB Cache, UDMA(66)

Aug 12 23:02:03 craig-desktop kernel: [    8.000000] Uniform CD-ROM driver Revision: 3.20

Aug 12 23:02:03 craig-desktop kernel: [    8.112000] usb 1-4: configuration #1 chosen from 1 choice

Aug 12 23:02:03 craig-desktop kernel: [    8.124000] usbcore: registered new interface driver hiddev

Aug 12 23:02:03 craig-desktop kernel: [    8.132000] input: Logitech USB Receiver as /class/input/input2

Aug 12 23:02:03 craig-desktop kernel: [    8.136000] input: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:02.0-4

Aug 12 23:02:03 craig-desktop kernel: [    8.136000] usbcore: registered new interface driver usbhid

Aug 12 23:02:03 craig-desktop kernel: [    8.136000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver

Aug 12 23:02:03 craig-desktop kernel: [    8.256000] Attempting manual resume

Aug 12 23:02:03 craig-desktop kernel: [    8.256000] swsusp: Resume From Partition 3:5

Aug 12 23:02:03 craig-desktop kernel: [    8.256000] PM: Checking swsusp image.

Aug 12 23:02:03 craig-desktop kernel: [    8.256000] PM: Resume from disk failed.

Aug 12 23:02:03 craig-desktop kernel: [    8.268000] EXT3-fs: INFO: recovery required on readonly filesystem.

Aug 12 23:02:03 craig-desktop kernel: [    8.268000] EXT3-fs: write access will be enabled during recovery.

Aug 12 23:02:03 craig-desktop kernel: [   10.516000] kjournald starting.  Commit interval 5 seconds

Aug 12 23:02:03 craig-desktop kernel: [   10.516000] EXT3-fs: recovery complete.

Aug 12 23:02:03 craig-desktop kernel: [   10.532000] EXT3-fs: mounted filesystem with ordered data mode.

Aug 12 23:02:03 craig-desktop kernel: [   16.896000] NET: Registered protocol family 10

Aug 12 23:02:03 craig-desktop kernel: [   16.896000] lo: Disabled Privacy Extensions

Aug 12 23:02:03 craig-desktop kernel: [   17.472000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5

Aug 12 23:02:03 craig-desktop kernel: [   17.524000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4

Aug 12 23:02:03 craig-desktop kernel: [   17.824000] input: PC Speaker as /class/input/input3

Aug 12 23:02:03 craig-desktop kernel: [   17.896000] i2c_adapter i2c-0: nForce2 SMBus adapter at 0x4c00

Aug 12 23:02:03 craig-desktop kernel: [   17.896000] i2c_adapter i2c-1: nForce2 SMBus adapter at 0x4c40

Aug 12 23:02:03 craig-desktop kernel: [   17.924000] Linux agpgart interface v0.102 (c) Dave Jones

Aug 12 23:02:03 craig-desktop kernel: [   17.960000] usbcore: registered new interface driver lmpcm_usb

Aug 12 23:02:03 craig-desktop kernel: [   17.960000] ubuntu/misc/lmpcm_usb.c: v0.5.5:USB Logitech MediaPlay Cordless Mouse driver

Aug 12 23:02:03 craig-desktop kernel: [   18.136000] nvidia: module license 'NVIDIA' taints kernel.

Aug 12 23:02:03 craig-desktop kernel: [   18.388000] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18

Aug 12 23:02:03 craig-desktop kernel: [   18.388000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 20

Aug 12 23:02:03 craig-desktop kernel: [   18.388000] PCI: Setting latency timer of device 0000:01:00.0 to 64

Aug 12 23:02:03 craig-desktop kernel: [   18.388000] NVRM: loading NVIDIA UNIX x86 Kernel Module  100.14.11  Wed Jun 13 18:21:22 PDT 2007

Aug 12 23:02:03 craig-desktop kernel: [   18.452000] parport: PnPBIOS parport detected.

Aug 12 23:02:03 craig-desktop kernel: [   18.452000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]

Aug 12 23:02:03 craig-desktop kernel: [   18.544000] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 22

Aug 12 23:02:03 craig-desktop kernel: [   18.544000] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [APCJ] -> GSI 22 (level, low) -> IRQ 17

Aug 12 23:02:03 craig-desktop kernel: [   18.544000] PCI: Setting latency timer of device 0000:00:04.0 to 64

Aug 12 23:02:03 craig-desktop kernel: [   18.868000] intel8x0_measure_ac97_clock: measured 58740 usecs

Aug 12 23:02:03 craig-desktop kernel: [   18.868000] intel8x0: clocking to 46992

Aug 12 23:02:03 craig-desktop kernel: [   19.000000] fuse init (API version 7.8)

Aug 12 23:02:03 craig-desktop kernel: [   19.020000] lp0: using parport0 (interrupt-driven).

Aug 12 23:02:03 craig-desktop kernel: [   19.028000] usbcore: deregistering interface driver usbhid

Aug 12 23:02:03 craig-desktop kernel: [   19.028000] usbcore: deregistering interface driver hiddev

Aug 12 23:02:03 craig-desktop kernel: [   19.048000] usbcore: registered new interface driver hiddev

Aug 12 23:02:03 craig-desktop kernel: [   19.060000] input: Logitech USB Receiver as /class/input/input4

Aug 12 23:02:03 craig-desktop kernel: [   19.060000] input: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:02.0-4

Aug 12 23:02:03 craig-desktop kernel: [   19.060000] usbcore: registered new interface driver usbhid

Aug 12 23:02:03 craig-desktop kernel: [   19.060000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver

Aug 12 23:02:03 craig-desktop kernel: [   19.088000] Adding 1526132k swap on /dev/disk/by-uuid/ecd6bf48-cabf-4df1-8b42-4976d2b26ad4.  Priority:-1 extents:1 across:1526132k

Aug 12 23:02:03 craig-desktop kernel: [   19.204000] EXT3 FS on hda3, internal journal

Aug 12 23:02:03 craig-desktop kernel: [   21.004000] NET: Registered protocol family 17

Aug 12 23:02:03 craig-desktop kernel: [   25.008000] ibm_acpi: ec object not found

Aug 12 23:02:03 craig-desktop kernel: [   25.056000] Using specific hotkey driver

Aug 12 23:02:03 craig-desktop kernel: [   25.216000] input: Power Button (FF) as /class/input/input5

Aug 12 23:02:03 craig-desktop kernel: [   25.216000] ACPI: Power Button (FF) [PWRF]

Aug 12 23:02:03 craig-desktop kernel: [   25.216000] input: Power Button (CM) as /class/input/input6

Aug 12 23:02:03 craig-desktop kernel: [   25.216000] ACPI: Power Button (CM) [PWRB]

Aug 12 23:02:03 craig-desktop kernel: [   25.264000] No dock devices found.

Aug 12 23:02:03 craig-desktop kernel: [   25.312000] pcc_acpi: loading...

Aug 12 23:02:03 craig-desktop kernel: [   25.508000] powernow-k8: Found 2 AMD Athlon(tm) 64 X2 Dual Core Processor 4400+ processors (version 2.00.00)

Aug 12 23:02:03 craig-desktop kernel: [   25.508000] powernow-k8: MP systems not supported by PSB BIOS structure

Aug 12 23:02:03 craig-desktop kernel: [   25.508000] powernow-k8: MP systems not supported by PSB BIOS structure

Aug 12 23:02:04 craig-desktop dhcdbd: Started up.

Aug 12 23:02:04 craig-desktop NetworkManager: <information>^Istarting... 

Aug 12 23:02:04 craig-desktop avahi-daemon[5038]: Found user 'avahi' (UID 105) and group 'avahi' (GID 111).

Aug 12 23:02:04 craig-desktop avahi-daemon[5038]: Successfully dropped root privileges.

Aug 12 23:02:04 craig-desktop avahi-daemon[5038]: avahi-daemon 0.6.17 starting up.

Aug 12 23:02:04 craig-desktop avahi-daemon[5038]: Successfully called chroot().

Aug 12 23:02:04 craig-desktop avahi-daemon[5038]: Successfully dropped remaining capabilities.

Aug 12 23:02:04 craig-desktop avahi-daemon[5038]: No service found in /etc/avahi/services.

Aug 12 23:02:04 craig-desktop avahi-daemon[5038]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.0.2.

Aug 12 23:02:04 craig-desktop avahi-daemon[5038]: New relevant interface eth0.IPv4 for mDNS.

Aug 12 23:02:04 craig-desktop avahi-daemon[5038]: Network interface enumeration completed.

Aug 12 23:02:04 craig-desktop avahi-daemon[5038]: Registering new address record for fe80::217:31ff:feca:1421 on eth0.*.

Aug 12 23:02:04 craig-desktop avahi-daemon[5038]: Registering new address record for 192.168.0.2 on eth0.IPv4.

Aug 12 23:02:04 craig-desktop avahi-daemon[5038]: Registering HINFO record with values 'I686'/'LINUX'.

Aug 12 23:02:04 craig-desktop avahi-daemon[5038]: Server startup complete. Host name is craig-desktop.local. Local service cookie is 346346415.

Aug 12 23:02:05 craig-desktop kernel: [   27.896000] eth0: no IPv6 routers present

Aug 12 23:02:07 craig-desktop kernel: [   29.856000] ppdev: user-space parallel port driver

Aug 12 23:02:07 craig-desktop hpiod: 1.7.3 accepting connections at 2208... 

Aug 12 23:02:08 craig-desktop kernel: [   30.580000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)

Aug 12 23:02:08 craig-desktop kernel: [   30.580000] apm: disabled - APM is not SMP safe.

Aug 12 23:02:09 craig-desktop avgscan[5234]: Starting AVG Anti-Virus in daemon mode. 

Aug 12 23:02:09 craig-desktop avgscan[5235]: AVG Anti-Virus Daemon started.

Aug 12 23:02:09 craig-desktop avgscan[5234]: Starting AVG Anti-Virus on-access scanner. 

Aug 12 23:02:09 craig-desktop avgscan[5236]: ERROR: registration to Dazuko failed

Aug 12 23:02:09 craig-desktop anacron[5341]: Anacron 2.3 started on 2007-08-12

Aug 12 23:02:10 craig-desktop anacron[5341]: Normal exit (0 jobs run)

Aug 12 23:02:10 craig-desktop /usr/sbin/cron[5372]: (CRON) INFO (pidfile fd = 3)

Aug 12 23:02:10 craig-desktop /usr/sbin/cron[5373]: (CRON) STARTUP (fork ok)

Aug 12 23:02:10 craig-desktop /usr/sbin/cron[5373]: (CRON) INFO (Running @reboot jobs)

Aug 12 23:02:19 craig-desktop gconfd (craig-5515): starting (version 2.18.0.1), pid 5515 user 'craig'

Aug 12 23:02:19 craig-desktop gconfd (craig-5515): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0

Aug 12 23:02:19 craig-desktop gconfd (craig-5515): Resolved address "xml:readwrite:/home/craig/.gconf" to a writable configuration source at position 1

Aug 12 23:02:19 craig-desktop gconfd (craig-5515): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2

Aug 12 23:02:19 craig-desktop gconfd (craig-5515): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3

Aug 12 23:02:19 craig-desktop gconfd (craig-5515): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4

Aug 12 23:02:24 craig-desktop gconfd (craig-5515): Resolved address "xml:readwrite:/home/craig/.gconf" to a writable configuration source at position 0

Aug 12 23:02:31 craig-desktop NetworkManager: <information>^IUpdating allowed wireless network lists. 

Aug 12 23:02:31 craig-desktop NetworkManager: <WARNING>^I nm_dbus_get_networks_cb (): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 




it always seems to lock on the last bit, any help would be great, i don't want to have to reinstall, i just want to be able to fix or i'll never learn


craig


my specs are

athlon 64 x2 4400
2 gig ddr
asus a8nsli-se
nvidia 7300gs

---

### Post by texmurphy on 2007-08-13
think i may have solved it, i uninstalled network manager and so far no crashes

---

### Post by zero244 on 2007-08-13
I have found network manager a little quirky myself. Under the right scenerio it seems to crash or freeze. I am not really qualified to comment why. It may be a wireless driver problem, but none the less it can be a problem.
Its a problem that will probably be worked out at a later date.

---

### Post by texmurphy on 2007-08-14
well that worked for awhile now i get softlockup on cpu0, please note i have no wireless devices apart from my logitech mx1000 mouse, if that counts

---

