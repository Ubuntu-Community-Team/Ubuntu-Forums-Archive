---
title: "Really need help with mounting usb sticks"
date: 2008-07-02
forum: General Help
---

### Post by coggz on 2008-07-02
Hi all,
I'm unable to mount ANY sort of usb removeable dri```

```ve. I have tried many memorysticks, a external hard drive, a hard drive video camera and a usb card reader.
When I try to mount in dolphin or in a terminal I get this message:

```
mount: wrong fs type, bad option, bad superblock on /dev/hda5,
missing codepage or other error
In some cases useful info is found in syslog - try
dmesg | tail or so
```

I can mount these drives as root however, so it is not the computer.

I am using Kubuntu 7.10 on an Acer TravelMate C110, If you require any more information, please just ask...

Luke

---

### Post by pytheas22 on 2008-07-02
> I can mount these drives as root however, so it is not the computer.

What do you mean by you can mount them as root?  Are you trying to mount without using sudo?

Please try to mount the disk and then run the command:
```

dmesg
```

and post the output here.

---

### Post by coggz on 2008-07-02
Yes, without sudo in terminal, and I presume not in dolphin either then...
Here you go dmesg as requested, thanks!

```
[    0.000000] Linux version 2.6.22-15-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Jun 10 09:21:34 UTC 2008 (Ubuntu 2.6.22-15.54-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000ce000 - 00000000000d0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d8000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001f6e0000 (usable)
[    0.000000]  BIOS-e820: 000000001f6e0000 - 000000001f6e8000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001f6e8000 - 000000001f700000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001f700000 - 0000000020000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec10000 - 00000000fec20000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff800000 - 00000000ffc00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fffffc00 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 502MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 128736) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   128736
[    0.000000]   HighMem    128736 ->   128736
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   128736
[    0.000000] On node 0 totalpages: 128736
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 973 pages used for memmap
[    0.000000]   Normal zone: 123667 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00F60B0 checksum 0
[    0.000000] ACPI: RSDP 000F60B0, 0014 (r0 PTLTD )
[    0.000000] ACPI: RSDT 1F6E2D8E, 0030 (r1 PTLTD  Montara   6040000  LTP        0)
[    0.000000] ACPI: FACP 1F6E7ED2, 0074 (r1 INTEL  MONTARAG  6040000 PTL        50)
[    0.000000] ACPI: DSDT 1F6E32BD, 4C15 (r1 INTEL  MONTARAG  6040000 MSFT  100000E)
[    0.000000] ACPI: FACS 1F6F8FC0, 0040
[    0.000000] ACPI: BOOT 1F6E7FD8, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
[    0.000000] ACPI: SSDT 1F6E2DBE, 04F7 (r1 INTEL    GV3Ref     1001 MSFT  100000E)
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec10000)
[    0.000000] Built 1 zonelists.  Total pages: 127731
[    0.000000] Kernel command line: root=UUID=dee2ff15-8395-4d04-bbda-f355d0c9855d ro quiet splash
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffd000 (013fd000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 1000.072 MHz processor.
[    6.945497] Console: colour VGA+ 80x25
[    6.945720] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    6.946042] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    6.969625] Memory: 498956k/514944k available (2016k kernel code, 15380k reserved, 919k data, 364k init, 0k highmem)
[    6.969643] virtual kernel memory layout:
[    6.969645]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[    6.969648]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    6.969650]     vmalloc : 0xe0000000 - 0xff7fe000   ( 503 MB)
[    6.969652]     lowmem  : 0xc0000000 - 0xdf6e0000   ( 502 MB)
[    6.969655]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[    6.969657]       .data : 0xc02f8036 - 0xc03dde84   ( 919 kB)
[    6.969659]       .text : 0xc0100000 - 0xc02f8036   (2016 kB)
[    6.969665] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    6.969730] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[    7.049683] Calibrating delay using timer specific routine.. 2001.67 BogoMIPS (lpj=4003342)
[    7.049724] Security Framework v1.0.0 initialized
[    7.049735] SELinux:  Disabled at boot.
[    7.049759] Mount-cache hash table entries: 512
[    7.049957] CPU: After generic identify, caps: a7e9f9bf 00000000 00000000 00000000 00000180 00000000 00000000
[    7.049976] CPU: L1 I cache: 32K, L1 D cache: 32K
[    7.049980] CPU: L2 cache: 1024K
[    7.049985] CPU: After all inits, caps: a7e9f9bf 00000000 00000000 00002040 00000180 00000000 00000000
[    7.050000] Compat vDSO mapped to ffffe000.
[    7.050018] Checking 'hlt' instruction... OK.
[    7.065819] SMP alternatives: switching to UP code
[    7.066049] Freeing SMP alternatives: 11k freed
[    7.066463] Early unpacking initramfs... done
[    7.647924] ACPI: Core revision 20070126
[    7.648048] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[    7.651365] ACPI: setting ELCR to 0200 (from 0c00)
[    7.660361] CPU0: Intel(R) Pentium(R) M processor 1000MHz stepping 05
[    7.660370] SMP motherboard not detected.
[    7.660374] Local APIC not detected. Using dummy APIC emulation.
[    7.660425] Brought up 1 CPUs
[    7.660596] Booting paravirtualized kernel on bare hardware
[    7.660676] Time: 17:56:51  Date: 06/02/108
[    7.660711] NET: Registered protocol family 16
[    7.660831] EISA bus registered
[    7.660847] ACPI: bus type pci registered
[    7.662356] PCI: PCI BIOS revision 2.10 entry at 0xfd6b4, last bus=2
[    7.662360] PCI: Using configuration type 1
[    7.662363] Setting up standard PCI resources
[    7.673826] ACPI: EC: Look up EC in DSDT
[    7.674700] ACPI: EC: GPE=0x1c, ports=0x66, 0x62
[    7.676250] ACPI: Interpreter enabled
[    7.676255] ACPI: (supports S0 S3 S4 S5)
[    7.676281] ACPI: Using PIC for interrupt routing
[    8.084215] ACPI: EC: GPE=0x1c, ports=0x66, 0x62
[    8.084284] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    8.084305] PCI: Probing PCI hardware (bus 00)
[    8.084825] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[    8.084831] PCI quirk: region 1180-11bf claimed by ICH4 GPIO
[    8.085206] PCI: Firmware left 0000:02:08.0 e100 interrupts enabled, disabling
[    8.085271] PCI: Transparent bridge - 0000:00:1e.0
[    8.085359] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    8.085713] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    8.092637] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 *11)
[    8.092807] ACPI: PCI Interrupt Link [LNKB] (IRQs *10 11)
[    8.092937] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 *11)
[    8.093063] ACPI: PCI Interrupt Link [LNKD] (IRQs *11)
[    8.093188] ACPI: PCI Interrupt Link [LNKE] (IRQs *10 11)
[    8.093314] ACPI: PCI Interrupt Link [LNKF] (IRQs *10 11)
[    8.093440] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 *11)
[    8.093566] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 *11)
[    8.093706] Linux Plug and Play Support v0.97 (c) Adam Belay
[    8.093721] pnp: PnP ACPI init
[    8.093733] ACPI: bus type pnp registered
[    8.297485] pnp: PnP ACPI: found 11 devices
[    8.297489] ACPI: ACPI bus type pnp unregistered
[    8.297496] PnPBIOS: Disabled by ACPI PNP
[    8.297564] PCI: Using ACPI for IRQ routing
[    8.297568] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    8.303370] NET: Registered protocol family 8
[    8.303373] NET: Registered protocol family 20
[    8.303458] pnp: 00:04: ioport range 0x600-0x60f has been reserved
[    8.303465] pnp: 00:04: iomem range 0xfec10000-0xfec1ffff could not be reserved
[    8.304572] Time: tsc clocksource has been installed.
[    8.333892] PCI: Bus 3, cardbus bridge: 0000:02:01.0
[    8.333896]   IO window: 00003400-000034ff
[    8.333903]   IO window: 00003800-000038ff
[    8.333909]   PREFETCH window: 30000000-33ffffff
[    8.333915]   MEM window: 38000000-3bffffff
[    8.333920] PCI: Bridge: 0000:00:1e.0
[    8.333925]   IO window: 3000-3fff
[    8.333932]   MEM window: e0200000-e02fffff
[    8.333938]   PREFETCH window: 30000000-33ffffff
[    8.333953] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    8.334182] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 10
[    8.334187] PCI: setting IRQ 10 as level-triggered
[    8.334192] ACPI: PCI Interrupt 0000:02:01.0[A] -> Link [LNKE] -> GSI 10 (level, low) -> IRQ 10
[    8.334217] NET: Registered protocol family 2
[    8.372564] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    8.372620] TCP established hash table entries: 16384 (order: 5, 196608 bytes)
[    8.372853] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    8.373014] TCP: Hash tables configured (established 16384 bind 16384)
[    8.373019] TCP reno registered
[    8.384715] checking if image is initramfs...<6>Switched to high resolution mode on CPU 0
[    8.938718]  it is
[    9.532928] Freeing initrd memory: 7065k freed
[    9.533132] Simple Boot Flag at 0x36 set to 0x1
[    9.533430] audit: initializing netlink socket (disabled)
[    9.533452] audit(1215021412.336:1): initialized
[    9.536985] VFS: Disk quotas dquot_6.5.1
[    9.537073] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    9.537234] io scheduler noop registered
[    9.537238] io scheduler anticipatory registered
[    9.537241] io scheduler deadline registered
[    9.537275] io scheduler cfq registered (default)
[    9.537299] Boot video device is 0000:00:02.0
[    9.537697] isapnp: Scanning for PnP cards...
[    9.891438] isapnp: No Plug & Play device found
[    9.937745] Real Time Clock Driver v1.12ac
[    9.937896] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    9.938178] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    9.939216] 00:07: ttyS0 at I/O 0x6f8 (irq = 6) is a 16550A
[    9.939851] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[    9.939858] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[    9.939872] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
[    9.940708] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    9.941056] input: Macintosh mouse button emulation as /class/input/input0
[    9.941176] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    9.944863] i8042.c: Detected active multiplexing controller, rev 1.1.
[    9.946082] serio: i8042 KBD port at 0x60,0x64 irq 1
[    9.946090] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    9.946095] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    9.946100] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    9.946105] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    9.946394] mice: PS/2 mouse device common for all mice
[    9.946658] EISA: Probing bus 0 at eisa.0
[    9.946671] Cannot allocate resource for EISA slot 1
[    9.946676] Cannot allocate resource for EISA slot 2
[    9.946680] Cannot allocate resource for EISA slot 3
[    9.946706] EISA: Detected 0 cards.
[    9.946864] TCP cubic registered
[    9.946895] NET: Registered protocol family 1
[    9.946938] Using IPI No-Shortcut mode
[    9.947223]   Magic number: 0:848:945
[    9.947252]   hash matches device ttya0
[    9.947423]   hash matches device tty2
[    9.947681] Freeing unused kernel memory: 364k freed
[   10.067826] input: AT Translated Set 2 keyboard as /class/input/input1
[   11.257577] AppArmor: AppArmor initialized<5>audit(1215021413.836:2):  type=1505 info="AppArmor initialized" pid=1191
[   11.271718] fuse init (API version 7.8)
[   11.278935] Failure registering capabilities with primary security module.
[   11.300846] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3] C4[C3])
[   11.300858] ACPI: Processor [CPU0] (supports 8 throttling states)
[   11.386491] ACPI: Thermal Zone [THRS] (57 C)
[   11.470366] ACPI: Thermal Zone [THRC] (58 C)
[   12.101729] usbcore: registered new interface driver usbfs
[   12.101766] usbcore: registered new interface driver hub
[   12.101796] usbcore: registered new device driver usb
[   12.104088] USB Universal Host Controller Interface driver v3.0
[   12.104475] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[   12.104481] PCI: setting IRQ 11 as level-triggered
[   12.104486] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   12.104503] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   12.104509] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   12.104751] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   12.104779] uhci_hcd 0000:00:1d.0: irq 11, io base 0x00001820
[   12.104986] usb usb1: configuration #1 chosen from 1 choice
[   12.105028] hub 1-0:1.0: USB hub found
[   12.105037] hub 1-0:1.0: 2 ports detected
[   12.209276] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[   12.209284] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   12.209301] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   12.209307] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   12.209347] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   12.209375] uhci_hcd 0000:00:1d.1: irq 11, io base 0x00001840
[   12.209544] usb usb2: configuration #1 chosen from 1 choice
[   12.209592] hub 2-0:1.0: USB hub found
[   12.209601] hub 2-0:1.0: 2 ports detected
[   12.258987] SCSI subsystem initialized
[   12.276222] libata version 2.21 loaded.
[   12.321900] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[   12.321908] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   12.321926] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   12.321932] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   12.321974] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   12.322002] uhci_hcd 0000:00:1d.2: irq 11, io base 0x00001860
[   12.322168] usb usb3: configuration #1 chosen from 1 choice
[   12.322218] hub 3-0:1.0: USB hub found
[   12.322227] hub 3-0:1.0: 2 ports detected
[   12.376405] e100: Intel(R) PRO/100 Network Driver, 3.5.17-k4-NAPI
[   12.376412] e100: Copyright(c) 1999-2006 Intel Corporation
[   12.425346] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
[   12.425354] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNKH] -> GSI 11 (level, low) -> IRQ 11
[   12.425373] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   12.425379] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   12.425421] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[   12.425463] ehci_hcd 0000:00:1d.7: debug port 1
[   12.425471] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   12.425484] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xe0100000
[   12.429376] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   12.429519] usb usb4: configuration #1 chosen from 1 choice
[   12.429563] hub 4-0:1.0: USB hub found
[   12.429573] hub 4-0:1.0: 6 ports detected
[   12.532931] ata_piix 0000:00:1f.1: version 2.11
[   12.532951] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[   12.532965] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   12.533010] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   12.533135] scsi0 : ata_piix
[   12.533198] scsi1 : ata_piix
[   12.533363] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011810 irq 14
[   12.533370] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011818 irq 15
[   12.696713] ata1.00: ATA-6: IC25N040ATMR04-0, MO2OAD0A, max UDMA/100
[   12.696721] ata1.00: 78140160 sectors, multi 16: LBA48
[   12.712702] ata1.00: configured for UDMA/100
[   12.712747] ata2: port disabled. ignoring.
[   12.720345] scsi 0:0:0:0: Direct-Access     ATA      IC25N040ATMR04-0 MO2O PQ: 0 ANSI: 5
[   12.725446] ACPI: PCI Interrupt Link [LNKF] enabled at IRQ 10
[   12.725454] ACPI: PCI Interrupt 0000:02:01.1[B] -> Link [LNKF] -> GSI 10 (level, low) -> IRQ 10
[   12.794357] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
[   12.794385] sd 0:0:0:0: [sda] Write Protect is off
[   12.794389] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   12.794413] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   12.794501] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
[   12.794514] sd 0:0:0:0: [sda] Write Protect is off
[   12.794519] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   12.794540] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   12.794547]  sda:<6>ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[10]  MMIO=[e0202000-e02027ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[   12.804108] ACPI: PCI Interrupt 0000:02:08.0[A] -> Link [LNKE] -> GSI 10 (level, low) -> IRQ 10
[   12.827710] e100: eth0: e100_probe: addr 0xe0201000, irq 10, MAC addr 00:0A:E4:01:C2:BC
[   12.832208] usb 4-1: new high speed USB device using ehci_hcd and address 2
[   12.850649]  sda1 sda2 sda3
[   12.872748] sd 0:0:0:0: [sda] Attached SCSI disk
[   12.881028] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    5.976000] Marking TSC unstable due to: possible TSC halt in C2.
[    5.980000] Time: acpi_pm clocksource has been installed.
[    6.000000] usb 4-1: configuration #1 chosen from 1 choice
[    6.024000] usbcore: registered new interface driver libusual
[    6.040000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    6.040000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    6.048000] Initializing USB Mass Storage driver...
[    6.048000] scsi2 : SCSI emulation for USB Mass Storage devices
[    6.048000] usb-storage: device found at 2
[    6.048000] usb-storage: waiting for device to settle before scanning
[    6.048000] usbcore: registered new interface driver usb-storage
[    6.048000] USB Mass Storage support registered.
[    6.244000] Attempting manual resume
[    6.244000] swsusp: Resume From Partition 8:3
[    6.244000] PM: Checking swsusp image.
[    6.244000] PM: Resume from disk failed.
[    6.292000] kjournald starting.  Commit interval 5 seconds
[    6.292000] EXT3-fs: mounted filesystem with ordered data mode.
[    7.108000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[03e40a006d010a31]
[   11.048000] usb-storage: device scan complete
[   11.048000] scsi 2:0:0:0: Direct-Access     SanDisk  Cruzer Micro     0.1  PQ: 0 ANSI: 2
[   11.048000] sd 2:0:0:0: [sdb] 2001888 512-byte hardware sectors (1025 MB)
[   11.048000] sd 2:0:0:0: [sdb] Write Protect is off
[   11.048000] sd 2:0:0:0: [sdb] Mode Sense: 03 00 00 00
[   11.048000] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   11.052000] sd 2:0:0:0: [sdb] 2001888 512-byte hardware sectors (1025 MB)
[   11.052000] sd 2:0:0:0: [sdb] Write Protect is off
[   11.052000] sd 2:0:0:0: [sdb] Mode Sense: 03 00 00 00
[   11.052000] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   11.052000]  sdb: sdb1
[   11.052000] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[   11.052000] sd 2:0:0:0: Attached scsi generic sg1 type 0
[   14.864000] Clocksource tsc unstable (delta = -497340431 ns)
[   17.304000] Linux agpgart interface v0.102 (c) Dave Jones
[   17.376000] agpgart: Detected an Intel 855GM Chipset.
[   17.380000] agpgart: Detected 8060K stolen memory.
[   17.388000] agpgart: AGP aperture is 128M @ 0xe8000000
[   18.916000] intel_rng: FWH not detected
[   19.388000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   19.420000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   19.656000] Synaptics Touchpad, model: 1, fw: 5.8, id: 0xa648b1, caps: 0x904713/0x4000
[   19.696000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[   19.928000] parport_pc 00:06: reported by Plug and Play ACPI
[   19.928000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   20.132000] iTCO_vendor_support: vendor-support=0
[   20.136000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   20.136000] iTCO_wdt: Found a ICH4-M TCO device (Version=1, TCOBASE=0x1060)
[   20.136000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   20.176000] Yenta: CardBus bridge found at 0000:02:01.0 [17c0:3302]
[   20.304000] Yenta: ISA IRQ mask 0x0038, PCI irq 10
[   20.304000] Socket status: 30000006
[   20.304000] Yenta: Raising subordinate bus# of parent bus (#02) from #02 to #06
[   20.304000] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
[   20.304000] cs: IO port probe 0x3000-0x3fff: clean.
[   20.304000] pcmcia: parent PCI bridge Memory window: 0xe0200000 - 0xe02fffff
[   20.304000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x33ffffff
[   20.332000] ieee80211_crypt: registered algorithm 'NULL'
[   20.352000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   20.352000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   20.396000] irda_init()
[   20.396000] NET: Registered protocol family 23
[   20.468000] ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, git-1.2.2
[   20.468000] ipw2100: Copyright(c) 2003-2006 Intel Corporation
[   20.468000] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 11
[   20.468000] ACPI: PCI Interrupt 0000:02:05.0[A] -> Link [LNKG] -> GSI 11 (level, low) -> IRQ 11
[   20.468000] ipw2100: Detected Intel PRO/Wireless 2100 Network Connection
[   20.480000] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 3.
[   20.480000] nsc-ircc, chip->init
[   20.480000] nsc-ircc, Found chip at base=0x02e
[   20.480000] nsc-ircc, driver loaded (Dag Brattli)
[   20.480000] nsc_ircc_open(), can't get iobase of 0x2f8
[   20.480000] nsc-ircc, Found chip at base=0x02e
[   20.480000] nsc-ircc, driver loaded (Dag Brattli)
[   20.480000] nsc_ircc_open(), can't get iobase of 0x2f8
[   20.480000] pnp: Device 00:08 disabled.
[   21.028000] cs: IO port probe 0x100-0x3af: clean.
[   21.028000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   21.028000] cs: IO port probe 0x820-0x8ff: clean.
[   21.028000] cs: IO port probe 0xc00-0xcf7: clean.
[   21.028000] cs: IO port probe 0xa00-0xaff: clean.
[   21.220000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[   21.220000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   22.660000] intel8x0_measure_ac97_clock: measured 55448 usecs
[   22.660000] intel8x0: clocking to 48000
[   23.300000] lp0: using parport0 (interrupt-driven).
[   23.508000] input: Acer hotkey driver as /class/input/input3
[   23.516000] Acer Travelmate hotkey driver v0.5.34
[   23.568000] Adding 979956k swap on /dev/sda3.  Priority:-1 extents:1 across:979956k
[   23.944000] EXT3 FS on sda1, internal journal
[   24.668000] kjournald starting.  Commit interval 5 seconds
[   24.672000] EXT3 FS on sda2, internal journal
[   24.672000] EXT3-fs: mounted filesystem with ordered data mode.
[   27.112000] pnp: Device 00:08 activated.
[   27.124000] serial8250: too much work for irq3
[   27.152000] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 3.
[   27.152000] nsc-ircc, chip->init
[   27.152000] nsc-ircc, Found chip at base=0x02e
[   27.152000] nsc-ircc, driver loaded (Dag Brattli)
[   27.152000] IrDA: Registered device irda0
[   28.244000] ACPI: Battery Slot [BAT0] (battery present)
[   28.564000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   28.632000] ACPI: AC Adapter [AC] (off-line)
[   28.708000] No dock devices found.
[   29.036000] input: Power Button (FF) as /class/input/input4
[   29.036000] ACPI: Power Button (FF) [PWRF]
[   29.068000] input: Lid Switch as /class/input/input5
[   29.068000] ACPI: Lid Switch [LID]
[   29.084000] input: Sleep Button (CM) as /class/input/input6
[   29.084000] ACPI: Sleep Button (CM) [SLP2]
[   33.176000] ppdev: user-space parallel port driver
[   33.840000] audit(1215021444.324:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4756 profile="/usr/sbin/cupsd"
[   33.908000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   33.908000] apm: overridden by ACPI.
[   35.700000] [drm] Initialized drm 1.1.0 20060810
[   35.720000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   35.720000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   35.720000] [drm] Initialized i915 1.6.0 20060119 on minor 1
[   36.492000] irlap_change_speed(), setting speed to 9600
[   39.520000] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[   39.704000] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   39.724000] NFSD: starting 90-second grace period
[   39.996000] Failure registering capabilities with primary security module.
[   40.424000] Bluetooth: Core ver 2.11
[   40.424000] NET: Registered protocol family 31
[   40.424000] Bluetooth: HCI device and connection manager initialized
[   40.424000] Bluetooth: HCI socket layer initialized
[   40.456000] Bluetooth: L2CAP ver 2.8
[   40.456000] Bluetooth: L2CAP socket layer initialized
[   40.768000] Bluetooth: RFCOMM socket layer initialized
[   40.768000] Bluetooth: RFCOMM TTY layer initialized
[   40.768000] Bluetooth: RFCOMM ver 1.8
[   80.984000] NET: Registered protocol family 10
[   80.984000] lo: Disabled Privacy Extensions
[   80.984000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   80.984000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  279.684000] NET: Registered protocol family 17
[  283.600000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  285.868000] ieee80211_crypt: registered algorithm 'TKIP'
[  304.252000] eth1: no IPv6 routers present
[  423.176000] UDF-fs: No partition found (1)
[  423.672000] Unable to identify CD-ROM format.
[  434.872000] usb 4-1: USB disconnect, address 2
[  554.184000] printk: 1 messages suppressed.
[ 3716.772000] usb 4-4: new high speed USB device using ehci_hcd and address 3
[ 3716.904000] usb 4-4: configuration #1 chosen from 1 choice
[ 3716.904000] scsi3 : SCSI emulation for USB Mass Storage devices
[ 3716.904000] usb-storage: device found at 3
[ 3716.904000] usb-storage: waiting for device to settle before scanning
[ 3721.904000] usb-storage: device scan complete
[ 3721.904000] scsi 3:0:0:0: Direct-Access     SanDisk  Cruzer Micro     0.1  PQ: 0 ANSI: 2
[ 3721.920000] sd 3:0:0:0: [sdb] 2001888 512-byte hardware sectors (1025 MB)
[ 3721.920000] sd 3:0:0:0: [sdb] Write Protect is off
[ 3721.920000] sd 3:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 3721.920000] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[ 3721.928000] sd 3:0:0:0: [sdb] 2001888 512-byte hardware sectors (1025 MB)
[ 3721.928000] sd 3:0:0:0: [sdb] Write Protect is off
[ 3721.928000] sd 3:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 3721.928000] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[ 3721.928000]  sdb: sdb1
[ 3721.932000] sd 3:0:0:0: [sdb] Attached SCSI removable disk
[ 3721.932000] sd 3:0:0:0: Attached scsi generic sg1 type 0
[ 3767.112000] UDF-fs: No partition found (1)
[ 3767.252000] Unable to identify CD-ROM format.
[ 6349.624000] UDF-fs: No partition found (1)
[ 6349.676000] Unable to identify CD-ROM format.

```

---

### Post by pytheas22 on 2008-07-02
Very strange...it seems to be thinking that these USB devices are CDs.  Which commands exactly are you using to try to mount them?

---

### Post by coggz on 2008-07-02
Well it worked before, but I right clicking and pressing mount in dolphin, or   typing in a terminal
```
mount /dev/hdb1 /media/
```
Although hdb1 changes from drive to drive...
Im stumped.... like I said, It was working perfectly until like last night so I have no idea what would have caused this...
Luke

---

### Post by soccerboy on 2008-07-02
you have to use ```
mount /dev/hdb1 /media/hdb1
```
/media has folders for other drives that can only be overwritten as root.  That is bad to overwrite them.  Try that command and it should work.

---

### Post by coggz on 2008-07-02
Ok, when I have been trying, I have mainly been using a GUI (dolphin) But I tried that command as me and sudo'ed, here are the results
```
luke@lukes-tablet:~$ mount /dev/hdb1 /media/hdb1
mount: only root can do that
luke@lukes-tablet:~$ sudo mount /dev/hdb1 /media/hdb1
mount: mount point /media/hdb1 does not exist

```

---

### Post by soccerboy on 2008-07-02
> **coggz said:**
> Ok, when I have been trying, I have mainly been using a GUI (dolphin) But I tried that command as me and sudo'ed, here are the results
```
luke@lukes-tablet:~$ mount /dev/hdb1 /media/hdb1
mount: only root can do that
luke@lukes-tablet:~$ sudo mount /dev/hdb1 /media/hdb1
mount: mount point /media/hdb1 does not exist

```

try ```
mkdir /media/hdb1
mount /dev/hdb1 /media/hdb1
```
you may need to sudo the mkdir.  Also, post your fdisk -l output when you insert usb drive.

---

### Post by coggz on 2008-07-02
Making the directory didn't work I'm afraid,
```
sudo mount /dev/hdb1 /media/hdb1
mount: special device /dev/hdb1 does not exist

```

And here is the results from fdisk -l when the stick was inserted...
```
luke@lukes-tablet:~$ fdisk -l

Disk /dev/sdb: 1024 MB, 1024966656 bytes
32 heads, 63 sectors/track, 993 cylinders
Units = cylinders of 2016 * 512 = 1032192 bytes
Disk identifier: 0x000d4574

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         992      999813+   b  W95 FAT32

```

Thanks again for taking the time!

---

### Post by soccerboy on 2008-07-02
aha! try ```
mkdir /media/sdb1
mount /dev/sdb1 /media/sdb1
```
Try mount without the sudo!  No reason to mount removables as root.  This should work.  You had the device name wrong.

---

### Post by coggz on 2008-07-02
I may have had the name wrong, but still no luck...
```
luke@lukes-tablet:~$ sudo mkdir /media/sdb1
luke@lukes-tablet:~$ mount /dev/sdb1 /media/sdb1
mount: only root can do that

```

Did you see the error message that I posted nearer the top of the page? This is what happens when I attempt to mount in a GUI, Oh I've thought of something else: A couple of times, the 'KDE Multimedia Protocol Died' I think it said... don't know if that helps at all...
Luke

---

### Post by soccerboy on 2008-07-02
what is the output of ```
mount
```

---

### Post by coggz on 2008-07-02
```
luke@lukes-tablet:~$ mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
/dev/sda2 on /home type ext3 (rw)
securityfs on /sys/kernel/security type securityfs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)

