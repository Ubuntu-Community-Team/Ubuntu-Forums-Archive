---
title: "Playing a video w/ Totem vs WIndows Media"
date: 2008-01-04
forum: General Help
---

### Post by sethfc on 2008-01-04
Hey All,

Currently, I'm using totem to view various videos.  Totem has prompted me twice to download codecs, which I did.  There were only two available on the "auto download" screen that popped up.

At any rate, I'm watching videos, and I feel that totem seems to look more pixelated than windows media does.

could this be true?  if so, is there a fix?

-seth

---

### Post by dannyboy79 on 2008-01-04
it's most likely the video driver you're using. do you know which graphics module you're using?

what does the output from these commands produce, please paste it in a response. enter the commands in a terminal session, that you can open from within Application, Accessories, Terminal

lspci

dmesg

---

### Post by sethfc on 2008-01-05
lspci:::

```

sethfc@sethfc-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IB (ICH9) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IB (ICH9) 2 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7800 GT] (rev a1)
03:00.0 IDE interface: JMicron Technologies, Inc. JMB368 IDE controller
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
05:02.0 Multimedia audio controller: Creative Labs SB Audigy LS

```

dmesg::

```

sethfc@sethfc-desktop:~$ dmesg
[    0.000000] Linux version 2.6.22-14-generic (buildd@king) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Dec 18 05:28:27 UTC 2007 (Ubuntu 2.6.22-14.47-generic)
[    0.000000] Command line: root=UUID=2239811b-70b3-4c63-8eb0-b95145351eb5 ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fee0000 (usable)
[    0.000000]  BIOS-e820: 000000007fee0000 - 000000007fee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fee3000 - 000000007fef0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007fef0000 - 000000007ff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 524000) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP signature @ 0xFFFF8100000F6AD0 checksum 0
[    0.000000] ACPI: RSDP 000F6AD0, 0014 (r0 GBT   )
[    0.000000] ACPI: RSDT 7FEE3040, 0034 (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
[    0.000000] ACPI: FACP 7FEE30C0, 0074 (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
[    0.000000] ACPI: DSDT 7FEE3180, 49E4 (r1 GBT    GBTUACPI     1000 MSFT  100000C)
[    0.000000] ACPI: FACS 7FEE0000, 0040
[    0.000000] ACPI: HPET 7FEE7CC0, 0038 (r1 GBT    GBTUACPI 42302E31 GBTU       98)
[    0.000000] ACPI: MCFG 7FEE7D40, 003C (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
[    0.000000] ACPI: APIC 7FEE7BC0, 0084 (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000007fee0000
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 524000) 1 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-000000007fee0000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      159
[    0.000000]     0:      256 ->   524000
[    0.000000] On node 0 totalpages: 523903
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1125 pages reserved
[    0.000000]   DMA zone: 2818 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 7108 pages used for memmap
[    0.000000]   DMA32 zone: 512796 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x03] enabled)
[    0.000000] Processor #3
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] Processor #2
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 7ff00000:70100000)
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 34696 bytes of per cpu data
[    0.000000] Built 1 zonelists.  Total pages: 515614
[    0.000000] Kernel command line: root=UUID=2239811b-70b3-4c63-8eb0-b95145351eb5 ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[   23.761054] time.c: Detected 2997.003 MHz processor.
[   23.761996] Console: colour VGA+ 80x25
[   23.762009] Checking aperture...
[   23.762015] Calgary: detecting Calgary via BIOS EBDA area
[   23.762017] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[   23.777616] Memory: 2054984k/2096000k available (2274k kernel code, 40628k reserved, 1181k data, 296k init)
[   23.777648] SLUB: Genslabs=23, HWalign=64, Order=0-1, MinObjects=4, CPUs=4, Nodes=1
[   23.855503] Calibrating delay using timer specific routine.. 5997.84 BogoMIPS (lpj=11995699)
[   23.855525] Security Framework v1.0.0 initialized
[   23.855530] SELinux:  Disabled at boot.
[   23.855654] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[   23.856648] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   23.857135] Mount-cache hash table entries: 256
[   23.857232] CPU: L1 I cache: 32K, L1 D cache: 32K
[   23.857234] CPU: L2 cache: 4096K
[   23.857236] CPU 0/0 -> Node 0
[   23.857238] using mwait in idle threads.
[   23.857239] CPU: Physical Processor ID: 0
[   23.857240] CPU: Processor Core ID: 0
[   23.857244] CPU0: Thermal monitoring enabled (TM2)
[   23.857252] SMP alternatives: switching to UP code
[   23.857435] Early unpacking initramfs... done
[   24.077189] ACPI: Core revision 20070126
[   24.077219] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   24.119747] Using local APIC timer interrupts.
[   24.153052] result 20812524
[   24.153053] Detected 20.812 MHz APIC timer.
[   24.154946] SMP alternatives: switching to SMP code
[   24.155002] Booting processor 1/4 APIC 0x3
[   24.165268] Initializing CPU#1
[   24.242734] Calibrating delay using timer specific routine.. 5994.24 BogoMIPS (lpj=11988491)
[   24.242739] CPU: L1 I cache: 32K, L1 D cache: 32K
[   24.242740] CPU: L2 cache: 4096K
[   24.242742] CPU 1/3 -> Node 0
[   24.242743] CPU: Physical Processor ID: 0
[   24.242744] CPU: Processor Core ID: 3
[   24.242747] CPU1: Thermal monitoring enabled (TM2)
[   24.243092] Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz stepping 0b
[   24.243127] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   24.266717] SMP alternatives: switching to SMP code
[   24.266733] Booting processor 2/4 APIC 0x1
[   24.276998] Initializing CPU#2
[   24.354513] Calibrating delay using timer specific routine.. 5994.11 BogoMIPS (lpj=11988227)
[   24.354518] CPU: L1 I cache: 32K, L1 D cache: 32K
[   24.354519] CPU: L2 cache: 4096K
[   24.354521] CPU 2/1 -> Node 0
[   24.354522] CPU: Physical Processor ID: 0
[   24.354522] CPU: Processor Core ID: 1
[   24.354526] CPU2: Thermal monitoring enabled (TM2)
[   24.354870] Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz stepping 0b
[   24.354957] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
[   24.378510] SMP alternatives: switching to SMP code
[   24.378570] Booting processor 3/4 APIC 0x2
[   24.388835] Initializing CPU#3
[   24.466293] Calibrating delay using timer specific routine.. 5994.25 BogoMIPS (lpj=11988500)
[   24.466297] CPU: L1 I cache: 32K, L1 D cache: 32K
[   24.466299] CPU: L2 cache: 4096K
[   24.466300] CPU 3/2 -> Node 0
[   24.466301] CPU: Physical Processor ID: 0
[   24.466302] CPU: Processor Core ID: 2
[   24.466306] CPU3: Thermal monitoring enabled (TM2)
[   24.466651] Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz stepping 0b
[   24.466695] checking TSC synchronization [CPU#0 -> CPU#3]: passed.
[   24.490251] Brought up 4 CPUs
[   24.986435] migration_cost=10,2728
[   24.986577] NET: Registered protocol family 16
[   24.986634] ACPI: bus type pci registered
[   24.986639] PCI: Using configuration type 1
[   24.987365] ACPI: EC: Look up EC in DSDT
[   24.990028] ACPI: Interpreter enabled
[   24.990032] ACPI: (supports S0 S3 S4 S5)
[   24.990047] ACPI: Using IOAPIC for interrupt routing
[   24.993628] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   24.993640] PCI: Probing PCI hardware (bus 00)
[   24.994657] PCI: Transparent bridge - 0000:00:1e.0
[   24.994701] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   24.994789] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[   24.994834] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX3._PRT]
[   24.994879] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX4._PRT]
[   24.994922] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   25.004158] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[   25.004216] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   25.004273] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 11 *12 14 15)
[   25.004329] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   25.004385] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   25.004442] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[   25.004498] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[   25.004554] ACPI: PCI Interrupt Link [LNK1] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[   25.004610] Linux Plug and Play Support v0.97 (c) Adam Belay
[   25.004617] pnp: PnP ACPI init
[   25.004625] ACPI: bus type pnp registered
[   25.006113] pnp: PnP ACPI: found 14 devices
[   25.006115] ACPI: ACPI bus type pnp unregistered
[   25.006148] PCI: Using ACPI for IRQ routing
[   25.006149] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   25.006217] NET: Registered protocol family 8
[   25.006218] NET: Registered protocol family 20
[   25.006228] PCI-GART: No AMD northbridge found.
[   25.006231] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[   25.006234] hpet0: 4 64-bit timers, 14318180 Hz
[   25.007265] pnp: 00:0a: ioport range 0x400-0x4bf has been reserved
[   25.007268] pnp: 00:0b: iomem range 0xf0000000-0xf3ffffff could not be reserved
[   25.007270] pnp: 00:0c: iomem range 0xcf000-0xcffff has been reserved
[   25.007272] pnp: 00:0c: iomem range 0xf0000-0xf7fff could not be reserved
[   25.007274] pnp: 00:0c: iomem range 0xf8000-0xfbfff could not be reserved
[   25.007275] pnp: 00:0c: iomem range 0xfc000-0xfffff could not be reserved
[   25.007447] PCI: Bridge: 0000:00:01.0
[   25.007449]   IO window: a000-afff
[   25.007451]   MEM window: f4000000-f6ffffff
[   25.007453]   PREFETCH window: e0000000-efffffff
[   25.007455] PCI: Bridge: 0000:00:1c.0
[   25.007457]   IO window: 9000-9fff
[   25.007459]   MEM window: disabled.
[   25.007461]   PREFETCH window: disabled.
[   25.007465] PCI: Bridge: 0000:00:1c.3
[   25.007466]   IO window: b000-bfff
[   25.007469]   MEM window: f7000000-f7ffffff
[   25.007472]   PREFETCH window: disabled.
[   25.007475] PCI: Bridge: 0000:00:1c.4
[   25.007476]   IO window: c000-cfff
[   25.007479]   MEM window: f8000000-f9ffffff
[   25.007482]   PREFETCH window: 80000000-800fffff
[   25.007485] PCI: Bridge: 0000:00:1e.0
[   25.007487]   IO window: d000-dfff
[   25.007489]   MEM window: disabled.
[   25.007492]   PREFETCH window: disabled.
[   25.007501] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   25.007504] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   25.007515] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[   25.007518] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   25.007529] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 19
[   25.007532] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   25.007543] ACPI: PCI Interrupt 0000:00:1c.4[A] -> GSI 16 (level, low) -> IRQ 16
[   25.007546] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   25.007553] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   25.007559] NET: Registered protocol family 2
[   25.009222] Time: tsc clocksource has been installed.
[   25.049184] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[   25.049585] TCP established hash table entries: 262144 (order: 10, 6291456 bytes)
[   25.051587] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   25.052016] TCP: Hash tables configured (established 262144 bind 65536)
[   25.052018] TCP reno registered
[   25.065226] checking if image is initramfs... it is
[   25.499854] Freeing initrd memory: 7202k freed
[   25.502344] audit: initializing netlink socket (disabled)
[   25.502355] audit(1199457627.672:1): initialized
[   25.503786] VFS: Disk quotas dquot_6.5.1
[   25.503817] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   25.503868] io scheduler noop registered
[   25.503870] io scheduler anticipatory registered
[   25.503871] io scheduler deadline registered
[   25.503932] io scheduler cfq registered (default)
[   25.506513] Boot video device is 0000:01:00.0
[   25.506622] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   25.506641] assign_interrupt_mode Found MSI capability
[   25.506643] Allocate Port Service[0000:00:01.0:pcie00]
[   25.506696] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   25.506723] assign_interrupt_mode Found MSI capability
[   25.506724] Allocate Port Service[0000:00:1c.0:pcie00]
[   25.506748] Allocate Port Service[0000:00:1c.0:pcie02]
[   25.506800] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   25.506828] assign_interrupt_mode Found MSI capability
[   25.506829] Allocate Port Service[0000:00:1c.3:pcie00]
[   25.506848] Allocate Port Service[0000:00:1c.3:pcie02]
[   25.506903] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   25.506930] assign_interrupt_mode Found MSI capability
[   25.506932] Allocate Port Service[0000:00:1c.4:pcie00]
[   25.506954] Allocate Port Service[0000:00:1c.4:pcie02]
[   25.520898] Real Time Clock Driver v1.12ac
[   25.520971] Linux agpgart interface v0.102 (c) Dave Jones
[   25.520973] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   25.521049] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   25.521384] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   25.521826] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   25.521910] input: Macintosh mouse button emulation as /class/input/input0
[   25.521958] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   25.521959] PNP: PS/2 controller doesn't have AUX irq; using default 12
[   25.524740] serio: i8042 KBD port at 0x60,0x64 irq 1
[   25.524831] mice: PS/2 mouse device common for all mice
[   25.524917] TCP cubic registered
[   25.524950] NET: Registered protocol family 1
[   25.525074] /build/buildd/linux-source-2.6.22-2.6.22/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   25.525081] Freeing unused kernel memory: 296k freed
[   25.548575] input: AT Translated Set 2 keyboard as /class/input/input1
[   26.626254] AppArmor: AppArmor initialized<5>audit(1199457628.800:2):  type=1505 info="AppArmor initialized" pid=1277
[   26.630205] fuse init (API version 7.8)
[   26.632551] Failure registering capabilities with primary security module.
[   26.661978] ACPI: Processor [CPU0] (supports 8 throttling states)
[   26.661990] ACPI: Processor [CPU1] (supports 8 throttling states)
[   26.662001] ACPI: Processor [CPU2] (supports 8 throttling states)
[   26.662014] ACPI: Processor [CPU3] (supports 8 throttling states)
[   26.901758] usbcore: registered new interface driver usbfs
[   26.901773] usbcore: registered new interface driver hub
[   26.905560] usbcore: registered new device driver usb
[   26.907015] SCSI subsystem initialized
[   26.911512] libata version 2.21 loaded.
[   26.912120] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 19 (level, low) -> IRQ 19
[   26.912144] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   26.912206] scsi0 : pata_jmicron
[   26.912233] scsi1 : pata_jmicron
[   26.912290] ata1: PATA max UDMA/100 cmd 0x000000000001b000 ctl 0x000000000001b102 bmdma 0x000000000001b400 irq 19
[   26.912292] ata2: PATA max UDMA/100 cmd 0x000000000001b200 ctl 0x000000000001b302 bmdma 0x000000000001b408 irq 19
[   26.916706] Floppy drive(s): fd0 is 1.44M
[   26.917542] USB Universal Host Controller Interface driver v3.0
[   26.937006] FDC 0 is a post-1991 82077
[   27.253283] ata1.00: ATAPI: Memorex 16X-DDL-IN, 1.A3, max UDMA/33
[   27.254306] ata1.01: ATA-6: WDC WD800BB-00DKA0, 77.07W77, max UDMA/100
[   27.254309] ata1.01: 156301488 sectors, multi 16: LBA48 
[   27.436921] ata1.00: configured for UDMA/33
[   27.461847] ata1.01: configured for UDMA/100
[   27.621659] scsi 0:0:0:0: CD-ROM            Memorex  16X-DDL-IN       1.A3 PQ: 0 ANSI: 5
[   27.621917] scsi 0:0:1:0: Direct-Access     ATA      WDC WD800BB-00DK 77.0 PQ: 0 ANSI: 5
[   27.622174] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 18 (level, low) -> IRQ 18
[   27.622845] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[   27.622849] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[   27.622963] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[   27.622992] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
[   27.622999] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfa004000
[   27.626872] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   27.626940] usb usb1: configuration #1 chosen from 1 choice
[   27.626955] hub 1-0:1.0: USB hub found
[   27.626958] hub 1-0:1.0: 6 ports detected
[   27.731913] r8169 Gigabit Ethernet driver 2.2LK loaded
[   27.731924] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 23
[   27.732206] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   27.732227] PCI: Setting latency timer of device 0000:04:00.0 to 64
[   27.732436] eth0: RTL8168b/8111b at 0xffffc20000aa4000, 00:1d:7d:9e:c9:35, XID 38000000 IRQ 16
[   27.732490] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   27.732495] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   27.732525] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[   27.732553] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   27.732561] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfa005000
[   27.736429] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   27.736486] usb usb2: configuration #1 chosen from 1 choice
[   27.736501] hub 2-0:1.0: USB hub found
[   27.736505] hub 2-0:1.0: 6 ports detected
[   27.843918] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 16
[   27.843926] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[   27.843928] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[   27.844039] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[   27.844060] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000e000
[   27.844299] usb usb3: configuration #1 chosen from 1 choice
[   27.844412] hub 3-0:1.0: USB hub found
[   27.844415] hub 3-0:1.0: 2 ports detected
[   27.849871] sd 0:0:1:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   27.849878] sd 0:0:1:0: [sda] Write Protect is off
[   27.849880] sd 0:0:1:0: [sda] Mode Sense: 00 3a 00 00
[   27.849887] sd 0:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   27.849918] sd 0:0:1:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   27.849924] sd 0:0:1:0: [sda] Write Protect is off
[   27.849925] sd 0:0:1:0: [sda] Mode Sense: 00 3a 00 00
[   27.849935] sd 0:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   27.849937]  sda: sda1
[   27.863052] sd 0:0:1:0: [sda] Attached SCSI disk
[   27.865479] sr 0:0:0:0: Attached scsi generic sg0 type 5
[   27.865576] sd 0:0:1:0: Attached scsi generic sg1 type 0
[   27.868900] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[   27.868903] Uniform CD-ROM driver Revision: 3.20
[   27.868932] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   27.951489] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 21
[   27.951498] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[   27.951501] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[   27.951519] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[   27.951541] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000e100
[   27.951603] usb usb4: configuration #1 chosen from 1 choice
[   27.951619] hub 4-0:1.0: USB hub found
[   27.951622] hub 4-0:1.0: 2 ports detected
[   28.059249] ACPI: PCI Interrupt 0000:00:1a.2[C] -> GSI 18 (level, low) -> IRQ 18
[   28.059255] PCI: Setting latency timer of device 0000:00:1a.2 to 64
[   28.059257] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[   28.059270] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[   28.059288] uhci_hcd 0000:00:1a.2: irq 18, io base 0x0000e500
[   28.059342] usb usb5: configuration #1 chosen from 1 choice
[   28.059356] hub 5-0:1.0: USB hub found
[   28.059359] hub 5-0:1.0: 2 ports detected
[   28.167018] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 23
[   28.167023] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   28.167025] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   28.167037] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[   28.167055] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000e200
[   28.167107] usb usb6: configuration #1 chosen from 1 choice
[   28.167122] hub 6-0:1.0: USB hub found
[   28.167125] hub 6-0:1.0: 2 ports detected
[   28.274803] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[   28.274807] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   28.274810] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   28.274823] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[   28.274840] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000e300
[   28.274894] usb usb7: configuration #1 chosen from 1 choice
[   28.274908] hub 7-0:1.0: USB hub found
[   28.274911] hub 7-0:1.0: 2 ports detected
[   28.302700] usb 4-2: new low speed USB device using uhci_hcd and address 2
[   28.382590] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   28.382596] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   28.382598] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   28.382609] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[   28.382626] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000e400
[   28.382679] usb usb8: configuration #1 chosen from 1 choice
[   28.382693] hub 8-0:1.0: USB hub found
[   28.382696] hub 8-0:1.0: 2 ports detected
[   28.486548] usb 4-2: configuration #1 chosen from 1 choice
[   28.490894] ata_piix 0000:00:1f.2: version 2.11
[   28.490899] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[   28.490916] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
[   28.490934] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   28.491135] scsi2 : ata_piix
[   28.491955] scsi3 : ata_piix
[   28.492021] ata3: SATA max UDMA/133 cmd 0x00000000000101f0 ctl 0x00000000000103f6 bmdma 0x000000000001f000 irq 14
[   28.492023] ata4: SATA max UDMA/133 cmd 0x0000000000010170 ctl 0x0000000000010376 bmdma 0x000000000001f008 irq 15
[   28.506770] usbcore: registered new interface driver hiddev
[   28.520568] input: B16_b_02 USB-PS/2 Optical Mouse as /class/input/input2
[   28.520579] input: USB HID v1.10 Mouse [B16_b_02 USB-PS/2 Optical Mouse] on usb-0000:00:1a.1-2
[   28.520585] usbcore: registered new interface driver usbhid
[   28.520587] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   28.829944] ata4.00: Host Protected Area detected:
[   28.829945]  current size: 156299375 sectors
[   28.829946]  native size: 156301488 sectors
[   28.830091] ata4.00: native size increased to 156301488 sectors
[   28.830094] ata4.00: ATA-6: WDC WD800JD-00HKA0, 13.03G13, max UDMA/133
[   28.830096] ata4.00: 156301488 sectors, multi 16: LBA 
[   28.853890] ata4.00: configured for UDMA/133
[   28.873635] scsi 3:0:0:0: Direct-Access     ATA      WDC WD800JD-00HK 13.0 PQ: 0 ANSI: 5
[   28.873682] sd 3:0:0:0: [sdb] 156301488 512-byte hardware sectors (80026 MB)
[   28.873688] sd 3:0:0:0: [sdb] Write Protect is off
[   28.873689] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   28.873697] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   28.873728] sd 3:0:0:0: [sdb] 156301488 512-byte hardware sectors (80026 MB)
[   28.873733] sd 3:0:0:0: [sdb] Write Protect is off
[   28.873734] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   28.873743] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   28.873745]  sdb: sdb1 sdb2 sdb3
[   28.903635] sd 3:0:0:0: [sdb] Attached SCSI disk
[   28.903661] sd 3:0:0:0: Attached scsi generic sg2 type 0
[   28.903684] ata_piix 0000:00:1f.5: MAP [ P0 P2 P1 P3 ]
[   28.903701] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 19 (level, low) -> IRQ 19
[   28.903719] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   28.903740] scsi4 : ata_piix
[   28.903765] scsi5 : ata_piix
[   28.903822] ata5: SATA max UDMA/133 cmd 0x000000000001e700 ctl 0x000000000001e802 bmdma 0x000000000001eb00 irq 19
[   28.903825] ata6: SATA max UDMA/133 cmd 0x000000000001e900 ctl 0x000000000001ea02 bmdma 0x000000000001eb08 irq 19
[   29.401505] Attempting manual resume
[   29.401507] swsusp: Resume From Partition 8:19
[   29.401508] PM: Checking swsusp image.
[   29.401696] PM: Resume from disk failed.
[   29.430798] kjournald starting.  Commit interval 5 seconds
[   29.430805] EXT3-fs: mounted filesystem with ordered data mode.
[   35.663570] input: PC Speaker as /class/input/input3
[   35.694879] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   35.705301] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   35.722126] parport_pc 00:08: reported by Plug and Play ACPI
[   35.722168] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   35.897873] nvidia: module license 'NVIDIA' taints kernel.
[   36.149879] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   36.149887] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   36.149965] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  100.14.19  Wed Sep 12 14:08:38 PDT 2007
[   36.214485] ACPI: PCI Interrupt 0000:05:02.0[A] -> GSI 18 (level, low) -> IRQ 18
[   36.214500] snd-ca0106: Model 100a Rev 00000000 Serial 100a1102
[   36.320564] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
[   36.321297] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   37.267674] lp0: using parport0 (interrupt-driven).
[   37.306037] Adding 16056k swap on /dev/sdb3.  Priority:-1 extents:1 across:16056k
[   37.730460] EXT3 FS on sdb2, internal journal
[   38.700730] No dock devices found.
[   38.819565] input: Power Button (FF) as /class/input/input4
[   38.819577] ACPI: Power Button (FF) [PWRF]
[   38.819603] input: Power Button (CM) as /class/input/input5
[   38.819611] ACPI: Power Button (CM) [PWRB]
[   39.941082] ppdev: user-space parallel port driver
[   40.097654] r8169: eth0: link up
[   40.097665] r8169: eth0: link up
[   40.181993] audit(1199486442.981:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5314 profile="/usr/sbin/cupsd"
[   40.292764] Failure registering capabilities with primary security module.
[   40.451677] Bluetooth: Core ver 2.11
[   40.451808] NET: Registered protocol family 31
[   40.451810] Bluetooth: HCI device and connection manager initialized
[   40.451812] Bluetooth: HCI socket layer initialized
[   40.458798] Bluetooth: L2CAP ver 2.8
[   40.458799] Bluetooth: L2CAP socket layer initialized
[   40.525025] Bluetooth: RFCOMM socket layer initialized
[   40.525037] Bluetooth: RFCOMM TTY layer initialized
[   40.525039] Bluetooth: RFCOMM ver 1.8
[   44.860029] NET: Registered protocol family 17
[   49.516856] NET: Registered protocol family 10
[   49.516928] lo: Disabled Privacy Extensions
[   60.319321] eth0: no IPv6 routers present

```

