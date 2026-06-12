---
title: "usb problem"
date: 2008-03-15
forum: General Help
---

### Post by jakupl on 2008-03-15
When I insert my usb flash pen, it shows up. everything is normal. However, if I remove it and insert it again, it never comes back. I have to reboot the computer every time I need it again.

Does anyone know the solution for this?

---

### Post by dcstar on 2008-03-16
> **jakupl said:**
> When I insert my usb flash pen, it shows up. everything is normal. However, if I remove it and insert it again, it never comes back. I have to reboot the computer every time I need it again.

Does anyone know the solution for this?

Do you unmount it before removing?

Run **dmesg** in a terminal to see what happens when you insert/remove it.

---

### Post by jakupl on 2008-03-16
I tried both... makes no difference if I unmount or not,


I get this :
And I certanly dont understand it.

```
[    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Feb 12 07:42:25 UTC 2008 (Ubuntu 2.6.22-14.52-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000037fd0000 (usable)
[    0.000000]  BIOS-e820: 0000000037fd0000 - 0000000037fde000 (ACPI data)
[    0.000000]  BIOS-e820: 0000000037fde000 - 0000000038000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff780000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 895MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 229328) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229328
[    0.000000]   HighMem    229328 ->   229328
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   229328
[    0.000000] On node 0 totalpages: 229328
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1759 pages used for memmap
[    0.000000]   Normal zone: 223473 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F8290 checksum 0
[    0.000000] ACPI: RSDP 000F8290, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT 37FD0000, 003C (r1 A M I  OEMRSDT   5000625 MSFT       97)
[    0.000000] ACPI: FACP 37FD0200, 0084 (r2 A M I  OEMFACP   5000625 MSFT       97)
[    0.000000] ACPI: DSDT 37FD0460, 6CDF (r1  0AAAA 0AAAAB58      B58 INTL  2002026)
[    0.000000] ACPI: FACS 37FDE000, 0040
[    0.000000] ACPI: APIC 37FD0390, 005C (r1 A M I  OEMAPIC   5000625 MSFT       97)
[    0.000000] ACPI: MCFG 37FD03F0, 003C (r1 A M I  OEMMCFG   5000625 MSFT       97)
[    0.000000] ACPI: BOOT 37FD0430, 0028 (r1 A M I  OEMBOOT   5000625 MSFT       97)
[    0.000000] ACPI: OEMB 37FDE040, 0056 (r1 A M I  AMI_OEM   5000625 MSFT       97)
[    0.000000] ACPI: HPET 37FD7140, 0038 (r1 A M I  OEMHPET   5000625 MSFT       97)
[    0.000000] ATI board detected. Disabling timer routing over 8254.
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:14 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled)
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 21 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x0 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 38000000:c6e00000)
[    0.000000] Built 1 zonelists.  Total pages: 227537
[    0.000000] Kernel command line: root=UUID=c98dfc78-177b-40f9-8013-6aea32a8c3d2 ro quiet splash hpet=disable
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1600.224 MHz processor.
[   25.833343] Console: colour VGA+ 80x25
[   25.834443] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   25.835241] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   25.865031] Memory: 897804k/917312k available (2015k kernel code, 18900k reserved, 915k data, 364k init, 0k highmem)
[   25.865041] virtual kernel memory layout:
[   25.865043]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   25.865044]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   25.865046]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   25.865047]     lowmem  : 0xc0000000 - 0xf7fd0000   ( 895 MB)
[   25.865048]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   25.865050]       .data : 0xc02f7e86 - 0xc03dce84   ( 915 kB)
[   25.865051]       .text : 0xc0100000 - 0xc02f7e86   (2015 kB)
[   25.865055] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   25.865099] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   25.945629] calibrate_delay_direct() failed to get a good estimate for loops_per_jiffy.
[   25.945631] Probably due to long platform interrupts. Consider using "lpj=" boot option.
[   25.945635] Calibrating delay loop... 2695.16 BogoMIPS (lpj=5390336)
[   26.049497] Security Framework v1.0.0 initialized
[   26.049507] SELinux:  Disabled at boot.
[   26.049523] Mount-cache hash table entries: 512
[   26.049666] CPU: After generic identify, caps: afe9fbff 00100000 00000000 00000000 0000c109 00000000 00000000
[   26.049676] monitor/mwait feature present.
[   26.049678] using mwait in idle threads.
[   26.049683] CPU: L1 I cache: 32K, L1 D cache: 32K
[   26.049686] CPU: L2 cache: 1024K
[   26.049689] CPU: After all inits, caps: afe9fbff 00100000 00000000 00002940 0000c109 00000000 00000000
[   26.049700] Compat vDSO mapped to ffffe000.
[   26.049716] Checking 'hlt' instruction... OK.
[   26.065572] SMP alternatives: switching to UP code
[   26.065788] Freeing SMP alternatives: 11k freed
[   26.066082] Early unpacking initramfs... done
[   26.492090] ACPI: Core revision 20070126
[   26.492184] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   26.552746] CPU0: Intel(R) Celeron(R) M CPU        420  @ 1.60GHz stepping 08
[   26.552775] Total of 1 processors activated (2695.16 BogoMIPS).
[   26.552954] ENABLING IO-APIC IRQs
[   26.553142] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   26.691972] Brought up 1 CPUs
[   26.692099] Booting paravirtualized kernel on bare hardware
[   26.692185] Time:  3:39:16  Date: 02/16/108
[   26.692212] NET: Registered protocol family 16
[   26.692310] EISA bus registered
[   26.692328] ACPI: bus type pci registered
[   26.692559] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=3
[   26.692561] PCI: Using configuration type 1
[   26.692564] Setting up standard PCI resources
[   26.696205] ACPI: EC: Look up EC in DSDT
[   26.697102] ACPI: EC: GPE=0x18, ports=0x66, 0x62
[   26.713257] ACPI: Interpreter enabled
[   26.713261] ACPI: (supports S0 S1 S3 S4 S5)
[   26.713284] ACPI: Using IOAPIC for interrupt routing
[   26.721956] ACPI: EC: GPE=0x18, ports=0x66, 0x62
[   26.722091] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   26.722110] PCI: Probing PCI hardware (bus 00)
[   26.723537] PCI: Transparent bridge - 0000:00:14.4
[   26.723658] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   26.723804] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[   26.723950] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
[   26.731345] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[   26.731505] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[   26.731663] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[   26.731820] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[   26.732006] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[   26.732163] ACPI: PCI Interrupt Link [LNKF] (IRQs 9) *0, disabled.
[   26.732317] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[   26.732473] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[   26.732588] Linux Plug and Play Support v0.97 (c) Adam Belay
[   26.732602] pnp: PnP ACPI init
[   26.732610] ACPI: bus type pnp registered
[   26.736050] pnp: PnP ACPI: found 14 devices
[   26.736053] ACPI: ACPI bus type pnp unregistered
[   26.736058] PnPBIOS: Disabled by ACPI PNP
[   26.736112] PCI: Using ACPI for IRQ routing
[   26.736115] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   26.736126] PCI: Cannot allocate resource region 3 of device 0000:00:00.0
[   26.746808] NET: Registered protocol family 8
[   26.746811] NET: Registered protocol family 20
[   26.746884] pnp: 00:07: ioport range 0xa00-0xa0f has been reserved
[   26.746890] pnp: 00:08: iomem range 0xfff80000-0xffffffff could not be reserved
[   26.746904] pnp: 00:0b: iomem range 0xfec00000-0xfec00fff has been reserved
[   26.746907] pnp: 00:0b: iomem range 0xfee00000-0xfee00fff could not be reserved
[   26.746912] pnp: 00:0c: iomem range 0xe0000000-0xefffffff has been reserved
[   26.746917] pnp: 00:0d: iomem range 0x0-0x9ffff could not be reserved
[   26.746920] pnp: 00:0d: iomem range 0xc0000-0xcffff could not be reserved
[   26.746924] pnp: 00:0d: iomem range 0xe0000-0xfffff could not be reserved
[   26.746927] pnp: 00:0d: iomem range 0x100000-0x37ffffff could not be reserved
[   26.747852] Time: tsc clocksource has been installed.
[   26.777190] PCI: Bridge: 0000:00:01.0
[   26.777192]   IO window: 9000-9fff
[   26.777197]   MEM window: fe100000-fe1fffff
[   26.777201]   PREFETCH window: bdf00000-ddefffff
[   26.777215] PCI: Bus 3, cardbus bridge: 0000:02:01.0
[   26.777218]   IO window: 0000a000-0000a0ff
[   26.777224]   IO window: 0000a400-0000a4ff
[   26.777231]   PREFETCH window: 40000000-43ffffff
[   26.777237]   MEM window: 44000000-47ffffff
[   26.777244] PCI: Bridge: 0000:00:14.4
[   26.777247]   IO window: a000-bfff
[   26.777255]   MEM window: fe200000-feafffff
[   26.777261]   PREFETCH window: ddf00000-dfefffff
[   26.777309] ACPI: PCI Interrupt 0000:02:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   26.777328] NET: Registered protocol family 2
[   26.815808] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   26.815995] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   26.818968] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   26.820263] TCP: Hash tables configured (established 131072 bind 65536)
[   26.820269] TCP reno registered
[   26.831979] checking if image is initramfs... it is
[   27.279087] Switched to high resolution mode on CPU 0
[   27.557663] Freeing initrd memory: 7056k freed
[   27.557877] Simple Boot Flag at 0xff set to 0x1
[   27.558276] audit: initializing netlink socket (disabled)
[   27.558299] audit(1205638756.220:1): initialized
[   27.560401] VFS: Disk quotas dquot_6.5.1
[   27.560457] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   27.560576] io scheduler noop registered
[   27.560578] io scheduler anticipatory registered
[   27.560581] io scheduler deadline registered
[   27.560597] io scheduler cfq registered (default)
[   27.610586] Boot video device is 0000:01:05.0
[   27.610774] isapnp: Scanning for PnP cards...
[   27.909303] isapnp: No Plug & Play device found
[   27.937944] Real Time Clock Driver v1.12ac
[   27.938142] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   27.938461] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   27.939694] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   27.939972] input: Macintosh mouse button emulation as /class/input/input0
[   27.940062] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   27.943032] i8042.c: Detected active multiplexing controller, rev 1.1.
[   27.943690] serio: i8042 KBD port at 0x60,0x64 irq 1
[   27.943697] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   27.943699] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   27.943702] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   27.943705] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   27.943928] mice: PS/2 mouse device common for all mice
[   27.944130] EISA: Probing bus 0 at eisa.0
[   27.944157] Cannot allocate resource for EISA slot 4
[   27.944178] EISA: Detected 0 cards.
[   27.944316] TCP cubic registered
[   27.944334] NET: Registered protocol family 1
[   27.944365] Using IPI No-Shortcut mode
[   27.944574]   Magic number: 0:630:664
[   27.944698]   hash matches device ptyef
[   27.945269] Freeing unused kernel memory: 364k freed
[   28.056542] input: AT Translated Set 2 keyboard as /class/input/input1
[   29.148890] AppArmor: AppArmor initialized<5>audit(1205638757.720:2):  type=1505 info="AppArmor initialized" pid=1204
[   29.157673] fuse init (API version 7.8)
[   29.163507] Failure registering capabilities with primary security module.
[   29.179835] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   29.179842] ACPI: Processor [CPU1] (supports 8 throttling states)
[   29.179856] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[    3.156000] Marking TSC unstable due to: possible TSC halt in C2.
[    3.156000] ACPI: Thermal Zone [THRM] (66 C)
[    3.160000] Time: acpi_pm clocksource has been installed.
[    3.632000] usbcore: registered new interface driver usbfs
[    3.632000] usbcore: registered new interface driver hub
[    3.632000] usbcore: registered new device driver usb
[    3.632000] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.632000] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 17
[    3.632000] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    3.632000] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[    3.632000] ohci_hcd 0000:00:13.0: irq 17, io mem 0xfebff000
[    3.692000] SCSI subsystem initialized
[    3.696000] libata version 2.21 loaded.
[    3.704000] usb usb1: configuration #1 chosen from 1 choice
[    3.704000] hub 1-0:1.0: USB hub found
[    3.704000] hub 1-0:1.0: 4 ports detected
[    3.808000] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 17
[    3.808000] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    3.808000] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[    3.808000] ohci_hcd 0000:00:13.1: irq 17, io mem 0xfebfe000
[    3.816000] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    3.864000] usb usb2: configuration #1 chosen from 1 choice
[    3.864000] hub 2-0:1.0: USB hub found
[    3.864000] hub 2-0:1.0: 4 ports detected
[    3.968000] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 17
[    3.968000] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    3.968000] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[    3.968000] ehci_hcd 0000:00:13.2: irq 17, io mem 0xfebfd000
[    4.112000] usb 1-1: new full speed USB device using ohci_hcd and address 2
[    4.112000] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.112000] usb usb3: configuration #1 chosen from 1 choice
[    4.112000] hub 3-0:1.0: USB hub found
[    4.112000] hub 3-0:1.0: 8 ports detected
[    4.220000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    4.220000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    4.220000] ATIIXP: IDE controller at PCI slot 0000:00:14.1
[    4.220000] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 16
[    4.220000] ATIIXP: chipset revision 128
[    4.220000] ATIIXP: not 100% native mode: will probe irqs later
[    4.220000]     ide0: BM-DMA at 0xff00-0xff07, BIOS settings: hda:DMA, hdb:pio
[    4.220000]     ide1: BM-DMA at 0xff08-0xff0f, BIOS settings: hdc:pio, hdd:DMA
[    4.220000] Probing IDE interface ide0...
[    4.508000] hda: ST980829A, ATA DISK drive
[    4.796000] usb 3-1: new high speed USB device using ehci_hcd and address 2
[    4.928000] usb 3-1: configuration #1 chosen from 1 choice
[    5.180000] hda: selected mode 0x45
[    5.180000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[    5.180000] Probing IDE interface ide1...
[    5.352000] usb 3-5: new high speed USB device using ehci_hcd and address 4
[    5.484000] usb 3-5: configuration #1 chosen from 1 choice
[    5.496000] usbcore: registered new interface driver libusual
[    5.508000] Initializing USB Mass Storage driver...
[    5.788000] usb 1-2: new low speed USB device using ohci_hcd and address 3
[    5.992000] usb 1-2: configuration #1 chosen from 1 choice
[    6.008000] usbcore: registered new interface driver hiddev
[    6.012000] scsi0 : SCSI emulation for USB Mass Storage devices
[    6.012000] usb-storage: device found at 2
[    6.012000] usb-storage: waiting for device to settle before scanning
[    6.012000] input: Logitech Optical USB Mouse as /class/input/input2
[    6.012000] input: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:13.0-2
[    6.012000] usbcore: registered new interface driver usbhid
[    6.012000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[    6.016000] usbcore: registered new interface driver usb-storage
[    6.016000] USB Mass Storage support registered.
[    6.192000] hdd: MATSHITADVD-RAM UJ-841S, ATAPI CD/DVD-ROM drive
[    6.248000] hdd: selected mode 0x42
[    6.248000] ide1 at 0x170-0x177,0x376 on irq 15
[    6.248000] 8139cp 0000:02:00.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[    6.248000] 8139cp 0000:02:00.0: Try the "8139too" driver instead.
[    6.252000] 8139too Fast Ethernet driver 0.9.28
[    6.252000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 20 (level, low) -> IRQ 18
[    6.252000] eth0: RealTek RTL8139 at 0xf8844c00, 00:17:31:c8:ba:44, IRQ 18
[    6.252000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[    6.260000] hda: max request size: 512KiB
[    6.272000] hda: 156301488 sectors (80026 MB) w/8192KiB Cache, CHS=16383/255/63, UDMA(100)
[    6.272000] hda: cache flushes supported
[    6.272000]  hda: hda1 hda2 < hda5 >
[    6.332000] hdd: ATAPI 24X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
[    6.332000] Uniform CD-ROM driver Revision: 3.20
[    6.592000] Attempting manual resume
[    6.592000] swsusp: Resume From Partition 3:5
[    6.592000] PM: Checking swsusp image.
[    6.592000] PM: Resume from disk failed.
[    6.608000] EXT3-fs: INFO: recovery required on readonly filesystem.
[    6.608000] EXT3-fs: write access will be enabled during recovery.
[    7.568000] kjournald starting.  Commit interval 5 seconds
[    7.568000] EXT3-fs: hda1: orphan cleanup on readonly fs
[    7.568000] ext3_orphan_cleanup: deleting unreferenced inode 966837
[    7.568000] ext3_orphan_cleanup: deleting unreferenced inode 9257259
[    7.568000] EXT3-fs: hda1: 2 orphan inodes deleted
[    7.568000] EXT3-fs: recovery complete.
[    7.572000] EXT3-fs: mounted filesystem with ordered data mode.
[   11.012000] usb-storage: device scan complete
[   11.012000] scsi 0:0:0:0: Direct-Access     Imation   USB Flash Drive 2.00 PQ: 0 ANSI: 2
[   14.404000] ip_tables: (C) 2000-2006 Netfilter Core Team
[   14.432000] Netfilter messages via NETLINK v0.30.
[   14.448000] nf_conntrack version 0.5.0 (7166 buckets, 57328 max)
[   16.432000] Linux agpgart interface v0.102 (c) Dave Jones
[   16.444000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   16.448000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   16.588000] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[   16.852000] Yenta: CardBus bridge found at 0000:02:01.0 [1043:1397]
[   16.984000] Yenta: ISA IRQ mask 0x0eb8, PCI irq 16
[   16.984000] Socket status: 30000006
[   16.984000] Yenta: Raising subordinate bus# of parent bus (#02) from #03 to #06
[   16.984000] pcmcia: parent PCI bridge I/O window: 0xa000 - 0xbfff
[   16.984000] cs: IO port probe 0xa000-0xbfff: clean.
[   16.984000] pcmcia: parent PCI bridge Memory window: 0xfe200000 - 0xfeafffff
[   16.984000] pcmcia: parent PCI bridge Memory window: 0xddf00000 - 0xdfefffff
[   17.120000] ieee80211_crypt: registered algorithm 'NULL'
[   17.476000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   17.476000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   17.548000] sdhci: Secure Digital Host Controller Interface driver
[   17.548000] sdhci: Copyright(c) Pierre Ossman
[   17.548000] sdhci: SDHCI controller found at 0000:02:01.1 [1180:0822] (rev 17)
[   17.548000] ACPI: PCI Interrupt 0000:02:01.1[C] -> GSI 18 (level, low) -> IRQ 19
[   17.548000] mmc0: SDHCI at 0xfeaff800 irq 19 DMA
[   17.756000] bcm43xx driver
[   17.756000] ACPI: PCI Interrupt 0000:02:03.0[A] -> GSI 22 (level, low) -> IRQ 20
[   17.992000] input: PC Speaker as /class/input/input3
[   18.020000] sd 0:0:0:0: [sda] 4052992 512-byte hardware sectors (2075 MB)
[   18.032000] sd 0:0:0:0: [sda] Write Protect is off
[   18.032000] sd 0:0:0:0: [sda] Mode Sense: 03 00 00 00
[   18.032000] sd 0:0:0:0: [sda] Assuming drive cache: write through
[   18.100000] sd 0:0:0:0: [sda] 4052992 512-byte hardware sectors (2075 MB)
[   18.100000] sd 0:0:0:0: [sda] Write Protect is off
[   18.100000] sd 0:0:0:0: [sda] Mode Sense: 03 00 00 00
[   18.100000] sd 0:0:0:0: [sda] Assuming drive cache: write through
[   18.100000]  sda: sda1
[   18.104000] sd 0:0:0:0: [sda] Attached SCSI removable disk
[   18.128000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   18.240000] irda_init()
[   18.240000] NET: Registered protocol family 23
[   18.264000] Synaptics Touchpad, model: 1, fw: 6.1, id: 0xa3a0b3, caps: 0xa04713/0x10008
[   18.316000] input: SynPS/2 Synaptics TouchPad as /class/input/input4
[   18.320000] parport_pc 00:06: reported by Plug and Play ACPI
[   18.320000] parport0: PC-style at 0x378, irq 7 [PCSPP,EPP]
[   18.472000] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 16
[   18.504000] cs: IO port probe 0x100-0x3af: clean.
[   18.504000] cs: IO port probe 0x3e0-0x4ff: excluding 0x408-0x40f 0x4d0-0x4d7
[   18.508000] cs: IO port probe 0x820-0x8ff: excluding 0x830-0x837
[   18.508000] cs: IO port probe 0xc00-0xcf7: excluding 0xc00-0xc07 0xc10-0xc17 0xc50-0xc57 0xc68-0xc6f 0xcd0-0xcdf
[   18.508000] cs: IO port probe 0xa00-0xaff: clean.
[   19.328000] lp0: using parport0 (interrupt-driven).
[   19.412000] Adding 2650684k swap on /dev/hda5.  Priority:-1 extents:1 across:2650684k
[   19.824000] EXT3 FS on hda1, internal journal
[   20.848000] ACPI: Battery Slot [BAT0] (battery present)
[   21.048000] ACPI: AC Adapter [AC0] (on-line)
[   21.068000] Asus Laptop ACPI Extras version 0.30
[   21.068000]   BSTS called, 0x7f returned
[   21.068000]   unsupported model A6Rp, trying default values
[   21.068000]   send /proc/acpi/dsdt to the developers
[   21.108000] No dock devices found.
[   21.164000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   21.260000] input: Power Button (FF) as /class/input/input5
[   21.264000] ACPI: Power Button (FF) [PWRF]
[   21.304000] input: Lid Switch as /class/input/input6
[   21.308000] ACPI: Lid Switch [LID]
[   21.352000] input: Power Button (CM) as /class/input/input7
[   21.356000] ACPI: Power Button (CM) [PWRB]
[   21.400000] input: Sleep Button (CM) as /class/input/input8
[   21.404000] ACPI: Sleep Button (CM) [SLPB]
[   22.648000] ppdev: user-space parallel port driver
[   22.776000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   23.308000] audit(1205638778.999:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4924 profile="/usr/sbin/cupsd"
[   23.352000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   23.352000] apm: overridden by ACPI.
[   24.160000] Failure registering capabilities with primary security module.
[   24.320000] Bluetooth: Core ver 2.11
[   24.320000] NET: Registered protocol family 31
[   24.320000] Bluetooth: HCI device and connection manager initialized
[   24.320000] Bluetooth: HCI socket layer initialized
[   24.332000] Bluetooth: L2CAP ver 2.8
[   24.332000] Bluetooth: L2CAP socket layer initialized
[   24.420000] Bluetooth: RFCOMM socket layer initialized
[   24.420000] Bluetooth: RFCOMM TTY layer initialized
[   24.420000] Bluetooth: RFCOMM ver 1.8
[   25.888000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   25.892000] [fglrx] Maximum main memory to use for locked dma buffers: 804 MBytes.
[   25.892000] [fglrx] module loaded - fglrx 8.37.6 [May 25 2007] on minor 0
[   25.916000] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 17 (level, low) -> IRQ 22
[   27.676000] [fglrx] total      GART = 130023424
[   27.676000] [fglrx] free       GART = 114032640
[   27.676000] [fglrx] max single GART = 114032640
[   27.676000] [fglrx] total      LFB  = 134217728
[   27.676000] [fglrx] free       LFB  = 119828480
[   27.676000] [fglrx] max single LFB  = 119828480
[   27.676000] [fglrx] total      Inv  = 0
[   27.676000] [fglrx] free       Inv  = 0
[   27.676000] [fglrx] max single Inv  = 0
[   27.676000] [fglrx] total      TIM  = 0
[   28.848000] NET: Registered protocol family 17
[   33.468000] hda-intel: Invalid position buffer, using LPIB read method instead.
[   34.944000] NET: Registered protocol family 10
[   34.944000] lo: Disabled Privacy Extensions
[   34.944000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   45.156000] eth0: no IPv6 routers present
[  726.340000] usb 3-1: USB disconnect, address 2
[  726.340000] Buffer I/O error on device sda1, logical block 1502105
[  726.340000] lost page write due to I/O error on sda1
[  726.340000] Buffer I/O error on device sda1, logical block 504
[  726.340000] lost page write due to I/O error on sda1
[  753.648000] usb 3-1: new high speed USB device using ehci_hcd and address 5
[  753.792000] usb 3-1: configuration #1 chosen from 1 choice
[  753.792000] scsi1 : SCSI emulation for USB Mass Storage devices
[  753.792000] usb-storage: device found at 5
[  753.792000] usb-storage: waiting for device to settle before scanning
[  758.792000] usb-storage: device scan complete
[  758.792000] scsi 1:0:0:0: Direct-Access     Imation   USB Flash Drive 2.00 PQ: 0 ANSI: 2
[  762.496000] ready
[  762.500000] sd 1:0:0:0: [sda] 4052992 512-byte hardware sectors (2075 MB)
[  762.500000] sd 1:0:0:0: [sda] Write Protect is off
[  762.500000] sd 1:0:0:0: [sda] Mode Sense: 03 00 00 00
[  762.500000] sd 1:0:0:0: [sda] Assuming drive cache: write through
[  762.512000] sd 1:0:0:0: [sda] 4052992 512-byte hardware sectors (2075 MB)
[  762.516000] sd 1:0:0:0: [sda] Write Protect is off
[  762.516000] sd 1:0:0:0: [sda] Mode Sense: 03 00 00 00
[  762.516000] sd 1:0:0:0: [sda] Assuming drive cache: write through
[  762.516000]  sda: sda1
[  762.516000] sd 1:0:0:0: [sda] Attached SCSI removable disk
[  762.516000] sd 1:0:0:0: Attached scsi generic sg0 type 0
[  905.296000] eth0: no IPv6 routers present
[  946.004000] SoftMAC: Authentication timed out with 00:09:5b:fe:52:de
[ 2589.768000] ppdev0: registered pardevice
[ 2589.768000] ppdev0: unregistered pardevice
[ 2590.360000] ppdev0: registered pardevice
[ 2590.412000] ppdev0: unregistered pardevice
[ 4047.708000] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:30:6e:be:5e:00:08:00 SRC=10.0.51.251 DST=10.0.40.0 LEN=48 TOS=0x00 PREC=0x00 TTL=127 ID=52739 DF PROTO=TCP SPT=3583 DPT=445 WINDOW=65535 RES=0x00 SYN URGP=0 
[ 4048.208000] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:30:6e:be:5e:00:08:00 SRC=10.0.51.251 DST=10.0.40.0 LEN=48 TOS=0x00 PREC=0x00 TTL=127 ID=52743 DF PROTO=TCP SPT=3583 DPT=445 WINDOW=65535 RES=0x00 SYN URGP=0 
[ 4048.708000] Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:30:6e:be:5e:00:08:00 SRC=10.0.51.251 DST=10.0.40.0 LEN=48 TOS=0x00 PREC=0x00 TTL=127 ID=52748 DF PROTO=TCP SPT=3583 DPT=445 WINDOW=65535 RES=0x00 SYN URGP=0 
[ 4752.096000] Inbound IN=eth0 OUT= MAC=00:17:31:c8:ba:44:00:30:6e:be:5e:00:08:00 SRC=10.0.51.251 DST=10.0.43.241 LEN=48 TOS=0x00 PREC=0x00 TTL=127 ID=55874 DF PROTO=TCP SPT=4615 DPT=445 WINDOW=65535 RES=0x00 SYN URGP=0 
[ 4755.096000] Inbound IN=eth0 OUT= MAC=00:17:31:c8:ba:44:00:30:6e:be:5e:00:08:00 SRC=10.0.51.251 DST=10.0.43.241 LEN=48 TOS=0x00 PREC=0x00 TTL=127 ID=55889 DF PROTO=TCP SPT=4615 DPT=445 WINDOW=65535 RES=0x00 SYN URGP=0 
[ 4761.104000] Inbound IN=eth0 OUT= MAC=00:17:31:c8:ba:44:00:30:6e:be:5e:00:08:00 SRC=10.0.51.251 DST=10.0.43.241 LEN=48 TOS=0x00 PREC=0x00 TTL=127 ID=55926 DF PROTO=TCP SPT=4615 DPT=445 WINDOW=65535 RES=0x00 SYN URGP=0 

```

