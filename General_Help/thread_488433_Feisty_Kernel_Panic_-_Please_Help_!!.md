---
title: "Feisty Kernel Panic - Please Help !!"
date: 2007-06-30
forum: General Help
---

### Post by JamesX on 2007-06-30
Since upgrading to Feisty 64bit from 6.06 LTS 64bit my NX6125 Laptop has gone from Rock Solid to Kernel Panicking nearly every 24hrs when left alone overnight.

I'm sure it has something to do with APIC as when I installed 6.06 LTS I had to use the NOAPIC and NOLAPIC options to make my system run smoothly instead of like slug with double time clock.

When I upgraded to Feisty 64Bit my Laptop kept Kernel Panicking when I left it overnight, the Laptop screen would be black, nothing at all could wake it up and the Cap's Lock key would flash - only that key and it wasn't morse code trying to tell me a message but a steady flash.

I noticed that the NOLAPIC and NOAPIC options were still present on Feisty so I removed them and the Laptop booted as normal so I assumed these options were no longer needed and the Laptop went for 3 days without freezing so I thought great - problem solved but it's since frozen twice but this time the Cap's Lock key stays solid on and not flashing but the Laptop is dead requiring a hard boot as before.

I'm not a Linux Newbie having ditched Microsoft over 6 months ago now but not a hard core Linux user either so need help in resolving this as I'm sure sooner or later these hard boots are going to cause corruption to my system.

I've googled for Kernel Panic messages and can't find anything on the Internet that will tell me what the flashing and solid Cap's Lock signals mean or how to find out what I need to look at within my system to explain what is causing the Kernel Panics.

One thing I have looked at is the Kernel Logs and it used to complain of losing Ticks right before Kernel Panicking with the NOLAPIC and NOAPIC options in place and now with those options removed my Kernel Logs are full of APIC errors every few minutes and the Laptop just randomly freezes.

Please help as I really miss having a Rock Solid Ubuntu system that I have come to take for granted of Linux. If anyone can tell me where to look or what to do to find out more information from my system that may shed light on what is causing these Kernel Panics I'll update this post so that we can hopefully stop this happening and help anyone else having the same issues.

EDIT:

I've been browsing my System Logs and have pasted the following Kernel Log that shows ACPI errors up until 01:18am, then the Kernel Panic happened, I did not notice again until checking the Laptop at 10:30am and as you can see after rebooting the APIC erros continue...any ideas?

```

Jun 30 00:21:16 localhost kernel: [ 9580.206151] APIC error on CPU0: 40(40)
Jun 30 00:46:14 localhost kernel: [10245.634325] APIC error on CPU0: 40(40)
Jun 30 00:48:21 localhost kernel: [10302.188812] APIC error on CPU0: 40(40)
Jun 30 00:52:32 localhost kernel: [10413.948719] APIC error on CPU0: 40(40)
Jun 30 00:52:50 localhost kernel: [10421.724734] APIC error on CPU0: 40(40)
Jun 30 01:03:42 localhost kernel: [10711.574624] APIC error on CPU0: 40(40)
Jun 30 01:18:47 localhost kernel: [11113.794088] APIC error on CPU0: 40(40)
Jun 30 10:30:31 localhost kernel: [    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
Jun 30 10:30:31 localhost kernel: [    0.000000] Entering add_active_range(0, 256, 491472) 1 entries of 3200 used
Jun 30 10:30:31 localhost kernel: [    0.000000] ACPI: RSDP (v000 HP                                    ) @ 0x00000000000fe270
Jun 30 10:30:31 localhost kernel: [    0.000000] ACPI: RSDT (v001 HP     0944     0x22110520 HP   0x00000001) @ 0x0000000077fefc84
Jun 30 10:30:31 localhost kernel: [    0.000000] ACPI: FADT (v002 HP     0944     0x00000002 HP   0x00000001) @ 0x0000000077fefc00
Jun 30 10:30:31 localhost kernel: [    0.000000] ACPI: MADT (v001 HP     0944     0x00000001 HP   0x00000001) @ 0x0000000077fefcb8
Jun 30 10:30:31 localhost kernel: [    0.000000] ACPI: MCFG (v001 HP     0944     0x00000001 HP   0x00000001) @ 0x0000000077fefd14
Jun 30 10:30:31 localhost kernel: [    0.000000] ACPI: SSDT (v001 HP       HPQPpc 0x00001001 MSFT 0x0100000e) @ 0x0000000077ff71d9
Jun 30 10:30:31 localhost kernel: [    0.000000] ACPI: DSDT (v001 HP        SB400 0x00010000 MSFT 0x0100000e) @ 0x0000000000000000
Jun 30 10:30:31 localhost kernel: [    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
Jun 30 10:30:31 localhost kernel: [    0.000000] Entering add_active_range(0, 256, 491472) 1 entries of 3200 used
Jun 30 10:30:31 localhost kernel: [    0.000000] NUMA: Using 63 for the hash shift.
Jun 30 10:30:31 localhost kernel: [    0.000000] On node 0 totalpages: 491375
Jun 30 10:30:31 localhost kernel: [    0.000000]   DMA zone: 56 pages used for memmap
Jun 30 10:30:31 localhost kernel: [    0.000000]   DMA zone: 1085 pages reserved
Jun 30 10:30:31 localhost kernel: [    0.000000]   DMA zone: 2858 pages, LIFO batch:0
Jun 30 10:30:31 localhost kernel: [    0.000000]   DMA32 zone: 6663 pages used for memmap
Jun 30 10:30:31 localhost kernel: [    0.000000]   DMA32 zone: 480713 pages, LIFO batch:31
Jun 30 10:30:31 localhost kernel: [    0.000000]   Normal zone: 0 pages used for memmap
Jun 30 10:30:31 localhost kernel: [    0.000000] ACPI: Local APIC address 0xfec01000
Jun 30 10:30:31 localhost kernel: [    0.000000] ACPI: IRQ0 used by override.
Jun 30 10:30:31 localhost kernel: [    0.000000] ACPI: IRQ2 used by override.
Jun 30 10:30:31 localhost kernel: [   17.544171] PCI: Probing PCI hardware (bus 00)
Jun 30 10:30:31 localhost kernel: [   17.548410] Boot video device is 0000:01:05.0
Jun 30 10:30:31 localhost kernel: [   17.549290] ACPI: PCI Interrupt Routing Table [\_SB_.C047._PRT]
Jun 30 10:30:31 localhost kernel: [   17.566274] ACPI: PCI Interrupt Routing Table [\_SB_.C047.C048._PRT]
Jun 30 10:30:31 localhost kernel: [   17.566673] ACPI: PCI Interrupt Routing Table [\_SB_.C047.C0AB._PRT]
Jun 30 10:30:31 localhost kernel: [   17.594138] PCI: Setting latency timer of device 0000:00:04.0 to 64
Jun 30 10:30:31 localhost kernel: [   17.594145] PCI: Setting latency timer of device 0000:00:05.0 to 64
Jun 30 10:30:31 localhost kernel: [   18.447847] PCI: Setting latency timer of device 0000:00:04.0 to 64
Jun 30 10:30:31 localhost kernel: [   18.447872] Allocate Port Service[0000:00:04.0:pcie00]
Jun 30 10:30:31 localhost kernel: [   18.447902] Allocate Port Service[0000:00:04.0:pcie02]
Jun 30 10:30:31 localhost kernel: [   18.447969] PCI: Setting latency timer of device 0000:00:05.0 to 64
Jun 30 10:30:31 localhost kernel: [   18.447993] Allocate Port Service[0000:00:05.0:pcie00]
Jun 30 10:30:31 localhost kernel: [   18.448022] Allocate Port Service[0000:00:05.0:pcie02]
Jun 30 10:30:31 localhost kernel: [   21.166472] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
Jun 30 10:30:31 localhost kernel: [   21.315650] ieee1394: Initialized config rom entry `ip1394'
Jun 30 10:30:31 localhost kernel: [   21.622245] Probing IDE interface ide0...
Jun 30 10:30:31 localhost kernel: [   22.630820] Probing IDE interface ide1...
Jun 30 10:30:31 localhost kernel: [   23.718626] libata version 2.20 loaded.
Jun 30 10:30:31 localhost kernel: [   25.084413] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023f9929913c0a]
Jun 30 10:30:31 localhost kernel: [   41.047401] PM: Writing back config space on device 0000:02:01.0 at offset c (was 9eff0000, writing 0)
Jun 30 10:30:31 localhost kernel: [   41.047411] PM: Writing back config space on device 0000:02:01.0 at offset b (was 3ed173b, writing 308b103c)
Jun 30 10:30:31 localhost kernel: [   41.047433] PM: Writing back config space on device 0000:02:01.0 at offset 3 (was 0, writing 4010)
Jun 30 10:30:31 localhost kernel: [   41.047441] PM: Writing back config space on device 0000:02:01.0 at offset 2 (was 2000000, writing 2000003)
Jun 30 10:30:31 localhost kernel: [   41.047449] PM: Writing back config space on device 0000:02:01.0 at offset 1 (was 2b00000, writing 2b00006)
Jun 30 10:30:31 localhost kernel: [   41.047457] PM: Writing back config space on device 0000:02:01.0 at offset 0 (was 3ed173b, writing 169c14e4)
Jun 30 10:30:39 localhost xinetd[5497]: Reading included configuration file: /etc/xinetd.d/chargen [file=/etc/xinetd.conf] [line=14]
Jun 30 10:30:39 localhost xinetd[5497]: Reading included configuration file: /etc/xinetd.d/daytime [file=/etc/xinetd.d/daytime] [line=28]
Jun 30 10:30:39 localhost xinetd[5497]: Reading included configuration file: /etc/xinetd.d/discard [file=/etc/xinetd.d/discard] [line=26]
Jun 30 10:30:39 localhost xinetd[5497]: Reading included configuration file: /etc/xinetd.d/echo [file=/etc/xinetd.d/echo] [line=25]
Jun 30 10:30:39 localhost xinetd[5497]: Reading included configuration file: /etc/xinetd.d/time [file=/etc/xinetd.d/time] [line=26]
Jun 30 10:30:39 localhost xinetd[5497]: removing chargen
Jun 30 10:30:39 localhost xinetd[5497]: removing chargen
Jun 30 10:30:39 localhost xinetd[5497]: removing daytime
Jun 30 10:30:39 localhost xinetd[5497]: removing daytime
Jun 30 10:30:39 localhost xinetd[5497]: removing discard
Jun 30 10:30:39 localhost xinetd[5497]: removing discard
Jun 30 10:30:39 localhost xinetd[5497]: removing echo
Jun 30 10:30:39 localhost xinetd[5497]: removing echo
Jun 30 10:30:39 localhost xinetd[5497]: removing time
Jun 30 10:30:39 localhost xinetd[5497]: removing time
Jun 30 10:30:39 localhost ntpd[5526]: signal_no_reset: signal 17 had flags 4000000
Jun 30 10:31:27 localhost kernel: [   91.415792] eth1: no IPv6 routers present
Jun 30 10:32:26 localhost kernel: [  137.152942] APIC error on CPU0: 00(40)
Jun 30 10:34:48 localhost kernel: [  228.393425] APIC error on CPU0: 40(40)
Jun 30 10:35:23 localhost kernel: [  247.962887] APIC error on CPU0: 40(40)
Jun 30 10:35:58 localhost kernel: [  268.236019] APIC error on CPU0: 40(40)
Jun 30 10:41:53 localhost kernel: [  438.957351] Losing some ticks... checking if CPU frequency changed.
Jun 30 10:54:55 localhost kernel: [  818.523446] APIC error on CPU0: 40(40)
Jun 30 10:56:05 localhost kernel: [  851.661506] APIC error on CPU0: 40(40)
Jun 30 10:59:53 localhost kernel: [  966.775890] APIC error on CPU0: 40(40)
Jun 30 11:03:30 localhost kernel: [ 1089.048424] APIC error on CPU0: 40(40)
Jun 30 11:05:05 localhost kernel: [ 1150.159151] APIC error on CPU0: 40(40)
Jun 30 11:07:28 localhost kernel: [ 1233.314754] APIC error on CPU0: 40(40)
Jun 30 11:08:54 localhost kernel: [ 1272.368718] APIC error on CPU0: 40(40)
Jun 30 11:12:42 localhost kernel: [ 1385.289867] APIC error on CPU0: 40(40)
Jun 30 11:14:10 localhost kernel: [ 1437.765602] APIC error on CPU0: 40(40)
Jun 30 11:22:14 localhost kernel: [ 1688.108970] APIC error on CPU0: 40(40)
Jun 30 11:27:04 localhost kernel: [ 1823.947845] APIC error on CPU0: 40(40)
Jun 30 11:31:58 localhost kernel: [ 1959.909557] APIC error on CPU0: 40(40)
Jun 30 11:34:18 localhost kernel: [ 2025.650349] APIC error on CPU0: 40(40)
Jun 30 11:36:08 localhost kernel: [ 2086.450219] APIC error on CPU0: 40(40)
Jun 30 11:42:01 localhost kernel: [ 2265.516238] APIC error on CPU0: 40(40)

