---
title: "Gutsy doesn't recognize unformatted USB drive..."
date: 2007-11-16
forum: General Help
---

### Post by Arbiter on 2007-11-16
Hi all,

I've got a few hard drives that need to be formatted for the very first time.  I'm using an external USB enclosure to do so.  If the drive is already formatted, Gutsy recognizes it.  If  the drive is not formatted, then gutsy does literally nothing.  It doesn't even show the device in lsusb.  What gives?  Why can't I format or even see these hard drives?  It works fine in XP.

Any help would be greatly appreciated, thanks in advance!

---

### Post by minus198 on 2007-11-16
What does "dmesg" and "lsusb" say?

Post the output here.

---

### Post by Arbiter on 2007-11-16
Here is the output of lsusb with an unformatted drive in the enclosure...

```
adam@mercury:~$ lsusb
Bus 002 Device 005: ID 11b0:6566  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 413c:2005 Dell Computer Corp. 
Bus 001 Device 001: ID 0000:0000  
```


and here it is with a formatted drive in the enclosure...

```
adam@mercury:~$ lsusb
Bus 002 Device 009: ID 152d:2336  
Bus 002 Device 005: ID 11b0:6566  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 413c:2005 Dell Computer Corp. 
Bus 001 Device 001: ID 0000:0000 
```



dmesg with an UNformatted drive attached...

