---
title: "Windows XP Doesn't Recognize My Hard Drive"
date: 2008-02-20
forum: General Help
---

### Post by tomihasa on 2008-02-20
I have installed Ubuntu 7.10 with my HP laptop to my LaCie 160 GB USB hard drive. But now when in Windows XP I plug in my LaCie 500 GB USB hard drive, no "E:" icon appears so I could open my Windows files there. How can I make my HP laptop Windows XP understand that only one of my LaCie hard disks has Ubuntu installed in it, and the others have Windows files? My Fujitsu Siemens laptop having also Windows XP still recognizes the same 500 GB drive, so it might be some setting in Windows XP I could change?

---

### Post by bernied on 2008-02-20
This really does sound like a windows problem, not linux. Especially since your other XP machine can read the drive fine.

If you right-click on My Computer, then go Manage, then in the GUI you want Storage - Removable Storage, you might find some information.

The other place to look is in the device manager, also in the Computer Management GUI, especially under USB controllers.

Does nothing at all happen when you plug in the device? No icons in the notification area?
Do you have trouble with other USB devices?
Is the drive self powered, or does it get its power from USB cable, and if it does get power from the USB cable, are you sure that the hub (either internal or external) is supplying enough?
Have you tried a different port and or hub?

---

### Post by timcredible on 2008-02-20
did you format your lacie drive?  if so, you need to re-format it as fat32.  if you didn't format your drive, then it's strictly a windows problem.  solution is to quit using windows ;-)

---

### Post by tomihasa on 2008-02-21
> **bernied said:**
> This really does sound like a windows problem, not linux. Especially since your other XP machine can read the drive fine.

If you right-click on My Computer, then go Manage, then in the GUI you want Storage - Removable Storage, you might find some information.

The other place to look is in the device manager, also in the Computer Management GUI, especially under USB controllers.

Does nothing at all happen when you plug in the device? No icons in the notification area?
Do you have trouble with other USB devices?
Is the drive self powered, or does it get its power from USB cable, and if it does get power from the USB cable, are you sure that the hub (either internal or external) is supplying enough?
Have you tried a different port and or hub?

My LaCie hard drive uses external power source and I don't have problems with my other USB devices. In Computer Management, Storage, Disk Management (I guess LaCie should be in Removable Storage, as you mention, unless Removable Storage is for optical discs and such), I see four volumes, and LaCie 500 GB hard drive is one of them:

Volume: LACIE 500
Layout: Partition
Type: Basic
File System: FAT32
Status: Healthy (Active)
Capacity: 465.65 GB
Free Space: 232.08 GB
% Free: 49 %
Fault Tolerance: No
Overhead: 0%

I think I will re-install my Windows XP and partition the hard drive to give some space for Ubuntu there. :)

---

### Post by tomihasa on 2008-02-22
I re-installed Windows XP and then Ubuntu 7.10 to my internal hard drive on my HP laptop and both seem to work fine. But is it normal that I only can find **hda1** (Windows XP partition) with Ubuntu? My partitions are hda1 (Windows XP/NTFS), hda5 (root/Ext3) and hda6 (swap). Does the "File System" section in the File Browser mean the same as hda5 in my case?

Here's the dmesg in case needed:

