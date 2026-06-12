---
title: "Crazy unexplainable slowdown issue?"
date: 2007-12-18
forum: General Help
---

### Post by Simimi on 2007-12-18
I am not sure how to explain this one... Let me try though. Basically, I was using my notebook as normal. 100% Ubuntu Gutsy machine. One day, I noticed it was laggy. Not just slow, but ridiculously so. So I restarted it. After a few days and more than a few restarts, the system starts up completely bogged down it feels like. Moving the mouse is lagged from a fresh login. The login takes quite a bit of time now. Clicking an icon on my gnome-panal has a significant lag. Even typing in the terminal is quite slow.

I have no idea what could be causing this. The only thing my computer was doing when the lag started was running Deluge (bit torrent client). The only event that has happened within memory of this happening is myself installing a new libcairo2 from backports I think it was, when it came up on my check.

For some reason, Deluge now will not get even a quarter of the speed it used to, even though our internet is just fine. I haven't tried switching to a different desktop (since I do not have one, suppose I could try openbox...) but I do not think that would do a lot.

Any ideas would be really helpful, at this point I am kind of out of ideas. I have checked the forums as well as the net and I haven't found the issue or answer yet. I saw something on launchpad but it does not seem to be the same as my issue.
:confused:

EDIT: Even with just Openbox, the slow down remains... I am fresh out of ideas now.

---

### Post by cdenley on 2007-12-18
A few troubleshooting steps you can try:

-run dmesg and check for errors
-run memory test from grub menu
-boot to livecd, see if slowdown occurs when not using your hard drive
-try running another live linux distribution, such as dsl

---

### Post by Simimi on 2007-12-18
After 3 failed attempts at the memory test I do not think I can do it. The system shuts down before it even gets half way. Also, as of <after the memory test failing> when I turn the system on it starts off kind of warm and the fan is going full speed, even though it has a cooling mat beneath it with fans on it too...