---

### Post by jakupl on 2008-03-16
anyone??

---

### Post by happyhamster on 2008-03-16
- Could you show the output of:

lsusb

cat /proc/interrupts

- both when the usb pen is recognised and when not recognised (but connected). Also, it helps to issue:

tail -f /var/log/messages

- before the pen is connected and see what it outputs when the pen is connected, removed and connected again. Also, after that procedure (the pen isn't recognised anymore), could you show the output of:

dmesg | grep irq -i

---

### Post by jakupl on 2008-03-16
thankyou.

usb connected and recognised:

```
jakup@bobby:~$ lsusb
Bus 003 Device 002: ID 0718:0069 Imation Corp. 
Bus 003 Device 004: ID 174f:a311  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 001 Device 001: ID 0000:0000 
``` 
```

jakup@bobby:~$ cat /proc/interrupts
           CPU0       
  0:       7315   IO-APIC-edge      timer
  1:        107   IO-APIC-edge      i8042
  7:          0   IO-APIC-edge      parport0
  8:          3   IO-APIC-edge      rtc
 12:        136   IO-APIC-edge      i8042
 14:       7633   IO-APIC-edge      ide0
 15:        350   IO-APIC-edge      ide1
 16:        907   IO-APIC-fasteoi   yenta, HDA Intel
 17:       2910   IO-APIC-fasteoi   ohci_hcd:usb1, ohci_hcd:usb2, ehci_hcd:usb3
 18:        116   IO-APIC-fasteoi   eth0
 19:          0   IO-APIC-fasteoi   sdhci:slot0
 20:       1794   IO-APIC-fasteoi   bcm43xx
 21:        501   IO-APIC-fasteoi   acpi
 22:       5317   IO-APIC-fasteoi   fglrx
NMI:          0 
LOC:      10033 
ERR:          0
MIS:          0
```

-----------------------------------




usb connected but NOT recognised:

```
jakup@bobby:~$ lsusb
Bus 003 Device 005: ID 0718:0069 Imation Corp. 
Bus 003 Device 004: ID 174f:a311  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 001 Device 001: ID 0000:0000  
```
```

jakup@bobby:~$ cat /proc/interrupts
           CPU0       
  0:      18055   IO-APIC-edge      timer
  1:        277   IO-APIC-edge      i8042
  7:          0   IO-APIC-edge      parport0
  8:          3   IO-APIC-edge      rtc
 12:        136   IO-APIC-edge      i8042
 14:       7992   IO-APIC-edge      ide0
 15:        908   IO-APIC-edge      ide1
 16:        907   IO-APIC-fasteoi   yenta, HDA Intel
 17:       7906   IO-APIC-fasteoi   ohci_hcd:usb1, ohci_hcd:usb2, ehci_hcd:usb3
 18:        195   IO-APIC-fasteoi   eth0
 19:          0   IO-APIC-fasteoi   sdhci:slot0
 20:       5456   IO-APIC-fasteoi   bcm43xx
 21:        635   IO-APIC-fasteoi   acpi
 22:      16512   IO-APIC-fasteoi   fglrx
NMI:          0 
LOC:      13077 
ERR:          0
MIS:          0
```


---------------------------------------------

(I reboot the computer.)

Before I connect the usb:

```
jakup@bobby:~$ tail -f /var/log/messages
Mar 16 21:02:02 bobby kernel: [   26.808000] [fglrx] max single Inv  = 0
Mar 16 21:02:02 bobby kernel: [   26.808000] [fglrx] total      TIM  = 0
Mar 16 21:02:03 bobby kernel: [   27.624000] NET: Registered protocol family 17
Mar 16 21:02:08 bobby dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Mar 16 21:02:08 bobby dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Mar 16 21:02:08 bobby dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Mar 16 21:02:08 bobby kernel: [   32.592000] hda-intel: Invalid position buffer, using LPIB read method instead.
Mar 16 21:02:10 bobby kernel: [   34.548000] NET: Registered protocol family 10
Mar 16 21:02:10 bobby kernel: [   34.548000] lo: Disabled Privacy Extensions
Mar 16 21:02:10 bobby kernel: [   34.548000] ADDRCONF(NETDEV_UP): eth1: link is not ready

```
------------------------------------------------


usb connected and recognised:

```
jakup@bobby:~$ tail -f /var/log/messages
Mar 16 21:05:14 bobby kernel: [  218.320000] USB Mass Storage support registered.
Mar 16 21:05:19 bobby kernel: [  223.320000] scsi 0:0:0:0: Direct-Access     Imation   USB Flash Drive 2.00 PQ: 0 ANSI: 2
Mar 16 21:05:22 bobby kernel: [  227.020000] ready
Mar 16 21:05:22 bobby kernel: [  227.020000] sd 0:0:0:0: [sda] 4052992 512-byte hardware sectors (2075 MB)
Mar 16 21:05:22 bobby kernel: [  227.020000] sd 0:0:0:0: [sda] Write Protect is off
Mar 16 21:05:22 bobby kernel: [  227.024000] sd 0:0:0:0: [sda] 4052992 512-byte hardware sectors (2075 MB)
Mar 16 21:05:22 bobby kernel: [  227.024000] sd 0:0:0:0: [sda] Write Protect is off
Mar 16 21:05:22 bobby kernel: [  227.024000]  sda: sda1
Mar 16 21:05:22 bobby kernel: [  227.024000] sd 0:0:0:0: [sda] Attached SCSI removable disk
Mar 16 21:05:22 bobby kernel: [  227.044000] sd 0:0:0:0: Attached scsi generic sg0 type 0

```


--------------------------------------------------


usb connected but NOT recognised:

```
jakup@bobby:~$ tail -f /var/log/messages
Mar 16 21:06:37 bobby kernel: [  301.156000] scsi1 : SCSI emulation for USB Mass Storage devices
Mar 16 21:06:41 bobby kernel: [  306.156000] scsi 1:0:0:0: Direct-Access     Imation   USB Flash Drive 2.00 PQ: 0 ANSI: 2
Mar 16 21:06:46 bobby kernel: [  310.336000] ready
Mar 16 21:06:46 bobby kernel: [  310.340000] sd 1:0:0:0: [sda] 4052992 512-byte hardware sectors (2075 MB)
Mar 16 21:06:46 bobby kernel: [  310.340000] sd 1:0:0:0: [sda] Write Protect is off
Mar 16 21:06:46 bobby kernel: [  310.340000] sd 1:0:0:0: [sda] 4052992 512-byte hardware sectors (2075 MB)
Mar 16 21:06:46 bobby kernel: [  310.340000] sd 1:0:0:0: [sda] Write Protect is off
Mar 16 21:06:46 bobby kernel: [  310.340000]  sda: sda1
Mar 16 21:06:46 bobby kernel: [  310.344000] sd 1:0:0:0: [sda] Attached SCSI removable disk
Mar 16 21:06:46 bobby kernel: [  310.344000] sd 1:0:0:0: Attached scsi generic sg0 type 0
```

```
jakup@bobby:~$ dmesg | grep irq -i
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 21 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[   23.094016] ENABLING IO-APIC IRQs
[   23.271923] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[   23.272083] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[   23.272240] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[   23.272397] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[   23.272583] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[   23.272740] ACPI: PCI Interrupt Link [LNKF] (IRQs 9) *0, disabled.
[   23.272894] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[   23.273050] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[   23.276689] PCI: Using ACPI for IRQ routing
[   23.276692] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   23.317894] ACPI: PCI Interrupt 0000:02:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   24.478179] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   24.478486] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   24.480145] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   24.483753] serio: i8042 KBD port at 0x60,0x64 irq 1
[   24.483761] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   24.483763] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   24.483766] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   24.483769] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    3.612000] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 17
[    3.612000] ohci_hcd 0000:00:13.0: irq 17, io mem 0xfebff000
[    3.796000] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 17
[    3.796000] ohci_hcd 0000:00:13.1: irq 17, io mem 0xfebfe000
[    3.956000] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 17
[    3.956000] ehci_hcd 0000:00:13.2: irq 17, io mem 0xfebfd000
[    4.208000] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 16
[    4.208000] ATIIXP: not 100% native mode: will probe irqs later
[    5.168000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[    6.236000] ide1 at 0x170-0x177,0x376 on irq 15
[    6.240000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 20 (level, low) -> IRQ 18
[    6.240000] eth0: RealTek RTL8139 at 0xf8844c00, 00:17:31:c8:ba:44, IRQ 18
[   17.000000] parport0: PC-style at 0x378, irq 7 [PCSPP,EPP]
[   17.140000] Yenta: ISA IRQ mask 0x0e38, PCI irq 16
[   17.144000] ACPI: PCI Interrupt 0000:02:03.0[A] -> GSI 22 (level, low) -> IRQ 19
[   17.272000] ACPI: PCI Interrupt 0000:02:01.1[C] -> GSI 18 (level, low) -> IRQ 20
[   17.272000] mmc0: SDHCI at 0xfeaff800 irq 20 DMA
[   17.548000] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 16
[   25.060000] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 17 (level, low) -> IRQ 22

```

I think that should be it??

---

### Post by happyhamster on 2008-03-16
Weird. It appears to be recognised by the system in both cases. Perhaps it just isn't mounted. You can check with:

mount

It should show a line about sda1 looking somewhat like this (just an example):

/dev/sda1 on /media/disk type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077,usefree)