```

Oh, don't know if this is important, but I have no CD, Floppy... and only 1 40gb HDD in this laptop

---

### Post by soccerboy on 2008-07-02
was your external plugged in when you ran that last mount?

---

### Post by coggz on 2008-07-02
yes, would you like me to try another memory stick?

---

### Post by soccerboy on 2008-07-02
what is in the output of ```
cat /etc/fstab
```?

---

### Post by coggz on 2008-07-02
```
cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=dee2ff15-8395-4d04-bbda-f355d0c9855d /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=f3358b12-a34c-4217-bc89-518b62a894d2 /home           ext3    defaults        0       2
# /dev/sda3
UUID=52c4f6e5-63ac-4253-91f6-5de5418dc204 none            swap    sw              0       0
/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

```

---

### Post by pytheas22 on 2008-07-02
What if you:
```

sudo mount /dev/sdb1 /media/sdb1
```

this should work!

---

### Post by pytheas22 on 2008-07-02
Wait...did you add this line to /etc/fstab:
```

/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```

and if so why?  I don't know how else it would gotten there, if you don't have any CD drive in this computer (maybe you did previously?).  It's a big problem and explains why the computer thinks the device is a CD...it says to mount sdb1, which is your USB stick (I think) with a UDF file system, which should only be used when mounting CDs or DVDs.

Open a terminal and type:
```