DMESG output:
```

[    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
[    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003bf10000 (usable)
[    0.000000]  BIOS-e820: 000000003bf10000 - 000000003bf19000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003bf19000 - 000000003bf80000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003bf80000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 63MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f8790
[    0.000000] Entering add_active_range(0, 0, 245520) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   245520
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   245520
[    0.000000] On node 0 totalpages: 245520
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 126 pages used for memmap
[    0.000000]   HighMem zone: 16018 pages, LIFO batch:3
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00F87C0 checksum 0
[    0.000000] ACPI: RSDP 000F87C0, 0014 (r0 HP    )
[    0.000000] ACPI: RSDT 3BF131F0, 0038 (r1 HP     30B5      6040000  LTP        0)
[    0.000000] ACPI: FACP 3BF18D52, 0074 (r1 HP     30B5      6040000 PTL_    F4240)
[    0.000000] ACPI: DSDT 3BF13228, 5B2A (r1 HP       30B5    6040000 MSFT  100000E)
[    0.000000] ACPI: FACS 3BF19FC0, 0040
[    0.000000] ACPI: MCFG 3BF18DC6, 003C (r1 HP     30B5      6040000  LTP        0)
[    0.000000] ACPI: APIC 3BF18E02, 0054 (r1 HP     30B5      6040000  LTP        0)
[    0.000000] ACPI: BOOT 3BF18E56, 0028 (r1 HP     30B5      6040000  LTP        1)
[    0.000000] ACPI: SSDT 3BF18E7E, 0182 (r1 HP     30B5      6040000  LTP        1)
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:8 APIC version 16
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:8 APIC version 16
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:a0000000)
[    0.000000] Built 1 zonelists.  Total pages: 243602
[    0.000000] Kernel command line: root=UUID=82e7952f-e72c-41bc-93f6-fff47ab3c0b6 ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1607.338 MHz processor.
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Memory: 961796k/982080k available (2015k kernel code, 19740k reserved, 916k data, 364k init, 64576k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    0.000000]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[    0.000000]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
[    0.000000]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    0.000000] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[    0.084000] Calibrating delay using timer specific routine.. 3217.69 BogoMIPS (lpj=6435380)
[    0.084000] Security Framework v1.0.0 initialized
[    0.084000] SELinux:  Disabled at boot.
[    0.084000] Mount-cache hash table entries: 512
[    0.084000] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000001f
[    0.084000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.084000] CPU: L2 Cache: 256K (64 bytes/line)
[    0.084000] CPU 0(2) -> Core 0
[    0.084000] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000410 00002001 00000000 0000001f
[    0.084000] Compat vDSO mapped to ffffe000.
[    0.084000] Checking 'hlt' instruction... OK.
[    0.100000] SMP alternatives: switching to UP code
[    0.100000] Early unpacking initramfs... done
[    0.472000] ACPI: Core revision 20070126
[    0.472000] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[    0.476000] CPU0: AMD Turion(tm) 64 X2  stepping 02
[    0.476000] SMP alternatives: switching to SMP code
[    0.476000] Booting processor 1/1 eip 3000
[    0.484000] Initializing CPU#1
[    0.568000] Calibrating delay using timer specific routine.. 3214.86 BogoMIPS (lpj=6429724)
[    0.568000] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000001f
[    0.568000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.568000] CPU: L2 Cache: 256K (64 bytes/line)
[    0.568000] CPU 1(2) -> Core 1
[    0.568000] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000410 00002001 00000000 0000001f
[    0.568000] CPU1: AMD Turion(tm) 64 X2  stepping 02
[    0.568000] Total of 2 processors activated (6432.55 BogoMIPS).
[    0.568000] ENABLING IO-APIC IRQs
[    0.568000] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[    0.612000] Brought up 2 CPUs
[    0.636000] migration_cost=4000
[    0.640000] Booting paravirtualized kernel on bare hardware
[    0.640000] Time:  1:42:29  Date: 11/19/107
[    0.640000] NET: Registered protocol family 16
[    0.640000] EISA bus registered
[    0.640000] ACPI: bus type pci registered
[    0.664000] PCI: BIOS BUG #81[49435000] found
[    0.664000] PCI: Using configuration type 1
[    0.664000] Setting up standard PCI resources
[    0.664000] ACPI: EC: Look up EC in DSDT
[    0.668000] ACPI: EC: GPE=0x01, ports=0x66, 0x62
[    0.676000] ACPI: Interpreter enabled
[    0.676000] ACPI: (supports S0 S3 S4 S5)
[    0.676000] ACPI: Using IOAPIC for interrupt routing
[    0.684000] ACPI: EC: GPE=0x01, ports=0x66, 0x62
[    0.684000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.684000] PCI: Probing PCI hardware (bus 00)
[    0.688000] PCI: Transparent bridge - 0000:00:10.0
[    0.688000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.688000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P0._PRT]
[    0.688000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR1._PRT]
[    0.688000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR2._PRT]
[    0.776000] ACPI: PCI Interrupt Link [LNK1] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.780000] ACPI: PCI Interrupt Link [LNK2] (IRQs 16 17 18 19 20 21 22 23) *10
[    0.780000] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 10 *11 14 15)
[    0.780000] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 10 11 14 15) *0, disabled.
[    0.780000] ACPI: PCI Interrupt Link [LK1E] (IRQs 20) *0, disabled.
[    0.780000] ACPI: PCI Interrupt Link [LK2E] (IRQs 19) *10
[    0.780000] ACPI: PCI Interrupt Link [LK3E] (IRQs 21) *10
[    0.780000] ACPI: PCI Interrupt Link [LK4E] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.780000] ACPI: PCI Interrupt Link [LSMB] (IRQs 16 17 18 19 20 21 22 23) *10
[    0.780000] ACPI: PCI Interrupt Link [LSMU] (IRQs 16 17 18 19 20 21 22 23) *11
[    0.780000] ACPI: PCI Interrupt Link [LUS0] (IRQs 16 17 18 19 20 21 22 23) *11
[    0.780000] ACPI: PCI Interrupt Link [LUS2] (IRQs 16 17 18 19 20 21 22 23) *7
[    0.780000] ACPI: PCI Interrupt Link [LMAC] (IRQs 16 17 18 19 20 21 22 23) *11
[    0.780000] ACPI: PCI Interrupt Link [LAZA] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.780000] ACPI: PCI Interrupt Link [LACI] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.780000] ACPI: PCI Interrupt Link [LMCI] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.780000] ACPI: PCI Interrupt Link [LPID] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.780000] ACPI: PCI Interrupt Link [LTID] (IRQs 16 17 18 19 20 21 22 23) *5
[    0.780000] ACPI: PCI Interrupt Link [LSI1] (IRQs 16 17 18 19 20 21 22 23) *0
[    0.780000] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.780000] pnp: PnP ACPI init
[    0.780000] ACPI: bus type pnp registered
[    0.784000] pnp: PnP ACPI: found 11 devices
[    0.784000] ACPI: ACPI bus type pnp unregistered
[    0.784000] PnPBIOS: Disabled by ACPI PNP
[    0.784000] PCI: Using ACPI for IRQ routing
[    0.784000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    0.784000] NET: Registered protocol family 8
[    0.784000] NET: Registered protocol family 20
[    0.784000] pnp: 00:00: iomem range 0xffc00000-0xffffffff could not be reserved
[    0.784000] pnp: 00:00: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.784000] pnp: 00:00: iomem range 0xfee00000-0xfeefffff could not be reserved
[    0.784000] pnp: 00:00: iomem range 0x0-0x0 could not be reserved
[    0.784000] pnp: 00:02: iomem range 0xe0000000-0xefffffff could not be reserved
[    0.784000] pnp: 00:03: ioport range 0x1000-0x107f has been reserved
[    0.784000] pnp: 00:03: ioport range 0x1080-0x10ff has been reserved
[    0.784000] pnp: 00:03: ioport range 0x1400-0x147f has been reserved
[    0.784000] pnp: 00:03: ioport range 0x1480-0x14ff has been reserved
[    0.784000] pnp: 00:03: ioport range 0x1800-0x187f has been reserved
[    0.784000] pnp: 00:03: ioport range 0x1880-0x18ff has been reserved
[    0.784000] pnp: 00:03: ioport range 0x2000-0x203f has been reserved
[    0.816000] PCI: Bridge: 0000:00:02.0
[    0.816000]   IO window: disabled.
[    0.816000]   MEM window: c3000000-c30fffff
[    0.816000]   PREFETCH window: disabled.
[    0.816000] PCI: Bridge: 0000:00:03.0
[    0.816000]   IO window: 4000-4fff
[    0.816000]   MEM window: c8000000-c87fffff
[    0.816000]   PREFETCH window: disabled.
[    0.816000] PCI: Bridge: 0000:00:10.0
[    0.816000]   IO window: disabled.
[    0.816000]   MEM window: c3100000-c31fffff
[    0.816000]   PREFETCH window: disabled.
[    0.816000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[    0.816000] PCI: Setting latency timer of device 0000:00:03.0 to 64
[    0.816000] PCI: Setting latency timer of device 0000:00:10.0 to 64
[    0.816000] NET: Registered protocol family 2
[    0.820000] Time: acpi_pm clocksource has been installed.
[    0.864000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.864000] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[    0.864000] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.864000] TCP: Hash tables configured (established 131072 bind 65536)
[    0.864000] TCP reno registered
[    0.880000] checking if image is initramfs... it is
[    1.612000] Freeing initrd memory: 7345k freed
[    1.612000] Simple Boot Flag at 0x36 set to 0x1
[    1.612000] audit: initializing netlink socket (disabled)
[    1.612000] audit(1198028549.320:1): initialized
[    1.612000] highmem bounce pool size: 64 pages
[    1.616000] VFS: Disk quotas dquot_6.5.1
[    1.616000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.616000] io scheduler noop registered
[    1.616000] io scheduler anticipatory registered
[    1.616000] io scheduler deadline registered
[    1.616000] io scheduler cfq registered (default)
[    1.616000] Boot video device is 0000:00:05.0
[    1.636000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[    1.636000] assign_interrupt_mode Found MSI capability
[    1.636000] Allocate Port Service[0000:00:02.0:pcie00]
[    1.636000] PCI: Setting latency timer of device 0000:00:03.0 to 64
[    1.636000] assign_interrupt_mode Found MSI capability
[    1.636000] Allocate Port Service[0000:00:03.0:pcie00]
[    1.636000] isapnp: Scanning for PnP cards...
[    1.988000] isapnp: No Plug & Play device found
[    2.012000] Real Time Clock Driver v1.12ac
[    2.012000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    2.016000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    2.016000] input: Macintosh mouse button emulation as /class/input/input0
[    2.016000] PNP: PS/2 Controller [PNP0303:KBD0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.016000] i8042.c: Detected active multiplexing controller, rev 1.1.
[    2.016000] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.016000] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    2.016000] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    2.016000] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    2.016000] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    2.016000] mice: PS/2 mouse device common for all mice
[    2.016000] EISA: Probing bus 0 at eisa.0
[    2.016000] Cannot allocate resource for EISA slot 1
[    2.016000] Cannot allocate resource for EISA slot 2
[    2.016000] Cannot allocate resource for EISA slot 3
[    2.016000] Cannot allocate resource for EISA slot 4
[    2.016000] EISA: Detected 0 cards.
[    2.016000] TCP cubic registered
[    2.016000] NET: Registered protocol family 1
[    2.016000] Using IPI No-Shortcut mode
[    2.016000]   Magic number: 3:252:711
[    2.016000] Freeing unused kernel memory: 364k freed
[    2.020000] input: AT Translated Set 2 keyboard as /class/input/input1
[    3.284000] AppArmor: AppArmor initialized<5>audit(1198028551.320:2):  type=1505 info="AppArmor initialized" pid=1244
[    3.292000] fuse init (API version 7.8)
[    3.300000] Failure registering capabilities with primary security module.
[    3.328000] ACPI: Processor [CPU0] (supports 8 throttling states)
[    3.328000] ACPI: Processor [CPU1] (supports 8 throttling states)
[    3.340000] ACPI: Thermal Zone [TZS0] (97 C)
[    3.348000] ACPI: Thermal Zone [TZS1] (98 C)
[    4.104000] usbcore: registered new interface driver usbfs
[    4.104000] usbcore: registered new interface driver hub
[    4.104000] usbcore: registered new device driver usb
[    4.104000] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    4.104000] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 23
[    4.104000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LUS0] -> GSI 23 (level, high) -> IRQ 16
[    4.104000] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[    4.104000] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[    4.104000] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 1
[    4.104000] ohci_hcd 0000:00:0b.0: irq 16, io mem 0xc0004000
[    4.128000] SCSI subsystem initialized
[    4.136000] libata version 2.21 loaded.
[    4.168000] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.60.
[    4.180000] usb usb1: configuration #1 chosen from 1 choice
[    4.180000] hub 1-0:1.0: USB hub found
[    4.180000] hub 1-0:1.0: 8 ports detected
[    4.284000] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 22
[    4.284000] ACPI: PCI Interrupt 0000:00:14.0[A] -> Link [LMAC] -> GSI 22 (level, high) -> IRQ 17
[    4.284000] PCI: Setting latency timer of device 0000:00:14.0 to 64
[    4.284000] forcedeth: using HIGHDMA
[    4.812000] eth0: forcedeth.c: subsystem: 0103c:30b5 bound to 0000:00:14.0
[    4.812000] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 21
[    4.812000] ACPI: PCI Interrupt 0000:00:0b.1[B] -> Link [LUS2] -> GSI 21 (level, high) -> IRQ 18
[    4.812000] PCI: Setting latency timer of device 0000:00:0b.1 to 64
[    4.812000] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[    4.812000] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 2
[    4.812000] ehci_hcd 0000:00:0b.1: debug port 1
[    4.812000] PCI: cache line size of 64 is not supported by device 0000:00:0b.1
[    4.812000] ehci_hcd 0000:00:0b.1: irq 18, io mem 0xc0005000
[    4.812000] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.812000] usb usb2: configuration #1 chosen from 1 choice
[    4.812000] hub 2-0:1.0: USB hub found
[    4.812000] hub 2-0:1.0: 8 ports detected
[    4.816000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    4.816000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    4.916000] sata_nv 0000:00:0e.0: version 3.4
[    4.916000] PCI: Enabling device 0000:00:0e.0 (0005 -> 0007)
[    4.916000] ACPI: PCI Interrupt Link [LTID] enabled at IRQ 20
[    4.916000] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [LTID] -> GSI 20 (level, high) -> IRQ 19
[    4.916000] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[    4.916000] scsi0 : sata_nv
[    4.916000] scsi1 : sata_nv
[    4.916000] ata1: SATA max UDMA/133 cmd 0x000130b0 ctl 0x000130a6 bmdma 0x00013090 irq 19
[    4.916000] ata2: SATA max UDMA/133 cmd 0x000130a8 ctl 0x000130a2 bmdma 0x00013098 irq 19
[    5.388000] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    5.396000] ata1.00: ATA-7: WDC WD1200BEVS-60LAT0, 01.06M01, max UDMA/100
[    5.396000] ata1.00: 234441648 sectors, multi 16: LBA48 
[    5.404000] ata1.00: configured for UDMA/100
[    5.716000] ata2: SATA link down (SStatus 0 SControl 300)
[    5.720000] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1200BEVS-6 01.0 PQ: 0 ANSI: 5
[    5.724000] NFORCE-MCP51: IDE controller at PCI slot 0000:00:0d.0
[    5.724000] NFORCE-MCP51: chipset revision 241
[    5.724000] NFORCE-MCP51: not 100% native mode: will probe irqs later
[    5.724000] NFORCE-MCP51: 0000:00:0d.0 (rev f1) UDMA133 controller
[    5.724000]     ide0: BM-DMA at 0x3080-0x3087, BIOS settings: hda:pio, hdb:pio
[    5.724000]     ide1: BM-DMA at 0x3088-0x308f, BIOS settings: hdc:pio, hdd:pio
[    5.724000] Probing IDE interface ide0...
[    5.736000] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[    5.736000] sd 0:0:0:0: [sda] Write Protect is off
[    5.736000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.736000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.736000] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[    5.736000] sd 0:0:0:0: [sda] Write Protect is off
[    5.736000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.736000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.736000]  sda: sda1 sda2 sda3
[    5.812000] sd 0:0:0:0: [sda] Attached SCSI disk
[    5.820000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    6.204000] Attempting manual resume
[    6.204000] swsusp: Resume From Partition 8:1
[    6.204000] PM: Checking swsusp image.
[    6.204000] PM: Resume from disk failed.
[    6.236000] kjournald starting.  Commit interval 5 seconds
[    6.236000] EXT3-fs: mounted filesystem with ordered data mode.
[    6.292000] Probing IDE interface ide1...
[    7.028000] hdc: HL-DT-ST DVDRAM GSA-4084N, ATAPI CD/DVD-ROM drive
[    7.364000] ide1 at 0x170-0x177,0x376 on irq 15
[    7.368000] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 19
[    7.368000] ACPI: PCI Interrupt 0000:03:09.0[A] -> Link [LNK1] -> GSI 19 (level, high) -> IRQ 20
[    7.420000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[20]  MMIO=[c3100000-c31007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    8.712000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[06e40a00ed925044]
[   13.536000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   13.544000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   14.000000] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x3040
[   14.004000] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x3000
[   14.380000] ieee80211_crypt: registered algorithm 'NULL'
[   14.396000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   14.396000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   14.436000] Linux agpgart interface v0.102 (c) Dave Jones
[   14.496000] sdhci: Secure Digital Host Controller Interface driver
[   14.496000] sdhci: Copyright(c) Pierre Ossman
[   14.496000] sdhci: SDHCI controller found at 0000:03:09.1 [1180:0822] (rev 19)
[   14.496000] ACPI: PCI Interrupt Link [LNK2] enabled at IRQ 18
[   14.496000] ACPI: PCI Interrupt 0000:03:09.1[B] -> Link [LNK2] -> GSI 18 (level, high) -> IRQ 21
[   14.496000] mmc0: SDHCI at 0xc3100800 irq 21 DMA
[   14.548000] input: PC Speaker as /class/input/input2
[   14.624000] bcm43xx driver
[   14.624000] ACPI: PCI Interrupt Link [LK2E] enabled at IRQ 19
[   14.624000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LK2E] -> GSI 19 (level, high) -> IRQ 20
[   14.624000] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   14.660000] hdc: ATAPI 24X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, DMA
[   14.660000] Uniform CD-ROM driver Revision: 3.20
[   14.744000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04713/0x200000
[   14.776000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[   14.952000] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 17
[   14.952000] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [LAZA] -> GSI 17 (level, high) -> IRQ 22
[   14.952000] PCI: Setting latency timer of device 0000:00:10.1 to 64
[   16.436000] lp: driver loaded but no devices found
[   16.512000] Adding 2000052k swap on /dev/sda1.  Priority:-1 extents:1 across:2000052k
[   17.000000] EXT3 FS on sda2, internal journal
[   17.740000] kjournald starting.  Commit interval 5 seconds
[   17.740000] EXT3 FS on sda3, internal journal
[   17.740000] EXT3-fs: mounted filesystem with ordered data mode.
[   18.724000] ACPI: AC Adapter [ADP1] (on-line)
[   18.872000] ACPI: Battery Slot [BAT0] (battery present)
[   18.888000] input: Power Button (FF) as /class/input/input4
[   18.888000] ACPI: Power Button (FF) [PWRF]
[   18.888000] input: Lid Switch as /class/input/input5
[   18.888000] ACPI: Lid Switch [LID0]
[   18.888000] input: Sleep Button (CM) as /class/input/input6
[   18.888000] ACPI: Sleep Button (CM) [SLPB]
[   18.888000] input: Power Button (CM) as /class/input/input7
[   18.888000] ACPI: Power Button (CM) [PWRB]
[   18.976000] No dock devices found.
[   19.024000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   19.216000] powernow-k8: Found 2 AMD Turion(tm) 64 X2  processors (version 2.00.00)
[   19.216000] powernow-k8:    0 : fid 0x8 (1600 MHz), vid 0x13
[   19.216000] powernow-k8:    1 : fid 0x0 (800 MHz), vid 0x1e
[   19.976000] apm: BIOS not found.
[   20.344000] Failure registering capabilities with primary security module.
[   20.524000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[   21.816000] Clocksource tsc unstable (delta = -250045828 ns)
[   23.740000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[   26.280000] NET: Registered protocol family 17
[   29.064000] NET: Registered protocol family 10
[   29.064000] lo: Disabled Privacy Extensions
[   39.076000] eth0: no IPv6 routers present
[   49.856000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

```
The wireless card error is normal, since I do not need wireless I do not have the driver installed for it. I even tried a different kernel and the problem persists, let me try a live cd...

---

### Post by cdenley on 2007-12-19
Sounds like a hardware problem.

---

### Post by t-bone510 on 2007-12-19
1. Is your hard drive full or very close to it?

2. Memory Problems.

3. PSU Problem (possible)

---

### Post by Craigus on 2007-12-19
What is shown if you open a terminal and run [COLOR="RoyalBlue"]top[/COLOR] ?

Is something using all of the CPU resources ?

Edit: also, if you boot from a livecd (try another distro), does the same thing happen ?

---