---

### Post by sethfc on 2008-01-05
just an FYI

when i went to "Screen and Graphics", it listed my monitor as "Custom 1".

I changed my monitor to the correct model: Samsung 226BW.

Now my resolution went from 1680 x 1050 (optimal resolution for this monitor) to 1400x1024 or something.

looks fine but.... o_0

---

### Post by dannyboy79 on 2008-01-05
what does your /etc/X11/xorg.conf look like. paste that here as well. You're using the correct nvidia driver I would say. I am not sure why you think it's pixalted more then wmp? have you tried mplayer? just curious. sometimes if your horizontal anmd vertical sync rates in your xorg.conf don't match your monitor you can get bad video problems. look up your monitor on gogle or your manual to find out the monitors specs. are you using nvidia-settings for modifying your X server? i believe it's in synaptic, it's a gui driven way to modify your xorg.conf but sometimes the gui can't detect the optimal settings for your monitor by reading the edid from the monitor so we need to tweek it ourselves byu editing xorg.conf directly.

---

### Post by sethfc on 2008-01-05
xorg.conf::

```

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Boardname	"nv"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Vendorname	"Samsung"
	Modelname	"Samsung SyncMaster 226BW (Digital)"
	Horizsync	30-81
	Vertrefresh	56-75
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@75" 107.21 1280 1360 1496 1712 800 801 804 835 -hsync +vsync
  modeline  "1280x768@75" 102.98 1280 1360 1496 1712 768 769 772 802 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
  modeline  "1440x900@75" 136.49 1440 1536 1688 1936 900 901 904 940 -hsync +vsync
  modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
  modeline  "1600x1024@60" 136.36 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
  modeline  "1680x1050@60" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
  modeline  "1920x1200@60" 193.16 1920 2048 2256 2592 1200 1201 1204 1242 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1920	1200
		Modes		"1680x1050@60"	"1920x1200@60"	"1600x1024@60"	"1440x900@60"	"1440x900@75"	"1280x800@60"	"1280x768@75"	"1280x800@75"	"1280x720@60"	"1280x768@60"	"800x600@60"	"800x600@75"	"800x600@72"	"800x600@56"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
Section "Module"
	Load		"glx"
	Load		"v4l"
EndSection
Section "device" #          
	Identifier	"device1"
	Boardname	"nv"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	1
EndSection
Section "screen" #          
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
		Modes		"640x480@60"
	EndSubSection
EndSection
Section "monitor" #          
	Identifier	"monitor1"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection

```