sudo gedit /etc/fstab
```

and remove the line above from the file.  Then save the file and reboot, and try to mount stuff again.

---

### Post by coggz on 2008-07-02
```
luke@lukes-tablet:~$ sudo mount /dev/sdb1 /media/sdb1
[sudo] password for luke:
luke@lukes-tablet:~$ ls /media/sdb1
Lots Of Files...

```

Okay, so that did work! Hooray!

But... I still can't mount from the icon, and more importantly from dolphin...

This is a great bit of progress though..
Luke

---

### Post by pytheas22 on 2008-07-02
> luke@lukes-tablet:~$ sudo mount /dev/sdb1 /media/sdb1
[sudo] password for luke:
luke@lukes-tablet:~$ ls /media/sdb1
Lots Of Files...

Okay, so that did work! Hooray!

But... I still can't mount from the icon, and more importantly from dolphin...

This is a great bit of progress though..
Luke

Good that it worked.  It wasn't working before because you needed to use sudo with the command "mount /dev/sdb1 /media/sdb1"

Please now try removing (or commenting out by putting ### in front of it) that strange line in /etc/fstab, as per my previous post, and rebooting.  I suspect that it's the source of the failure to mount from the GUI.

---

### Post by soccerboy on 2008-07-02
> **pytheas22 said:**
> Good that it worked.  It wasn't working before because you needed to use sudo with the command "mount /dev/sdb1 /media/sdb1"

Please now try removing (or commenting out by putting ### in front of it) that strange line in /etc/fstab, as per my previous post, and rebooting.  I suspect that it's the source of the failure to mount from the GUI.

that is impressive work identifying fstab errors from dmesg.  dmesg logs are usually too much stuff for me to sort through but I see where you got it from.

---

### Post by coggz on 2008-07-02
Right, I didn't see that reply, but no, I didn't add it and I have never had a CD drive (it's a tablet pc) But Ive commented and Im about to reboot...

---

### Post by coggz on 2008-07-02
Brilliant!! It works! Thank you very much for taking the time out to do this... much appreciated.
Luke

---

### Post by pytheas22 on 2008-07-02
> that is impressive work identifying fstab errors from dmesg. dmesg logs are usually too much stuff for me to sort through but I see where you got it from.

Well, luckily the relevant lines in dmesg were right towards the bottom:)I still have a lot to learn about dmesg but I'm getting better.  I'm finding that the source of almost every problem can be tracked down there with a little work.
> 
Brilliant!! It works! Thank you very much for taking the time out to do this... much appreciated.

No problem; I'm glad it's fixed.  I would like to know how that weird line got into fstab--I hope it's not some bug in the Ubuntu installer--but at least the problem for you is solved.

EDIT: actually some quick Googling turns up others with the same weird fstab behavior, like [here]("http://linux.derkeiler.com/Mailing-Lists/Ubuntu/2008-03/msg02166.html") and [here]("http://www.kubuntuforums.net/forums/index.php?topic=3095802"), so I guess it probably is just some bug.

---

### Post by mullinsn2000 on 2010-01-24
> **pytheas22 said:**
> Wait...did you add this line to /etc/fstab:
```

/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```and if so why?  I don't know how else it would gotten there, if you don't have any CD drive in this computer (maybe you did previously?).  It's a big problem and explains why the computer thinks the device is a CD...it says to mount sdb1, which is your USB stick (I think) with a UDF file system, which should only be used when mounting CDs or DVDs.

Open a terminal and type:
```

sudo gedit /etc/fstab
```and remove the line above from the file.  Then save the file and reboot, and try to mount stuff again.
You are a genius.  I have been searching the forums for hours and posted a thread trying to figure out how to get Ubuntu to stop thinking the USB drive was a cdrom.  I typed in sudo gedit/etc/fstab and removed the line and now it works perfectly.  I am not the original poster of this thread, but thanks for the help anyways, lol.

---