```


Cheers, James...

---

### Post by JamesX on 2007-06-30
I've been reading the Ubuntu Bug's section but haven't found anything similar logged so far, I've pasted the output from a terminal after running "dmesg" below...

Cheers, James...

```
james@james-laptop:~$ dmesg
[    0.000000] Linux version 2.6.20-16-generic (root@king) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Thu Jun 7 19:00:28 UTC 2007 (Ubuntu 2.6.20-16.29-generic)
[    0.000000] Command line: root=UUID=b3e7deb6-c86d-4129-9927-487402b8ba9a ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000077fd0000 (usable)
[    0.000000]  BIOS-e820: 0000000077fd0000 - 0000000077fefc00 (reserved)
[    0.000000]  BIOS-e820: 0000000077fefc00 - 0000000077ffb000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000077ffb000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec02000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb80000 - 00000000ffc00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 491472) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 HP                                    ) @ 0x00000000000fe270
[    0.000000] ACPI: RSDT (v001 HP     0944     0x22110520 HP   0x00000001) @ 0x0000000077fefc84
[    0.000000] ACPI: FADT (v002 HP     0944     0x00000002 HP   0x00000001) @ 0x0000000077fefc00
[    0.000000] ACPI: MADT (v001 HP     0944     0x00000001 HP   0x00000001) @ 0x0000000077fefcb8
[    0.000000] ACPI: MCFG (v001 HP     0944     0x00000001 HP   0x00000001) @ 0x0000000077fefd14
[    0.000000] ACPI: SSDT (v001 HP       HPQPpc 0x00001001 MSFT 0x0100000e) @ 0x0000000077ff71d9
[    0.000000] ACPI: DSDT (v001 HP        SB400 0x00010000 MSFT 0x0100000e) @ 0x0000000000000000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] Number of nodes 1
[    0.000000] Node 0 MemBase 0000000000000000 Limit 0000000077fd0000
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 491472) 1 entries of 3200 used
[    0.000000] NUMA: Using 63 for the hash shift.
[    0.000000] Using node hash shift of 63
[    0.000000] Bootmem setup node 0 0000000000000000-0000000077fd0000
[    0.000000] No mptable found.
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      159
[    0.000000]     0:      256 ->   491472
[    0.000000] On node 0 totalpages: 491375
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1085 pages reserved
[    0.000000]   DMA zone: 2858 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 6663 pages used for memmap
[    0.000000]   DMA32 zone: 480713 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000] ATI board detected. Disabling timer routing over 8254.
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfec01000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 21 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] Setting APIC routing to physical flat
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Nosave address range: 000000000009f000 - 00000000000a0000
[    0.000000] Nosave address range: 00000000000a0000 - 00000000000e0000
[    0.000000] Nosave address range: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 34048 bytes of per cpu data
[    0.000000] Built 1 zonelists.  Total pages: 483571
[    0.000000] Kernel command line: root=UUID=b3e7deb6-c86d-4129-9927-487402b8ba9a ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[   16.831181] Console: colour VGA+ 80x25
[   16.833545] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[   16.837268] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   16.837497] Checking aperture...
[   16.837501] CPU 0: aperture @ e772000000 size 32 MB
[   16.837503] Aperture too small (32 MB)
[   16.849883] No AGP bridge found
[   16.883584] Memory: 1922868k/1965888k available (2217k kernel code, 42632k reserved, 1162k data, 304k init)
[   16.960265] Calibrating delay using timer specific routine.. 3594.95 BogoMIPS (lpj=7189901)
[   16.960331] Security Framework v1.0.0 initialized
[   16.960338] SELinux:  Disabled at boot.
[   16.960365] Mount-cache hash table entries: 256
[   16.960544] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   16.960547] CPU: L2 Cache: 1024K (64 bytes/line)
[   16.960551] CPU 0/0 -> Node 0
[   16.960573] SMP alternatives: switching to UP code
[   16.960904] Freeing SMP alternatives: 28k freed
[   16.961032] Early unpacking initramfs... done
[   17.351219] ACPI: Core revision 20060707
[   17.351464] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   17.428239] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[   17.468311] Using local APIC timer interrupts.
[   17.523979] result 12469030
[   17.523980] Detected 12.469 MHz APIC timer.
[   17.528040] Brought up 1 CPUs
[   17.528084] time.c: Using 3.579545 MHz WALL PM GTOD PIT/TSC timer.
[   17.528086] time.c: Detected 1795.539 MHz processor.
[   17.528449] Time:  9:29:54  Date: 05/30/107
[   17.528495] NET: Registered protocol family 16
[   17.528596] ACPI: bus type pci registered
[   17.528605] PCI: Using configuration type 1
[   17.543709] ACPI: Interpreter enabled
[   17.543711] ACPI: Using IOAPIC for interrupt routing
[   17.544166] ACPI: PCI Root Bridge [C047] (0000:00)
[   17.544171] PCI: Probing PCI hardware (bus 00)
[   17.544191] ACPI: Assume root bridge [\_SB_.C047] bus is 0
[   17.548410] Boot video device is 0000:01:05.0
[   17.549174] PCI: Transparent bridge - 0000:00:14.4
[   17.549250] PCI: Bus #03 (-#06) is hidden behind transparent bridge #02 (-#03) (try 'pci=assign-busses')
[   17.549252] Please report the result to linux-kernel to fix this permanently
[   17.549290] ACPI: PCI Interrupt Routing Table [\_SB_.C047._PRT]
[   17.566274] ACPI: PCI Interrupt Routing Table [\_SB_.C047.C048._PRT]
[   17.566673] ACPI: PCI Interrupt Routing Table [\_SB_.C047.C0AB._PRT]
[   17.567220] ACPI: Power Resource [C1CF] (off)
[   17.576542] ACPI: Power Resource [C1C7] (on)
[   17.578338] ACPI: PCI Interrupt Link [C0F0] (IRQs 10 11) *0, disabled.
[   17.578745] ACPI: PCI Interrupt Link [C0F1] (IRQs 10 11) *0, disabled.
[   17.579150] ACPI: PCI Interrupt Link [C0F2] (IRQs 10 11) *0, disabled.
[   17.579552] ACPI: PCI Interrupt Link [C0F3] (IRQs 10 11) *0, disabled.
[   17.579973] ACPI: PCI Interrupt Link [C0F4] (IRQs 10 11) *0, disabled.
[   17.580373] ACPI: PCI Interrupt Link [C0F5] (IRQs 9) *0, disabled.
[   17.580775] ACPI: PCI Interrupt Link [C0F6] (IRQs 10 11) *0, disabled.
[   17.581183] ACPI: PCI Interrupt Link [C0F7] (IRQs *10 11)
[   17.583556] ACPI: Power Resource [C26C] (off)
[   17.583689] ACPI: Power Resource [C26D] (off)
[   17.583829] ACPI: Power Resource [C26E] (off)
[   17.583968] ACPI: Power Resource [C26F] (off)
[   17.584260] Linux Plug and Play Support v0.97 (c) Adam Belay
[   17.584270] pnp: PnP ACPI init
[   17.591757] pnp: PnP ACPI: found 11 devices
[   17.591812] PCI: Using ACPI for IRQ routing
[   17.591814] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   17.591822] PCI: Cannot allocate resource region 7 of bridge 0000:00:04.0
[   17.591824] PCI: Cannot allocate resource region 8 of bridge 0000:00:04.0
[   17.591827] PCI: Cannot allocate resource region 9 of bridge 0000:00:04.0
[   17.591829] PCI: Cannot allocate resource region 7 of bridge 0000:00:05.0
[   17.591832] PCI: Cannot allocate resource region 8 of bridge 0000:00:05.0
[   17.591834] PCI: Cannot allocate resource region 9 of bridge 0000:00:05.0
[   17.591980] NET: Registered protocol family 8
[   17.591982] NET: Registered protocol family 20
[   17.593730] pnp: 00:08: ioport range 0x40b-0x40b has been reserved
[   17.593733] pnp: 00:08: ioport range 0x4d0-0x4d1 has been reserved
[   17.593736] pnp: 00:08: ioport range 0x4d6-0x4d6 has been reserved
[   17.593741] pnp: 00:09: ioport range 0x8000-0x802f could not be reserved
[   17.593745] pnp: 00:09: ioport range 0x8100-0x811f could not be reserved
[   17.594044] PCI: Bridge: 0000:00:01.0
[   17.594047]   IO window: 2000-2fff
[   17.594050]   MEM window: d0400000-d07fffff
[   17.594053]   PREFETCH window: c0000000-cfffffff
[   17.594056] PCI: Bridge: 0000:00:04.0
[   17.594058]   IO window: disabled.
[   17.594060]   MEM window: disabled.
[   17.594062]   PREFETCH window: disabled.
[   17.594065] PCI: Bridge: 0000:00:05.0
[   17.594066]   IO window: disabled.
[   17.594069]   MEM window: disabled.
[   17.594071]   PREFETCH window: disabled.
[   17.594077] PCI: Bus 3, cardbus bridge: 0000:02:04.0
[   17.594079]   IO window: 00001000-000010ff
[   17.594085]   IO window: 00001400-000014ff
[   17.594091]   PREFETCH window: 88000000-8bffffff
[   17.594097]   MEM window: 8c000000-8fffffff
[   17.594103] PCI: Bridge: 0000:00:14.4
[   17.594106]   IO window: 1000-1fff
[   17.594113]   MEM window: d0000000-d03fffff
[   17.594119]   PREFETCH window: 88000000-8bffffff
[   17.594138] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   17.594145] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   17.594174] ACPI: PCI Interrupt 0000:02:04.0[A] -> GSI 20 (level, low) -> IRQ 20
[   17.594261] NET: Registered protocol family 2
[   17.632036] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[   17.632844] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[   17.637938] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   17.639212] TCP: Hash tables configured (established 262144 bind 65536)
[   17.639215] TCP reno registered
[   17.648071] checking if image is initramfs... it is
[   18.437173] Freeing initrd memory: 8181k freed
[   18.447329] audit: initializing netlink socket (disabled)
[   18.447345] audit(1183195794.496:1): initialized
[   18.447505] VFS: Disk quotas dquot_6.5.1
[   18.447530] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   18.447584] io scheduler noop registered
[   18.447588] io scheduler anticipatory registered
[   18.447590] io scheduler deadline registered
[   18.447602] io scheduler cfq registered (default)
[   18.447847] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   18.447869] assign_interrupt_mode Found MSI capability
[   18.447872] Allocate Port Service[0000:00:04.0:pcie00]
[   18.447902] Allocate Port Service[0000:00:04.0:pcie02]
[   18.447969] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   18.447990] assign_interrupt_mode Found MSI capability
[   18.447993] Allocate Port Service[0000:00:05.0:pcie00]
[   18.448022] Allocate Port Service[0000:00:05.0:pcie02]
[   18.472454] Real Time Clock Driver v1.12ac
[   18.472503] Linux agpgart interface v0.102 (c) Dave Jones
[   18.472506] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   18.473033] ACPI: PCI Interrupt 0000:00:14.6[B] -> GSI 17 (level, low) -> IRQ 17
[   18.473044] ACPI: PCI interrupt for device 0000:00:14.6 disabled
[   18.473122] mice: PS/2 mouse device common for all mice
[   18.473681] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   18.473934] input: Macintosh mouse button emulation as /class/input/input0
[   18.473966] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   18.473970] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   18.474245] PNP: PS/2 Controller [PNP0303:C1C4,PNP0f13:C1C5] at 0x60,0x64 irq 1,12
[   18.476900] i8042.c: Detected active multiplexing controller, rev 1.1.
[   18.477612] serio: i8042 KBD port at 0x60,0x64 irq 1
[   18.477617] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   18.477620] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   18.477623] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   18.477626] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   18.477719] TCP cubic registered
[   18.477728] NET: Registered protocol family 1
[   18.477869] ACPI: (supports S0 S3 S4 S5)
[   18.477914]   Magic number: 11:134:476
[   18.478046] drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   18.478145] Freeing unused kernel memory: 304k freed
[   18.499926] input: AT Translated Set 2 keyboard as /class/input/input1
[   19.661690] Capability LSM initialized
[   19.963946] device-mapper: ioctl: 4.11.0-ioctl (2006-10-12) initialised: dm-devel@redhat.com
[   19.986921] ACPI: Transitioning device [C270] to D3
[   19.986925] ACPI: Transitioning device [C270] to D3
[   19.986929] ACPI: Fan [C270] (off)
[   19.987107] ACPI: Transitioning device [C271] to D3
[   19.987109] ACPI: Transitioning device [C271] to D3
[   19.987114] ACPI: Fan [C271] (off)
[   19.987290] ACPI: Transitioning device [C272] to D3
[   19.987292] ACPI: Transitioning device [C272] to D3
[   19.987294] ACPI: Fan [C272] (off)
[   19.987470] ACPI: Transitioning device [C273] to D3
[   19.987472] ACPI: Transitioning device [C273] to D3
[   19.987475] ACPI: Fan [C273] (off)
[   20.024972] ACPI: CPU0 (power states: C1[C1] C3[C3])
[   20.024978] ACPI: Processor [C000] (supports 8 throttling states)
[   20.033461] ACPI: Thermal Zone [TZ1] (78 C)
[   20.037540] ACPI: Thermal Zone [TZ2] (66 C)
[   20.045216] ACPI: Thermal Zone [TZ3] (38 C)
[   20.101343] md: linear personality registered for level -1
[   20.104397] md: multipath personality registered for level -4
[   20.107107] md: raid0 personality registered for level 0
[   20.110365] md: raid1 personality registered for level 1
[   20.112960] raid5: automatically using best checksumming function: generic_sse
[   20.130710]    generic_sse:  5716.000 MB/sec
[   20.130712] raid5: using function: generic_sse (5716.000 MB/sec)
[   20.202676] raid6: int64x1   1653 MB/s
[   20.270645] raid6: int64x2   2216 MB/s
[   20.338608] raid6: int64x4   2324 MB/s
[   20.406572] raid6: int64x8   1600 MB/s
[   20.474537] raid6: sse2x1    2303 MB/s
[   20.542492] raid6: sse2x2    3083 MB/s
[   20.610459] raid6: sse2x4    3325 MB/s
[   20.610461] raid6: using algorithm sse2x4 (3325 MB/s)
[   20.610464] md: raid6 personality registered for level 6
[   20.610466] md: raid5 personality registered for level 5
[   20.610468] md: raid4 personality registered for level 4
[   20.725592] md: raid10 personality registered for level 10
[   21.165645] usbcore: registered new interface driver usbfs
[   21.165671] usbcore: registered new interface driver hub
[   21.165694] usbcore: registered new device driver usb
[   21.166472] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   21.166512] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 19
[   21.166529] ohci_hcd 0000:00:13.0: OHCI Host Controller
[   21.166716] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[   21.166738] ohci_hcd 0000:00:13.0: irq 19, io mem 0xd0800000
[   21.253838] usb usb1: configuration #1 chosen from 1 choice
[   21.253867] hub 1-0:1.0: USB hub found
[   21.253881] hub 1-0:1.0: 4 ports detected
[   21.315650] ieee1394: Initialized config rom entry `ip1394'
[   21.354282] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 19
[   21.354303] ohci_hcd 0000:00:13.1: OHCI Host Controller
[   21.354330] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[   21.354350] ohci_hcd 0000:00:13.1: irq 19, io mem 0xd0801000
[   21.414206] usb usb2: configuration #1 chosen from 1 choice
[   21.414235] hub 2-0:1.0: USB hub found
[   21.414252] hub 2-0:1.0: 4 ports detected
[   21.518256] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 19
[   21.518275] ehci_hcd 0000:00:13.2: EHCI Host Controller
[   21.518299] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[   21.518364] ehci_hcd 0000:00:13.2: irq 19, io mem 0xd0802000
[   21.518377] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   21.518494] usb usb3: configuration #1 chosen from 1 choice
[   21.518518] hub 3-0:1.0: USB hub found
[   21.518525] hub 3-0:1.0: 8 ports detected
[   21.622169] ATIIXP: IDE controller at PCI slot 0000:00:14.1
[   21.622191] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 16
[   21.622204] ATIIXP: chipset revision 0
[   21.622206] ATIIXP: not 100% native mode: will probe irqs later
[   21.622217]     ide0: BM-DMA at 0x3010-0x3017, BIOS settings: hda:DMA, hdb:pio
[   21.622233]     ide1: BM-DMA at 0x3018-0x301f, BIOS settings: hdc:DMA, hdd:pio
[   21.622245] Probing IDE interface ide0...
[   21.910260] hda: TOSHIBA MK8026GAX, ATA DISK drive
[   22.581599] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   22.630820] Probing IDE interface ide1...
[   23.137206] usb 1-2: new full speed USB device using ohci_hcd and address 3
[   23.348629] usb 1-2: configuration #1 chosen from 1 choice
[   23.365575] hdc: HL-DT-ST DVD-RW GWA-4082N, ATAPI CD/DVD-ROM drive
[   23.652953] usb 1-3: new low speed USB device using ohci_hcd and address 4
[   23.701870] ide1 at 0x170-0x177,0x376 on irq 15
[   23.712428] SCSI subsystem initialized
[   23.718626] libata version 2.20 loaded.
[   23.720105] tg3.c:v3.72 (January 8, 2007)
[   23.720137] ACPI: PCI Interrupt 0000:02:01.0[A] -> GSI 23 (level, low) -> IRQ 23
[   23.727634] hda: max request size: 128KiB
[   23.765866] eth0: Tigon3 [partno(BCM95788A50) rev 3003 PHY(5705)] (PCI:33MHz:32-bit) 10/100/1000Base-T Ethernet 00:0f:b0:74:25:e7
[   23.765874] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] Split[0] WireSpeed[0] TSOcap[1] 
[   23.765878] eth0: dma_rwctrl[763f0000] dma_mask[32-bit]
[   23.765928] ACPI: PCI Interrupt 0000:02:04.2[C] -> GSI 21 (level, low) -> IRQ 21
[   23.816196] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[d0013000-d00137ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   23.817802] hda: 156301488 sectors (80026 MB), CHS=65535/16/63, UDMA(100)
[   23.817880] hda: cache flushes supported
[   23.817918]  hda: hda1 hda2
[   23.892081] hdc: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, DMA
[   23.892090] Uniform CD-ROM driver Revision: 3.20
[   23.900341] usb 1-3: configuration #1 chosen from 1 choice
[   24.204695] usb 2-1: new full speed USB device using ohci_hcd and address 2
[   24.205873] EXT3-fs: INFO: recovery required on readonly filesystem.
[   24.205876] EXT3-fs: write access will be enabled during recovery.
[   24.409587] usb 2-1: configuration #1 chosen from 1 choice
[   24.712435] usb 2-3: new full speed USB device using ohci_hcd and address 3
[   24.924275] usb 2-3: configuration #1 chosen from 1 choice
[   24.930389] usbcore: registered new interface driver hiddev
[   24.936891] input: USB Mouse               as /class/input/input2
[   24.936911] input: USB HID v1.10 Mouse [USB Mouse              ] on usb-0000:00:13.0-3
[   24.936929] usbcore: registered new interface driver usbhid
[   24.936932] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   25.084413] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023f9929913c0a]
[   29.663532] kjournald starting.  Commit interval 5 seconds
[   29.663549] EXT3-fs: recovery complete.
[   29.664536] EXT3-fs: mounted filesystem with ordered data mode.
[   41.047401] PM: Writing back config space on device 0000:02:01.0 at offset c (was 9eff0000, writing 0)
[   41.047411] PM: Writing back config space on device 0000:02:01.0 at offset b (was 3ed173b, writing 308b103c)
[   41.047433] PM: Writing back config space on device 0000:02:01.0 at offset 3 (was 0, writing 4010)
[   41.047441] PM: Writing back config space on device 0000:02:01.0 at offset 2 (was 2000000, writing 2000003)
[   41.047449] PM: Writing back config space on device 0000:02:01.0 at offset 1 (was 2b00000, writing 2b00006)
[   41.047457] PM: Writing back config space on device 0000:02:01.0 at offset 0 (was 3ed173b, writing 169c14e4)
[   43.134318] NET: Registered protocol family 17
[   43.414150] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   43.417841] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   43.559008] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[   44.211895] Yenta: CardBus bridge found at 0000:02:04.0 [103c:308b]
[   44.211923] Yenta: Enabling burst memory read transactions
[   44.211929] Yenta: Using INTVAL to route CSC interrupts to PCI
[   44.211931] Yenta: Routing CardBus interrupts to PCI
[   44.211938] Yenta TI: socket 0000:02:04.0, mfunc 0x01a11b22, devctl 0x64
[   44.417000] Bluetooth: Core ver 2.11
[   44.417074] NET: Registered protocol family 31
[   44.417076] Bluetooth: HCI device and connection manager initialized
[   44.417080] Bluetooth: HCI socket layer initialized
[   44.443628] Yenta: ISA IRQ mask 0x0ef8, PCI irq 20
[   44.443635] Socket status: 30000006
[   44.443638] Yenta: Raising subordinate bus# of parent bus (#02) from #03 to #06
[   44.443646] pcmcia: parent PCI bridge I/O window: 0x1000 - 0x1fff
[   44.443650] pcmcia: parent PCI bridge Memory window: 0xd0000000 - 0xd03fffff
[   44.443653] pcmcia: parent PCI bridge Memory window: 0x88000000 - 0x8bffffff
[   44.505591] ACPI: PCI Interrupt 0000:02:04.3[B] -> GSI 21 (level, low) -> IRQ 21
[   44.663326] Bluetooth: HCI USB driver ver 2.9
[   44.715085] usbcore: registered new interface driver hci_usb
[   44.789399] input: PC Speaker as /class/input/input3
[   44.812088] sdhci: Secure Digital Host Controller Interface driver
[   44.812093] sdhci: Copyright(c) Pierre Ossman
[   44.812142] sdhci: SDHCI controller found at 0000:02:04.4 [104c:8034] (rev 0)
[   44.812167] ACPI: PCI Interrupt 0000:02:04.4[C] -> GSI 21 (level, low) -> IRQ 21
[   44.812246] mmc0: SDHCI at 0xd001a000 irq 21 DMA
[   44.816381] mmc1: SDHCI at 0xd001b000 irq 21 DMA
[   44.816431] mmc2: SDHCI at 0xd001c000 irq 21 DMA
[   45.148428] usbcore: registered new interface driver usbserial
[   45.148453] drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
[   45.162870] ACPI: PCI Interrupt 0000:00:14.5[B] -> GSI 17 (level, low) -> IRQ 17
[   45.183731] ACPI: PCI Interrupt 0000:00:14.6[B] -> GSI 17 (level, low) -> IRQ 17
[   45.294358] MC'97 0 converters and GPIO not ready (0x1)
[   45.324495] usbcore: registered new interface driver usbserial_generic
[   45.324500] drivers/usb/serial/usb-serial.c: USB Serial Driver core
[   45.336957] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04713/0x200000
[   45.340919] drivers/usb/serial/usb-serial.c: USB Serial support registered for FTDI USB Serial Device
[   45.340967] ftdi_sio 2-3:1.0: FTDI USB Serial Device converter detected
[   45.340973] drivers/usb/serial/ftdi_sio.c: Detected FT232BM
[   45.341188] usb 2-3: FTDI USB Serial Device converter now attached to ttyUSB0
[   45.341196] usbcore: registered new interface driver ftdi_sio
[   45.341199] drivers/usb/serial/ftdi_sio.c: v1.4.3:USB FTDI Serial Converters Driver
[   45.379143] input: SynPS/2 Synaptics TouchPad as /class/input/input4
[   45.712788] lp: driver loaded but no devices found
[   45.891319] ndiswrapper version 1.38 loaded (preempt=no,smp=yes)
[   45.987615] ndiswrapper (link_pe_images:577): fixing KI_USER_SHARED_DATA address in the driver
[   45.988831] ndiswrapper: driver bcmwl5 (Broadcom,02/11/2005, 3.100.64.0) loaded
[   45.989176] ACPI: PCI Interrupt 0000:02:02.0[A] -> GSI 22 (level, low) -> IRQ 22
[   45.997475] ndiswrapper: using IRQ 22
[   46.664546] eth1: ethernet device 00:90:4b:f9:43:e8 using NDIS driver: bcmwl5, version: 0x364400a, NDIS version: 0x501, vendor: '', 14E4:4318.5.conf
[   46.664595] eth1: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   46.670228] usbcore: registered new interface driver ndiswrapper
[   46.759681] Adding 2096440k swap on /dev/disk/by-uuid/92049a5f-9b83-40fc-b54c-bfc2f61cb58e.  Priority:-1 extents:1 across:2096440k
[   46.815960] EXT3 FS on hda2, internal journal
[   48.026025] Adding 2096440k swap on /dev/disk/by-uuid/92049a5f-9b83-40fc-b54c-bfc2f61cb58e.  Priority:-2 extents:1 across:2096440k
[   53.194129] ACPI: AC Adapter [C177] (on-line)
[   53.252146] ACPI: Battery Slot [C179] (battery present)
[   53.252379] ACPI: Battery Slot [C178] (battery absent)
[   53.297562] input: Power Button (FF) as /class/input/input5
[   53.301896] ACPI: Power Button (FF) [PWRF]
[   53.331712] input: Sleep Button (CM) as /class/input/input6
[   53.336067] ACPI: Sleep Button (CM) [C1F0]
[   53.365584] input: Lid Switch as /class/input/input7
[   53.369951] ACPI: Lid Switch [C1F1]
[   53.385832] Using specific hotkey driver
[   53.413354] No dock devices found.
[   53.450033] ibm_acpi: ec object not found
[   53.533086] ACPI: Video Device [C049] (multi-head: yes  rom: no  post: no)
[   53.597006] pcc_acpi: loading...
[   53.605452] wmi_add device=ffff810074e11000
[   53.605457] calling WQBA
[   53.830770] powernow-k8: Found 1 AMD Turion(tm) 64 Mobile ML-34                  processors (version 2.00.00)
[   53.832981] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x4
[   53.832984] powernow-k8:    1 : fid 0x8 (1600 MHz), vid 0x6
[   53.832986] powernow-k8:    2 : fid 0x0 (800 MHz), vid 0x16
[   53.834477] powernow-k8: ph2 null fid transition 0xa
[   57.522639] [fglrx] Maximum main memory to use for locked dma buffers: 1765 MBytes.
[   57.522939] [fglrx] module loaded - fglrx 8.34.8 [Feb 20 2007] on minor 0
[   57.554889] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 17 (level, low) -> IRQ 17
[   60.296860] [fglrx] total      GART = 130023424
[   60.296867] [fglrx] free       GART = 114032640
[   60.296870] [fglrx] max single GART = 114032640
[   60.296872] [fglrx] total      LFB  = 134217728
[   60.296874] [fglrx] free       LFB  = 114274304
[   60.296877] [fglrx] max single LFB  = 114274304
[   60.296878] [fglrx] total      Inv  = 0
[   60.296880] [fglrx] free       Inv  = 0
[   60.296882] [fglrx] max single Inv  = 0
[   60.296883] [fglrx] total      TIM  = 0
[   60.938011] ppdev: user-space parallel port driver
[   61.821779] NET: Registered protocol family 10
[   61.821889] lo: Disabled Privacy Extensions
[   61.821957] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   61.821961] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   62.453551] Bluetooth: L2CAP ver 2.8
[   62.453556] Bluetooth: L2CAP socket layer initialized
[   62.487500] Bluetooth: RFCOMM socket layer initialized
[   62.487512] Bluetooth: RFCOMM TTY layer initialized
[   62.487514] Bluetooth: RFCOMM ver 1.8
[   82.656063] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   91.415792] eth1: no IPv6 routers present
[  137.152942] APIC error on CPU0: 00(40)
[  228.393425] APIC error on CPU0: 40(40)
[  247.962887] APIC error on CPU0: 40(40)
[  268.236019] APIC error on CPU0: 40(40)
[  438.957351] Losing some ticks... checking if CPU frequency changed.
[  818.523446] APIC error on CPU0: 40(40)
[  851.661506] APIC error on CPU0: 40(40)
[  966.775890] APIC error on CPU0: 40(40)
[ 1089.048424] APIC error on CPU0: 40(40)
[ 1150.159151] APIC error on CPU0: 40(40)
[ 1233.314754] APIC error on CPU0: 40(40)
[ 1272.368718] APIC error on CPU0: 40(40)
[ 1385.289867] APIC error on CPU0: 40(40)
[ 1437.765602] APIC error on CPU0: 40(40)
[ 1688.108970] APIC error on CPU0: 40(40)
[ 1823.947845] APIC error on CPU0: 40(40)
[ 1959.909557] APIC error on CPU0: 40(40)
[ 2025.650349] APIC error on CPU0: 40(40)
[ 2086.450219] APIC error on CPU0: 40(40)
[ 2265.516238] APIC error on CPU0: 40(40)
[ 2736.078960] APIC error on CPU0: 40(40)
[ 2804.513446] APIC error on CPU0: 40(40)
[ 2820.584527] APIC error on CPU0: 40(40)
[ 2878.779520] APIC error on CPU0: 40(40)
[ 2981.885275] APIC error on CPU0: 40(40)
[ 3085.655920] APIC error on CPU0: 40(40)
[ 3140.088206] APIC error on CPU0: 40(40)
[ 3264.506649] APIC error on CPU0: 40(40)
[ 3391.503798] APIC error on CPU0: 40(40)
[ 3482.563200] APIC error on CPU0: 40(40)
[ 3669.676971] APIC error on CPU0: 40(40)
[ 3800.695613] APIC error on CPU0: 40(40)
[ 4011.970096] APIC error on CPU0: 40(40)
[ 4331.706562] APIC error on CPU0: 40(40)
[ 4346.792888] APIC error on CPU0: 40(40)
[ 4616.820675] APIC error on CPU0: 40(40)
[ 4930.330950] APIC error on CPU0: 40(40)
[ 4979.379452] APIC error on CPU0: 40(40)
```