resolution is another problem as well.  on "Screens and Graphics", my monitor used to be listed as custom 1.  The resolution was correct at 1680x1050, and the refresh rate was listed at 50Hz (wrong).

I figured changing my monitor to the correct model would fix this.  I changed it to Samsung Syncmaster 226BW digital (as I use DVI).

Now whenever i boot i'm at 1600x1024 resolution at 50HZ.  I can manually change it to 1680x1050, but the only refresh rate option is 62HZ.  If I do this, a restart simply defaults me back to the 1600x1024.

o_0

---

### Post by sethfc on 2008-01-05
new developments

under "  sudo nvidia-settings  " i can change my resolution 1680x1050 @ 60HZ.

Although, it does not save.  It reverts back to 1600x1024 @ "Auto" Hz when system reboots.

In Nvidia-Settings under "X Screen 0" (on the left column) it says my Screen Number 0 is dimensions of 1600 x 1024.

This may be my problem....


so how do i edit "Screen 0" in Xorg.conf?

---

### Post by sethfc on 2008-01-05
up to the top!

---

### Post by shamrock_uk on 2008-01-06
> **sethfc said:**
> new developments

under "  sudo nvidia-settings  " i can change my resolution 1680x1050 @ 60HZ.

Although, it does not save.  It reverts back to 1600x1024 @ "Auto" Hz when system reboots.