```
[    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007bff0000 (usable)
[    0.000000]  BIOS-e820: 000000007bff0000 - 000000007bff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007bff3000 - 000000007c000000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007c000000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f2000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] 1087MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f4ae0
[    0.000000] Entering add_active_range(0, 0, 507888) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   507888
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   507888
[    0.000000] On node 0 totalpages: 507888
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2175 pages used for memmap
[    0.000000]   HighMem zone: 276337 pages, LIFO batch:31
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F64A0 checksum 0
[    0.000000] ACPI: RSDP 000F64A0, 0014 (r0 GBT   )
[    0.000000] ACPI: RSDT 7BFF3000, 0038 (r1 GBT    NVDAACPI 42302E31 NVDA  1010101)
[    0.000000] ACPI: FACP 7BFF3040, 0074 (r1 GBT    NVDAACPI 42302E31 NVDA  1010101)
[    0.000000] ACPI: DSDT 7BFF30C0, 46EB (r1 GBT    NVDAACPI     1000 MSFT  100000C)
[    0.000000] ACPI: FACS 7BFF0000, 0040
[    0.000000] ACPI: SSDT 7BFF7840, 0206 (r1 PTLTD  POWERNOW        1  LTP        1)
[    0.000000] ACPI: HPET 7BFF7A80, 0038 (r1 GBT    NVDAACPI 42302E31 NVDA       98)
[    0.000000] ACPI: MCFG 7BFF7AC0, 003C (r1 GBT    NVDAACPI 42302E31 NVDA  1010101)
[    0.000000] ACPI: APIC 7BFF77C0, 007C (r1 GBT    NVDAACPI 42302E31 NVDA  1010101)
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:11 APIC version 16
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:11 APIC version 16
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfeff0000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:70000000)
[    0.000000] Built 1 zonelists.  Total pages: 503921
[    0.000000] Kernel command line: root=UUID=00d7022a-0a42-4ce5-aba2-9514f1deac11 ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2109.592 MHz processor.
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Memory: 2002624k/2031552k available (2015k kernel code, 27708k reserved, 916k data, 364k init, 1114048k highmem)
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
[    0.000000] hpet0: at MMIO 0xfeff0000, IRQs 2, 8, 31
[    0.000000] hpet0: 3 32-bit timers, 25000000 Hz
[    0.080000] Calibrating delay using timer specific routine.. 4223.30 BogoMIPS (lpj=8446609)
[    0.080000] Security Framework v1.0.0 initialized
[    0.080000] SELinux:  Disabled at boot.
[    0.080000] Mount-cache hash table entries: 512
[    0.080000] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000011f
[    0.080000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.080000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.080000] CPU 0(2) -> Core 0
[    0.080000] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000410 00002001 00000000 0000011f
[    0.080000] Compat vDSO mapped to ffffe000.
[    0.080000] Checking 'hlt' instruction... OK.
[    0.096000] SMP alternatives: switching to UP code
[    0.096000] Early unpacking initramfs... done
[    0.380000] ACPI: Core revision 20070126
[    0.380000] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[    0.384000] CPU0: AMD Athlon(tm) 64 X2 Dual Core Processor 4000+ stepping 01
[    0.384000] SMP alternatives: switching to SMP code
[    0.384000] Booting processor 1/1 eip 3000
[    0.396000] Initializing CPU#1
[    0.476000] Calibrating delay using timer specific routine.. 4219.20 BogoMIPS (lpj=8438412)
[    0.476000] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000011f
[    0.476000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.476000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.476000] CPU 1(2) -> Core 1
[    0.476000] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000410 00002001 00000000 0000011f
[    0.476000] CPU1: AMD Athlon(tm) 64 X2 Dual Core Processor 4000+ stepping 01
[    0.476000] Total of 2 processors activated (8442.51 BogoMIPS).
[    0.476000] ENABLING IO-APIC IRQs
[    0.476000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.516000] Brought up 2 CPUs
[    0.528000] migration_cost=4000
[    0.528000] Booting paravirtualized kernel on bare hardware
[    0.528000] Time: 16:15:06  Date: 09/25/107
[    0.528000] NET: Registered protocol family 16
[    0.528000] EISA bus registered
[    0.528000] ACPI: bus type pci registered
[    0.536000] PCI: PCI BIOS revision 3.00 entry at 0xfb300, last bus=1
[    0.536000] PCI: Using configuration type 1
[    0.536000] Setting up standard PCI resources
[    0.540000] ACPI: EC: Look up EC in DSDT
[    0.544000] ACPI: Interpreter enabled
[    0.544000] ACPI: (supports S0 S1 S4 S5)
[    0.544000] ACPI: Using IOAPIC for interrupt routing
[    0.552000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.552000] PCI: Probing PCI hardware (bus 00)
[    0.552000] PCI: Transparent bridge - 0000:00:04.0
[    0.552000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.552000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.580000] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.580000] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.580000] ACPI: PCI Interrupt Link [LNK3] (IRQs *5 7 9 10 11 14 15)
[    0.580000] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.580000] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.580000] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.580000] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.580000] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.580000] ACPI: PCI Interrupt Link [LIGP] (IRQs 5 7 9 10 *11 14 15)
[    0.580000] ACPI: PCI Interrupt Link [LP2P] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.580000] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 *10 11 14 15)
[    0.580000] ACPI: PCI Interrupt Link [LMAC] (IRQs *5 7 9 10 11 14 15)
[    0.580000] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 *10 11 14 15)
[    0.580000] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.580000] ACPI: PCI Interrupt Link [LSMB] (IRQs *5 7 9 10 11 14 15)
[    0.580000] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 10 *11 14 15)
[    0.580000] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.580000] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 10 *11 14 15)
[    0.580000] ACPI: PCI Interrupt Link [LFID] (IRQs 5 7 9 *10 11 14 15)
[    0.580000] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[    0.584000] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[    0.584000] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0
[    0.584000] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
[    0.584000] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0, disabled.
[    0.584000] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
[    0.584000] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
[    0.584000] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
[    0.584000] ACPI: PCI Interrupt Link [AIGP] (IRQs 20 21 22 23) *0
[    0.584000] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0
[    0.584000] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0
[    0.584000] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0, disabled.
[    0.584000] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0
[    0.584000] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
[    0.584000] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0
[    0.584000] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
[    0.584000] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[    0.584000] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
[    0.584000] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0
[    0.584000] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.584000] pnp: PnP ACPI init
[    0.584000] ACPI: bus type pnp registered
[    0.588000] pnp: PnP ACPI: found 13 devices
[    0.588000] ACPI: ACPI bus type pnp unregistered
[    0.588000] PnPBIOS: Disabled by ACPI PNP
[    0.588000] PCI: Using ACPI for IRQ routing
[    0.588000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    0.608000] NET: Registered protocol family 8
[    0.608000] NET: Registered protocol family 20
[    0.608000] pnp: 00:01: ioport range 0x1000-0x107f has been reserved
[    0.608000] pnp: 00:01: ioport range 0x1080-0x10ff has been reserved
[    0.608000] pnp: 00:01: ioport range 0x1400-0x147f has been reserved
[    0.608000] pnp: 00:01: ioport range 0x1480-0x14ff has been reserved
[    0.608000] pnp: 00:01: ioport range 0x1800-0x187f has been reserved
[    0.608000] pnp: 00:01: ioport range 0x1880-0x18ff has been reserved
[    0.608000] pnp: 00:01: iomem range 0xfefe0000-0xfefe01ff could not be reserved
[    0.608000] pnp: 00:01: iomem range 0xfefe1000-0xfefe10ff could not be reserved
[    0.608000] pnp: 00:01: iomem range 0x7c000000-0x7fffffff could not be reserved
[    0.608000] pnp: 00:0b: iomem range 0xf0000000-0xf1ffffff could not be reserved
[    0.608000] pnp: 00:0c: iomem range 0xd0000-0xd3fff has been reserved
[    0.608000] pnp: 00:0c: iomem range 0xf0000-0xf7fff could not be reserved
[    0.608000] pnp: 00:0c: iomem range 0xf8000-0xfbfff could not be reserved
[    0.608000] pnp: 00:0c: iomem range 0xfc000-0xfffff could not be reserved
[    0.612000] Time: hpet clocksource has been installed.
[    0.612000] Switched to high resolution mode on CPU 0
[    0.612000] Switched to high resolution mode on CPU 1
[    0.640000] PCI: Bridge: 0000:00:04.0
[    0.640000]   IO window: disabled.
[    0.640000]   MEM window: f5000000-f50fffff
[    0.640000]   PREFETCH window: disabled.
[    0.640000] PCI: Setting latency timer of device 0000:00:04.0 to 64
[    0.640000] NET: Registered protocol family 2
[    0.684000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.684000] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[    0.684000] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.684000] TCP: Hash tables configured (established 131072 bind 65536)
[    0.684000] TCP reno registered
[    0.700000] checking if image is initramfs... it is
[    1.252000] Freeing initrd memory: 7099k freed
[    1.252000] audit: initializing netlink socket (disabled)
[    1.252000] audit(1193328906.112:1): initialized
[    1.252000] highmem bounce pool size: 64 pages
[    1.252000] VFS: Disk quotas dquot_6.5.1
[    1.252000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.252000] io scheduler noop registered
[    1.252000] io scheduler anticipatory registered
[    1.252000] io scheduler deadline registered
[    1.252000] io scheduler cfq registered (default)
[    1.280000] Boot video device is 0000:00:0d.0
[    1.280000] isapnp: Scanning for PnP cards...
[    1.632000] isapnp: No Plug & Play device found
[    1.652000] Real Time Clock Driver v1.12ac
[    1.652000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    1.652000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.652000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.652000] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.652000] 00:08: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.652000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    1.652000] input: Macintosh mouse button emulation as /class/input/input0
[    1.652000] PNP: PS/2 Controller [PNP0f13:PS2M] at 0x60,0x64 irq 12
[    1.652000] PNP: PS/2 controller doesn't have KBD irq; using default 1
[    1.656000] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.656000] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.656000] mice: PS/2 mouse device common for all mice
[    1.656000] EISA: Probing bus 0 at eisa.0
[    1.656000] Cannot allocate resource for EISA slot 1
[    1.656000] EISA: Detected 0 cards.
[    1.656000] TCP cubic registered
[    1.656000] NET: Registered protocol family 1
[    1.656000] Using IPI No-Shortcut mode
[    1.656000]   Magic number: 11:320:288
[    1.656000]   hash matches device ttyz2
[    1.656000]   hash matches device tty21
[    1.656000] Freeing unused kernel memory: 364k freed
[    3.016000] AppArmor: AppArmor initialized<5>audit(1193328907.612:2):  type=1505 info="AppArmor initialized" pid=1239
[    3.028000] fuse init (API version 7.8)
[    3.040000] Failure registering capabilities with primary security module.
[    4.108000] usbcore: registered new interface driver usbfs
[    4.108000] usbcore: registered new interface driver hub
[    4.108000] usbcore: registered new device driver usb
[    4.108000] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    4.108000] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 23
[    4.108000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [APCF] -> GSI 23 (level, low) -> IRQ 16
[    4.108000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[    4.108000] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    4.108000] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[    4.108000] ohci_hcd 0000:00:02.0: irq 16, io mem 0xf5105000
[    4.188000] usb usb1: configuration #1 chosen from 1 choice
[    4.188000] hub 1-0:1.0: USB hub found
[    4.188000] hub 1-0:1.0: 10 ports detected
[    4.244000] SCSI subsystem initialized
[    4.248000] libata version 2.21 loaded.
[    4.252000] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.60.
[    4.292000] sata_nv 0000:00:08.0: version 3.4
[    4.292000] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 22
[    4.292000] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [APSI] -> GSI 22 (level, low) -> IRQ 17
[    4.292000] PCI: Setting latency timer of device 0000:00:08.0 to 64
[    4.292000] scsi0 : sata_nv
[    4.292000] scsi1 : sata_nv
[    4.292000] ata1: SATA max UDMA/133 cmd 0x000109f0 ctl 0x00010bf2 bmdma 0x0001d000 irq 17
[    4.292000] ata2: SATA max UDMA/133 cmd 0x00010970 ctl 0x00010b72 bmdma 0x0001d008 irq 17
[    4.596000] usb 1-4: new low speed USB device using ohci_hcd and address 2
[    4.760000] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    4.768000] ata1.00: ATA-7: WDC WD800JD-60LSA5, 10.01E03, max UDMA/100
[    4.768000] ata1.00: 156301488 sectors, multi 16: LBA48 
[    4.776000] ata1.00: configured for UDMA/100
[    4.808000] usb 1-4: configuration #1 chosen from 1 choice
[    5.088000] ata2: SATA link down (SStatus 0 SControl 300)
[    5.096000] scsi 0:0:0:0: Direct-Access     ATA      WDC WD800JD-60LS 10.0 PQ: 0 ANSI: 5
[    5.096000] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 21
[    5.096000] ACPI: PCI Interrupt 0000:00:08.1[B] -> Link [APSJ] -> GSI 21 (level, low) -> IRQ 18
[    5.096000] PCI: Setting latency timer of device 0000:00:08.1 to 64
[    5.096000] scsi2 : sata_nv
[    5.096000] scsi3 : sata_nv
[    5.096000] ata3: SATA max UDMA/133 cmd 0x000109e0 ctl 0x00010be2 bmdma 0x0001e400 irq 18
[    5.096000] ata4: SATA max UDMA/133 cmd 0x00010960 ctl 0x00010b62 bmdma 0x0001e408 irq 18
[    5.116000] usb 1-9: new full speed USB device using ohci_hcd and address 3
[    5.328000] usb 1-9: configuration #1 chosen from 1 choice
[    5.332000] usbcore: registered new interface driver hiddev
[    5.336000] input: DELL DELL USB Keyboard as /class/input/input1
[    5.336000] input: USB HID v1.10 Keyboard [DELL DELL USB Keyboard] on usb-0000:00:02.0-4
[    5.336000] usbcore: registered new interface driver usbhid
[    5.336000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[    5.344000] usbcore: registered new interface driver libusual
[    5.352000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    5.352000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    5.356000] Initializing USB Mass Storage driver...
[    5.356000] scsi4 : SCSI emulation for USB Mass Storage devices
[    5.356000] usb-storage: device found at 3
[    5.356000] usb-storage: waiting for device to settle before scanning
[    5.356000] usbcore: registered new interface driver usb-storage
[    5.356000] USB Mass Storage support registered.
[    5.408000] ata3: SATA link down (SStatus 0 SControl 300)
[    5.728000] ata4: SATA link down (SStatus 0 SControl 300)
[    5.736000] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 20
[    5.736000] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [APCL] -> GSI 20 (level, low) -> IRQ 19
[    5.736000] PCI: Setting latency timer of device 0000:00:02.1 to 64
[    5.736000] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    5.736000] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
[    5.736000] ehci_hcd 0000:00:02.1: debug port 1
[    5.736000] PCI: cache line size of 64 is not supported by device 0000:00:02.1
[    5.736000] ehci_hcd 0000:00:02.1: irq 19, io mem 0xf5106000
[    5.736000] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    5.736000] usb 1-4: USB disconnect, address 2
[    5.736000] usb usb2: configuration #1 chosen from 1 choice
[    5.736000] hub 2-0:1.0: USB hub found
[    5.736000] hub 2-0:1.0: 10 ports detected
[    5.840000] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 23
[    5.840000] ACPI: PCI Interrupt 0000:00:07.0[A] -> Link [APCH] -> GSI 23 (level, low) -> IRQ 16
[    5.840000] PCI: Setting latency timer of device 0000:00:07.0 to 64
[    5.840000] forcedeth: using HIGHDMA
[    5.872000] usb 1-9: USB disconnect, address 3
[    6.360000] eth0: forcedeth.c: subsystem: 01458:e000 bound to 0000:00:07.0
[    6.360000] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[    6.360000] ACPI: PCI Interrupt 0000:01:0e.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 20
[    6.412000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[20]  MMIO=[f5004000-f50047ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    6.412000] NFORCE-MCP61: IDE controller at PCI slot 0000:00:06.0
[    6.412000] NFORCE-MCP61: chipset revision 162
[    6.412000] NFORCE-MCP61: not 100% native mode: will probe irqs later
[    6.412000] NFORCE-MCP61: BIOS didn't set cable bits correctly. Enabling workaround.
[    6.412000] NFORCE-MCP61: 0000:00:06.0 (rev a2) UDMA133 controller
[    6.412000]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:DMA
[    6.412000] Probing IDE interface ide0...
[    6.420000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[    6.420000] sd 0:0:0:0: [sda] Write Protect is off
[    6.420000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.420000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.420000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[    6.420000] sd 0:0:0:0: [sda] Write Protect is off
[    6.420000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.420000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.420000]  sda:<6>usb 2-9: new high speed USB device using ehci_hcd and address 3
[    6.444000]  sda1 sda2 < sda5 >
[    6.464000] sd 0:0:0:0: [sda] Attached SCSI disk
[    6.468000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    6.556000] usb 2-9: configuration #1 chosen from 1 choice
[    6.556000] scsi5 : SCSI emulation for USB Mass Storage devices
[    6.556000] usb-storage: device found at 3
[    6.556000] usb-storage: waiting for device to settle before scanning
[    6.780000] Attempting manual resume
[    6.780000] swsusp: Resume From Partition 8:5
[    6.780000] PM: Checking swsusp image.
[    6.780000] PM: Resume from disk failed.
[    6.796000] ReiserFS: sda1: found reiserfs format "3.6" with standard journal
[    6.796000] ReiserFS: sda1: using ordered data mode
[    6.804000] ReiserFS: sda1: journal params: device sda1, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[    6.804000] ReiserFS: sda1: checking transaction log (sda1)
[    6.844000] ReiserFS: sda1: Using r5 hash to sort names
[    6.864000] usb 1-4: new low speed USB device using ohci_hcd and address 4
[    7.064000] usb 1-4: configuration #1 chosen from 1 choice
[    7.076000] input: DELL DELL USB Keyboard as /class/input/input2
[    7.076000] input: USB HID v1.10 Keyboard [DELL DELL USB Keyboard] on usb-0000:00:02.0-4
[    7.148000] hda: LITE-ON DVDRW LH-20A1H, ATAPI CD/DVD-ROM drive
[    7.684000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001a4d0000eb7d4c]
[    7.820000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   11.556000] usb-storage: device scan complete
[   11.560000] scsi 5:0:0:0: Direct-Access     USB2.0   CardReader CF    0100 PQ: 0 ANSI: 0
[   11.564000] scsi 5:0:0:1: Direct-Access     USB2.0   CardReader SM XD 0100 PQ: 0 ANSI: 0
[   11.568000] scsi 5:0:0:2: Direct-Access     USB2.0   CardReader MS    0100 PQ: 0 ANSI: 0
[   11.568000] scsi 5:0:0:3: Direct-Access     USB2.0   CardReader SD    0100 PQ: 0 ANSI: 0
[   11.568000] sd 5:0:0:0: [sdb] Attached SCSI removable disk
[   11.568000] sd 5:0:0:0: Attached scsi generic sg1 type 0
[   11.572000] sd 5:0:0:1: [sdc] Attached SCSI removable disk
[   11.572000] sd 5:0:0:1: Attached scsi generic sg2 type 0
[   11.572000] sd 5:0:0:2: [sdd] Attached SCSI removable disk
[   11.572000] sd 5:0:0:2: Attached scsi generic sg3 type 0
[   11.572000] sd 5:0:0:3: [sde] Attached SCSI removable disk
[   11.572000] sd 5:0:0:3: Attached scsi generic sg4 type 0
[   13.284000] NET: Registered protocol family 10
[   13.284000] lo: Disabled Privacy Extensions
[   13.872000] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x1c00
[   13.872000] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x1c40
[   14.080000] input: PC Speaker as /class/input/input3
[   14.328000] Linux agpgart interface v0.102 (c) Dave Jones
[   14.432000] nvidia: module license 'NVIDIA' taints kernel.
[   14.692000] hda: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(66)
[   14.692000] Uniform CD-ROM driver Revision: 3.20
[   14.744000] ACPI: PCI Interrupt Link [AIGP] enabled at IRQ 22
[   14.744000] ACPI: PCI Interrupt 0000:00:0d.0[A] -> Link [AIGP] -> GSI 22 (level, low) -> IRQ 17
[   14.744000] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   14.744000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9639  Mon Apr 16 20:20:06 PDT 2007
[   15.016000] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 21
[   15.016000] ACPI: PCI Interrupt 0000:00:05.0[B] -> Link [AAZA] -> GSI 21 (level, low) -> IRQ 18
[   15.016000] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   15.192000] input: ImPS/2 Logitech Wheel Mouse as /class/input/input4
[   15.196000] parport_pc 00:09: reported by Plug and Play ACPI
[   15.196000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   15.516000] lp0: using parport0 (interrupt-driven).
[   15.720000] Adding 3229024k swap on /dev/sda5.  Priority:-1 extents:1 across:3229024k
[   23.832000] eth0: no IPv6 routers present
[   27.964000] No dock devices found.
[   28.044000] input: Power Button (FF) as /class/input/input5
[   28.044000] ACPI: Power Button (FF) [PWRF]
[   28.044000] input: Power Button (CM) as /class/input/input6
[   28.044000] ACPI: Power Button (CM) [PWRB]
[   28.500000] powernow-k8: Found 2 AMD Athlon(tm) 64 X2 Dual Core Processor 4000+ processors (version 2.00.00)
[   28.500000] powernow-k8:    0 : fid 0xd (2100 MHz), vid 0xa
[   28.500000] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0xb
[   28.500000] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0xd
[   28.500000] powernow-k8:    3 : fid 0x2 (1000 MHz), vid 0x12
[   33.124000] ppdev: user-space parallel port driver
[   33.356000] audit(1193343338.730:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5526 profile="/usr/sbin/cupsd"
[   36.352000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   36.352000] apm: disabled - APM is not SMP safe.
[   37.504000] Clocksource tsc unstable (delta = -72023337 ns)
[   37.864000] Failure registering capabilities with primary security module.
[   38.168000] Bluetooth: Core ver 2.11
[   38.168000] NET: Registered protocol family 31
[   38.168000] Bluetooth: HCI device and connection manager initialized
[   38.168000] Bluetooth: HCI socket layer initialized
[   38.244000] Bluetooth: L2CAP ver 2.8
[   38.244000] Bluetooth: L2CAP socket layer initialized
[   38.252000] Bluetooth: RFCOMM socket layer initialized
[   38.252000] Bluetooth: RFCOMM TTY layer initialized
[   38.252000] Bluetooth: RFCOMM ver 1.8
[ 2639.452000] cdrom: This disc doesn't have any tracks I recognize!
[80460.936000] usb 2-9: USB disconnect, address 3
[80461.240000] usb 2-9: new high speed USB device using ehci_hcd and address 4
[80461.372000] usb 2-9: configuration #1 chosen from 1 choice
[80461.372000] scsi6 : SCSI emulation for USB Mass Storage devices
[80461.372000] usb-storage: device found at 4
[80461.372000] usb-storage: waiting for device to settle before scanning
[80466.372000] usb-storage: device scan complete
[80466.372000] scsi 6:0:0:0: Direct-Access     USB2.0   CardReader CF    0100 PQ: 0 ANSI: 0
[80466.372000] scsi 6:0:0:1: Direct-Access     USB2.0   CardReader SM XD 0100 PQ: 0 ANSI: 0
[80466.372000] scsi 6:0:0:2: Direct-Access     USB2.0   CardReader MS    0100 PQ: 0 ANSI: 0
[80466.372000] scsi 6:0:0:3: Direct-Access     USB2.0   CardReader SD    0100 PQ: 0 ANSI: 0
[80467.176000] sd 6:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[80467.180000] sd 6:0:0:0: [sdb] Write Protect is off
[80467.180000] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
[80467.180000] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[80467.180000] sd 6:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[80467.180000] sd 6:0:0:0: [sdb] Write Protect is off
[80467.180000] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
[80467.180000] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[80467.180000]  sdb: sdb1
[80467.204000] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[80467.204000] sd 6:0:0:0: Attached scsi generic sg1 type 0
[80467.212000] sd 6:0:0:1: [sdc] Attached SCSI removable disk
[80467.212000] sd 6:0:0:1: Attached scsi generic sg2 type 0
[80467.212000] sd 6:0:0:2: [sdd] Attached SCSI removable disk
[80467.212000] sd 6:0:0:2: Attached scsi generic sg3 type 0
[80467.220000] sd 6:0:0:3: [sde] Attached SCSI removable disk
[80467.220000] sd 6:0:0:3: Attached scsi generic sg4 type 0
[83678.648000] sd 6:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[83678.648000] sd 6:0:0:0: [sdb] Write Protect is off
[83678.648000] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
[83678.648000] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[83678.648000] sd 6:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[83678.648000] sd 6:0:0:0: [sdb] Write Protect is off
[83678.648000] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
[83678.648000] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[83678.648000]  sdb: sdb1
[83863.880000] Buffer I/O error on device sdb1, logical block 491
[83863.880000] lost page write due to I/O error on sdb1
[83934.660000] sd 6:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[83934.660000] sd 6:0:0:0: [sdb] Write Protect is off
[83934.660000] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
[83934.660000] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[83934.664000] sd 6:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[83934.668000] sd 6:0:0:0: [sdb] Write Protect is off
[83934.668000] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
[83934.668000] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[83934.668000]  sdb: sdb1
[85261.772000] ppdev0: registered pardevice
[85261.820000] ppdev0: unregistered pardevice
[85263.116000] audit(1193428568.538:4):  type=1503 operation="sysctl" requested_mask="r" denied_mask="r" name="/proc/sys/dev/parport/parport0/autoprobe" pid=19901 profile="/usr/sbin/cupsd"
[85263.136000] audit(1193428568.538:5):  type=1503 operation="sysctl" requested_mask="r" denied_mask="r" name="/proc/sys/dev/parport/parport0/autoprobe" pid=19902 profile="/usr/sbin/cupsd"
[85263.912000] ppdev0: registered pardevice
[85263.960000] ppdev0: unregistered pardevice
[85451.884000] audit(1193428757.036:6):  type=1503 operation="inode_permission" requested_mask="rw" denied_mask="rw" name="/dev/tty" pid=19964 profile="/usr/sbin/cupsd"
[85451.948000] audit(1193428757.536:7):  type=1503 operation="inode_permission" requested_mask="rw" denied_mask="rw" name="/dev/tty" pid=19967 profile="/usr/sbin/cupsd"
[87280.772000] sd 6:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[87280.772000] sd 6:0:0:0: [sdb] Write Protect is off
[87280.772000] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
[87280.772000] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[87280.772000] sd 6:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[87280.776000] sd 6:0:0:0: [sdb] Write Protect is off
[87280.776000] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
[87280.776000] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[87280.776000]  sdb: sdb1
[88012.820000] sd 6:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[88012.820000] sd 6:0:0:0: [sdb] Write Protect is off
[88012.820000] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
[88012.820000] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[88012.824000] sd 6:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[88012.824000] sd 6:0:0:0: [sdb] Write Protect is off
[88012.824000] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
[88012.824000] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[88012.824000]  sdb: sdb1
[88876.400000] audit(1193432182.009:8):  type=1503 operation="inode_permission" requested_mask="rw" denied_mask="rw" name="/dev/tty" pid=20301 profile="/usr/sbin/cupsd"
[88876.464000] audit(1193432182.009:9):  type=1503 operation="inode_permission" requested_mask="rw" denied_mask="rw" name="/dev/tty" pid=20304 profile="/usr/sbin/cupsd"
[90140.616000] cdrom: This disc doesn't have any tracks I recognize!
[347733.192000] sd 6:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[347733.192000] sd 6:0:0:0: [sdb] Write Protect is off
[347733.192000] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
[347733.192000] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[347733.192000] sd 6:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[347733.192000] sd 6:0:0:0: [sdb] Write Protect is off
[347733.192000] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
[347733.192000] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[347733.192000]  sdb: sdb1
[511054.088000] sd 6:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[511054.088000] sd 6:0:0:0: [sdb] Write Protect is off
[511054.088000] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
[511054.088000] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[511054.092000] sd 6:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[511054.092000] sd 6:0:0:0: [sdb] Write Protect is off
[511054.092000] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
[511054.092000] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[511054.092000]  sdb: sdb1
[597700.356000] sd 6:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[597700.356000] sd 6:0:0:0: [sdb] Write Protect is off
[597700.356000] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
[597700.356000] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[597700.360000] sd 6:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[597700.360000] sd 6:0:0:0: [sdb] Write Protect is off
[597700.360000] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
[597700.360000] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[597700.360000]  sdb: sdb1
[600739.972000] usb 2-9: USB disconnect, address 4
[600740.264000] usb 2-9: new high speed USB device using ehci_hcd and address 5
[600740.396000] usb 2-9: configuration #1 chosen from 1 choice
[600740.396000] scsi7 : SCSI emulation for USB Mass Storage devices
[600740.396000] usb-storage: device found at 5
[600740.396000] usb-storage: waiting for device to settle before scanning
[600745.396000] usb-storage: device scan complete
[600745.396000] scsi 7:0:0:0: Direct-Access     USB2.0   CardReader CF    0100 PQ: 0 ANSI: 0
[600745.396000] scsi 7:0:0:1: Direct-Access     USB2.0   CardReader SM XD 0100 PQ: 0 ANSI: 0
[600745.396000] scsi 7:0:0:2: Direct-Access     USB2.0   CardReader MS    0100 PQ: 0 ANSI: 0
[600745.396000] scsi 7:0:0:3: Direct-Access     USB2.0   CardReader SD    0100 PQ: 0 ANSI: 0
[600746.200000] sd 7:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[600746.204000] sd 7:0:0:0: [sdb] Write Protect is off
[600746.204000] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[600746.204000] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[600746.204000] sd 7:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[600746.204000] sd 7:0:0:0: [sdb] Write Protect is off
[600746.204000] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[600746.204000] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[600746.204000]  sdb: sdb1
[600746.228000] sd 7:0:0:0: [sdb] Attached SCSI removable disk
[600746.228000] sd 7:0:0:0: Attached scsi generic sg1 type 0
[600746.232000] sd 7:0:0:1: [sdc] Attached SCSI removable disk
[600746.232000] sd 7:0:0:1: Attached scsi generic sg2 type 0
[600746.232000] sd 7:0:0:2: [sdd] Attached SCSI removable disk
[600746.232000] sd 7:0:0:2: Attached scsi generic sg3 type 0
[600746.236000] sd 7:0:0:3: [sde] Attached SCSI removable disk
[600746.236000] sd 7:0:0:3: Attached scsi generic sg4 type 0
[600789.160000] Buffer I/O error on device sdb1, logical block 491
[600789.160000] lost page write due to I/O error on sdb1
[600789.160000] Buffer I/O error on device sdb1, logical block 523
[600789.160000] lost page write due to I/O error on sdb1
[600789.164000] Buffer I/O error on device sdb1, logical block 74315
[600789.164000] lost page write due to I/O error on sdb1
[600851.936000] sd 7:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[600851.936000] sd 7:0:0:0: [sdb] Write Protect is off
[600851.936000] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[600851.936000] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[600851.940000] sd 7:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[600851.940000] sd 7:0:0:0: [sdb] Write Protect is off
[600851.940000] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[600851.940000] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[600851.940000]  sdb: sdb1
[602686.036000] sd 7:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[602686.036000] sd 7:0:0:0: [sdb] Write Protect is off
[602686.036000] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[602686.036000] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[602686.040000] sd 7:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[602686.044000] sd 7:0:0:0: [sdb] Write Protect is off
[602686.044000] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[602686.044000] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[602686.044000]  sdb: sdb1
[603992.112000] sd 7:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[603992.112000] sd 7:0:0:0: [sdb] Write Protect is off
[603992.112000] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[603992.112000] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[603992.120000] sd 7:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[603992.120000] sd 7:0:0:0: [sdb] Write Protect is off
[603992.120000] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[603992.120000] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[603992.120000]  sdb: sdb1
[605144.136000] sd 7:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[605144.136000] sd 7:0:0:0: [sdb] Write Protect is off
[605144.136000] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[605144.136000] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[605144.140000] sd 7:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[605144.144000] sd 7:0:0:0: [sdb] Write Protect is off
[605144.144000] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[605144.144000] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[605144.144000]  sdb: sdb1
[606024.204000] sd 7:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[606024.204000] sd 7:0:0:0: [sdb] Write Protect is off
[606024.204000] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[606024.204000] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[606024.208000] sd 7:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[606024.208000] sd 7:0:0:0: [sdb] Write Protect is off
[606024.208000] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[606024.208000] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[606024.208000]  sdb: sdb1
[606266.208000] sd 7:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[606266.208000] sd 7:0:0:0: [sdb] Write Protect is off
[606266.208000] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[606266.208000] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[606266.212000] sd 7:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[606266.216000] sd 7:0:0:0: [sdb] Write Protect is off
[606266.216000] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[606266.216000] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[606266.216000]  sdb: sdb1
[607782.088000] cdrom: This disc doesn't have any tracks I recognize!
[683918.280000] ppdev0: registered pardevice
[683918.280000] ppdev0: unregistered pardevice
[683919.040000] ppdev0: registered pardevice
[683919.088000] ppdev0: unregistered pardevice
[945748.952000] sd 7:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[945748.956000] sd 7:0:0:0: [sdb] Write Protect is off
[945748.956000] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[945748.956000] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[945748.960000] sd 7:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[945748.964000] sd 7:0:0:0: [sdb] Write Protect is off
[945748.964000] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[945748.964000] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[945748.964000]  sdb: sdb1
[946756.980000] audit(1194290049.536:10):  type=1503 operation="inode_permission" requested_mask="rw" denied_mask="rw" name="/dev/tty" pid=3375 profile="/usr/sbin/cupsd"
[946757.020000] audit(1194290049.536:11):  type=1503 operation="inode_permission" requested_mask="rw" denied_mask="rw" name="/dev/tty" pid=3378 profile="/usr/sbin/cupsd"
[955881.092000] sd 7:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[955881.092000] sd 7:0:0:0: [sdb] Write Protect is off
[955881.092000] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[955881.092000] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[955881.092000] sd 7:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[955881.092000] sd 7:0:0:0: [sdb] Write Protect is off
[955881.092000] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[955881.092000] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[955881.092000]  sdb: sdb1
[1032453.772000] audit(1194375746.030:12):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4836 profile="/usr/sbin/cupsd"
[1033875.728000] audit(1194377168.441:13):  type=1503 operation="inode_permission" requested_mask="rw" denied_mask="rw" name="/dev/tty" pid=4990 profile="/usr/sbin/cupsd"
[1033875.824000] audit(1194377168.441:14):  type=1503 operation="inode_permission" requested_mask="rw" denied_mask="rw" name="/dev/tty" pid=4993 profile="/usr/sbin/cupsd"
[1036239.620000] sd 7:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[1036239.624000] sd 7:0:0:0: [sdb] Write Protect is off
[1036239.624000] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[1036239.624000] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[1036239.624000] sd 7:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[1036239.624000] sd 7:0:0:0: [sdb] Write Protect is off
[1036239.624000] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[1036239.624000] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[1036239.624000]  sdb: sdb1
[1036398.860000] Buffer I/O error on device sdb1, logical block 523
[1036398.860000] lost page write due to I/O error on sdb1
[1036398.860000] Buffer I/O error on device sdb1, logical block 74315
[1036398.860000] lost page write due to I/O error on sdb1
[1036398.860000] Buffer I/O error on device sdb1, logical block 1
[1036398.860000] lost page write due to I/O error on sdb1
[1036398.860000] Buffer I/O error on device sdb1, logical block 2
[1036398.860000] lost page write due to I/O error on sdb1
[1036398.860000] Buffer I/O error on device sdb1, logical block 3
[1036398.860000] lost page write due to I/O error on sdb1
[1036398.860000] Buffer I/O error on device sdb1, logical block 4
[1036398.860000] lost page write due to I/O error on sdb1
[1036398.860000] Buffer I/O error on device sdb1, logical block 5
[1036398.860000] lost page write due to I/O error on sdb1
[1036398.860000] Buffer I/O error on device sdb1, logical block 6
[1036398.860000] lost page write due to I/O error on sdb1
[1036398.860000] Buffer I/O error on device sdb1, logical block 7
[1036398.860000] lost page write due to I/O error on sdb1
[1036398.860000] Buffer I/O error on device sdb1, logical block 8
[1036398.860000] lost page write due to I/O error on sdb1
[1036471.640000] sd 7:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[1036471.640000] sd 7:0:0:0: [sdb] Write Protect is off
[1036471.640000] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[1036471.640000] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[1036471.644000] sd 7:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[1036471.644000] sd 7:0:0:0: [sdb] Write Protect is off
[1036471.644000] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[1036471.644000] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[1036471.644000]  sdb: sdb1
[1041703.920000] sd 7:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[1041703.924000] sd 7:0:0:0: [sdb] Write Protect is off
[1041703.924000] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[1041703.924000] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[1041703.924000] sd 7:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[1041703.924000] sd 7:0:0:0: [sdb] Write Protect is off
[1041703.924000] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[1041703.924000] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[1041703.924000]  sdb: sdb1
[1042985.036000] cdrom: This disc doesn't have any tracks I recognize!
[1117882.188000] sd 7:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[1117882.188000] sd 7:0:0:0: [sdb] Write Protect is off
[1117882.188000] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[1117882.188000] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[1117882.192000] sd 7:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[1117882.192000] sd 7:0:0:0: [sdb] Write Protect is off
[1117882.192000] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[1117882.192000] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[1117882.192000]  sdb: sdb1
[1206655.048000] sd 7:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[1206655.048000] sd 7:0:0:0: [sdb] Write Protect is off
[1206655.048000] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[1206655.048000] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[1206655.056000] sd 7:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[1206655.056000] sd 7:0:0:0: [sdb] Write Protect is off
[1206655.056000] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[1206655.056000] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[1206655.056000]  sdb: sdb1
[1212782.552000] ppdev0: registered pardevice
[1212782.552000] ppdev0: unregistered pardevice
[1212783.304000] ppdev0: registered pardevice
[1212783.352000] ppdev0: unregistered pardevice
[1216134.172000] cdrom: This disc doesn't have any tracks I recognize!
[1289003.628000] audit(1194632295.938:15):  type=1503 operation="inode_permission" requested_mask="rw" denied_mask="rw" name="/dev/tty" pid=17123 profile="/usr/sbin/cupsd"
[1289003.668000] audit(1194632295.938:16):  type=1503 operation="inode_permission" requested_mask="rw" denied_mask="rw" name="/dev/tty" pid=17126 profile="/usr/sbin/cupsd"
[1290262.408000] audit(1194633554.858:17):  type=1503 operation="inode_permission" requested_mask="rw" denied_mask="rw" name="/dev/tty" pid=17173 profile="/usr/sbin/cupsd"
[1290262.448000] audit(1194633554.858:18):  type=1503 operation="inode_permission" requested_mask="rw" denied_mask="rw" name="/dev/tty" pid=17176 profile="/usr/sbin/cupsd"
[1646755.032000] sd 7:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[1646755.036000] sd 7:0:0:0: [sdb] Write Protect is off
[1646755.036000] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[1646755.036000] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[1646755.040000] sd 7:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[1646755.044000] sd 7:0:0:0: [sdb] Write Protect is off
[1646755.044000] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[1646755.044000] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[1646755.044000]  sdb: sdb1
[1648837.064000] sd 7:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[1648837.068000] sd 7:0:0:0: [sdb] Write Protect is off
[1648837.068000] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[1648837.068000] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[1648837.072000] sd 7:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[1648837.072000] sd 7:0:0:0: [sdb] Write Protect is off
[1648837.072000] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[1648837.072000] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[1648837.072000]  sdb: sdb1
[1731336.204000] audit(1195074628.720:19):  type=1503 operation="inode_permission" requested_mask="rw" denied_mask="rw" name="/dev/tty" pid=23153 profile="/usr/sbin/cupsd"
[1731336.244000] audit(1195074628.720:20):  type=1503 operation="inode_permission" requested_mask="rw" denied_mask="rw" name="/dev/tty" pid=23156 profile="/usr/sbin/cupsd"
[1735074.836000] cdrom: This disc doesn't have any tracks I recognize!
[1810178.076000] eth0: link down.
[1810186.068000] eth0: link up.
[1813250.124000] usb 2-8: new high speed USB device using ehci_hcd and address 6
[1813250.256000] usb 2-8: configuration #1 chosen from 1 choice
[1813250.256000] scsi8 : SCSI emulation for USB Mass Storage devices
[1813250.256000] usb-storage: device found at 6
[1813250.256000] usb-storage: waiting for device to settle before scanning
[1813255.256000] usb-storage: device scan complete
[1813255.256000] scsi 8:0:0:0: Direct-Access     WDC WD80      WD-WCAM9T89 10.0 PQ: 0 ANSI: 2 CCS
[1813255.260000] sd 8:0:0:0: [sdf] 156301488 512-byte hardware sectors (80026 MB)
[1813255.260000] sd 8:0:0:0: [sdf] Write Protect is off
[1813255.260000] sd 8:0:0:0: [sdf] Mode Sense: 00 38 00 00
[1813255.260000] sd 8:0:0:0: [sdf] Assuming drive cache: write through
[1813255.268000] sd 8:0:0:0: [sdf] 156301488 512-byte hardware sectors (80026 MB)
[1813255.268000] sd 8:0:0:0: [sdf] Write Protect is off
[1813255.268000] sd 8:0:0:0: [sdf] Mode Sense: 00 38 00 00
[1813255.268000] sd 8:0:0:0: [sdf] Assuming drive cache: write through
[1813255.268000]  sdf: unknown partition table
[1813255.276000] sd 8:0:0:0: [sdf] Attached SCSI disk
[1813255.276000] sd 8:0:0:0: Attached scsi generic sg5 type 0
[1813317.940000] usb 2-8: USB disconnect, address 6
[1813505.252000] usb 2-7: new high speed USB device using ehci_hcd and address 7
[1813505.384000] usb 2-7: configuration #1 chosen from 1 choice
[1813505.384000] scsi9 : SCSI emulation for USB Mass Storage devices
[1813505.384000] usb-storage: device found at 7
[1813505.384000] usb-storage: waiting for device to settle before scanning
[1813510.384000] usb-storage: device scan complete
[1813510.384000] scsi 9:0:0:0: Direct-Access     WDC WD80      WD-WCAM9T89 10.0 PQ: 0 ANSI: 2 CCS
[1813510.388000] sd 9:0:0:0: [sdf] 156301488 512-byte hardware sectors (80026 MB)
[1813510.388000] sd 9:0:0:0: [sdf] Write Protect is off
[1813510.388000] sd 9:0:0:0: [sdf] Mode Sense: 00 38 00 00
[1813510.388000] sd 9:0:0:0: [sdf] Assuming drive cache: write through
[1813510.388000] sd 9:0:0:0: [sdf] 156301488 512-byte hardware sectors (80026 MB)
[1813510.388000] sd 9:0:0:0: [sdf] Write Protect is off
[1813510.388000] sd 9:0:0:0: [sdf] Mode Sense: 00 38 00 00
[1813510.388000] sd 9:0:0:0: [sdf] Assuming drive cache: write through
[1813510.388000]  sdf: unknown partition table
[1813510.400000] sd 9:0:0:0: [sdf] Attached SCSI disk
[1813510.400000] sd 9:0:0:0: Attached scsi generic sg5 type 0
[1813742.580000] usb 2-7: USB disconnect, address 7
[1817206.944000] usb 2-7: new high speed USB device using ehci_hcd and address 8
[1817207.076000] usb 2-7: configuration #1 chosen from 1 choice
[1817207.076000] scsi10 : SCSI emulation for USB Mass Storage devices
[1817207.076000] usb-storage: device found at 8
[1817207.076000] usb-storage: waiting for device to settle before scanning
[1817212.076000] usb-storage: device scan complete
[1817212.076000] scsi 10:0:0:0: Direct-Access     WDC WD80      WD-WCAM9T89 10.0 PQ: 0 ANSI: 2 CCS
[1817212.076000] sd 10:0:0:0: [sdf] 156301488 512-byte hardware sectors (80026 MB)
[1817212.076000] sd 10:0:0:0: [sdf] Write Protect is off
[1817212.076000] sd 10:0:0:0: [sdf] Mode Sense: 00 38 00 00
[1817212.076000] sd 10:0:0:0: [sdf] Assuming drive cache: write through
[1817212.080000] sd 10:0:0:0: [sdf] 156301488 512-byte hardware sectors (80026 MB)
[1817212.080000] sd 10:0:0:0: [sdf] Write Protect is off
[1817212.080000] sd 10:0:0:0: [sdf] Mode Sense: 00 38 00 00
[1817212.080000] sd 10:0:0:0: [sdf] Assuming drive cache: write through
[1817212.080000]  sdf: sdf1
[1817212.088000] sd 10:0:0:0: [sdf] Attached SCSI disk
[1817212.088000] sd 10:0:0:0: Attached scsi generic sg5 type 0
[1819189.936000] usb 2-7: USB disconnect, address 8
[1893170.064000] sd 7:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[1893170.064000] sd 7:0:0:0: [sdb] Write Protect is off
[1893170.064000] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[1893170.064000] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[1893170.068000] sd 7:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[1893170.072000] sd 7:0:0:0: [sdb] Write Protect is off
[1893170.072000] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[1893170.072000] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[1893170.072000]  sdb: sdb1
[1893608.068000] sd 7:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[1893608.068000] sd 7:0:0:0: [sdb] Write Protect is off
[1893608.068000] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[1893608.068000] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[1893608.068000] sd 7:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[1893608.072000] sd 7:0:0:0: [sdb] Write Protect is off
[1893608.072000] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[1893608.072000] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[1893608.072000]  sdb: sdb1
[1894617.024000] usb 2-7: new high speed USB device using ehci_hcd and address 9
[1894617.156000] usb 2-7: configuration #1 chosen from 1 choice
[1894617.156000] scsi11 : SCSI emulation for USB Mass Storage devices
[1894617.156000] usb-storage: device found at 9
[1894617.156000] usb-storage: waiting for device to settle before scanning
[1894622.156000] usb-storage: device scan complete
[1894622.156000] scsi 11:0:0:0: Direct-Access     WDC WD80      WD-WCAM9T89 10.0 PQ: 0 ANSI: 2 CCS
[1894622.160000] sd 11:0:0:0: [sdf] 156301488 512-byte hardware sectors (80026 MB)
[1894622.164000] sd 11:0:0:0: [sdf] Write Protect is off
[1894622.164000] sd 11:0:0:0: [sdf] Mode Sense: 00 38 00 00
[1894622.164000] sd 11:0:0:0: [sdf] Assuming drive cache: write through
[1894622.164000] sd 11:0:0:0: [sdf] 156301488 512-byte hardware sectors (80026 MB)
[1894622.168000] sd 11:0:0:0: [sdf] Write Protect is off
[1894622.168000] sd 11:0:0:0: [sdf] Mode Sense: 00 38 00 00
[1894622.168000] sd 11:0:0:0: [sdf] Assuming drive cache: write through
[1894622.168000]  sdf: sdf1
[1894622.168000] sd 11:0:0:0: [sdf] Attached SCSI disk
[1894622.168000] sd 11:0:0:0: Attached scsi generic sg5 type 0
[1895220.776000] audit(1195238513.172:21):  type=1503 operation="inode_permission" requested_mask="rw" denied_mask="rw" name="/dev/tty" pid=27169 profile="/usr/sbin/cupsd"
[1895220.816000] audit(1195238513.172:22):  type=1503 operation="inode_permission" requested_mask="rw" denied_mask="rw" name="/dev/tty" pid=27172 profile="/usr/sbin/cupsd"
[1896927.124000] usb 2-7: USB disconnect, address 9
```