- Could you show the output of 'mount' when the pendrive doesn't work.
- Also: try if the problem goes away when using another usb port.
- And a question: are you using a laptop (with webcam)?

---

### Post by jakupl on 2008-03-16
```
jakup@bobby:~$ mount
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)

```

the usb was inserted when I got this.

The problem does not go away when I use another port.

and yeah :) I have an ASUS A6Rp labtop with inbuilt webcam. but I dont know if it works.

What an irritating problem :confused:](*,)

---

### Post by jakupl on 2008-03-17
:-({|=:-\"

---

### Post by jakupl on 2008-03-17
help help help

---

### Post by happyhamster on 2008-03-17
- Ok, try mounting the pendrive manually. Make a temporary folder called 'test' in your home dir, make sure the pendrive is connected, and then try:

sudo mount -t auto /dev/sda1 ~/test

- If that doesn't work, could you show the error(s) you get. 

BTW. to unmount, do: sudo umount ~/test

---

### Post by jakupl on 2008-03-17
This works! thanks. A nice temporary solution.
But what is wrong then? why doesn't it launch automatically ?

---

### Post by happyhamster on 2008-03-17
I don't know. It seems the hardware is recognised, but the drive just isn't mounted. Perhaps it's a module issue: a software module that works fine the first try, but isn't 'deactivated' properly or something (just a wild guess without knowing if that's even possible). Anyway, if you want to manually mount the drive as a workaround, then the way to do it properly is by adding a few parameters (allowing you to access the files on the drive as a regular user instead of root for example).

- Allow the drive to be auto-mounted by the system (after a reboot), and issue:

mount

- It will show a line for the pendrive looking somewhat like this (example from one of my own pendrives):

/dev/sda1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)

- So the full line to manually mount it would be:
```

sudo mount -t vfat -o 
rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,iocharset=utf8,umask=077,flush /dev/sda1 ~/test
```

- And I would probably mount it in the mnt folder (instead of my home folder):

sudo mkdir /mnt/pendrive

```

sudo mount -t vfat -o 
rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,iocharset=utf8,umask=077,flush /dev/sda1 /mnt/pendrive

```

- And to unmount:

sudo umount /mnt/pendrive

- Good luck, and if you have trouble, could you show the output of 'mount' here?

---

### Post by jakupl on 2008-03-17
```
mount: special device /dev/sda1 does not exist
```

```
jakup@bobby:~$ mount
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
/dev/sda1 on /media/USB type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077,usefree)

```

this is all while the usb is not registred

---

### Post by happyhamster on 2008-03-17
Ok, then it should mount properly on the chosen folder, using:

```

sudo mount -t vfat -o 
rw,nosuid,nodev,shortname=mixed,uid=1000,iocharset=utf8,umask=077,usefree /dev/sda1 ~/test
```

Instead of ~/test use the folder of your liking, but make sure that folder exists (and that it's empty to avoid complications). The advantage of mounting it to a folder in the /mnt or /media map is that the device's icon will show up on your desktop IIRC.

> 
mount: special device /dev/sda1 does not exist
I don't really understand: when did you get that message exactly?

---

### Post by DorianX on 2008-04-13
I'm having exactly this issue.  I get this dmesg when I connect the drive:

> 
Apr 13 23:35:41 saxon kernel: [66867.018754] usb 11-3: new high speed USB device using ehci_hcd and address 6
Apr 13 23:35:41 saxon kernel: [66867.153238] usb 11-3: configuration #1 chosen from 1 choice
Apr 13 23:35:41 saxon kernel: [66867.153480] scsi23 : SCSI emulation for USB Mass Storage devices
Apr 13 23:35:46 saxon kernel: [66872.146547] scsi 23:0:0:0: Direct-Access              USB FLASH DRIVE  PMAP PQ: 0 ANSI: 0 CCS
Apr 13 23:35:46 saxon kernel: [66872.370720] sd 23:0:0:0: [sdb] 2015232 512-byte hardware sectors (1032 MB)
Apr 13 23:35:46 saxon kernel: [66872.371584] sd 23:0:0:0: [sdb] Write Protect is off
Apr 13 23:35:46 saxon kernel: [66872.373711] sd 23:0:0:0: [sdb] 2015232 512-byte hardware sectors (1032 MB)
Apr 13 23:35:46 saxon kernel: [66872.374478] sd 23:0:0:0: [sdb] Write Protect is off
Apr 13 23:35:46 saxon kernel: [66872.374493]  sdb: sdb1
Apr 13 23:35:46 saxon kernel: [66872.375294] sd 23:0:0:0: [sdb] Attached SCSI removable disk
Apr 13 23:35:46 saxon kernel: [66872.375347] sd 23:0:0:0: Attached scsi generic sg2 type 0



But when I try to mount it:

> 
$sudo mount /dev/sdb1 /media/disk
mount: special device /dev/sdb1 does not exist


I've tried removing and reinserting usbcore and usb-storage, I've tried restarting hal and udev, but rebooting is the only thing that has restored things.  It seems almost as if the device functions properly for a moment, but then disconnects immediately.

One of the flash drives I've tried has an LED light on it which normally blinks whenever the drive is in use. It flashes briefly while messages are being printed to dmesg, then goes out.

This is, I think, the relevant part of the output of lshw:

> 
     *-scsi
          physical id: 1
          bus info: usb@11:3
          logical name: scsi24
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk UNCLAIMED
             description: SCSI Disk
             product: USB FLASH DRIVE
             physical id: 0.0.0
             bus info: scsi@24:0.0.0
             version: PMAP
             capabilities: removable


---

### Post by jakupl on 2008-04-14
After I upgraded to Hardy beta, the problem dissapeared.

---

### Post by smo0th on 2008-04-19
hi there,

I have the same problem, I had to restart the pc in order to get my usb drives working back, it's kinda annoying and if my idea works for you it'll be a good enough workaround to do the following when we have the USB devices working:
```
sudo fdisk -l
```
take note of the usb drive location (/dev/sdc1 or something similar) and just for reference
```
ls /media
```
to get the name of the drive assignment (/media/MyFlashDrive for example)

whenever we get bugged we could try forcing the mount:
```
sudo mount /dev/sdc1 /media/MyUSB -o force
```

hope this helps.

---

### Post by smo0th on 2008-04-21
I just tried it :lolflag: but it doesn't work, the hardware just does not get recognized :(

---

### Post by DorianX on 2008-04-21
As a temporary workaround, I've found that if I leave a spare USB drive plugged in all the time, the bug doesn't seem to manifes: it looks like the problem only shows up after a certain period of inactivity on the USB system.

---

### Post by smo0th on 2008-05-06
I agree with DorianX, I've been running 5 days with a USB drive always in and mounted, did several tests and tried some weird stuff, the problem arises when you unmount the USB drive and at some times it may be immediate(right after you unmount the USB drive) or delayed(after some time period).

So, as DorianX says, in the meantime we should get a cheap USB spare fixed drive! =)

---