---

### Post by JamesX on 2007-06-30
Ok a bit more information, after reading the Debugging System Crash Ubuntu Documentation I found the Kernel Log for today and have posted it below and I recognise something that may be significant that I noticed from prior Kernel Logs when I still had the NOAPIC and NOLAPIC options enabled.... and that lines 4,5,and 6 stating many lost ticks and that a driver may be hogging resources but I don't recollect seeing the 7th line in logs before so I'm going to google on it now after posting this...

Cheers, James...

P.S. had to chop a bit off the bottom of the below Kernel Log due to the post being too large for Ubuntu Forum.

```
Jun 30 00:21:16 localhost kernel: [ 9580.206151] APIC error on CPU0: 40(40)
Jun 30 00:46:14 localhost kernel: [10245.634325] APIC error on CPU0: 40(40)
Jun 30 00:48:21 localhost kernel: [10302.188812] APIC error on CPU0: 40(40)
Jun 30 00:48:33 localhost kernel: [10307.680922] warning: many lost ticks.
Jun 30 00:48:33 localhost kernel: [10307.680924] Your time source seems to be instable or some driver is hogging interupts
Jun 30 00:48:33 localhost kernel: [10307.680950] rip acpi_safe_halt+0x28/0x39 [processor]
Jun 30 00:52:32 localhost kernel: [10413.948719] APIC error on CPU0: 40(40)
Jun 30 00:52:50 localhost kernel: [10421.724734] APIC error on CPU0: 40(40)
Jun 30 01:03:42 localhost kernel: [10711.574624] APIC error on CPU0: 40(40)
Jun 30 01:18:47 localhost kernel: [11113.794088] APIC error on CPU0: 40(40)
Jun 30 10:30:31 localhost kernel: Inspecting /boot/System.map-2.6.20-16-generic
Jun 30 10:30:31 localhost kernel: Loaded 25651 symbols from /boot/System.map-2.6.20-16-generic.
Jun 30 10:30:31 localhost kernel: Symbols match kernel version 2.6.20.
Jun 30 10:30:31 localhost kernel: No module symbols loaded - kernel modules not enabled. 
Jun 30 10:30:31 localhost kernel: [    0.000000] Linux version 2.6.20-16-generic (root@king) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Thu Jun 7 19:00:28 UTC 2007 (Ubuntu 2.6.20-16.29-generic)
Jun 30 10:30:31 localhost kernel: [    0.000000] Command line: root=UUID=b3e7deb6-c86d-4129-9927-487402b8ba9a ro quiet splash
Jun 30 10:30:31 localhost kernel: [    0.000000] BIOS-provided physical RAM map:
Jun 30 10:30:31 localhost kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Jun 30 10:30:31 localhost kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Jun 30 10:30:31 localhost kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Jun 30 10:30:31 localhost kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 0000000077fd0000 (usable)
Jun 30 10:30:31 localhost kernel: [    0.000000]  BIOS-e820: 0000000077fd0000 - 0000000077fefc00 (reserved)
Jun 30 10:30:31 localhost kernel: [    0.000000]  BIOS-e820: 0000000077fefc00 - 0000000077ffb000 (ACPI NVS)
Jun 30 10:30:31 localhost kernel: [    0.000000]  BIOS-e820: 0000000077ffb000 - 0000000080000000 (reserved)
Jun 30 10:30:31 localhost kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Jun 30 10:30:31 localhost kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec02000 (reserved)
Jun 30 10:30:31 localhost kernel: [    0.000000]  BIOS-e820: 00000000ffb80000 - 00000000ffc00000 (reserved)
Jun 30 10:30:31 localhost kernel: [    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
Jun 30 10:30:31 localhost kernel: [    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
Jun 30 10:30:31 localhost kernel: [    0.000000] Entering add_active_range(0, 256, 491472) 1 entries of 3200 used
Jun 30 10:30:31 localhost kernel: [    0.000000] end_pfn_map = 1048576
Jun 30 10:30:31 localhost kernel: [    0.000000] DMI 2.3 present.
Jun 30 10:30:31 localhost kernel: [    0.000000] ACPI: RSDP (v000 HP                                    ) @ 0x00000000000fe270
Jun 30 10:30:31 localhost kernel: [    0.000000] ACPI: RSDT (v001 HP     0944     0x22110520 HP   0x00000001) @ 0x0000000077fefc84
Jun 30 10:30:31 localhost kernel: [    0.000000] ACPI: FADT (v002 HP     0944     0x00000002 HP   0x00000001) @ 0x0000000077fefc00
Jun 30 10:30:31 localhost kernel: [    0.000000] ACPI: MADT (v001 HP     0944     0x00000001 HP   0x00000001) @ 0x0000000077fefcb8
Jun 30 10:30:31 localhost kernel: [    0.000000] ACPI: MCFG (v001 HP     0944     0x00000001 HP   0x00000001) @ 0x0000000077fefd14
Jun 30 10:30:31 localhost kernel: [    0.000000] ACPI: SSDT (v001 HP       HPQPpc 0x00001001 MSFT 0x0100000e) @ 0x0000000077ff71d9
Jun 30 10:30:31 localhost kernel: [    0.000000] ACPI: DSDT (v001 HP        SB400 0x00010000 MSFT 0x0100000e) @ 0x0000000000000000
Jun 30 10:30:31 localhost kernel: [    0.000000] Scanning NUMA topology in Northbridge 24
Jun 30 10:30:31 localhost kernel: [    0.000000] Number of nodes 1
Jun 30 10:30:31 localhost kernel: [    0.000000] Node 0 MemBase 0000000000000000 Limit 0000000077fd0000
Jun 30 10:30:31 localhost kernel: [    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
Jun 30 10:30:31 localhost kernel: [    0.000000] Entering add_active_range(0, 256, 491472) 1 entries of 3200 used
Jun 30 10:30:31 localhost kernel: [    0.000000] NUMA: Using 63 for the hash shift.
Jun 30 10:30:31 localhost kernel: [    0.000000] Using node hash shift of 63
Jun 30 10:30:31 localhost kernel: [    0.000000] Bootmem setup node 0 0000000000000000-0000000077fd0000
Jun 30 10:30:31 localhost kernel: [    0.000000] No mptable found.
Jun 30 10:30:31 localhost kernel: [    0.000000] Zone PFN ranges:
Jun 30 10:30:31 localhost kernel: [    0.000000]   DMA             0 ->     4096
Jun 30 10:30:31 localhost kernel: [    0.000000]   DMA32        4096 ->  1048576
Jun 30 10:30:31 localhost kernel: [    0.000000]   Normal    1048576 ->  1048576
Jun 30 10:30:31 localhost kernel: [    0.000000] early_node_map[2] active PFN ranges
Jun 30 10:30:31 localhost kernel: [    0.000000]     0:        0 ->      159
Jun 30 10:30:31 localhost kernel: [    0.000000]     0:      256 ->   491472
Jun 30 10:30:31 localhost kernel: [    0.000000] On node 0 totalpages: 491375
Jun 30 10:30:31 localhost kernel: [    0.000000]   DMA zone: 56 pages used for memmap
Jun 30 10:30:31 localhost kernel: [    0.000000]   DMA zone: 1085 pages reserved
Jun 30 10:30:31 localhost kernel: [    0.000000]   DMA zone: 2858 pages, LIFO batch:0
Jun 30 10:30:31 localhost kernel: [    0.000000]   DMA32 zone: 6663 pages used for memmap
Jun 30 10:30:31 localhost kernel: [    0.000000]   DMA32 zone: 480713 pages, LIFO batch:31
Jun 30 10:30:31 localhost kernel: [    0.000000]   Normal zone: 0 pages used for memmap
Jun 30 10:30:31 localhost kernel: [    0.000000] ATI board detected. Disabling timer routing over 8254.
Jun 30 10:30:31 localhost kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x8008
Jun 30 10:30:31 localhost kernel: [    0.000000] ACPI: Local APIC address 0xfec01000
Jun 30 10:30:31 localhost kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Jun 30 10:30:31 localhost kernel: [    0.000000] Processor #0 (Bootup-CPU)
Jun 30 10:30:31 localhost kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Jun 30 10:30:31 localhost kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Jun 30 10:30:31 localhost kernel: [    0.000000] IOAPIC[0]: apic_id 1, address 0xfec00000, GSI 0-23
Jun 30 10:30:31 localhost kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jun 30 10:30:31 localhost kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 21 low level)
Jun 30 10:30:31 localhost kernel: [    0.000000] ACPI: IRQ0 used by override.
Jun 30 10:30:31 localhost kernel: [    0.000000] ACPI: IRQ2 used by override.
Jun 30 10:30:31 localhost kernel: [    0.000000] Setting APIC routing to physical flat
Jun 30 10:30:31 localhost kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jun 30 10:30:31 localhost kernel: [    0.000000] Nosave address range: 000000000009f000 - 00000000000a0000
Jun 30 10:30:31 localhost kernel: [    0.000000] Nosave address range: 00000000000a0000 - 00000000000e0000
Jun 30 10:30:31 localhost kernel: [    0.000000] Nosave address range: 00000000000e0000 - 0000000000100000
Jun 30 10:30:31 localhost kernel: [    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
Jun 30 10:30:31 localhost kernel: [    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
Jun 30 10:30:31 localhost kernel: [    0.000000] PERCPU: Allocating 34048 bytes of per cpu data
Jun 30 10:30:31 localhost kernel: [    0.000000] Built 1 zonelists.  Total pages: 483571
Jun 30 10:30:31 localhost kernel: [    0.000000] Kernel command line: root=UUID=b3e7deb6-c86d-4129-9927-487402b8ba9a ro quiet splash
Jun 30 10:30:31 localhost kernel: [    0.000000] Initializing CPU#0
Jun 30 10:30:31 localhost kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
Jun 30 10:30:31 localhost kernel: [   16.831181] Console: colour VGA+ 80x25
Jun 30 10:30:31 localhost kernel: [   16.833545] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
Jun 30 10:30:31 localhost kernel: [   16.837268] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
Jun 30 10:30:31 localhost kernel: [   16.837497] Checking aperture...
Jun 30 10:30:31 localhost kernel: [   16.837501] CPU 0: aperture @ e772000000 size 32 MB
Jun 30 10:30:31 localhost kernel: [   16.837503] Aperture too small (32 MB)
Jun 30 10:30:31 localhost kernel: [   16.849883] No AGP bridge found
Jun 30 10:30:31 localhost kernel: [   16.883584] Memory: 1922868k/1965888k available (2217k kernel code, 42632k reserved, 1162k data, 304k init)
Jun 30 10:30:31 localhost kernel: [   16.960265] Calibrating delay using timer specific routine.. 3594.95 BogoMIPS (lpj=7189901)
Jun 30 10:30:31 localhost kernel: [   16.960331] Security Framework v1.0.0 initialized
Jun 30 10:30:31 localhost kernel: [   16.960338] SELinux:  Disabled at boot.
Jun 30 10:30:31 localhost kernel: [   16.960365] Mount-cache hash table entries: 256
Jun 30 10:30:31 localhost kernel: [   16.960544] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Jun 30 10:30:31 localhost kernel: [   16.960547] CPU: L2 Cache: 1024K (64 bytes/line)
Jun 30 10:30:31 localhost kernel: [   16.960551] CPU 0/0 -> Node 0
Jun 30 10:30:31 localhost kernel: [   16.960573] SMP alternatives: switching to UP code
Jun 30 10:30:31 localhost kernel: [   16.960904] Freeing SMP alternatives: 28k freed
Jun 30 10:30:31 localhost kernel: [   16.961032] Early unpacking initramfs... done
Jun 30 10:30:31 localhost kernel: [   17.351219] ACPI: Core revision 20060707
Jun 30 10:30:31 localhost kernel: [   17.351464] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
Jun 30 10:30:31 localhost kernel: [   17.428239] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
Jun 30 10:30:31 localhost kernel: [   17.468311] Using local APIC timer interrupts.
Jun 30 10:30:31 localhost kernel: [   17.523979] result 12469030
Jun 30 10:30:31 localhost kernel: [   17.523980] Detected 12.469 MHz APIC timer.
Jun 30 10:30:31 localhost kernel: [   17.528040] Brought up 1 CPUs
Jun 30 10:30:31 localhost kernel: [   17.528084] time.c: Using 3.579545 MHz WALL PM GTOD PIT/TSC timer.
Jun 30 10:30:31 localhost kernel: [   17.528086] time.c: Detected 1795.539 MHz processor.
Jun 30 10:30:31 localhost kernel: [   17.528449] Time:  9:29:54  Date: 05/30/107
Jun 30 10:30:31 localhost kernel: [   17.528495] NET: Registered protocol family 16
Jun 30 10:30:31 localhost kernel: [   17.528596] ACPI: bus type pci registered
Jun 30 10:30:31 localhost kernel: [   17.528605] PCI: Using configuration type 1
Jun 30 10:30:31 localhost kernel: [   17.543709] ACPI: Interpreter enabled
Jun 30 10:30:31 localhost kernel: [   17.543711] ACPI: Using IOAPIC for interrupt routing
Jun 30 10:30:31 localhost kernel: [   17.544166] ACPI: PCI Root Bridge [C047] (0000:00)
Jun 30 10:30:31 localhost kernel: [   17.544171] PCI: Probing PCI hardware (bus 00)
Jun 30 10:30:31 localhost kernel: [   17.544191] ACPI: Assume root bridge [\_SB_.C047] bus is 0
Jun 30 10:30:31 localhost kernel: [   17.548410] Boot video device is 0000:01:05.0
Jun 30 10:30:31 localhost kernel: [   17.549174] PCI: Transparent bridge - 0000:00:14.4
Jun 30 10:30:31 localhost kernel: [   17.549250] PCI: Bus #03 (-#06) is hidden behind transparent bridge #02 (-#03) (try 'pci=assign-busses')
Jun 30 10:30:31 localhost kernel: [   17.549252] Please report the result to linux-kernel to fix this permanently
Jun 30 10:30:31 localhost kernel: [   17.549290] ACPI: PCI Interrupt Routing Table [\_SB_.C047._PRT]
Jun 30 10:30:31 localhost kernel: [   17.566274] ACPI: PCI Interrupt Routing Table [\_SB_.C047.C048._PRT]
Jun 30 10:30:31 localhost kernel: [   17.566673] ACPI: PCI Interrupt Routing Table [\_SB_.C047.C0AB._PRT]
Jun 30 10:30:31 localhost kernel: [   17.567220] ACPI: Power Resource [C1CF] (off)
Jun 30 10:30:31 localhost kernel: [   17.576542] ACPI: Power Resource [C1C7] (on)
Jun 30 10:30:31 localhost kernel: [   17.578338] ACPI: PCI Interrupt Link [C0F0] (IRQs 10 11) *0, disabled.
Jun 30 10:30:31 localhost kernel: [   17.578745] ACPI: PCI Interrupt Link [C0F1] (IRQs 10 11) *0, disabled.
Jun 30 10:30:31 localhost kernel: [   17.579150] ACPI: PCI Interrupt Link [C0F2] (IRQs 10 11) *0, disabled.
Jun 30 10:30:31 localhost kernel: [   17.579552] ACPI: PCI Interrupt Link [C0F3] (IRQs 10 11) *0, disabled.
Jun 30 10:30:31 localhost kernel: [   17.579973] ACPI: PCI Interrupt Link [C0F4] (IRQs 10 11) *0, disabled.
Jun 30 10:30:31 localhost kernel: [   17.580373] ACPI: PCI Interrupt Link [C0F5] (IRQs 9) *0, disabled.
Jun 30 10:30:31 localhost kernel: [   17.580775] ACPI: PCI Interrupt Link [C0F6] (IRQs 10 11) *0, disabled.
Jun 30 10:30:31 localhost kernel: [   17.581183] ACPI: PCI Interrupt Link [C0F7] (IRQs *10 11)
Jun 30 10:30:31 localhost kernel: [   17.583556] ACPI: Power Resource [C26C] (off)
Jun 30 10:30:31 localhost kernel: [   17.583689] ACPI: Power Resource [C26D] (off)
Jun 30 10:30:31 localhost kernel: [   17.583829] ACPI: Power Resource [C26E] (off)
Jun 30 10:30:31 localhost kernel: [   17.583968] ACPI: Power Resource [C26F] (off)
Jun 30 10:30:31 localhost kernel: [   17.584260] Linux Plug and Play Support v0.97 (c) Adam Belay
Jun 30 10:30:31 localhost kernel: [   17.584270] pnp: PnP ACPI init
Jun 30 10:30:31 localhost kernel: [   17.591757] pnp: PnP ACPI: found 11 devices
Jun 30 10:30:31 localhost kernel: [   17.591812] PCI: Using ACPI for IRQ routing
Jun 30 10:30:31 localhost kernel: [   17.591814] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Jun 30 10:30:31 localhost kernel: [   17.591822] PCI: Cannot allocate resource region 7 of bridge 0000:00:04.0
Jun 30 10:30:31 localhost kernel: [   17.591824] PCI: Cannot allocate resource region 8 of bridge 0000:00:04.0
Jun 30 10:30:31 localhost kernel: [   17.591827] PCI: Cannot allocate resource region 9 of bridge 0000:00:04.0
Jun 30 10:30:31 localhost kernel: [   17.591829] PCI: Cannot allocate resource region 7 of bridge 0000:00:05.0
Jun 30 10:30:31 localhost kernel: [   17.591832] PCI: Cannot allocate resource region 8 of bridge 0000:00:05.0
Jun 30 10:30:31 localhost kernel: [   17.591834] PCI: Cannot allocate resource region 9 of bridge 0000:00:05.0
Jun 30 10:30:31 localhost kernel: [   17.591980] NET: Registered protocol family 8
Jun 30 10:30:31 localhost kernel: [   17.591982] NET: Registered protocol family 20
Jun 30 10:30:31 localhost kernel: [   17.593730] pnp: 00:08: ioport range 0x40b-0x40b has been reserved
Jun 30 10:30:31 localhost kernel: [   17.593733] pnp: 00:08: ioport range 0x4d0-0x4d1 has been reserved
Jun 30 10:30:31 localhost kernel: [   17.593736] pnp: 00:08: ioport range 0x4d6-0x4d6 has been reserved
Jun 30 10:30:31 localhost kernel: [   17.593741] pnp: 00:09: ioport range 0x8000-0x802f could not be reserved
Jun 30 10:30:31 localhost kernel: [   17.593745] pnp: 00:09: ioport range 0x8100-0x811f could not be reserved
Jun 30 10:30:31 localhost kernel: [   17.594044] PCI: Bridge: 0000:00:01.0
Jun 30 10:30:31 localhost kernel: [   17.594047]   IO window: 2000-2fff
Jun 30 10:30:31 localhost kernel: [   17.594050]   MEM window: d0400000-d07fffff
Jun 30 10:30:31 localhost kernel: [   17.594053]   PREFETCH window: c0000000-cfffffff
Jun 30 10:30:31 localhost kernel: [   17.594056] PCI: Bridge: 0000:00:04.0
Jun 30 10:30:31 localhost kernel: [   17.594058]   IO window: disabled.
Jun 30 10:30:31 localhost kernel: [   17.594060]   MEM window: disabled.
Jun 30 10:30:31 localhost kernel: [   17.594062]   PREFETCH window: disabled.
Jun 30 10:30:31 localhost kernel: [   17.594065] PCI: Bridge: 0000:00:05.0
Jun 30 10:30:31 localhost kernel: [   17.594066]   IO window: disabled.
Jun 30 10:30:31 localhost kernel: [   17.594069]   MEM window: disabled.
Jun 30 10:30:31 localhost kernel: [   17.594071]   PREFETCH window: disabled.
Jun 30 10:30:31 localhost kernel: [   17.594077] PCI: Bus 3, cardbus bridge: 0000:02:04.0
Jun 30 10:30:31 localhost kernel: [   17.594079]   IO window: 00001000-000010ff
Jun 30 10:30:31 localhost kernel: [   17.594085]   IO window: 00001400-000014ff
Jun 30 10:30:31 localhost kernel: [   17.594091]   PREFETCH window: 88000000-8bffffff
Jun 30 10:30:31 localhost kernel: [   17.594097]   MEM window: 8c000000-8fffffff
Jun 30 10:30:31 localhost kernel: [   17.594103] PCI: Bridge: 0000:00:14.4
Jun 30 10:30:31 localhost kernel: [   17.594106]   IO window: 1000-1fff
Jun 30 10:30:31 localhost kernel: [   17.594113]   MEM window: d0000000-d03fffff
Jun 30 10:30:31 localhost kernel: [   17.594119]   PREFETCH window: 88000000-8bffffff
Jun 30 10:30:31 localhost kernel: [   17.594138] PCI: Setting latency timer of device 0000:00:04.0 to 64
Jun 30 10:30:31 localhost kernel: [   17.594145] PCI: Setting latency timer of device 0000:00:05.0 to 64
Jun 30 10:30:31 localhost kernel: [   17.594174] ACPI: PCI Interrupt 0000:02:04.0[A] -> GSI 20 (level, low) -> IRQ 20
Jun 30 10:30:31 localhost kernel: [   17.594261] NET: Registered protocol family 2
Jun 30 10:30:31 localhost kernel: [   17.632036] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
Jun 30 10:30:31 localhost kernel: [   17.632844] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
Jun 30 10:30:31 localhost kernel: [   17.637938] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Jun 30 10:30:31 localhost kernel: [   17.639212] TCP: Hash tables configured (established 262144 bind 65536)
Jun 30 10:30:31 localhost kernel: [   17.639215] TCP reno registered
Jun 30 10:30:31 localhost kernel: [   17.648071] checking if image is initramfs... it is
Jun 30 10:30:31 localhost kernel: [   18.437173] Freeing initrd memory: 8181k freed
Jun 30 10:30:31 localhost kernel: [   18.447329] audit: initializing netlink socket (disabled)
Jun 30 10:30:31 localhost kernel: [   18.447345] audit(1183195794.496:1): initialized
Jun 30 10:30:31 localhost kernel: [   18.447505] VFS: Disk quotas dquot_6.5.1
Jun 30 10:30:31 localhost kernel: [   18.447530] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Jun 30 10:30:31 localhost kernel: [   18.447584] io scheduler noop registered
Jun 30 10:30:31 localhost kernel: [   18.447588] io scheduler anticipatory registered
Jun 30 10:30:31 localhost kernel: [   18.447590] io scheduler deadline registered
Jun 30 10:30:31 localhost kernel: [   18.447602] io scheduler cfq registered (default)
Jun 30 10:30:31 localhost kernel: [   18.447847] PCI: Setting latency timer of device 0000:00:04.0 to 64
Jun 30 10:30:31 localhost kernel: [   18.447869] assign_interrupt_mode Found MSI capability
Jun 30 10:30:31 localhost kernel: [   18.447872] Allocate Port Service[0000:00:04.0:pcie00]
Jun 30 10:30:31 localhost kernel: [   18.447902] Allocate Port Service[0000:00:04.0:pcie02]
Jun 30 10:30:31 localhost kernel: [   18.447969] PCI: Setting latency timer of device 0000:00:05.0 to 64
Jun 30 10:30:31 localhost kernel: [   18.447990] assign_interrupt_mode Found MSI capability
Jun 30 10:30:31 localhost kernel: [   18.447993] Allocate Port Service[0000:00:05.0:pcie00]
Jun 30 10:30:31 localhost kernel: [   18.448022] Allocate Port Service[0000:00:05.0:pcie02]
Jun 30 10:30:31 localhost kernel: [   18.472454] Real Time Clock Driver v1.12ac
Jun 30 10:30:31 localhost kernel: [   18.472503] Linux agpgart interface v0.102 (c) Dave Jones
Jun 30 10:30:31 localhost kernel: [   18.472506] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Jun 30 10:30:31 localhost kernel: [   18.473033] ACPI: PCI Interrupt 0000:00:14.6[B] -> GSI 17 (level, low) -> IRQ 17
Jun 30 10:30:31 localhost kernel: [   18.473044] ACPI: PCI interrupt for device 0000:00:14.6 disabled
Jun 30 10:30:31 localhost kernel: [   18.473122] mice: PS/2 mouse device common for all mice
Jun 30 10:30:31 localhost kernel: [   18.473681] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Jun 30 10:30:31 localhost kernel: [   18.473934] input: Macintosh mouse button emulation as /class/input/input0
Jun 30 10:30:31 localhost kernel: [   18.473966] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Jun 30 10:30:31 localhost kernel: [   18.473970] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Jun 30 10:30:31 localhost kernel: [   18.474245] PNP: PS/2 Controller [PNP0303:C1C4,PNP0f13:C1C5] at 0x60,0x64 irq 1,12
Jun 30 10:30:31 localhost kernel: [   18.476900] i8042.c: Detected active multiplexing controller, rev 1.1.
Jun 30 10:30:31 localhost kernel: [   18.477612] serio: i8042 KBD port at 0x60,0x64 irq 1
Jun 30 10:30:31 localhost kernel: [   18.477617] serio: i8042 AUX0 port at 0x60,0x64 irq 12
Jun 30 10:30:31 localhost kernel: [   18.477620] serio: i8042 AUX1 port at 0x60,0x64 irq 12
Jun 30 10:30:31 localhost kernel: [   18.477623] serio: i8042 AUX2 port at 0x60,0x64 irq 12
Jun 30 10:30:31 localhost kernel: [   18.477626] serio: i8042 AUX3 port at 0x60,0x64 irq 12
Jun 30 10:30:31 localhost kernel: [   18.477719] TCP cubic registered
Jun 30 10:30:31 localhost kernel: [   18.477728] NET: Registered protocol family 1
Jun 30 10:30:31 localhost kernel: [   18.477869] ACPI: (supports S0 S3 S4 S5)
Jun 30 10:30:31 localhost kernel: [   18.477914]   Magic number: 11:134:476
Jun 30 10:30:31 localhost kernel: [   18.478046] drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
Jun 30 10:30:31 localhost kernel: [   18.478145] Freeing unused kernel memory: 304k freed
Jun 30 10:30:31 localhost kernel: [   18.499926] input: AT Translated Set 2 keyboard as /class/input/input1
Jun 30 10:30:31 localhost kernel: [   19.661690] Capability LSM initialized
Jun 30 10:30:31 localhost kernel: [   19.963946] device-mapper: ioctl: 4.11.0-ioctl (2006-10-12) initialised: dm-devel@redhat.com
Jun 30 10:30:31 localhost kernel: [   19.986921] ACPI: Transitioning device [C270] to D3
Jun 30 10:30:31 localhost kernel: [   19.986925] ACPI: Transitioning device [C270] to D3
Jun 30 10:30:31 localhost kernel: [   19.986929] ACPI: Fan [C270] (off)
Jun 30 10:30:31 localhost kernel: [   19.987107] ACPI: Transitioning device [C271] to D3
Jun 30 10:30:31 localhost kernel: [   19.987109] ACPI: Transitioning device [C271] to D3
Jun 30 10:30:31 localhost kernel: [   19.987114] ACPI: Fan [C271] (off)
Jun 30 10:30:31 localhost kernel: [   19.987290] ACPI: Transitioning device [C272] to D3
Jun 30 10:30:31 localhost kernel: [   19.987292] ACPI: Transitioning device [C272] to D3
Jun 30 10:30:31 localhost kernel: [   19.987294] ACPI: Fan [C272] (off)
Jun 30 10:30:31 localhost kernel: [   19.987470] ACPI: Transitioning device [C273] to D3
Jun 30 10:30:31 localhost kernel: [   19.987472] ACPI: Transitioning device [C273] to D3
Jun 30 10:30:31 localhost kernel: [   19.987475] ACPI: Fan [C273] (off)
Jun 30 10:30:31 localhost kernel: [   20.024972] ACPI: CPU0 (power states: C1[C1] C3[C3])
Jun 30 10:30:31 localhost kernel: [   20.024978] ACPI: Processor [C000] (supports 8 throttling states)
Jun 30 10:30:31 localhost kernel: [   20.033461] ACPI: Thermal Zone [TZ1] (78 C)
Jun 30 10:30:31 localhost kernel: [   20.037540] ACPI: Thermal Zone [TZ2] (66 C)
Jun 30 10:30:31 localhost kernel: [   20.045216] ACPI: Thermal Zone [TZ3] (38 C)
Jun 30 10:30:31 localhost kernel: [   20.101343] md: linear personality registered for level -1
Jun 30 10:30:31 localhost kernel: [   20.104397] md: multipath personality registered for level -4
Jun 30 10:30:31 localhost kernel: [   20.107107] md: raid0 personality registered for level 0
Jun 30 10:30:31 localhost kernel: [   20.110365] md: raid1 personality registered for level 1
Jun 30 10:30:31 localhost kernel: [   20.112960] raid5: automatically using best checksumming function: generic_sse
Jun 30 10:30:31 localhost kernel: [   20.130710]    generic_sse:  5716.000 MB/sec
Jun 30 10:30:31 localhost kernel: [   20.130712] raid5: using function: generic_sse (5716.000 MB/sec)
Jun 30 10:30:31 localhost kernel: [   20.202676] raid6: int64x1   1653 MB/s
Jun 30 10:30:31 localhost kernel: [   20.270645] raid6: int64x2   2216 MB/s
Jun 30 10:30:31 localhost kernel: [   20.338608] raid6: int64x4   2324 MB/s
Jun 30 10:30:31 localhost kernel: [   20.406572] raid6: int64x8   1600 MB/s
Jun 30 10:30:31 localhost kernel: [   20.474537] raid6: sse2x1    2303 MB/s
Jun 30 10:30:31 localhost kernel: [   20.542492] raid6: sse2x2    3083 MB/s
Jun 30 10:30:31 localhost kernel: [   20.610459] raid6: sse2x4    3325 MB/s
Jun 30 10:30:31 localhost kernel: [   20.610461] raid6: using algorithm sse2x4 (3325 MB/s)
Jun 30 10:30:31 localhost kernel: [   20.610464] md: raid6 personality registered for level 6
Jun 30 10:30:31 localhost kernel: [   20.610466] md: raid5 personality registered for level 5
Jun 30 10:30:31 localhost kernel: [   20.610468] md: raid4 personality registered for level 4
Jun 30 10:30:31 localhost kernel: [   20.725592] md: raid10 personality registered for level 10
Jun 30 10:30:31 localhost kernel: [   21.165645] usbcore: registered new interface driver usbfs
Jun 30 10:30:31 localhost kernel: [   21.165671] usbcore: registered new interface driver hub
Jun 30 10:30:31 localhost kernel: [   21.165694] usbcore: registered new device driver usb
Jun 30 10:30:31 localhost kernel: [   21.166472] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
Jun 30 10:30:31 localhost kernel: [   21.166512] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 19
Jun 30 10:30:31 localhost kernel: [   21.166529] ohci_hcd 0000:00:13.0: OHCI Host Controller
Jun 30 10:30:31 localhost kernel: [   21.166716] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
Jun 30 10:30:31 localhost kernel: [   21.166738] ohci_hcd 0000:00:13.0: irq 19, io mem 0xd0800000
Jun 30 10:30:31 localhost kernel: [   21.253838] usb usb1: configuration #1 chosen from 1 choice
Jun 30 10:30:31 localhost kernel: [   21.253867] hub 1-0:1.0: USB hub found
Jun 30 10:30:31 localhost kernel: [   21.253881] hub 1-0:1.0: 4 ports detected
Jun 30 10:30:31 localhost kernel: [   21.315650] ieee1394: Initialized config rom entry `ip1394'
Jun 30 10:30:31 localhost kernel: [   21.354282] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 19
Jun 30 10:30:31 localhost kernel: [   21.354303] ohci_hcd 0000:00:13.1: OHCI Host Controller
Jun 30 10:30:31 localhost kernel: [   21.354330] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
Jun 30 10:30:31 localhost kernel: [   21.354350] ohci_hcd 0000:00:13.1: irq 19, io mem 0xd0801000
Jun 30 10:30:31 localhost kernel: [   21.414206] usb usb2: configuration #1 chosen from 1 choice
Jun 30 10:30:31 localhost kernel: [   21.414235] hub 2-0:1.0: USB hub found
Jun 30 10:30:31 localhost kernel: [   21.414252] hub 2-0:1.0: 4 ports detected
Jun 30 10:30:31 localhost kernel: [   21.518256] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 19
Jun 30 10:30:31 localhost kernel: [   21.518275] ehci_hcd 0000:00:13.2: EHCI Host Controller
Jun 30 10:30:31 localhost kernel: [   21.518299] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
Jun 30 10:30:31 localhost kernel: [   21.518364] ehci_hcd 0000:00:13.2: irq 19, io mem 0xd0802000
Jun 30 10:30:31 localhost kernel: [   21.518377] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Jun 30 10:30:31 localhost kernel: [   21.518494] usb usb3: configuration #1 chosen from 1 choice
Jun 30 10:30:31 localhost kernel: [   21.518518] hub 3-0:1.0: USB hub found
Jun 30 10:30:31 localhost kernel: [   21.518525] hub 3-0:1.0: 8 ports detected
Jun 30 10:30:31 localhost kernel: [   21.622169] ATIIXP: IDE controller at PCI slot 0000:00:14.1
Jun 30 10:30:31 localhost kernel: [   21.622191] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 16
Jun 30 10:30:31 localhost kernel: [   21.622204] ATIIXP: chipset revision 0
Jun 30 10:30:31 localhost kernel: [   21.622206] ATIIXP: not 100%% native mode: will probe irqs later
Jun 30 10:30:31 localhost kernel: [   21.622217]     ide0: BM-DMA at 0x3010-0x3017, BIOS settings: hda:DMA, hdb:pio
Jun 30 10:30:31 localhost kernel: [   21.622233]     ide1: BM-DMA at 0x3018-0x301f, BIOS settings: hdc:DMA, hdd:pio
Jun 30 10:30:31 localhost kernel: [   21.622245] Probing IDE interface ide0...
Jun 30 10:30:31 localhost kernel: [   21.910260] hda: TOSHIBA MK8026GAX, ATA DISK drive
Jun 30 10:30:31 localhost kernel: [   22.581599] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Jun 30 10:30:31 localhost kernel: [   22.630820] Probing IDE interface ide1...
Jun 30 10:30:31 localhost kernel: [   23.137206] usb 1-2: new full speed USB device using ohci_hcd and address 3
Jun 30 10:30:31 localhost kernel: [   23.348629] usb 1-2: configuration #1 chosen from 1 choice
Jun 30 10:30:31 localhost kernel: [   23.365575] hdc: HL-DT-ST DVD-RW GWA-4082N, ATAPI CD/DVD-ROM drive
Jun 30 10:30:31 localhost kernel: [   23.652953] usb 1-3: new low speed USB device using ohci_hcd and address 4
Jun 30 10:30:31 localhost kernel: [   23.701870] ide1 at 0x170-0x177,0x376 on irq 15
Jun 30 10:30:31 localhost kernel: [   23.712428] SCSI subsystem initialized
Jun 30 10:30:31 localhost kernel: [   23.718626] libata version 2.20 loaded.
Jun 30 10:30:31 localhost kernel: [   23.720105] tg3.c:v3.72 (January 8, 2007)
Jun 30 10:30:31 localhost kernel: [   23.720137] ACPI: PCI Interrupt 0000:02:01.0[A] -> GSI 23 (level, low) -> IRQ 23
Jun 30 10:30:31 localhost kernel: [   23.727634] hda: max request size: 128KiB
Jun 30 10:30:31 localhost kernel: [   23.765866] eth0: Tigon3 [partno(BCM95788A50) rev 3003 PHY(5705)] (PCI:33MHz:32-bit) 10/100/1000Base-T Ethernet 00:0f:b0:74:25:e7
Jun 30 10:30:31 localhost kernel: [   23.765874] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] Split[0] WireSpeed[0] TSOcap[1] 
Jun 30 10:30:31 localhost kernel: [   23.765878] eth0: dma_rwctrl[763f0000] dma_mask[32-bit]
Jun 30 10:30:31 localhost kernel: [   23.765928] ACPI: PCI Interrupt 0000:02:04.2[C] -> GSI 21 (level, low) -> IRQ 21
Jun 30 10:30:31 localhost kernel: [   23.816196] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[d0013000-d00137ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Jun 30 10:30:31 localhost kernel: [   23.817802] hda: 156301488 sectors (80026 MB), CHS=65535/16/63, UDMA(100)
Jun 30 10:30:31 localhost kernel: [   23.817880] hda: cache flushes supported
Jun 30 10:30:31 localhost kernel: [   23.817918]  hda: hda1 hda2
Jun 30 10:30:31 localhost kernel: [   23.892081] hdc: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, DMA
Jun 30 10:30:31 localhost kernel: [   23.892090] Uniform CD-ROM driver Revision: 3.20
Jun 30 10:30:31 localhost kernel: [   23.900341] usb 1-3: configuration #1 chosen from 1 choice
Jun 30 10:30:31 localhost kernel: [   24.204695] usb 2-1: new full speed USB device using ohci_hcd and address 2
Jun 30 10:30:31 localhost kernel: [   24.205873] EXT3-fs: INFO: recovery required on readonly filesystem.
Jun 30 10:30:31 localhost kernel: [   24.205876] EXT3-fs: write access will be enabled during recovery.
Jun 30 10:30:31 localhost kernel: [   24.409587] usb 2-1: configuration #1 chosen from 1 choice
Jun 30 10:30:31 localhost kernel: [   24.712435] usb 2-3: new full speed USB device using ohci_hcd and address 3
Jun 30 10:30:31 localhost kernel: [   24.924275] usb 2-3: configuration #1 chosen from 1 choice
Jun 30 10:30:31 localhost kernel: [   24.930389] usbcore: registered new interface driver hiddev
Jun 30 10:30:31 localhost kernel: [   24.936891] input: USB Mouse               as /class/input/input2
Jun 30 10:30:31 localhost kernel: [   24.936911] input: USB HID v1.10 Mouse [USB Mouse              ] on usb-0000:00:13.0-3
Jun 30 10:30:31 localhost kernel: [   24.936929] usbcore: registered new interface driver usbhid
Jun 30 10:30:31 localhost kernel: [   24.936932] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
Jun 30 10:30:31 localhost kernel: [   25.084413] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023f9929913c0a]
Jun 30 10:30:31 localhost kernel: [   29.663532] kjournald starting.  Commit interval 5 seconds
```

---

### Post by JamesX on 2007-06-30
Well I've logged it as an Ubuntu Bug No.#123234, and guess all I can do is sit back now and hope someone reads this post or the Bug I've logged and is able to help :-)

Cheers, James...

---