and here's dmesg with a formatted drive attached...

```
[    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007bff0000 (usable)
[    0.000000]  BIOS-e820: 000000007bff0000 - 000000007bff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007bff3000 - 000000007c000000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007c000000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f2000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] 1087MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f4ae0
[    0.000000] Entering add_active_range(0, 0, 507888) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   507888
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   507888
[    0.000000] On node 0 totalpages: 507888
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2175 pages used for memmap
[    0.000000]   HighMem zone: 276337 pages, LIFO batch:31
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F64A0 checksum 0
[    0.000000] ACPI: RSDP 000F64A0, 0014 (r0 GBT   )
[    0.000000] ACPI: RSDT 7BFF3000, 0038 (r1 GBT    NVDAACPI 42302E31 NVDA  1010101)
[    0.000000] ACPI: FACP 7BFF3040, 0074 (r1 GBT    NVDAACPI 42302E31 NVDA  1010101)
[    0.000000] ACPI: DSDT 7BFF30C0, 46EB (r1 GBT    NVDAACPI     1000 MSFT  100000C)
[    0.000000] ACPI: FACS 7BFF0000, 0040
[    0.000000] ACPI: SSDT 7BFF7840, 0206 (r1 PTLTD  POWERNOW        1  LTP        1)
[    0.000000] ACPI: HPET 7BFF7A80, 0038 (r1 GBT    NVDAACPI 42302E31 NVDA       98)
[    0.000000] ACPI: MCFG 7BFF7AC0, 003C (r1 GBT    NVDAACPI 42302E31 NVDA  1010101)
[    0.000000] ACPI: APIC 7BFF77C0, 007C (r1 GBT    NVDAACPI 42302E31 NVDA  1010101)
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:11 APIC version 16
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:11 APIC version 16
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfeff0000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:70000000)
[    0.000000] Built 1 zonelists.  Total pages: 503921
[    0.000000] Kernel command line: root=UUID=00d7022a-0a42-4ce5-aba2-9514f1deac11 ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2109.592 MHz processor.
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Memory: 2002624k/2031552k available (2015k kernel code, 27708k reserved, 916k data, 364k init, 1114048k highmem)
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
[    0.000000] hpet0: at MMIO 0xfeff0000, IRQs 2, 8, 31
[    0.000000] hpet0: 3 32-bit timers, 25000000 Hz
[    0.080000] Calibrating delay using timer specific routine.. 4223.30 BogoMIPS (lpj=8446609)
[    0.080000] Security Framework v1.0.0 initialized
[    0.080000] SELinux:  Disabled at boot.
[    0.080000] Mount-cache hash table entries: 512
[    0.080000] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000011f
[    0.080000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.080000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.080000] CPU 0(2) -> Core 0
[    0.080000] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000410 00002001 00000000 0000011f
[    0.080000] Compat vDSO mapped to ffffe000.
[    0.080000] Checking 'hlt' instruction... OK.
[    0.096000] SMP alternatives: switching to UP code
[    0.096000] Early unpacking initramfs... done
[    0.380000] ACPI: Core revision 20070126
[    0.380000] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[    0.384000] CPU0: AMD Athlon(tm) 64 X2 Dual Core Processor 4000+ stepping 01
[    0.384000] SMP alternatives: switching to SMP code
[    0.384000] Booting processor 1/1 eip 3000
[    0.396000] Initializing CPU#1
[    0.476000] Calibrating delay using timer specific routine.. 4219.20 BogoMIPS (lpj=8438412)
[    0.476000] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000011f
[    0.476000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.476000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.476000] CPU 1(2) -> Core 1
[    0.476000] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000410 00002001 00000000 0000011f
[    0.476000] CPU1: AMD Athlon(tm) 64 X2 Dual Core Processor 4000+ stepping 01
[    0.476000] Total of 2 processors activated (8442.51 BogoMIPS).
[    0.476000] ENABLING IO-APIC IRQs
[    0.476000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.516000] Brought up 2 CPUs
[    0.528000] migration_cost=4000
[    0.528000] Booting paravirtualized kernel on bare hardware
[    0.528000] Time: 16:15:06  Date: 09/25/107
[    0.528000] NET: Registered protocol family 16
[    0.528000] EISA bus registered
[    0.528000] ACPI: bus type pci registered
[    0.536000] PCI: PCI BIOS revision 3.00 entry at 0xfb300, last bus=1
[    0.536000] PCI: Using configuration type 1
[    0.536000] Setting up standard PCI resources
[    0.540000] ACPI: EC: Look up EC in DSDT
[    0.544000] ACPI: Interpreter enabled
[    0.544000] ACPI: (supports S0 S1 S4 S5)
[    0.544000] ACPI: Using IOAPIC for interrupt routing
[    0.552000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.552000] PCI: Probing PCI hardware (bus 00)
[    0.552000] PCI: Transparent bridge - 0000:00:04.0
[    0.552000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.552000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.580000] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.580000] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.580000] ACPI: PCI Interrupt Link [LNK3] (IRQs *5 7 9 10 11 14 15)
[    0.580000] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.580000] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.580000] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.580000] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.580000] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.580000] ACPI: PCI Interrupt Link [LIGP] (IRQs 5 7 9 10 *11 14 15)
[    0.580000] ACPI: PCI Interrupt Link [LP2P] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.580000] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 *10 11 14 15)
[    0.580000] ACPI: PCI Interrupt Link [LMAC] (IRQs *5 7 9 10 11 14 15)
[    0.580000] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 *10 11 14 15)
[    0.580000] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.580000] ACPI: PCI Interrupt Link [LSMB] (IRQs *5 7 9 10 11 14 15)
[    0.580000] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 10 *11 14 15)
[    0.580000] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.580000] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 10 *11 14 15)
[    0.580000] ACPI: PCI Interrupt Link [LFID] (IRQs 5 7 9 *10 11 14 15)
[    0.580000] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[    0.584000] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[    0.584000] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0
[    0.584000] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
[    0.584000] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0, disabled.
[    0.584000] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
[    0.584000] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
[    0.584000] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
[    0.584000] ACPI: PCI Interrupt Link [AIGP] (IRQs 20 21 22 23) *0
[    0.584000] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0
[    0.584000] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0
[    0.584000] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0, disabled.
[    0.584000] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0
[    0.584000] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
[    0.584000] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0
[    0.584000] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
[    0.584000] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[    0.584000] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
[    0.584000] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0
[    0.584000] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.584000] pnp: PnP ACPI init
[    0.584000] ACPI: bus type pnp registered
[    0.588000] pnp: PnP ACPI: found 13 devices
[    0.588000] ACPI: ACPI bus type pnp unregistered
[    0.588000] PnPBIOS: Disabled by ACPI PNP
[    0.588000] PCI: Using ACPI for IRQ routing
[    0.588000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    0.608000] NET: Registered protocol family 8
[    0.608000] NET: Registered protocol family 20
[    0.608000] pnp: 00:01: ioport range 0x1000-0x107f has been reserved
[    0.608000] pnp: 00:01: ioport range 0x1080-0x10ff has been reserved
[    0.608000] pnp: 00:01: ioport range 0x1400-0x147f has been reserved
[    0.608000] pnp: 00:01: ioport range 0x1480-0x14ff has been reserved
[    0.608000] pnp: 00:01: ioport range 0x1800-0x187f has been reserved
[    0.608000] pnp: 00:01: ioport range 0x1880-0x18ff has been reserved
[    0.608000] pnp: 00:01: iomem range 0xfefe0000-0xfefe01ff could not be reserved
[    0.608000] pnp: 00:01: iomem range 0xfefe1000-0xfefe10ff could not be reserved
[    0.608000] pnp: 00:01: iomem range 0x7c000000-0x7fffffff could not be reserved
[    0.608000] pnp: 00:0b: iomem range 0xf0000000-0xf1ffffff could not be reserved
[    0.608000] pnp: 00:0c: iomem range 0xd0000-0xd3fff has been reserved
[    0.608000] pnp: 00:0c: iomem range 0xf0000-0xf7fff could not be reserved
[    0.608000] pnp: 00:0c: iomem range 0xf8000-0xfbfff could not be reserved
[    0.608000] pnp: 00:0c: iomem range 0xfc000-0xfffff could not be reserved
[    0.612000] Time: hpet clocksource has been installed.
[    0.612000] Switched to high resolution mode on CPU 0
[    0.612000] Switched to high resolution mode on CPU 1
[    0.640000] PCI: Bridge: 0000:00:04.0
[    0.640000]   IO window: disabled.
[    0.640000]   MEM window: f5000000-f50fffff
[    0.640000]   PREFETCH window: disabled.
[    0.640000] PCI: Setting latency timer of device 0000:00:04.0 to 64
[    0.640000] NET: Registered protocol family 2
[    0.684000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.684000] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[    0.684000] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.684000] TCP: Hash tables configured (established 131072 bind 65536)
[    0.684000] TCP reno registered
[    0.700000] checking if image is initramfs... it is
[    1.252000] Freeing initrd memory: 7099k freed
[    1.252000] audit: initializing netlink socket (disabled)
[    1.252000] audit(1193328906.112:1): initialized
[    1.252000] highmem bounce pool size: 64 pages
[    1.252000] VFS: Disk quotas dquot_6.5.1
[    1.252000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.252000] io scheduler noop registered
[    1.252000] io scheduler anticipatory registered
[    1.252000] io scheduler deadline registered
[    1.252000] io scheduler cfq registered (default)
[    1.280000] Boot video device is 0000:00:0d.0
[    1.280000] isapnp: Scanning for PnP cards...
[    1.632000] isapnp: No Plug & Play device found
[    1.652000] Real Time Clock Driver v1.12ac
[    1.652000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    1.652000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.652000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.652000] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.652000] 00:08: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.652000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    1.652000] input: Macintosh mouse button emulation as /class/input/input0
[    1.652000] PNP: PS/2 Controller [PNP0f13:PS2M] at 0x60,0x64 irq 12
[    1.652000] PNP: PS/2 controller doesn't have KBD irq; using default 1
[    1.656000] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.656000] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.656000] mice: PS/2 mouse device common for all mice
[    1.656000] EISA: Probing bus 0 at eisa.0
[    1.656000] Cannot allocate resource for EISA slot 1
[    1.656000] EISA: Detected 0 cards.
[    1.656000] TCP cubic registered
[    1.656000] NET: Registered protocol family 1
[    1.656000] Using IPI No-Shortcut mode
[    1.656000]   Magic number: 11:320:288
[    1.656000]   hash matches device ttyz2
[    1.656000]   hash matches device tty21
[    1.656000] Freeing unused kernel memory: 364k freed
[    3.016000] AppArmor: AppArmor initialized<5>audit(1193328907.612:2):  type=1505 info="AppArmor initialized" pid=1239
[    3.028000] fuse init (API version 7.8)
[    3.040000] Failure registering capabilities with primary security module.
[    4.108000] usbcore: registered new interface driver usbfs
[    4.108000] usbcore: registered new interface driver hub
[    4.108000] usbcore: registered new device driver usb
[    4.108000] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    4.108000] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 23
[    4.108000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [APCF] -> GSI 23 (level, low) -> IRQ 16
[    4.108000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[    4.108000] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    4.108000] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[    4.108000] ohci_hcd 0000:00:02.0: irq 16, io mem 0xf5105000
[    4.188000] usb usb1: configuration #1 chosen from 1 choice
[    4.188000] hub 1-0:1.0: USB hub found
[    4.188000] hub 1-0:1.0: 10 ports detected
[    4.244000] SCSI subsystem initialized
[    4.248000] libata version 2.21 loaded.
[    4.252000] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.60.
[    4.292000] sata_nv 0000:00:08.0: version 3.4
[    4.292000] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 22
[    4.292000] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [APSI] -> GSI 22 (level, low) -> IRQ 17
[    4.292000] PCI: Setting latency timer of device 0000:00:08.0 to 64
[    4.292000] scsi0 : sata_nv
[    4.292000] scsi1 : sata_nv
[    4.292000] ata1: SATA max UDMA/133 cmd 0x000109f0 ctl 0x00010bf2 bmdma 0x0001d000 irq 17
[    4.292000] ata2: SATA max UDMA/133 cmd 0x00010970 ctl 0x00010b72 bmdma 0x0001d008 irq 17
[    4.596000] usb 1-4: new low speed USB device using ohci_hcd and address 2
[    4.760000] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    4.768000] ata1.00: ATA-7: WDC WD800JD-60LSA5, 10.01E03, max UDMA/100
[    4.768000] ata1.00: 156301488 sectors, multi 16: LBA48 
[    4.776000] ata1.00: configured for UDMA/100
[    4.808000] usb 1-4: configuration #1 chosen from 1 choice
[    5.088000] ata2: SATA link down (SStatus 0 SControl 300)
[    5.096000] scsi 0:0:0:0: Direct-Access     ATA      WDC WD800JD-60LS 10.0 PQ: 0 ANSI: 5
[    5.096000] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 21
[    5.096000] ACPI: PCI Interrupt 0000:00:08.1[B] -> Link [APSJ] -> GSI 21 (level, low) -> IRQ 18
[    5.096000] PCI: Setting latency timer of device 0000:00:08.1 to 64
[    5.096000] scsi2 : sata_nv
[    5.096000] scsi3 : sata_nv
[    5.096000] ata3: SATA max UDMA/133 cmd 0x000109e0 ctl 0x00010be2 bmdma 0x0001e400 irq 18
[    5.096000] ata4: SATA max UDMA/133 cmd 0x00010960 ctl 0x00010b62 bmdma 0x0001e408 irq 18
[    5.116000] usb 1-9: new full speed USB device using ohci_hcd and address 3
[    5.328000] usb 1-9: configuration #1 chosen from 1 choice
[    5.332000] usbcore: registered new interface driver hiddev
[    5.336000] input: DELL DELL USB Keyboard as /class/input/input1
[    5.336000] input: USB HID v1.10 Keyboard [DELL DELL USB Keyboard] on usb-0000:00:02.0-4
[    5.336000] usbcore: registered new interface driver usbhid
[    5.336000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[    5.344000] usbcore: registered new interface driver libusual
[    5.352000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    5.352000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    5.356000] Initializing USB Mass Storage driver...
[    5.356000] scsi4 : SCSI emulation for USB Mass Storage devices
[    5.356000] usb-storage: device found at 3
[    5.356000] usb-storage: waiting for device to settle before scanning
[    5.356000] usbcore: registered new interface driver usb-storage
[    5.356000] USB Mass Storage support registered.
[    5.408000] ata3: SATA link down (SStatus 0 SControl 300)
[    5.728000] ata4: SATA link down (SStatus 0 SControl 300)
[    5.736000] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 20
[    5.736000] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [APCL] -> GSI 20 (level, low) -> IRQ 19
[    5.736000] PCI: Setting latency timer of device 0000:00:02.1 to 64
[    5.736000] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    5.736000] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
[    5.736000] ehci_hcd 0000:00:02.1: debug port 1
[    5.736000] PCI: cache line size of 64 is not supported by device 0000:00:02.1
[    5.736000] ehci_hcd 0000:00:02.1: irq 19, io mem 0xf5106000
[    5.736000] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    5.736000] usb 1-4: USB disconnect, address 2
[    5.736000] usb usb2: configuration #1 chosen from 1 choice
[    5.736000] hub 2-0:1.0: USB hub found
[    5.736000] hub 2-0:1.0: 10 ports detected
[    5.840000] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 23
[    5.840000] ACPI: PCI Interrupt 0000:00:07.0[A] -> Link [APCH] -> GSI 23 (level, low) -> IRQ 16
[    5.840000] PCI: Setting latency timer of device 0000:00:07.0 to 64
[    5.840000] forcedeth: using HIGHDMA
[    5.872000] usb 1-9: USB disconnect, address 3
[    6.360000] eth0: forcedeth.c: subsystem: 01458:e000 bound to 0000:00:07.0
[    6.360000] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[    6.360000] ACPI: PCI Interrupt 0000:01:0e.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 20
[    6.412000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[20]  MMIO=[f5004000-f50047ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    6.412000] NFORCE-MCP61: IDE controller at PCI slot 0000:00:06.0
[    6.412000] NFORCE-MCP61: chipset revision 162
[    6.412000] NFORCE-MCP61: not 100% native mode: will probe irqs later
[    6.412000] NFORCE-MCP61: BIOS didn't set cable bits correctly. Enabling workaround.
[    6.412000] NFORCE-MCP61: 0000:00:06.0 (rev a2) UDMA133 controller
[    6.412000]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:DMA
[    6.412000] Probing IDE interface ide0...
[    6.420000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[    6.420000] sd 0:0:0:0: [sda] Write Protect is off
[    6.420000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.420000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.420000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[    6.420000] sd 0:0:0:0: [sda] Write Protect is off
[    6.420000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.420000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.420000]  sda:<6>usb 2-9: new high speed USB device using ehci_hcd and address 3
[    6.444000]  sda1 sda2 < sda5 >
[    6.464000] sd 0:0:0:0: [sda] Attached SCSI disk
[    6.468000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    6.556000] usb 2-9: configuration #1 chosen from 1 choice
[    6.556000] scsi5 : SCSI emulation for USB Mass Storage devices
[    6.556000] usb-storage: device found at 3
[    6.556000] usb-storage: waiting for device to settle before scanning
[    6.780000] Attempting manual resume
[    6.780000] swsusp: Resume From Partition 8:5
[    6.780000] PM: Checking swsusp image.
[    6.780000] PM: Resume from disk failed.
[    6.796000] ReiserFS: sda1: found reiserfs format "3.6" with standard journal
[    6.796000] ReiserFS: sda1: using ordered data mode
[    6.804000] ReiserFS: sda1: journal params: device sda1, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[    6.804000] ReiserFS: sda1: checking transaction log (sda1)
[    6.844000] ReiserFS: sda1: Using r5 hash to sort names
[    6.864000] usb 1-4: new low speed USB device using ohci_hcd and address 4
[    7.064000] usb 1-4: configuration #1 chosen from 1 choice
[    7.076000] input: DELL DELL USB Keyboard as /class/input/input2
[    7.076000] input: USB HID v1.10 Keyboard [DELL DELL USB Keyboard] on usb-0000:00:02.0-4
[    7.148000] hda: LITE-ON DVDRW LH-20A1H, ATAPI CD/DVD-ROM drive
[    7.684000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001a4d0000eb7d4c]
[    7.820000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   11.556000] usb-storage: device scan complete
[   11.560000] scsi 5:0:0:0: Direct-Access     USB2.0   CardReader CF    0100 PQ: 0 ANSI: 0
[   11.564000] scsi 5:0:0:1: Direct-Access     USB2.0   CardReader SM XD 0100 PQ: 0 ANSI: 0
[   11.568000] scsi 5:0:0:2: Direct-Access     USB2.0   CardReader MS    0100 PQ: 0 ANSI: 0
[   11.568000] scsi 5:0:0:3: Direct-Access     USB2.0   CardReader SD    0100 PQ: 0 ANSI: 0
[   11.568000] sd 5:0:0:0: [sdb] Attached SCSI removable disk
[   11.568000] sd 5:0:0:0: Attached scsi generic sg1 type 0
[   11.572000] sd 5:0:0:1: [sdc] Attached SCSI removable disk
[   11.572000] sd 5:0:0:1: Attached scsi generic sg2 type 0
[   11.572000] sd 5:0:0:2: [sdd] Attached SCSI removable disk
[   11.572000] sd 5:0:0:2: Attached scsi generic sg3 type 0
[   11.572000] sd 5:0:0:3: [sde] Attached SCSI removable disk
[   11.572000] sd 5:0:0:3: Attached scsi generic sg4 type 0
[   13.284000] NET: Registered protocol family 10
[   13.284000] lo: Disabled Privacy Extensions
[   13.872000] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x1c00
[   13.872000] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x1c40
[   14.080000] input: PC Speaker as /class/input/input3
[   14.328000] Linux agpgart interface v0.102 (c) Dave Jones
[   14.432000] nvidia: module license 'NVIDIA' taints kernel.
[   14.692000] hda: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(66)
[   14.692000] Uniform CD-ROM driver Revision: 3.20
[   14.744000] ACPI: PCI Interrupt Link [AIGP] enabled at IRQ 22
[   14.744000] ACPI: PCI Interrupt 0000:00:0d.0[A] -> Link [AIGP] -> GSI 22 (level, low) -> IRQ 17
[   14.744000] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   14.744000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9639  Mon Apr 16 20:20:06 PDT 2007
[   15.016000] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 21
[   15.016000] ACPI: PCI Interrupt 0000:00:05.0[B] -> Link [AAZA] -> GSI 21 (level, low) -> IRQ 18
[   15.016000] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   15.192000] input: ImPS/2 Logitech Wheel Mouse as /class/input/input4
[   15.196000] parport_pc 00:09: reported by Plug and Play ACPI
[   15.196000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   15.516000] lp0: using parport0 (interrupt-driven).
[   15.720000] Adding 3229024k swap on /dev/sda5.  Priority:-1 extents:1 across:3229024k
[   23.832000] eth0: no IPv6 routers present
[   27.964000] No dock devices found.
[   28.044000] input: Power Button (FF) as /class/input/input5
[   28.044000] ACPI: Power Button (FF) [PWRF]
[   28.044000] input: Power Button (CM) as /class/input/input6
[   28.044000] ACPI: Power Button (CM) [PWRB]
[   28.500000] powernow-k8: Found 2 AMD Athlon(tm) 64 X2 Dual Core Processor 4000+ processors (version 2.00.00)
[   28.500000] powernow-k8:    0 : fid 0xd (2100 MHz), vid 0xa
[   28.500000] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0xb
[   28.500000] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0xd
[   28.500000] powernow-k8:    3 : fid 0x2 (1000 MHz), vid 0x12
[   33.124000] ppdev: user-space parallel port driver
[   33.356000] audit(1193343338.730:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5526 profile="/usr/sbin/cupsd"
[   36.352000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   36.352000] apm: disabled - APM is not SMP safe.
[   37.504000] Clocksource tsc unstable (delta = -72023337 ns)
[   37.864000] Failure registering capabilities with primary security module.
[   38.168000] Bluetooth: Core ver 2.11
[   38.168000] NET: Registered protocol family 31
[   38.168000] Bluetooth: HCI device and connection manager initialized
[   38.168000] Bluetooth: HCI socket layer initialized
[   38.244000] Bluetooth: L2CAP ver 2.8
[   38.244000] Bluetooth: L2CAP socket layer initialized
[   38.252000] Bluetooth: RFCOMM socket layer initialized
[   38.252000] Bluetooth: RFCOMM TTY layer initialized
[   38.252000] Bluetooth: RFCOMM ver 1.8
[ 2639.452000] cdrom: This disc doesn't have any tracks I recognize!
[80460.936000] usb 2-9: USB disconnect, address 3
[80461.240000] usb 2-9: new high speed USB device using ehci_hcd and address 4
[80461.372000] usb 2-9: configuration #1 chosen from 1 choice
[80461.372000] scsi6 : SCSI emulation for USB Mass Storage devices
[80461.372000] usb-storage: device found at 4
[80461.372000] usb-storage: waiting for device to settle before scanning
[80466.372000] usb-storage: device scan complete
[80466.372000] scsi 6:0:0:0: Direct-Access     USB2.0   CardReader CF    0100 PQ: 0 ANSI: 0
[80466.372000] scsi 6:0:0:1: Direct-Access     USB2.0   CardReader SM XD 0100 PQ: 0 ANSI: 0
[80466.372000] scsi 6:0:0:2: Direct-Access     USB2.0   CardReader MS    0100 PQ: 0 ANSI: 0
[80466.372000] scsi 6:0:0:3: Direct-Access     USB2.0   CardReader SD    0100 PQ: 0 ANSI: 0
[80467.176000] sd 6:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[80467.180000] sd 6:0:0:0: [sdb] Write Protect is off
[80467.180000] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
[80467.180000] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[80467.180000] sd 6:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[80467.180000] sd 6:0:0:0: [sdb] Write Protect is off
[80467.180000] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
[80467.180000] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[80467.180000]  sdb: sdb1
[80467.204000] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[80467.204000] sd 6:0:0:0: Attached scsi generic sg1 type 0
[80467.212000] sd 6:0:0:1: [sdc] Attached SCSI removable disk
[80467.212000] sd 6:0:0:1: Attached scsi generic sg2 type 0
[80467.212000] sd 6:0:0:2: [sdd] Attached SCSI removable disk
[80467.212000] sd 6:0:0:2: Attached scsi generic sg3 type 0
[80467.220000] sd 6:0:0:3: [sde] Attached SCSI removable disk
[80467.220000] sd 6:0:0:3: Attached scsi generic sg4 type 0
[83678.648000] sd 6:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[83678.648000] sd 6:0:0:0: [sdb] Write Protect is off
[83678.648000] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
[83678.648000] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[83678.648000] sd 6:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[83678.648000] sd 6:0:0:0: [sdb] Write Protect is off
[83678.648000] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
[83678.648000] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[83678.648000]  sdb: sdb1
[83863.880000] Buffer I/O error on device sdb1, logical block 491
[83863.880000] lost page write due to I/O error on sdb1
[83934.660000] sd 6:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[83934.660000] sd 6:0:0:0: [sdb] Write Protect is off
[83934.660000] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
[83934.660000] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[83934.664000] sd 6:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[83934.668000] sd 6:0:0:0: [sdb] Write Protect is off
[83934.668000] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
[83934.668000] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[83934.668000]  sdb: sdb1
[85261.772000] ppdev0: registered pardevice
[85261.820000] ppdev0: unregistered pardevice
[85263.116000] audit(1193428568.538:4):  type=1503 operation="sysctl" requested_mask="r" denied_mask="r" name="/proc/sys/dev/parport/parport0/autoprobe" pid=19901 profile="/usr/sbin/cupsd"
[85263.136000] audit(1193428568.538:5):  type=1503 operation="sysctl" requested_mask="r" denied_mask="r" name="/proc/sys/dev/parport/parport0/autoprobe" pid=19902 profile="/usr/sbin/cupsd"
[85263.912000] ppdev0: registered pardevice
[85263.960000] ppdev0: unregistered pardevice
[85451.884000] audit(1193428757.036:6):  type=1503 operation="inode_permission" requested_mask="rw" denied_mask="rw" name="/dev/tty" pid=19964 profile="/usr/sbin/cupsd"
[85451.948000] audit(1193428757.536:7):  type=1503 operation="inode_permission" requested_mask="rw" denied_mask="rw" name="/dev/tty" pid=19967 profile="/usr/sbin/cupsd"
[87280.772000] sd 6:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[87280.772000] sd 6:0:0:0: [sdb] Write Protect is off
[87280.772000] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
[87280.772000] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[87280.772000] sd 6:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[87280.776000] sd 6:0:0:0: [sdb] Write Protect is off
[87280.776000] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
[87280.776000] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[87280.776000]  sdb: sdb1
[88012.820000] sd 6:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[88012.820000] sd 6:0:0:0: [sdb] Write Protect is off
[88012.820000] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
[88012.820000] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[88012.824000] sd 6:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[88012.824000] sd 6:0:0:0: [sdb] Write Protect is off
[88012.824000] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
[88012.824000] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[88012.824000]  sdb: sdb1
[88876.400000] audit(1193432182.009:8):  type=1503 operation="inode_permission" requested_mask="rw" denied_mask="rw" name="/dev/tty" pid=20301 profile="/usr/sbin/cupsd"
[88876.464000] audit(1193432182.009:9):  type=1503 operation="inode_permission" requested_mask="rw" denied_mask="rw" name="/dev/tty" pid=20304 profile="/usr/sbin/cupsd"
[90140.616000] cdrom: This disc doesn't have any tracks I recognize!
[347733.192000] sd 6:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[347733.192000] sd 6:0:0:0: [sdb] Write Protect is off
[347733.192000] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
[347733.192000] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[347733.192000] sd 6:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[347733.192000] sd 6:0:0:0: [sdb] Write Protect is off
[347733.192000] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
[347733.192000] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[347733.192000]  sdb: sdb1
[511054.088000] sd 6:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[511054.088000] sd 6:0:0:0: [sdb] Write Protect is off
[511054.088000] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
[511054.088000] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[511054.092000] sd 6:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[511054.092000] sd 6:0:0:0: [sdb] Write Protect is off
[511054.092000] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
[511054.092000] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[511054.092000]  sdb: sdb1
[597700.356000] sd 6:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[597700.356000] sd 6:0:0:0: [sdb] Write Protect is off
[597700.356000] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
[597700.356000] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[597700.360000] sd 6:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[597700.360000] sd 6:0:0:0: [sdb] Write Protect is off
[597700.360000] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
[597700.360000] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[597700.360000]  sdb: sdb1
[600739.972000] usb 2-9: USB disconnect, address 4
[600740.264000] usb 2-9: new high speed USB device using ehci_hcd and address 5
[600740.396000] usb 2-9: configuration #1 chosen from 1 choice
[600740.396000] scsi7 : SCSI emulation for USB Mass Storage devices
[600740.396000] usb-storage: device found at 5
[600740.396000] usb-storage: waiting for device to settle before scanning
[600745.396000] usb-storage: device scan complete
[600745.396000] scsi 7:0:0:0: Direct-Access     USB2.0   CardReader CF    0100 PQ: 0 ANSI: 0
[600745.396000] scsi 7:0:0:1: Direct-Access     USB2.0   CardReader SM XD 0100 PQ: 0 ANSI: 0
[600745.396000] scsi 7:0:0:2: Direct-Access     USB2.0   CardReader MS    0100 PQ: 0 ANSI: 0
[600745.396000] scsi 7:0:0:3: Direct-Access     USB2.0   CardReader SD    0100 PQ: 0 ANSI: 0
[600746.200000] sd 7:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[600746.204000] sd 7:0:0:0: [sdb] Write Protect is off
[600746.204000] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[600746.204000] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[600746.204000] sd 7:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[600746.204000] sd 7:0:0:0: [sdb] Write Protect is off
[600746.204000] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[600746.204000] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[600746.204000]  sdb: sdb1
[600746.228000] sd 7:0:0:0: [sdb] Attached SCSI removable disk
[600746.228000] sd 7:0:0:0: Attached scsi generic sg1 type 0
[600746.232000] sd 7:0:0:1: [sdc] Attached SCSI removable disk
[600746.232000] sd 7:0:0:1: Attached scsi generic sg2 type 0
[600746.232000] sd 7:0:0:2: [sdd] Attached SCSI removable disk
[600746.232000] sd 7:0:0:2: Attached scsi generic sg3 type 0
[600746.236000] sd 7:0:0:3: [sde] Attached SCSI removable disk
[600746.236000] sd 7:0:0:3: Attached scsi generic sg4 type 0
[600789.160000] Buffer I/O error on device sdb1, logical block 491
[600789.160000] lost page write due to I/O error on sdb1
[600789.160000] Buffer I/O error on device sdb1, logical block 523
[600789.160000] lost page write due to I/O error on sdb1
[600789.164000] Buffer I/O error on device sdb1, logical block 74315
[600789.164000] lost page write due to I/O error on sdb1
[600851.936000] sd 7:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[600851.936000] sd 7:0:0:0: [sdb] Write Protect is off
[600851.936000] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[600851.936000] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[600851.940000] sd 7:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[600851.940000] sd 7:0:0:0: [sdb] Write Protect is off
[600851.940000] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[600851.940000] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[600851.940000]  sdb: sdb1
[602686.036000] sd 7:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[602686.036000] sd 7:0:0:0: [sdb] Write Protect is off
[602686.036000] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[602686.036000] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[602686.040000] sd 7:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[602686.044000] sd 7:0:0:0: [sdb] Write Protect is off
[602686.044000] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[602686.044000] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[602686.044000]  sdb: sdb1
[603992.112000] sd 7:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[603992.112000] sd 7:0:0:0: [sdb] Write Protect is off
[603992.112000] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[603992.112000] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[603992.120000] sd 7:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[603992.120000] sd 7:0:0:0: [sdb] Write Protect is off
[603992.120000] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[603992.120000] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[603992.120000]  sdb: sdb1
[605144.136000] sd 7:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[605144.136000] sd 7:0:0:0: [sdb] Write Protect is off
[605144.136000] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[605144.136000] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[605144.140000] sd 7:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[605144.144000] sd 7:0:0:0: [sdb] Write Protect is off
[605144.144000] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[605144.144000] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[605144.144000]  sdb: sdb1
[606024.204000] sd 7:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[606024.204000] sd 7:0:0:0: [sdb] Write Protect is off
[606024.204000] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[606024.204000] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[606024.208000] sd 7:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[606024.208000] sd 7:0:0:0: [sdb] Write Protect is off
[606024.208000] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[606024.208000] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[606024.208000]  sdb: sdb1
[606266.208000] sd 7:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[606266.208000] sd 7:0:0:0: [sdb] Write Protect is off
[606266.208000] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[606266.208000] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[606266.212000] sd 7:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[606266.216000] sd 7:0:0:0: [sdb] Write Protect is off
[606266.216000] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[606266.216000] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[606266.216000]  sdb: sdb1
[607782.088000] cdrom: This disc doesn't have any tracks I recognize!
[683918.280000] ppdev0: registered pardevice
[683918.280000] ppdev0: unregistered pardevice
[683919.040000] ppdev0: registered pardevice
[683919.088000] ppdev0: unregistered pardevice
[945748.952000] sd 7:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[945748.956000] sd 7:0:0:0: [sdb] Write Protect is off
[945748.956000] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[945748.956000] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[945748.960000] sd 7:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[945748.964000] sd 7:0:0:0: [sdb] Write Protect is off
[945748.964000] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[945748.964000] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[945748.964000]  sdb: sdb1
[946756.980000] audit(1194290049.536:10):  type=1503 operation="inode_permission" requested_mask="rw" denied_mask="rw" name="/dev/tty" pid=3375 profile="/usr/sbin/cupsd"
[946757.020000] audit(1194290049.536:11):  type=1503 operation="inode_permission" requested_mask="rw" denied_mask="rw" name="/dev/tty" pid=3378 profile="/usr/sbin/cupsd"
[955881.092000] sd 7:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[955881.092000] sd 7:0:0:0: [sdb] Write Protect is off
[955881.092000] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[955881.092000] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[955881.092000] sd 7:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[955881.092000] sd 7:0:0:0: [sdb] Write Protect is off
[955881.092000] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[955881.092000] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[955881.092000]  sdb: sdb1
[1032453.772000] audit(1194375746.030:12):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4836 profile="/usr/sbin/cupsd"
[1033875.728000] audit(1194377168.441:13):  type=1503 operation="inode_permission" requested_mask="rw" denied_mask="rw" name="/dev/tty" pid=4990 profile="/usr/sbin/cupsd"
[1033875.824000] audit(1194377168.441:14):  type=1503 operation="inode_permission" requested_mask="rw" denied_mask="rw" name="/dev/tty" pid=4993 profile="/usr/sbin/cupsd"
[1036239.620000] sd 7:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[1036239.624000] sd 7:0:0:0: [sdb] Write Protect is off
[1036239.624000] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[1036239.624000] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[1036239.624000] sd 7:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[1036239.624000] sd 7:0:0:0: [sdb] Write Protect is off
[1036239.624000] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[1036239.624000] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[1036239.624000]  sdb: sdb1
[1036398.860000] Buffer I/O error on device sdb1, logical block 523
[1036398.860000] lost page write due to I/O error on sdb1
[1036398.860000] Buffer I/O error on device sdb1, logical block 74315
[1036398.860000] lost page write due to I/O error on sdb1
[1036398.860000] Buffer I/O error on device sdb1, logical block 1
[1036398.860000] lost page write due to I/O error on sdb1
[1036398.860000] Buffer I/O error on device sdb1, logical block 2
[1036398.860000] lost page write due to I/O error on sdb1
[1036398.860000] Buffer I/O error on device sdb1, logical block 3
[1036398.860000] lost page write due to I/O error on sdb1
[1036398.860000] Buffer I/O error on device sdb1, logical block 4
[1036398.860000] lost page write due to I/O error on sdb1
[1036398.860000] Buffer I/O error on device sdb1, logical block 5
[1036398.860000] lost page write due to I/O error on sdb1
[1036398.860000] Buffer I/O error on device sdb1, logical block 6
[1036398.860000] lost page write due to I/O error on sdb1
[1036398.860000] Buffer I/O error on device sdb1, logical block 7
[1036398.860000] lost page write due to I/O error on sdb1
[1036398.860000] Buffer I/O error on device sdb1, logical block 8
[1036398.860000] lost page write due to I/O error on sdb1
[1036471.640000] sd 7:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[1036471.640000] sd 7:0:0:0: [sdb] Write Protect is off
[1036471.640000] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[1036471.640000] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[1036471.644000] sd 7:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[1036471.644000] sd 7:0:0:0: [sdb] Write Protect is off
[1036471.644000] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[1036471.644000] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[1036471.644000]  sdb: sdb1
[1041703.920000] sd 7:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[1041703.924000] sd 7:0:0:0: [sdb] Write Protect is off
[1041703.924000] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[1041703.924000] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[1041703.924000] sd 7:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[1041703.924000] sd 7:0:0:0: [sdb] Write Protect is off
[1041703.924000] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[1041703.924000] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[1041703.924000]  sdb: sdb1
[1042985.036000] cdrom: This disc doesn't have any tracks I recognize!
[1117882.188000] sd 7:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[1117882.188000] sd 7:0:0:0: [sdb] Write Protect is off
[1117882.188000] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[1117882.188000] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[1117882.192000] sd 7:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[1117882.192000] sd 7:0:0:0: [sdb] Write Protect is off
[1117882.192000] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[1117882.192000] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[1117882.192000]  sdb: sdb1
[1206655.048000] sd 7:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[1206655.048000] sd 7:0:0:0: [sdb] Write Protect is off
[1206655.048000] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[1206655.048000] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[1206655.056000] sd 7:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[1206655.056000] sd 7:0:0:0: [sdb] Write Protect is off
[1206655.056000] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[1206655.056000] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[1206655.056000]  sdb: sdb1
[1212782.552000] ppdev0: registered pardevice
[1212782.552000] ppdev0: unregistered pardevice
[1212783.304000] ppdev0: registered pardevice
[1212783.352000] ppdev0: unregistered pardevice
[1216134.172000] cdrom: This disc doesn't have any tracks I recognize!
[1289003.628000] audit(1194632295.938:15):  type=1503 operation="inode_permission" requested_mask="rw" denied_mask="rw" name="/dev/tty" pid=17123 profile="/usr/sbin/cupsd"
[1289003.668000] audit(1194632295.938:16):  type=1503 operation="inode_permission" requested_mask="rw" denied_mask="rw" name="/dev/tty" pid=17126 profile="/usr/sbin/cupsd"
[1290262.408000] audit(1194633554.858:17):  type=1503 operation="inode_permission" requested_mask="rw" denied_mask="rw" name="/dev/tty" pid=17173 profile="/usr/sbin/cupsd"
[1290262.448000] audit(1194633554.858:18):  type=1503 operation="inode_permission" requested_mask="rw" denied_mask="rw" name="/dev/tty" pid=17176 profile="/usr/sbin/cupsd"
[1646755.032000] sd 7:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[1646755.036000] sd 7:0:0:0: [sdb] Write Protect is off
[1646755.036000] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[1646755.036000] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[1646755.040000] sd 7:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[1646755.044000] sd 7:0:0:0: [sdb] Write Protect is off
[1646755.044000] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[1646755.044000] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[1646755.044000]  sdb: sdb1
[1648837.064000] sd 7:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[1648837.068000] sd 7:0:0:0: [sdb] Write Protect is off
[1648837.068000] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[1648837.068000] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[1648837.072000] sd 7:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[1648837.072000] sd 7:0:0:0: [sdb] Write Protect is off
[1648837.072000] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[1648837.072000] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[1648837.072000]  sdb: sdb1
[1731336.204000] audit(1195074628.720:19):  type=1503 operation="inode_permission" requested_mask="rw" denied_mask="rw" name="/dev/tty" pid=23153 profile="/usr/sbin/cupsd"
[1731336.244000] audit(1195074628.720:20):  type=1503 operation="inode_permission" requested_mask="rw" denied_mask="rw" name="/dev/tty" pid=23156 profile="/usr/sbin/cupsd"
[1735074.836000] cdrom: This disc doesn't have any tracks I recognize!
[1810178.076000] eth0: link down.
[1810186.068000] eth0: link up.
[1813250.124000] usb 2-8: new high speed USB device using ehci_hcd and address 6
[1813250.256000] usb 2-8: configuration #1 chosen from 1 choice
[1813250.256000] scsi8 : SCSI emulation for USB Mass Storage devices
[1813250.256000] usb-storage: device found at 6
[1813250.256000] usb-storage: waiting for device to settle before scanning
[1813255.256000] usb-storage: device scan complete
[1813255.256000] scsi 8:0:0:0: Direct-Access     WDC WD80      WD-WCAM9T89 10.0 PQ: 0 ANSI: 2 CCS
[1813255.260000] sd 8:0:0:0: [sdf] 156301488 512-byte hardware sectors (80026 MB)
[1813255.260000] sd 8:0:0:0: [sdf] Write Protect is off
[1813255.260000] sd 8:0:0:0: [sdf] Mode Sense: 00 38 00 00
[1813255.260000] sd 8:0:0:0: [sdf] Assuming drive cache: write through
[1813255.268000] sd 8:0:0:0: [sdf] 156301488 512-byte hardware sectors (80026 MB)
[1813255.268000] sd 8:0:0:0: [sdf] Write Protect is off
[1813255.268000] sd 8:0:0:0: [sdf] Mode Sense: 00 38 00 00
[1813255.268000] sd 8:0:0:0: [sdf] Assuming drive cache: write through
[1813255.268000]  sdf: unknown partition table
[1813255.276000] sd 8:0:0:0: [sdf] Attached SCSI disk
[1813255.276000] sd 8:0:0:0: Attached scsi generic sg5 type 0
[1813317.940000] usb 2-8: USB disconnect, address 6
[1813505.252000] usb 2-7: new high speed USB device using ehci_hcd and address 7
[1813505.384000] usb 2-7: configuration #1 chosen from 1 choice
[1813505.384000] scsi9 : SCSI emulation for USB Mass Storage devices
[1813505.384000] usb-storage: device found at 7
[1813505.384000] usb-storage: waiting for device to settle before scanning
[1813510.384000] usb-storage: device scan complete
[1813510.384000] scsi 9:0:0:0: Direct-Access     WDC WD80      WD-WCAM9T89 10.0 PQ: 0 ANSI: 2 CCS
[1813510.388000] sd 9:0:0:0: [sdf] 156301488 512-byte hardware sectors (80026 MB)
[1813510.388000] sd 9:0:0:0: [sdf] Write Protect is off
[1813510.388000] sd 9:0:0:0: [sdf] Mode Sense: 00 38 00 00
[1813510.388000] sd 9:0:0:0: [sdf] Assuming drive cache: write through
[1813510.388000] sd 9:0:0:0: [sdf] 156301488 512-byte hardware sectors (80026 MB)
[1813510.388000] sd 9:0:0:0: [sdf] Write Protect is off
[1813510.388000] sd 9:0:0:0: [sdf] Mode Sense: 00 38 00 00
[1813510.388000] sd 9:0:0:0: [sdf] Assuming drive cache: write through
[1813510.388000]  sdf: unknown partition table
[1813510.400000] sd 9:0:0:0: [sdf] Attached SCSI disk
[1813510.400000] sd 9:0:0:0: Attached scsi generic sg5 type 0
[1813742.580000] usb 2-7: USB disconnect, address 7
[1817206.944000] usb 2-7: new high speed USB device using ehci_hcd and address 8
[1817207.076000] usb 2-7: configuration #1 chosen from 1 choice
[1817207.076000] scsi10 : SCSI emulation for USB Mass Storage devices
[1817207.076000] usb-storage: device found at 8
[1817207.076000] usb-storage: waiting for device to settle before scanning
[1817212.076000] usb-storage: device scan complete
[1817212.076000] scsi 10:0:0:0: Direct-Access     WDC WD80      WD-WCAM9T89 10.0 PQ: 0 ANSI: 2 CCS
[1817212.076000] sd 10:0:0:0: [sdf] 156301488 512-byte hardware sectors (80026 MB)
[1817212.076000] sd 10:0:0:0: [sdf] Write Protect is off
[1817212.076000] sd 10:0:0:0: [sdf] Mode Sense: 00 38 00 00
[1817212.076000] sd 10:0:0:0: [sdf] Assuming drive cache: write through
[1817212.080000] sd 10:0:0:0: [sdf] 156301488 512-byte hardware sectors (80026 MB)
[1817212.080000] sd 10:0:0:0: [sdf] Write Protect is off
[1817212.080000] sd 10:0:0:0: [sdf] Mode Sense: 00 38 00 00
[1817212.080000] sd 10:0:0:0: [sdf] Assuming drive cache: write through
[1817212.080000]  sdf: sdf1
[1817212.088000] sd 10:0:0:0: [sdf] Attached SCSI disk
[1817212.088000] sd 10:0:0:0: Attached scsi generic sg5 type 0
[1819189.936000] usb 2-7: USB disconnect, address 8
[1893170.064000] sd 7:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[1893170.064000] sd 7:0:0:0: [sdb] Write Protect is off
[1893170.064000] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[1893170.064000] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[1893170.068000] sd 7:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[1893170.072000] sd 7:0:0:0: [sdb] Write Protect is off
[1893170.072000] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[1893170.072000] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[1893170.072000]  sdb: sdb1
[1893608.068000] sd 7:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[1893608.068000] sd 7:0:0:0: [sdb] Write Protect is off
[1893608.068000] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[1893608.068000] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[1893608.068000] sd 7:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
[1893608.072000] sd 7:0:0:0: [sdb] Write Protect is off
[1893608.072000] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[1893608.072000] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[1893608.072000]  sdb: sdb1
[1894617.024000] usb 2-7: new high speed USB device using ehci_hcd and address 9
[1894617.156000] usb 2-7: configuration #1 chosen from 1 choice
[1894617.156000] scsi11 : SCSI emulation for USB Mass Storage devices
[1894617.156000] usb-storage: device found at 9
[1894617.156000] usb-storage: waiting for device to settle before scanning
[1894622.156000] usb-storage: device scan complete
[1894622.156000] scsi 11:0:0:0: Direct-Access     WDC WD80      WD-WCAM9T89 10.0 PQ: 0 ANSI: 2 CCS
[1894622.160000] sd 11:0:0:0: [sdf] 156301488 512-byte hardware sectors (80026 MB)
[1894622.164000] sd 11:0:0:0: [sdf] Write Protect is off
[1894622.164000] sd 11:0:0:0: [sdf] Mode Sense: 00 38 00 00
[1894622.164000] sd 11:0:0:0: [sdf] Assuming drive cache: write through
[1894622.164000] sd 11:0:0:0: [sdf] 156301488 512-byte hardware sectors (80026 MB)
[1894622.168000] sd 11:0:0:0: [sdf] Write Protect is off
[1894622.168000] sd 11:0:0:0: [sdf] Mode Sense: 00 38 00 00
[1894622.168000] sd 11:0:0:0: [sdf] Assuming drive cache: write through
[1894622.168000]  sdf: sdf1
[1894622.168000] sd 11:0:0:0: [sdf] Attached SCSI disk
[1894622.168000] sd 11:0:0:0: Attached scsi generic sg5 type 0
[1895220.776000] audit(1195238513.172:21):  type=1503 operation="inode_permission" requested_mask="rw" denied_mask="rw" name="/dev/tty" pid=27169 profile="/usr/sbin/cupsd"
[1895220.816000] audit(1195238513.172:22):  type=1503 operation="inode_permission" requested_mask="rw" denied_mask="rw" name="/dev/tty" pid=27172 profile="/usr/sbin/cupsd"

```



hopefully this gives some leads...

---

### Post by minus198 on 2007-11-16
You should be able to see it and format it in GParted.

sudo apt-get install gparted

---

### Post by Arbiter on 2007-11-16
Already tried gparted, it does not recognize the unformatted drive.

---

### Post by Arbiter on 2007-11-16
never mind, this was my mistake - drive jumpers were not set properly.  sorry bout all this...

---

### Post by minus198 on 2007-11-16
Set the thread as solved then :)

---