Just checking, after you make the change (and presumably the resolution alters), you are clicking the 'save to X configuration file' button afterwards, right?

A google search [here](http://www.nvnews.net/vbulletin/showpost.php?p=1200758&postcount=4) suggests some xorg.conf entries. 

I would suggest you back up your current one:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.con_backup
```

Then replace the existing sections with the following (or comment the old sections out with a # at the start of each line):

```

Section "Monitor"
    Identifier     "SyncMaster"
    DisplaySize     432    324
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection


Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "SyncMaster"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1680x1050" 
    EndSubSection

```

Then restart the X server with ctrl + alt + backspace, or do a full restart as you prefer.

Do let us know...

---

### Post by sethfc on 2008-01-06
i'm at work currently, and i guess the I.T. guys here have blocked the VNC port 5900 or whatever, cuz I cant remote to my computer at home.

When i make the nvidia-settings changes, i hit apply.  maybe i'm missing that button.

i'll try these things when i get home.

thank you very much!

-seth

---

### Post by shamrock_uk on 2008-01-06
> **sethfc said:**
> i'm at work currently, and i guess the I.T. guys here have blocked the VNC port 5900 or whatever, cuz I cant remote to my computer at home.

When i make the nvidia-settings changes, i hit apply.  maybe i'm missing that button.

i'll try these things when i get home.

thank you very much!

-seth

Don't mention it. On my version in the 'X server display configuration' tab, I have Apply, Detect Displays, Advanced and Reset buttons all alongside each other, then Save to X Config file under them and finally Quit and Help at the very bottom.

Looking at the 'X Server Information' tab, I'm using version 1.13 of the nVidia control panel which should be the default for an updated Gutsy as I haven't done anything fancy.

---

### Post by dannyboy79 on 2008-01-07
> **sethfc said:**
> i'm at work currently, and i guess the I.T. guys here have blocked the VNC port 5900 or whatever, cuz I cant remote to my computer at home.

When i make the nvidia-settings changes, i hit apply.  maybe i'm missing that button.

i'll try these things when i get home.

thank you very much!

-seth

you know how I solve that at my work? I use ssh and do some ssh tunneling (port forwarding). it's most likely that your work still has ssh port open or for sure they have port 80 open. within putty you define tunnels for instant messaging (dynamic tunnel) and also a local tunnel for VNC, then when you ssh into your box those tunnels will be setup and it forwards port 5900 thru ssh (making it more secure for one) and allows you to connect to the localhost:5900. It's really cool. Hope you figure out your video problem soon. I wish I could help more but I think I am at the end of my tips.

---

### Post by sethfc on 2008-01-07
> **dannyboy79 said:**
> you know how I solve that at my work? I use ssh and do some ssh tunneling (port forwarding). it's most likely that your work still has ssh port open or for sure they have port 80 open. within putty you define tunnels for instant messaging (dynamic tunnel) and also a local tunnel for VNC, then when you ssh into your box those tunnels will be setup and it forwards port 5900 thru ssh (making it more secure for one) and allows you to connect to the localhost:5900. It's really cool. Hope you figure out your video problem soon. I wish I could help more but I think I am at the end of my tips.

dude, that sounds awesome... mind if you and i talk sometime soon so i can figure this out?  i'm kinda a networking noob as well =p

SHAMROCK_UK

thanks bro!! it worked!!

mucho thanks!
-seth

---

### Post by dannyboy79 on 2008-01-07
no problem, you can IM me or just PM me.

---