```

[    0.000000] Linux version 2.6.22-14-generic (buildd@crested) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 21:45:15 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] Command line: root=UUID=50791c2c-a559-4e1a-bf54-fcddc91657d1 ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001fea0000 (usable)
[    0.000000]  BIOS-e820: 000000001fea0000 - 000000001feac000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001feac000 - 000000001ff00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001ff00000 - 0000000020000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 130720) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xFFFF8100000F7C20 checksum 0
[    0.000000] ACPI: RSDP 000F7C20, 0014 (r0 PTLTD )
[    0.000000] ACPI: RSDT 1FEA4598, 0034 (r1 PTLTD    RSDT    6040000  LTP        0)
[    0.000000] ACPI: FACP 1FEABE3B, 0074 (r1 HP     Piranha   6040000 ATI     F4240)
[    0.000000] ACPI: DSDT 1FEA45CC, 786F (r1     HP     309B  6040000 MSFT  100000E)
[    0.000000] ACPI: FACS 1FEACFC0, 0040
[    0.000000] ACPI: SSDT 1FEABEAF, 00CF (r1 PTLTD  POWERNOW  6040000  LTP        1)
[    0.000000] ACPI: APIC 1FEABF7E, 0046 (r1 PTLTD  	 APIC    6040000  LTP        0)
[    0.000000] ACPI: MCFG 1FEABFC4, 003C (r1 PTLTD    MCFG    6040000  LTP        0)
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000001fea0000
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 130720) 1 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-000000001fea0000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      159
[    0.000000]     0:      256 ->   130720
[    0.000000] On node 0 totalpages: 130623
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1124 pages reserved
[    0.000000]   DMA zone: 2819 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 1731 pages used for memmap
[    0.000000]   DMA32 zone: 124893 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000] ATI board detected. Disabling timer routing over 8254.
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000d0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000d0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:c0000000)
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 34696 bytes of per cpu data
[    0.000000] Built 1 zonelists.  Total pages: 127712
[    0.000000] Kernel command line: root=UUID=50791c2c-a559-4e1a-bf54-fcddc91657d1 ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 16384 bytes)
[   14.932607] time.c: Detected 1794.796 MHz processor.
[   14.933455] Console: colour VGA+ 80x25
[   14.933475] Checking aperture...
[   14.933479] CPU 0: aperture @ 220000000 size 32 MB
[   14.933481] Aperture too small (32 MB)
[   14.945449] No AGP bridge found
[   14.954110] Memory: 502996k/522880k available (2274k kernel code, 19496k reserved, 1181k data, 296k init)
[   14.954174] SLUB: Genslabs=23, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   15.030520] Calibrating delay using timer specific routine.. 3593.33 BogoMIPS (lpj=7186679)
[   15.030565] Security Framework v1.0.0 initialized
[   15.030576] SELinux:  Disabled at boot.
[   15.030646] Dentry cache hash table entries: 65536 (order: 7, 524288 bytes)
[   15.031240] Inode-cache hash table entries: 32768 (order: 6, 262144 bytes)
[   15.031544] Mount-cache hash table entries: 256
[   15.031731] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   15.031734] CPU: L2 Cache: 512K (64 bytes/line)
[   15.031737] CPU 0/0 -> Node 0
[   15.031761] SMP alternatives: switching to UP code
[   15.032070] Freeing SMP alternatives: 24k freed
[   15.032614] Early unpacking initramfs... done
[   15.379633] ACPI: Core revision 20070126
[   15.379724] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   16.061370] Using local APIC timer interrupts.
[   16.117037] result 12463867
[   16.117039] Detected 12.463 MHz APIC timer.
[   16.117595] Brought up 1 CPUs
[   16.117835] NET: Registered protocol family 16
[   16.117934] ACPI: bus type pci registered
[   16.117942] PCI: Using configuration type 1
[   16.118707] ACPI: EC: Look up EC in DSDT
[   16.119359] ACPI: EC: GPE=0x1a, ports=0x66, 0x62
[   16.120362] ACPI: Interpreter enabled
[   16.120365] ACPI: (supports S0 S3 S4 S5)
[   16.120380] ACPI: Using IOAPIC for interrupt routing
[   16.166144] ACPI: EC: GPE=0x1a, ports=0x66, 0x62
[   16.166183] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   16.166191] PCI: Probing PCI hardware (bus 00)
[   16.167662] PCI: Transparent bridge - 0000:00:14.4
[   16.167762] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   16.167892] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB5_._PRT]
[   16.168000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[   16.168115] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[   16.169909] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[   16.170008] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[   16.170105] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[   16.170202] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
[   16.170298] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[   16.170394] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[   16.170490] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[   16.170586] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[   16.170670] Linux Plug and Play Support v0.97 (c) Adam Belay
[   16.170681] pnp: PnP ACPI init
[   16.170690] ACPI: bus type pnp registered
[   16.193534] pnp: PnP ACPI: found 10 devices
[   16.193536] ACPI: ACPI bus type pnp unregistered
[   16.193598] PCI: Using ACPI for IRQ routing
[   16.193601] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   16.193609] PCI: Cannot allocate resource region 7 of bridge 0000:00:05.0
[   16.193656] PCI: Cannot allocate resource region 8 of bridge 0000:00:05.0
[   16.193813] NET: Registered protocol family 8
[   16.193815] NET: Registered protocol family 20
[   16.193943] pnp: 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
[   16.193947] pnp: 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
[   16.193951] pnp: 00:01: iomem range 0xfee00000-0xfee00fff could not be reserved
[   16.193959] pnp: 00:08: ioport range 0x1080-0x1080 has been reserved
[   16.193962] pnp: 00:08: ioport range 0x40b-0x40b has been reserved
[   16.193965] pnp: 00:08: ioport range 0x4d0-0x4d1 has been reserved
[   16.193968] pnp: 00:08: ioport range 0x4d6-0x4d6 has been reserved
[   16.193971] pnp: 00:08: ioport range 0x870-0x87f has been reserved
[   16.193976] pnp: 00:09: iomem range 0xe0000-0xfffff could not be reserved
[   16.193979] pnp: 00:09: iomem range 0xfff80000-0xffffffff could not be reserved
[   16.193982] pnp: 00:09: iomem range 0x0-0xfff could not be reserved
[   16.194274] PCI: Bridge: 0000:00:01.0
[   16.194277]   IO window: 9000-9fff
[   16.194281]   MEM window: c0100000-c01fffff
[   16.194284]   PREFETCH window: c8000000-cfffffff
[   16.194287] PCI: Bridge: 0000:00:05.0
[   16.194289]   IO window: disabled.
[   16.194291]   MEM window: disabled.
[   16.194293]   PREFETCH window: disabled.
[   16.194299] PCI: Bus 7, cardbus bridge: 0000:06:04.0
[   16.194301]   IO window: 0000a400-0000a4ff
[   16.194307]   IO window: 0000a800-0000a8ff
[   16.194313]   PREFETCH window: 30000000-33ffffff
[   16.194320]   MEM window: 34000000-37ffffff
[   16.194325] PCI: Bridge: 0000:00:14.4
[   16.194329]   IO window: a000-afff
[   16.194335]   MEM window: c0200000-c02fffff
[   16.194341]   PREFETCH window: 30000000-33ffffff
[   16.194361] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   16.194392] ACPI: PCI Interrupt 0000:06:04.0[A] -> GSI 20 (level, low) -> IRQ 20
[   16.194446] NET: Registered protocol family 2
[   16.197467] Time: tsc clocksource has been installed.
[   16.229505] IP route cache hash table entries: 4096 (order: 3, 32768 bytes)
[   16.229601] TCP established hash table entries: 16384 (order: 6, 393216 bytes)
[   16.229955] TCP bind hash table entries: 16384 (order: 6, 262144 bytes)
[   16.230220] TCP: Hash tables configured (established 16384 bind 16384)
[   16.230223] TCP reno registered
[   16.241584] checking if image is initramfs... it is
[   16.911644] Freeing initrd memory: 7743k freed
[   16.920645] audit: initializing netlink socket (disabled)
[   16.920662] audit(1203678764.300:1): initialized
[   16.922680] VFS: Disk quotas dquot_6.5.1
[   16.922740] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   16.922861] io scheduler noop registered
[   16.922863] io scheduler anticipatory registered
[   16.922865] io scheduler deadline registered
[   16.922958] io scheduler cfq registered (default)
[   16.922966] PCI: MSI quirk detected. MSI deactivated.
[   16.923657] Boot video device is 0000:01:05.0
[   16.923818] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   16.923838] assign_interrupt_mode Found MSI capability
[   16.923842] Allocate Port Service[0000:00:05.0:pcie00]
[   16.948337] Real Time Clock Driver v1.12ac
[   16.948432] Linux agpgart interface v0.102 (c) Dave Jones
[   16.948435] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   16.949077] ACPI: PCI Interrupt 0000:00:14.6[B] -> GSI 17 (level, low) -> IRQ 17
[   16.949086] ACPI: PCI interrupt for device 0000:00:14.6 disabled
[   16.949626] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   16.949872] input: Macintosh mouse button emulation as /class/input/input0
[   16.949941] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[   16.968708] i8042.c: Detected active multiplexing controller, rev 1.1.
[   16.985063] serio: i8042 KBD port at 0x60,0x64 irq 1
[   16.985068] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   16.985071] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   16.985074] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   16.985077] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   16.985373] mice: PS/2 mouse device common for all mice
[   16.985521] TCP cubic registered
[   16.986373] NET: Registered protocol family 1
[   16.986615] /build/buildd/linux-source-2.6.22-2.6.22/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   16.986624] Freeing unused kernel memory: 296k freed
[   17.012776] input: AT Translated Set 2 keyboard as /class/input/input1
[   18.183211] AppArmor: AppArmor initialized<5>audit(1203678765.564:2):  type=1505 info="AppArmor initialized" pid=1204
[   18.294215] fuse init (API version 7.8)
[   18.399596] Failure registering capabilities with primary security module.
[   18.707150] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   18.707157] ACPI: Processor [CPU0] (supports 8 throttling states)
[   19.306743] ACPI Exception (thermal-0400): AE_NOT_FOUND, Invalid active threshold [0] [20070126]
[   19.506532] ACPI: Thermal Zone [THRM] (0 C)
[   29.169933] usbcore: registered new interface driver usbfs
[   29.169961] usbcore: registered new interface driver hub
[   29.169984] usbcore: registered new device driver usb
[   29.170761] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   29.170808] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 19
[   29.170977] ohci_hcd 0000:00:13.0: OHCI Host Controller
[   29.171162] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[   29.171189] ohci_hcd 0000:00:13.0: irq 19, io mem 0xc0000000
[   29.229943] usb usb1: configuration #1 chosen from 1 choice
[   29.229971] hub 1-0:1.0: USB hub found
[   29.229984] hub 1-0:1.0: 4 ports detected
[   29.333833] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 19
[   29.334019] ohci_hcd 0000:00:13.1: OHCI Host Controller
[   29.334079] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[   29.334103] ohci_hcd 0000:00:13.1: irq 19, io mem 0xc0001000
[   29.393824] usb usb2: configuration #1 chosen from 1 choice
[   29.393860] hub 2-0:1.0: USB hub found
[   29.393877] hub 2-0:1.0: 4 ports detected
[   29.508857] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 19
[   29.509005] ehci_hcd 0000:00:13.2: EHCI Host Controller
[   29.509067] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[   29.509134] ehci_hcd 0000:00:13.2: irq 19, io mem 0xc0002000
[   29.509148] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   29.509265] usb usb3: configuration #1 chosen from 1 choice
[   29.509298] hub 3-0:1.0: USB hub found
[   29.509305] hub 3-0:1.0: 8 ports detected
[   29.522047] SCSI subsystem initialized
[   29.527563] libata version 2.21 loaded.
[   29.614528] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   29.614535] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   29.615338] ATIIXP: IDE controller at PCI slot 0000:00:14.1
[   29.615360] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 16
[   29.615375] ATIIXP: chipset revision 0
[   29.615377] ATIIXP: not 100% native mode: will probe irqs later
[   29.615388]     ide0: BM-DMA at 0x8410-0x8417, BIOS settings: hda:DMA, hdb:pio
[   29.615403]     ide1: BM-DMA at 0x8418-0x841f, BIOS settings: hdc:DMA, hdd:pio
[   29.615413] Probing IDE interface ide0...
[   29.901596] hda: ST960821A, ATA DISK drive
[   30.144955] usb 2-3: new low speed USB device using ohci_hcd and address 2
[   30.353014] usb 2-3: configuration #1 chosen from 1 choice
[   30.546699] 8139too Fast Ethernet driver 0.9.28
[   30.572601] hda: selected mode 0x45
[   30.574477] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   30.797051] Probing IDE interface ide1...
[   31.238005] usbcore: registered new interface driver hiddev
[   31.243594] input: Logitech Optical USB Mouse as /class/input/input2
[   31.243740] input: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:13.1-3
[   31.243755] usbcore: registered new interface driver usbhid
[   31.243759] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   31.532138] hdc: HL-DT-ST DVDRAM GSA-4082N, ATAPI CD/DVD-ROM drive
[   31.867416] hdc: selected mode 0x22
[   31.868329] ide1 at 0x170-0x177,0x376 on irq 15
[   31.872322] ACPI: PCI Interrupt 0000:06:04.2[C] -> GSI 23 (level, low) -> IRQ 23
[   31.923681] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[23]  MMIO=[c0209000-c02097ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   31.923966] ACPI: PCI Interrupt 0000:06:06.0[A] -> GSI 22 (level, low) -> IRQ 22
[   31.925216] eth0: RealTek RTL8139 at 0xffffc20000194400, 00:16:d4:9d:e5:67, IRQ 22
[   31.925221] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   31.927615] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   31.935282] hda: max request size: 512KiB
[   31.935288] hda: 117210240 sectors (60011 MB) w/8192KiB Cache, CHS=16383/255/63, UDMA(100)
[   31.942706] hda: cache flushes supported
[   31.942768]  hda: hda1 hda2 < hda5 hda6 >
[   32.082599] hdc: ATAPI 24X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, DMA
[   32.082610] Uniform CD-ROM driver Revision: 3.20
[   33.692466] Attempting manual resume
[   33.692471] swsusp: Resume From Partition 3:6
[   33.692473] PM: Checking swsusp image.
[   33.789666] PM: Resume from disk failed.
[   34.301276] kjournald starting.  Commit interval 5 seconds
[   34.301289] EXT3-fs: mounted filesystem with ordered data mode.
[  124.960088] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[  124.966605] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[  125.160173] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[  126.464032] ieee80211_crypt: registered algorithm 'NULL'
[  126.466520] ieee80211: 802.11 data/management/control stack, git-1.1.13
[  126.466525] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[  126.564493] bcm43xx driver
[  126.564615] ACPI: PCI Interrupt 0000:06:02.0[A] -> GSI 21 (level, low) -> IRQ 21
[  126.823378] Yenta: CardBus bridge found at 0000:06:04.0 [103c:30a4]
[  126.823406] Yenta: Enabling burst memory read transactions
[  126.823412] Yenta: Using INTVAL to route CSC interrupts to PCI
[  126.823414] Yenta: Routing CardBus interrupts to ISA
[  126.823421] Yenta TI: socket 0000:06:04.0, mfunc 0x00a61b22, devctl 0x64
[  126.924271] sdhci: Secure Digital Host Controller Interface driver
[  126.924276] sdhci: Copyright(c) Pierre Ossman
[  127.062659] Yenta: ISA IRQ mask 0x0cf8, PCI irq 20
[  127.062666] Socket status: 30000006
[  127.062670] pcmcia: parent PCI bridge I/O window: 0xa000 - 0xafff
[  127.062675] pcmcia: parent PCI bridge Memory window: 0xc0200000 - 0xc02fffff
[  127.062678] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x33ffffff
[  127.070145] ACPI: PCI Interrupt 0000:06:04.3[B] -> GSI 23 (level, low) -> IRQ 23
[  127.070724] sdhci: SDHCI controller found at 0000:06:04.4 [104c:8034] (rev 0)
[  127.070748] ACPI: PCI Interrupt 0000:06:04.4[A] -> GSI 20 (level, low) -> IRQ 20
[  127.071085] mmc0: SDHCI at 0xc020a000 irq 20 DMA
[  127.075318] mmc1: SDHCI at 0xc0209c00 irq 20 DMA
[  127.075532] mmc2: SDHCI at 0xc0209800 irq 20 DMA
[  127.085313] ACPI: PCI Interrupt 0000:00:14.6[B] -> GSI 17 (level, low) -> IRQ 17
[  127.193802] MC'97 0 converters and GPIO not ready (0x1)
[  127.394617] input: PC Speaker as /class/input/input3
[  127.637335] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04713/0x200000
[  127.701258] input: SynPS/2 Synaptics TouchPad as /class/input/input4
[  127.754132] ACPI: PCI Interrupt 0000:00:14.5[B] -> GSI 17 (level, low) -> IRQ 17
[  131.051568] lp: driver loaded but no devices found
[  131.163495] Adding 4321444k swap on /dev/hda6.  Priority:-1 extents:1 across:4321444k
[  133.221447] EXT3 FS on hda5, internal journal
[  142.504042] ACPI: AC Adapter [ACAD] (on-line)
[  142.818467] No dock devices found.
[  143.867257] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[  144.298440] ACPI: Battery Slot [BAT1] (battery present)
[  144.541166] input: Power Button (FF) as /class/input/input5
[  144.545964] ACPI: Power Button (FF) [PWRF]
[  144.576566] input: Sleep Button (FF) as /class/input/input6
[  144.581291] ACPI: Sleep Button (FF) [SLPF]
[  144.612003] input: Lid Switch as /class/input/input7
[  144.616745] ACPI: Lid Switch [LID]
[  144.647511] input: Power Button (CM) as /class/input/input8
[  144.652248] ACPI: Power Button (CM) [PWRB]
[  146.970598] powernow-k8: Found 1 AMD Turion(tm) 64 Mobile Technology ML-32 processors (version 2.00.00)
[  146.970641] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x4
[  146.970644] powernow-k8:    1 : fid 0x8 (1600 MHz), vid 0x6
[  146.970646] powernow-k8:    2 : fid 0x0 (800 MHz), vid 0x16
[  146.972519] powernow-k8: ph2 null fid transition 0xa
[  155.586218] eth0: link down
[  155.894687] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  156.365704] ppdev: user-space parallel port driver
[  158.262055] audit(1203671707.268:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5160 profile="/usr/sbin/cupsd"
[  159.121609] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  160.207498] Failure registering capabilities with primary security module.
[  162.106952] Bluetooth: Core ver 2.11
[  162.107065] NET: Registered protocol family 31
[  162.107067] Bluetooth: HCI device and connection manager initialized
[  162.107071] Bluetooth: HCI socket layer initialized
[  162.179342] Bluetooth: L2CAP ver 2.8
[  162.179347] Bluetooth: L2CAP socket layer initialized
[  162.184965] Bluetooth: RFCOMM socket layer initialized
[  162.185048] Bluetooth: RFCOMM TTY layer initialized
[  162.185051] Bluetooth: RFCOMM ver 1.8
[  173.472188] Marking TSC unstable due to possible TSC halt in C2
[  173.472199] Time: acpi_pm clocksource has been installed.
[  174.280259] [drm] Initialized drm 1.1.0 20060810
[  174.300887] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 17 (level, low) -> IRQ 17
[  174.303781] [drm] Initialized radeon 1.27.0 20060524 on minor 0
[  175.852337] [drm] Setting GART location based on new memory map
[  175.852524] [drm] Loading R300 Microcode
[  175.852538] [drm] writeback test succeeded in 1 usecs
[  178.346157] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  191.132179] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  205.889342] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  219.443760] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  231.147996] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  294.682655] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  318.977971] usb 2-3: USB disconnect, address 2
[  335.434856] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[  336.736430] NET: Registered protocol family 17
[  338.659475] NET: Registered protocol family 10
[  338.659613] lo: Disabled Privacy Extensions
[  340.564898] usb 2-3: new low speed USB device using ohci_hcd and address 3
[  340.657376] usb 2-3: configuration #1 chosen from 1 choice
[  340.660561] input: Logitech Optical USB Mouse as /class/input/input9
[  340.660602] input: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:13.1-3
[  343.731093] eth0: no IPv6 routers present
[  349.725057] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  416.259025] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  437.388978] usb 3-4: new high speed USB device using ehci_hcd and address 4
[  437.485223] usb 3-4: configuration #1 chosen from 1 choice
[  437.560433] usbcore: registered new interface driver libusual
[  437.586831] Initializing USB Mass Storage driver...
[  437.587005] scsi0 : SCSI emulation for USB Mass Storage devices
[  437.587112] usb-storage: device found at 4
[  437.587115] usb-storage: waiting for device to settle before scanning
[  437.587243] usbcore: registered new interface driver usb-storage
[  437.587317] USB Mass Storage support registered.
[  439.811344] usb-storage: device scan complete
[  439.811740] scsi 0:0:0:0: Direct-Access     Kingston DataTraveler 2.0 1.00 PQ: 0 ANSI: 2
[  439.839148] sd 0:0:0:0: [sda] 1001472 512-byte hardware sectors (513 MB)
[  439.839645] sd 0:0:0:0: [sda] Write Protect is off
[  439.839648] sd 0:0:0:0: [sda] Mode Sense: 0b 00 00 08
[  439.839651] sd 0:0:0:0: [sda] Assuming drive cache: write through
[  439.843477] sd 0:0:0:0: [sda] 1001472 512-byte hardware sectors (513 MB)
[  439.843921] sd 0:0:0:0: [sda] Write Protect is off
[  439.843924] sd 0:0:0:0: [sda] Mode Sense: 0b 00 00 08
[  439.843926] sd 0:0:0:0: [sda] Assuming drive cache: write through
[  439.843929]  sda: sda1
[  439.845180] sd 0:0:0:0: [sda] Attached SCSI removable disk
[  439.854825] sd 0:0:0:0: Attached scsi generic sg0 type 0
[  484.994259] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  552.591607] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  613.195280] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  669.077377] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  730.011479] usb 3-4: USB disconnect, address 4
[  742.839843] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  824.497218] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

```

---

