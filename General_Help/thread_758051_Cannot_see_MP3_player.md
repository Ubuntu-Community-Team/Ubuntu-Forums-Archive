---
title: "Cannot see MP3 player"
date: 2008-04-17
forum: General Help
---

### Post by Spookie71 on 2008-04-17
Hello

I tried plugging my MP3 player which is a "RCA Lyra MCS102C" and Ubuntu Gutsy Gibbon doesn't seem to recognized it. Or I'm just looking in the wrong place. Can anyone tell me how I can get the system to recognize it so I can transfer files to and from

Regards

---

### Post by handband2 on 2008-04-17
Looks like the RCA Lyra has some problems.

Here are some places to read about the problems:
[https://bugs.launchpad.net/ubuntu/+source/hal-info/+bug/157904](https://bugs.launchpad.net/ubuntu/+source/hal-info/+bug/157904)
[http://ubuntuforums.org/showthread.php?t=111118](http://ubuntuforums.org/showthread.php?t=111118)
[http://ubuntuforums.org/showthread.php?t=129431](http://ubuntuforums.org/showthread.php?t=129431)

---

### Post by Spookie71 on 2008-04-18
I took a look at those links you provided me and it seems that even in their cases Ubuntu doesn't recognize my MP3 player as a just that, It will recognize in their cases that it is a mass storage device.  I can't even get that. Are their any suggestions on how to get it recognized as a storage device. It's a pain to have to boot into windows XP to do it.

Thanks

---

### Post by handband2 on 2008-04-18
What is your output when you type?:
```
$ lsusb
```

---

### Post by Spookie71 on 2008-04-18
This is my output if I type lsusb

name@name-desktop:~$ lsusb
Bus 003 Device 004: ID 069b:077c Thomson, Inc. 
Bus 003 Device 002: ID 04b4:6830 Cypress Semiconductor Corp. USB-2.0 IDE Adapter
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 03f0:2f11 Hewlett-Packard 
Bus 002 Device 003: ID 04fc:0003 Sunplus Technology Co., Ltd CM1092 Optical Scroller Mouse
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
name@namet-desktop:~$

---

### Post by handband2 on 2008-04-18
It looks like your system sees it as:
```
Bus 003 Device 004: ID 069b:077c Thomson, Inc. 
```

Lets see if it is detected as a drive.  What is the out with the following:
```
# dmesg
```
&
```
# fdisk -l
```

---

### Post by Spookie71 on 2008-04-18
Here are the outputs of those commands
> 
[    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Feb 12 07:42:25 UTC 2008 (Ubuntu 2.6.22-14.52-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fffc000 (usable)
[    0.000000]  BIOS-e820: 000000003fffc000 - 000000003ffff000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003ffff000 - 0000000040000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] 127MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 262140) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   262140
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   262140
[    0.000000] On node 0 totalpages: 262140
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 255 pages used for memmap
[    0.000000]   HighMem zone: 32509 pages, LIFO batch:7
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F5690 checksum 0
[    0.000000] ACPI: RSDP 000F5690, 0014 (r0 ASUS  )
[    0.000000] ACPI: RSDT 3FFFC000, 0030 (r1 ASUS   P4S533-X 42302E31 MSFT 31313031)
[    0.000000] ACPI: FACP 3FFFC0C0, 0074 (r1 ASUS   P4S533-X 42302E31 MSFT 31313031)
[    0.000000] ACPI: DSDT 3FFFC134, 287C (r1   ASUS P4S533-X     1000 MSFT  100000B)
[    0.000000] ACPI: FACS 3FFFF000, 0040
[    0.000000] ACPI: BOOT 3FFFC030, 0028 (r1 ASUS   P4S533-X 42302E31 MSFT 31313031)
[    0.000000] ACPI: APIC 3FFFC058, 005A (r1 ASUS   P4S533-X 42302E31 MSFT 31313031)
[    0.000000] ACPI: PM-Timer IO Port: 0xe408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:2 APIC version 20
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 128, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 20 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bec00000)
[    0.000000] Built 1 zonelists.  Total pages: 260093
[    0.000000] Kernel command line: root=UUID=52ae15b2-a7c0-4ada-be4a-5eb1a55218ba ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2394.104 MHz processor.
[   99.489086] Console: colour VGA+ 80x25
[   99.489826] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   99.490546] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   99.523854] Memory: 1027936k/1048560k available (2015k kernel code, 19932k reserved, 915k data, 364k init, 131056k highmem)
[   99.523867] virtual kernel memory layout:
[   99.523869]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   99.523870]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   99.523873]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   99.523874]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   99.523876]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   99.523877]       .data : 0xc02f7e86 - 0xc03dce84   ( 915 kB)
[   99.523878]       .text : 0xc0100000 - 0xc02f7e86   (2015 kB)
[   99.523882] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   99.523939] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   99.603838] Calibrating delay using timer specific routine.. 4792.06 BogoMIPS (lpj=9584131)
[   99.603878] Security Framework v1.0.0 initialized
[   99.603891] SELinux:  Disabled at boot.
[   99.603908] Mount-cache hash table entries: 512
[   99.604116] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
[   99.604132] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   99.604135] CPU: L2 cache: 512K
[   99.604138] CPU: Hyper-Threading is disabled
[   99.604141] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b080 00004400 00000000 00000000
[   99.604157] Compat vDSO mapped to ffffe000.
[   99.604176] Checking 'hlt' instruction... OK.
[   99.619983] SMP alternatives: switching to UP code
[   99.620295] Freeing SMP alternatives: 11k freed
[   99.620631] Early unpacking initramfs... done
[   99.955750] ACPI: Core revision 20070126
[   99.955810] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   99.957088] CPU0: Intel(R) Pentium(R) 4 CPU 2.40GHz stepping 09
[   99.957133] Total of 1 processors activated (4792.06 BogoMIPS).
[   99.957243] ENABLING IO-APIC IRQs
[   99.957431] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[  100.103067] Brought up 1 CPUs
[  100.103216] Booting paravirtualized kernel on bare hardware
[  100.103297] Time: 16:54:40  Date: 03/18/108
[  100.103324] NET: Registered protocol family 16
[  100.103442] EISA bus registered
[  100.103459] ACPI: bus type pci registered
[  100.105009] PCI: PCI BIOS revision 2.10 entry at 0xf1060, last bus=1
[  100.105012] PCI: Using configuration type 1
[  100.105014] Setting up standard PCI resources
[  100.114363] ACPI: EC: Look up EC in DSDT
[  100.120456] ACPI: Interpreter enabled
[  100.120461] ACPI: (supports S0 S1 S3 S4 S5)
[  100.120484] ACPI: Using IOAPIC for interrupt routing
[  100.132791] ACPI: PCI Root Bridge [PCI0] (0000:00)
[  100.132808] PCI: Probing PCI hardware (bus 00)
[  100.133026] Enabling SiS 96x SMBus.
[  100.133694] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[  100.133898] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[  100.175573] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[  100.175663] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[  100.175747] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[  100.175833] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[  100.175927] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *9
[  100.176022] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *9
[  100.176109] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[  100.176193] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[  100.176302] Linux Plug and Play Support v0.97 (c) Adam Belay
[  100.176317] pnp: PnP ACPI init
[  100.176334] ACPI: bus type pnp registered
[  100.181753] pnp: PnP ACPI: found 17 devices
[  100.181757] ACPI: ACPI bus type pnp unregistered
[  100.181762] PnPBIOS: Disabled by ACPI PNP
[  100.181831] PCI: Using ACPI for IRQ routing
[  100.181834] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[  100.187827] NET: Registered protocol family 8
[  100.187829] NET: Registered protocol family 20
[  100.187913] pnp: 00:00: iomem range 0x0-0x9ffff could not be reserved
[  100.187917] pnp: 00:00: iomem range 0xf0000-0xfffff could not be reserved
[  100.187920] pnp: 00:00: iomem range 0x100000-0x3fffffff could not be reserved
[  100.187924] pnp: 00:00: iomem range 0xfec00000-0xfec000ff could not be reserved
[  100.187931] pnp: 00:02: ioport range 0xe400-0xe47f has been reserved
[  100.187934] pnp: 00:02: ioport range 0xe480-0xe4ff has been reserved
[  100.187937] pnp: 00:02: ioport range 0xe600-0xe61f has been reserved
[  100.187940] pnp: 00:02: ioport range 0x480-0x48f has been reserved
[  100.187944] pnp: 00:02: iomem range 0xffee0000-0xffefffff has been reserved
[  100.187950] pnp: 00:03: iomem range 0xfffe0000-0xffffffff could not be reserved
[  100.187965] pnp: 00:10: ioport range 0x3f0-0x3f1 has been reserved
[  100.187968] pnp: 00:10: ioport range 0x290-0x297 has been reserved
[  100.190878] Time: tsc clocksource has been installed.
[  100.218293] PCI: Bridge: 0000:00:01.0
[  100.218295]   IO window: disabled.
[  100.218302]   MEM window: d6000000-d7ffffff
[  100.218308]   PREFETCH window: dff00000-febfffff
[  100.218325] PCI: Setting latency timer of device 0000:00:01.0 to 64
[  100.218344] NET: Registered protocol family 2
[  100.254825] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[  100.255010] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[  100.257129] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[  100.257982] TCP: Hash tables configured (established 131072 bind 65536)
[  100.257990] TCP reno registered
[  100.266971] checking if image is initramfs... it is
[  100.718008] Switched to high resolution mode on CPU 0
[  100.925483] Freeing initrd memory: 7066k freed
[  100.925701] Simple Boot Flag at 0x3a set to 0x1
[  100.926003] audit: initializing netlink socket (disabled)
[  100.926023] audit(1208537681.064:1): initialized
[  100.926132] highmem bounce pool size: 64 pages
[  100.928505] VFS: Disk quotas dquot_6.5.1
[  100.928574] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[  100.928700] io scheduler noop registered
[  100.928703] io scheduler anticipatory registered
[  100.928705] io scheduler deadline registered
[  100.928724] io scheduler cfq registered (default)
[  100.957555] Boot video device is 0000:01:00.0
[  100.957758] isapnp: Scanning for PnP cards...
[  101.311159] isapnp: No Plug & Play device found
[  101.340682] Real Time Clock Driver v1.12ac
[  101.340791] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[  101.340961] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[  101.341220] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[  101.341966] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[  101.342313] 00:0c: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[  101.343214] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[  101.343507] input: Macintosh mouse button emulation as /class/input/input0
[  101.343614] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[  101.343944] serio: i8042 KBD port at 0x60,0x64 irq 1
[  101.343951] serio: i8042 AUX port at 0x60,0x64 irq 12
[  101.344139] mice: PS/2 mouse device common for all mice
[  101.344276] EISA: Probing bus 0 at eisa.0
[  101.344314] EISA: Detected 0 cards.
[  101.344552] TCP cubic registered
[  101.344572] NET: Registered protocol family 1
[  101.344601] Using IPI No-Shortcut mode
[  101.344786]   Magic number: 4:926:944
[  101.344961]   hash matches device ptyyf
[  101.345036]   hash matches device tty1
[  101.345483] Freeing unused kernel memory: 364k freed
[  101.388920] input: AT Translated Set 2 keyboard as /class/input/input1
[  102.611253] AppArmor: AppArmor initialized<5>audit(1208537682.564:2):  type=1505 info="AppArmor initialized" pid=1180
[  102.621692] fuse init (API version 7.8)
[  102.629051] Failure registering capabilities with primary security module.
[  102.648537] ACPI: Invalid PBLK length [5]
[  102.648582] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[  103.359150] SCSI subsystem initialized
[  103.365779] libata version 2.21 loaded.
[  103.369082] pata_sis 0000:00:02.5: version 0.5.1
[  103.369123] ACPI: PCI Interrupt 0000:00:02.5[A] -> GSI 16 (level, low) -> IRQ 16
[  103.369266] scsi0 : pata_sis
[  103.369320] scsi1 : pata_sis
[  103.369465] ata1: PATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001b400 irq 14
[  103.369469] ata2: PATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001b408 irq 15
[  103.429516] usbcore: registered new interface driver usbfs
[  103.429554] usbcore: registered new interface driver hub
[  103.429579] usbcore: registered new device driver usb
[  103.465986] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[  103.469993] sis900.c: v1.08.10 Apr. 2 2006
[  103.582965] Floppy drive(s): fd0 is 1.44M
[  103.644104] FDC 0 is a post-1991 82077
[  103.709160] ata1.00: ATA-6: ST340014A, 3.54, max UDMA/100
[  103.709166] ata1.00: 78165360 sectors, multi 16: LBA48 
[  103.709307] ata1.01: ATA-6: WDC WD800JB-00JJC0, 05.01C05, max UDMA/100
[  103.709310] ata1.01: 156301488 sectors, multi 16: LBA 
[  103.725143] ata1.00: configured for UDMA/100
[  103.733037] ata1.01: configured for UDMA/100
[  104.216199] ata2.00: ATAPI: HL-DT-STDVD-RAM GSA-H22N, 1.02, max UDMA/66
[  104.216206] ata2.01: ATAPI: HL-DT-ST RW/DVD GCC-4521B, 1.07, max UDMA/33
[  104.387899] ata2.00: configured for UDMA/66
[  104.559523] ata2.01: configured for UDMA/33
[  104.559677] scsi 0:0:0:0: Direct-Access     ATA      ST340014A        3.54 PQ: 0 ANSI: 5
[  104.560197] scsi 0:0:1:0: Direct-Access     ATA      WDC WD800JB-00JJ 05.0 PQ: 0 ANSI: 5
[  104.561752] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVD-RAM GSA-H22N 1.02 PQ: 0 ANSI: 5
[  104.562583] scsi 1:0:1:0: CD-ROM            HL-DT-ST RW/DVD GCC-4521B 1.07 PQ: 0 ANSI: 5
[  104.563054] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 20 (level, low) -> IRQ 20
[  104.563072] ohci_hcd 0000:00:03.0: OHCI Host Controller
[  104.563447] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
[  104.563468] ohci_hcd 0000:00:03.0: irq 20, io mem 0xd5800000
[  104.583369] sd 0:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[  104.583390] sd 0:0:0:0: [sda] Write Protect is off
[  104.583393] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  104.583414] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  104.583497] sd 0:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[  104.583509] sd 0:0:0:0: [sda] Write Protect is off
[  104.583512] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  104.583532] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  104.583539]  sda: sda1
[  104.591051] sd 0:0:0:0: [sda] Attached SCSI disk
[  104.592303] sd 0:0:1:0: [sdb] 156301488 512-byte hardware sectors (80026 MB)
[  104.592321] sd 0:0:1:0: [sdb] Write Protect is off
[  104.592324] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[  104.592346] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  104.592420] sd 0:0:1:0: [sdb] 156301488 512-byte hardware sectors (80026 MB)
[  104.592432] sd 0:0:1:0: [sdb] Write Protect is off
[  104.592435] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[  104.592454] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  104.592458]  sdb: sdb1 < sdb5 > sdb2 sdb3
[  104.621349] usb usb1: configuration #1 chosen from 1 choice
[  104.621384] hub 1-0:1.0: USB hub found
[  104.621399] hub 1-0:1.0: 3 ports detected
[  104.630909] sd 0:0:1:0: [sdb] Attached SCSI disk
[  104.635980] sd 0:0:0:0: Attached scsi generic sg0 type 0
[  104.636007] sd 0:0:1:0: Attached scsi generic sg1 type 0
[  104.636039] scsi 1:0:0:0: Attached scsi generic sg2 type 5
[  104.636062] scsi 1:0:1:0: Attached scsi generic sg3 type 5
[  104.690503] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[  104.690511] Uniform CD-ROM driver Revision: 3.20
[  104.690819] sr 1:0:0:0: Attached scsi CD-ROM sr0
[  104.693698] sr1: scsi3-mmc drive: 0x/0x writer cd/rw xa/form2 cdda tray
[  104.693945] sr 1:0:1:0: Attached scsi CD-ROM sr1
[  104.723232] ACPI: PCI Interrupt 0000:00:03.1[B] -> GSI 21 (level, low) -> IRQ 17
[  104.723253] ohci_hcd 0000:00:03.1: OHCI Host Controller
[  104.723282] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 2
[  104.723301] ohci_hcd 0000:00:03.1: irq 17, io mem 0xd5000000
[  104.781133] usb usb2: configuration #1 chosen from 1 choice
[  104.781168] hub 2-0:1.0: USB hub found
[  104.781183] hub 2-0:1.0: 3 ports detected
[  104.883023] PCI: Enabling device 0000:00:04.0 (0004 -> 0007)
[  104.883040] ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 19 (level, low) -> IRQ 18
[  104.884543] 0000:00:04.0: Realtek RTL8201 PHY transceiver found at address 1.
[  104.897014] 0000:00:04.0: Using transceiver found at address 1 as default
[  104.897948] eth0: SiS 900 PCI Fast Ethernet at 0x9800, IRQ 18, 00:0c:6e:42:2e:60.
[  104.898068] PCI: Enabling device 0000:00:03.3 (0004 -> 0006)
[  104.898075] ACPI: PCI Interrupt 0000:00:03.3[D] -> GSI 23 (level, low) -> IRQ 19
[  104.898088] ehci_hcd 0000:00:03.3: EHCI Host Controller
[  104.898122] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 3
[  104.898167] PCI: cache line size of 128 is not supported by device 0000:00:03.3
[  104.898181] ehci_hcd 0000:00:03.3: irq 19, io mem 0xd4800000
[  105.026499] usb 1-1: new full speed USB device using ohci_hcd and address 2
[  105.026529] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[  105.026669] usb usb3: configuration #1 chosen from 1 choice
[  105.026703] hub 3-0:1.0: USB hub found
[  105.026714] hub 3-0:1.0: 6 ports detected
[  105.173316] Attempting manual resume
[  105.173321] swsusp: Resume From Partition 8:18
[  105.173323] PM: Checking swsusp image.
[  105.173547] PM: Resume from disk failed.
[  105.208684] kjournald starting.  Commit interval 5 seconds
[  105.208698] EXT3-fs: mounted filesystem with ordered data mode.
[  105.841074] usb 3-1: new high speed USB device using ehci_hcd and address 2
[  105.975488] usb 3-1: configuration #1 chosen from 1 choice
[  106.452016] usb 3-5: new high speed USB device using ehci_hcd and address 4
[  106.585889] usb 3-5: configuration #1 chosen from 1 choice
[  107.070930] usb 2-2: new full speed USB device using ohci_hcd and address 2
[  107.295555] usb 2-2: configuration #1 chosen from 1 choice
[  107.602007] usb 2-3: new low speed USB device using ohci_hcd and address 3
[  107.812619] usb 2-3: configuration #1 chosen from 1 choice
[  112.529709] Linux agpgart interface v0.102 (c) Dave Jones
[  112.575921] agpgart: Detected SiS chipset - id:1606
[  112.579713] agpgart: AGP aperture is 64M @ 0xd8000000
[  112.670147] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[  112.672353] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[  112.707410] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0xe600
[  113.239375] nvidia: module license 'NVIDIA' taints kernel.
[  113.646196] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[  113.646499] NVRM: loading NVIDIA UNIX x86 Kernel Module  100.14.19  Wed Sep 12 14:12:24 PDT 2007
[  114.258196] parport_pc 00:0a: reported by Plug and Play ACPI
[  114.258253] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[  114.522612] input: PC Speaker as /class/input/input2
[  114.715333] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 2 if 1 alt 0 proto 2 vid 0x03F0 pid 0x2F11
[  114.715361] usbcore: registered new interface driver usblp
[  114.715365] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[  114.717749] input: PS/2 Logitech Mouse as /class/input/input3
[  114.859781] PCI: Enabling device 0000:00:02.7 (0004 -> 0005)
[  114.859796] ACPI: PCI Interrupt 0000:00:02.7[C] -> GSI 18 (level, low) -> IRQ 21
[  114.866979] usbcore: registered new interface driver libusual
[  114.888774] usbcore: registered new interface driver hiddev
[  114.895353] input: USB OpticalWheel Mouse as /class/input/input4
[  114.895726] input: USB HID v1.10 Mouse [USB OpticalWheel Mouse] on usb-0000:00:03.1-3
[  114.895746] usbcore: registered new interface driver usbhid
[  114.895751] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[  114.964396] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[  114.964403] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[  114.968864] Initializing USB Mass Storage driver...
[  114.968967] scsi2 : SCSI emulation for USB Mass Storage devices
[  115.026091] usbcore: registered new interface driver usb-storage
[  115.026097] USB Mass Storage support registered.
[  115.026225] usb-storage: device found at 2
[  115.026228] usb-storage: waiting for device to settle before scanning
[  115.280665] intel8x0_measure_ac97_clock: measured 52351 usecs
[  115.280670] intel8x0: clocking to 48000
[  116.332686] lp0: using parport0 (interrupt-driven).
[  116.392173] Adding 1461904k swap on /dev/sdb2.  Priority:-1 extents:1 across:1461904k
[  116.835943] EXT3 FS on sdb3, internal journal
[  118.485107] No dock devices found.
[  118.763608] input: Power Button (FF) as /class/input/input5
[  118.769218] ACPI: Power Button (FF) [PWRF]
[  118.815618] input: Power Button (CM) as /class/input/input6
[  118.821165] ACPI: Power Button (CM) [PWRB]
[  120.016752] usb-storage: device scan complete
[  120.020501] scsi 2:0:0:0: Direct-Access     ST316081 2A               0000 PQ: 0 ANSI: 0
[  120.044446] sd 2:0:0:0: [sdc] 312581808 512-byte hardware sectors (160042 MB)
[  120.048459] sd 2:0:0:0: [sdc] Write Protect is off
[  120.048468] sd 2:0:0:0: [sdc] Mode Sense: 27 00 00 00
[  120.048471] sd 2:0:0:0: [sdc] Assuming drive cache: write through
[  120.052427] sd 2:0:0:0: [sdc] 312581808 512-byte hardware sectors (160042 MB)
[  120.056435] sd 2:0:0:0: [sdc] Write Protect is off
[  120.056443] sd 2:0:0:0: [sdc] Mode Sense: 27 00 00 00
[  120.056446] sd 2:0:0:0: [sdc] Assuming drive cache: write through
[  120.056454]  sdc: sdc1 < sdc5 >
[  120.074258] sd 2:0:0:0: [sdc] Attached SCSI disk
[  120.074316] sd 2:0:0:0: Attached scsi generic sg4 type 0
[  120.358538] Failure registering capabilities with primary security module.
[  120.749061] ppdev: user-space parallel port driver
[  121.377995] audit(1208552101.939:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4804 profile="/usr/sbin/cupsd"
[  121.464547] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[  121.464553] apm: overridden by ACPI.
[  121.903035] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[  121.903042] vboxdrv: Successfully done.
[  121.906101] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[  121.906109] vboxdrv: Successfully loaded version 1.5.6 (interface 0x00050002).
[  122.485376] Bluetooth: Core ver 2.11
[  122.485536] NET: Registered protocol family 31
[  122.485540] Bluetooth: HCI device and connection manager initialized
[  122.485544] Bluetooth: HCI socket layer initialized
[  122.499004] Bluetooth: L2CAP ver 2.8
[  122.499010] Bluetooth: L2CAP socket layer initialized
[  122.545238] eth0: Media Link On 100mbps full-duplex 
[  122.546228] Bluetooth: RFCOMM socket layer initialized
[  122.546350] Bluetooth: RFCOMM TTY layer initialized
[  122.546353] Bluetooth: RFCOMM ver 1.8
[  124.521327] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[  124.521352] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[  124.521392] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[  125.876672] /dev/vmmon[5263]: VMCI: Driver initialized.
[  125.879783] /dev/vmmon[5263]: Module vmmon: registered with major=10 minor=165
[  125.880148] /dev/vmmon[5263]: Initial HV check: anyNotCapable=1 anyUnlocked=0 anyEnabled=0 anyDisabled=0
[  125.880153] /dev/vmmon[5263]: Module vmmon: initialized
[  126.285931] /dev/vmnet: open called by PID 5307 (vmnet-bridge)
[  126.286265] /dev/vmnet: hub 0 does not exist, allocating memory.
[  126.286477] /dev/vmnet: port on hub 0 successfully opened
[  126.286673] bridge-eth0: enabling the bridge
[  126.286843] bridge-eth0: up
[  126.286979] bridge-eth0: already up
[  126.286984] bridge-eth0: attached
[  126.520875] /dev/vmnet: open called by PID 5326 (vmnet-netifup)
[  126.521231] /dev/vmnet: hub 1 does not exist, allocating memory.
[  126.521474] /dev/vmnet: port on hub 1 successfully opened
[  126.796543] /dev/vmnet: open called by PID 5323 (vmnet-dhcpd)
[  126.796824] /dev/vmnet: port on hub 1 successfully opened
[  126.802665] /dev/vmnet: open called by PID 5350 (vmnet-netifup)
[  126.802996] /dev/vmnet: hub 8 does not exist, allocating memory.
[  126.803210] /dev/vmnet: port on hub 8 successfully opened
[  126.836092] NET: Registered protocol family 17
[  126.852785] /dev/vmnet: open called by PID 5365 (vmnet-dhcpd)
[  126.853040] /dev/vmnet: port on hub 8 successfully opened
[  126.858484] /dev/vmnet: open called by PID 5372 (vmnet-natd)
[  126.858807] /dev/vmnet: port on hub 8 successfully opened
[  130.852046] NET: Registered protocol family 10
[  130.852775] lo: Disabled Privacy Extensions
[  140.840252] vmnet1: no IPv6 routers present
[  140.932090] eth0: no IPv6 routers present
[  141.327401] vmnet8: no IPv6 routers present
name@name-desktop:~$ 


and 
> Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdc6ca795

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               2       19457   156280320    f  W95 Ext'd (LBA)
/dev/sdc5               2       19457   156280288+   7  HPFS/NTFS


---

### Post by handband2 on 2008-04-18
I see two more drives which didn't pop up in your fdisk -l

Run fdisk -l as root:
```
$sudo fdisk -l
```

---

### Post by Spookie71 on 2008-04-22
Sorry about the delay of my response I changed Ubuntu to being my primary O/S here are the outputs for which you asked

> 
dmesg:

~$ dmesg
[    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Feb 12 07:42:25 UTC 2008 (Ubuntu 2.6.22-14.52-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fffc000 (usable)
[    0.000000]  BIOS-e820: 000000003fffc000 - 000000003ffff000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003ffff000 - 0000000040000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] 127MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 262140) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   262140
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   262140
[    0.000000] On node 0 totalpages: 262140
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 255 pages used for memmap
[    0.000000]   HighMem zone: 32509 pages, LIFO batch:7
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F5690 checksum 0
[    0.000000] ACPI: RSDP 000F5690, 0014 (r0 ASUS  )
[    0.000000] ACPI: RSDT 3FFFC000, 0030 (r1 ASUS   P4S533-X 42302E31 MSFT 31313031)
[    0.000000] ACPI: FACP 3FFFC0C0, 0074 (r1 ASUS   P4S533-X 42302E31 MSFT 31313031)
[    0.000000] ACPI: DSDT 3FFFC134, 287C (r1   ASUS P4S533-X     1000 MSFT  100000B)
[    0.000000] ACPI: FACS 3FFFF000, 0040
[    0.000000] ACPI: BOOT 3FFFC030, 0028 (r1 ASUS   P4S533-X 42302E31 MSFT 31313031)
[    0.000000] ACPI: APIC 3FFFC058, 005A (r1 ASUS   P4S533-X 42302E31 MSFT 31313031)
[    0.000000] ACPI: PM-Timer IO Port: 0xe408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:2 APIC version 20
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 128, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 20 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bec00000)
[    0.000000] Built 1 zonelists.  Total pages: 260093
[    0.000000] Kernel command line: root=UUID=43c22b1f-b0a1-4a40-b782-056b6b5809c5 ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2394.018 MHz processor.
[   16.361213] Console: colour VGA+ 80x25
[   16.361948] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   16.362669] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   16.396105] Memory: 1027936k/1048560k available (2015k kernel code, 19928k reserved, 915k data, 364k init, 131056k highmem)
[   16.396118] virtual kernel memory layout:
[   16.396120]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   16.396121]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   16.396124]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   16.396125]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   16.396126]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   16.396128]       .data : 0xc02f7e86 - 0xc03dce84   ( 915 kB)
[   16.396129]       .text : 0xc0100000 - 0xc02f7e86   (2015 kB)
[   16.396132] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   16.396190] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   16.476087] Calibrating delay using timer specific routine.. 4792.06 BogoMIPS (lpj=9584120)
[   16.476129] Security Framework v1.0.0 initialized
[   16.476141] SELinux:  Disabled at boot.
[   16.476157] Mount-cache hash table entries: 512
[   16.476368] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
[   16.476383] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   16.476387] CPU: L2 cache: 512K
[   16.476390] CPU: Hyper-Threading is disabled
[   16.476393] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b080 00004400 00000000 00000000
[   16.476407] Compat vDSO mapped to ffffe000.
[   16.476427] Checking 'hlt' instruction... OK.
[   16.492232] SMP alternatives: switching to UP code
[   16.492548] Freeing SMP alternatives: 11k freed
[   16.492883] Early unpacking initramfs... done
[   16.827376] ACPI: Core revision 20070126
[   16.827438] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   16.828718] CPU0: Intel(R) Pentium(R) 4 CPU 2.40GHz stepping 09
[   16.828763] Total of 1 processors activated (4792.06 BogoMIPS).
[   16.828872] ENABLING IO-APIC IRQs
[   16.829061] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   16.975316] Brought up 1 CPUs
[   16.975463] Booting paravirtualized kernel on bare hardware
[   16.975545] Time: 18:06:50  Date: 03/22/108
[   16.975571] NET: Registered protocol family 16
[   16.975688] EISA bus registered
[   16.975704] ACPI: bus type pci registered
[   16.977258] PCI: PCI BIOS revision 2.10 entry at 0xf1060, last bus=1
[   16.977260] PCI: Using configuration type 1
[   16.977262] Setting up standard PCI resources
[   16.986642] ACPI: EC: Look up EC in DSDT
[   16.992746] ACPI: Interpreter enabled
[   16.992751] ACPI: (supports S0 S1 S3 S4 S5)
[   16.992773] ACPI: Using IOAPIC for interrupt routing
[   17.005086] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   17.005103] PCI: Probing PCI hardware (bus 00)
[   17.005322] Enabling SiS 96x SMBus.
[   17.005984] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   17.006188] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[   17.047829] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   17.047918] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   17.048002] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   17.048087] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   17.048182] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *9
[   17.048277] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *9
[   17.048363] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   17.048447] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   17.048553] Linux Plug and Play Support v0.97 (c) Adam Belay
[   17.048567] pnp: PnP ACPI init
[   17.048583] ACPI: bus type pnp registered
[   17.053928] pnp: PnP ACPI: found 17 devices
[   17.053931] ACPI: ACPI bus type pnp unregistered
[   17.053937] PnPBIOS: Disabled by ACPI PNP
[   17.054008] PCI: Using ACPI for IRQ routing
[   17.054011] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   17.060010] NET: Registered protocol family 8
[   17.060013] NET: Registered protocol family 20
[   17.060092] pnp: 00:00: iomem range 0x0-0x9ffff could not be reserved
[   17.060096] pnp: 00:00: iomem range 0xf0000-0xfffff could not be reserved
[   17.060099] pnp: 00:00: iomem range 0x100000-0x3fffffff could not be reserved
[   17.060102] pnp: 00:00: iomem range 0xfec00000-0xfec000ff could not be reserved
[   17.060110] pnp: 00:02: ioport range 0xe400-0xe47f has been reserved
[   17.060113] pnp: 00:02: ioport range 0xe480-0xe4ff has been reserved
[   17.060116] pnp: 00:02: ioport range 0xe600-0xe61f has been reserved
[   17.060119] pnp: 00:02: ioport range 0x480-0x48f has been reserved
[   17.060122] pnp: 00:02: iomem range 0xffee0000-0xffefffff has been reserved
[   17.060129] pnp: 00:03: iomem range 0xfffe0000-0xffffffff could not be reserved
[   17.060144] pnp: 00:10: ioport range 0x3f0-0x3f1 has been reserved
[   17.060147] pnp: 00:10: ioport range 0x290-0x297 has been reserved
[   17.063127] Time: tsc clocksource has been installed.
[   17.090482] PCI: Bridge: 0000:00:01.0
[   17.090484]   IO window: disabled.
[   17.090491]   MEM window: d6000000-d7ffffff
[   17.090496]   PREFETCH window: dff00000-febfffff
[   17.090513] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   17.090533] NET: Registered protocol family 2
[   17.127069] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   17.127255] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   17.129376] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   17.130223] TCP: Hash tables configured (established 131072 bind 65536)
[   17.130230] TCP reno registered
[   17.139225] checking if image is initramfs... it is
[   17.590258] Switched to high resolution mode on CPU 0
[   17.797948] Freeing initrd memory: 7063k freed
[   17.798139] Simple Boot Flag at 0x3a set to 0x1
[   17.798446] audit: initializing netlink socket (disabled)
[   17.798467] audit(1208887611.064:1): initialized
[   17.798577] highmem bounce pool size: 64 pages
[   17.800946] VFS: Disk quotas dquot_6.5.1
[   17.801014] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   17.801140] io scheduler noop registered
[   17.801143] io scheduler anticipatory registered
[   17.801145] io scheduler deadline registered
[   17.801165] io scheduler cfq registered (default)
[   17.829779] Boot video device is 0000:01:00.0
[   17.829977] isapnp: Scanning for PnP cards...
[   18.183378] isapnp: No Plug & Play device found
[   18.214445] Real Time Clock Driver v1.12ac
[   18.214565] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   18.214677] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   18.214918] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   18.215672] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   18.216033] 00:0c: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   18.216950] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   18.217257] input: Macintosh mouse button emulation as /class/input/input0
[   18.217367] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   18.217701] serio: i8042 KBD port at 0x60,0x64 irq 1
[   18.217707] serio: i8042 AUX port at 0x60,0x64 irq 12
[   18.217903] mice: PS/2 mouse device common for all mice
[   18.218038] EISA: Probing bus 0 at eisa.0
[   18.218077] EISA: Detected 0 cards.
[   18.218317] TCP cubic registered
[   18.218336] NET: Registered protocol family 1
[   18.218364] Using IPI No-Shortcut mode
[   18.218547]   Magic number: 4:614:140
[   18.219195] Freeing unused kernel memory: 364k freed
[   18.261140] input: AT Translated Set 2 keyboard as /class/input/input1
[   19.473771] AppArmor: AppArmor initialized<5>audit(1208887612.564:2):  type=1505 info="AppArmor initialized" pid=1180
[   19.484363] fuse init (API version 7.8)
[   19.490481] Failure registering capabilities with primary security module.
[   19.505869] ACPI: Invalid PBLK length [5]
[   19.505914] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   20.259291] usbcore: registered new interface driver usbfs
[   20.259323] usbcore: registered new interface driver hub
[   20.259350] usbcore: registered new device driver usb
[   20.260345] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   20.260384] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 20 (level, low) -> IRQ 20
[   20.260399] ohci_hcd 0000:00:03.0: OHCI Host Controller
[   20.260593] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
[   20.260611] ohci_hcd 0000:00:03.0: irq 20, io mem 0xd5800000
[   20.266699] SCSI subsystem initialized
[   20.272928] libata version 2.21 loaded.
[   20.326829] sis900.c: v1.08.10 Apr. 2 2006
[   20.383463] usb usb1: configuration #1 chosen from 1 choice
[   20.383504] hub 1-0:1.0: USB hub found
[   20.383519] hub 1-0:1.0: 3 ports detected
[   20.427950] Floppy drive(s): fd0 is 1.44M
[   20.485226] pata_sis 0000:00:02.5: version 0.5.1
[   20.485271] ACPI: PCI Interrupt 0000:00:02.5[A] -> GSI 16 (level, low) -> IRQ 16
[   20.485431] scsi0 : pata_sis
[   20.485485] scsi1 : pata_sis
[   20.485607] ata1: PATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001b400 irq 14
[   20.485611] ata2: PATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001b408 irq 15
[   20.507387] FDC 0 is a post-1991 82077
[   20.788527] usb 1-1: new full speed USB device using ohci_hcd and address 2
[   20.824847] ata1.00: ATA-6: ST340014A, 3.54, max UDMA/100
[   20.824851] ata1.00: 78165360 sectors, multi 16: LBA48 
[   20.824980] ata1.01: ATA-6: WDC WD800JB-00JJC0, 05.01C05, max UDMA/100
[   20.824983] ata1.01: 156301488 sectors, multi 16: LBA 
[   20.840798] ata1.00: configured for UDMA/100
[   20.848723] ata1.01: configured for UDMA/100
[   21.003320] usb 1-1: configuration #1 chosen from 1 choice
[   21.307613] usb 1-3: new full speed USB device using ohci_hcd and address 3
[   21.331871] ata2.00: ATAPI: HL-DT-STDVD-RAM GSA-H22N, 1.02, max UDMA/66
[   21.331877] ata2.01: ATAPI: HL-DT-ST RW/DVD GCC-4521B, 1.07, max UDMA/33
[   21.503591] ata2.00: configured for UDMA/66
[   21.522380] usb 1-3: configuration #1 chosen from 1 choice
[   21.675186] ata2.01: configured for UDMA/33
[   21.675339] scsi 0:0:0:0: Direct-Access     ATA      ST340014A        3.54 PQ: 0 ANSI: 5
[   21.675877] scsi 0:0:1:0: Direct-Access     ATA      WDC WD800JB-00JJ 05.0 PQ: 0 ANSI: 5
[   21.677467] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVD-RAM GSA-H22N 1.02 PQ: 0 ANSI: 5
[   21.678310] scsi 1:0:1:0: CD-ROM            HL-DT-ST RW/DVD GCC-4521B 1.07 PQ: 0 ANSI: 5
[   21.683194] PCI: Enabling device 0000:00:03.3 (0004 -> 0006)
[   21.683209] ACPI: PCI Interrupt 0000:00:03.3[D] -> GSI 23 (level, low) -> IRQ 17
[   21.683225] ehci_hcd 0000:00:03.3: EHCI Host Controller
[   21.683482] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 2
[   21.683528] PCI: cache line size of 128 is not supported by device 0000:00:03.3
[   21.683542] ehci_hcd 0000:00:03.3: irq 17, io mem 0xd4800000
[   21.683551] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   21.683600] usb 1-1: USB disconnect, address 2
[   21.685099] usb usb2: configuration #1 chosen from 1 choice
[   21.685300] hub 2-0:1.0: USB hub found
[   21.685313] hub 2-0:1.0: 6 ports detected
[   21.706952] sd 0:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[   21.707571] sd 0:0:0:0: [sda] Write Protect is off
[   21.707575] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   21.707624] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   21.707704] sd 0:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[   21.707716] sd 0:0:0:0: [sda] Write Protect is off
[   21.707719] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   21.707739] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   21.707745]  sda: sda1 sda2 < sda5 >
[   21.746832] sd 0:0:0:0: [sda] Attached SCSI disk
[   21.747778] sd 0:0:1:0: [sdb] 156301488 512-byte hardware sectors (80026 MB)
[   21.747795] sd 0:0:1:0: [sdb] Write Protect is off
[   21.747798] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   21.747820] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   21.747882] sd 0:0:1:0: [sdb] 156301488 512-byte hardware sectors (80026 MB)
[   21.747894] sd 0:0:1:0: [sdb] Write Protect is off
[   21.747897] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   21.747917] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   21.747921]  sdb: sdb1 < sdb5 > sdb2 sdb3
[   21.786544] sd 0:0:1:0: [sdb] Attached SCSI disk
[   21.786980] PCI: Enabling device 0000:00:04.0 (0004 -> 0007)
[   21.786995] ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 19 (level, low) -> IRQ 18
[   21.788498] 0000:00:04.0: Realtek RTL8201 PHY transceiver found at address 1.
[   21.800730] 0000:00:04.0: Using transceiver found at address 1 as default
[   21.801630] eth0: SiS 900 PCI Fast Ethernet at 0x9800, IRQ 18, 00:0c:6e:42:2e:60.
[   21.801736] ACPI: PCI Interrupt 0000:00:03.1[B] -> GSI 21 (level, low) -> IRQ 19
[   21.801749] ohci_hcd 0000:00:03.1: OHCI Host Controller
[   21.801785] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 3
[   21.801804] ohci_hcd 0000:00:03.1: irq 19, io mem 0xd5000000
[   21.806476] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   21.806502] sd 0:0:1:0: Attached scsi generic sg1 type 0
[   21.806525] scsi 1:0:0:0: Attached scsi generic sg2 type 5
[   21.806549] scsi 1:0:1:0: Attached scsi generic sg3 type 5
[   21.810750] usb 1-3: USB disconnect, address 3
[   21.836631] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[   21.836639] Uniform CD-ROM driver Revision: 3.20
[   21.836713] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   21.839566] sr1: scsi3-mmc drive: 52x/52x writer cd/rw xa/form2 cdda tray
[   21.839652] sr 1:0:1:0: Attached scsi CD-ROM sr1
[   21.856823] usb usb3: configuration #1 chosen from 1 choice
[   21.856860] hub 3-0:1.0: USB hub found
[   21.856875] hub 3-0:1.0: 3 ports detected
[   22.178089] usb 2-1: new high speed USB device using ehci_hcd and address 2
[   22.312544] usb 2-1: configuration #1 chosen from 1 choice
[   22.349675] Attempting manual resume
[   22.349680] swsusp: Resume From Partition 8:5
[   22.349682] PM: Checking swsusp image.
[   22.350035] PM: Resume from disk failed.
[   22.377198] kjournald starting.  Commit interval 5 seconds
[   22.377213] EXT3-fs: mounted filesystem with ordered data mode.
[   22.788987] usb 2-5: new high speed USB device using ehci_hcd and address 4
[   22.922805] usb 2-5: configuration #1 chosen from 1 choice
[   23.407889] usb 3-2: new full speed USB device using ohci_hcd and address 2
[   23.632613] usb 3-2: configuration #1 chosen from 1 choice
[   23.938939] usb 3-3: new low speed USB device using ohci_hcd and address 3
[   24.149669] usb 3-3: configuration #1 chosen from 1 choice
[   24.152751] usbcore: registered new interface driver libusual
[   24.647212] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   24.647220] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   24.802361] Initializing USB Mass Storage driver...
[   24.802441] scsi2 : SCSI emulation for USB Mass Storage devices
[   24.802495] usb-storage: device found at 2
[   24.802497] usb-storage: waiting for device to settle before scanning
[   24.802531] usbcore: registered new interface driver usb-storage
[   24.802534] USB Mass Storage support registered.
[   29.792794] usb-storage: device scan complete
[   29.795675] scsi 2:0:0:0: Direct-Access     ST316081 2A               0000 PQ: 0 ANSI: 0
[   29.803072] sd 2:0:0:0: [sdc] 312581808 512-byte hardware sectors (160042 MB)
[   29.804657] sd 2:0:0:0: [sdc] Write Protect is off
[   29.804663] sd 2:0:0:0: [sdc] Mode Sense: 27 00 00 00
[   29.804666] sd 2:0:0:0: [sdc] Assuming drive cache: write through
[   29.806642] sd 2:0:0:0: [sdc] 312581808 512-byte hardware sectors (160042 MB)
[   29.808588] sd 2:0:0:0: [sdc] Write Protect is off
[   29.808594] sd 2:0:0:0: [sdc] Mode Sense: 27 00 00 00
[   29.808597] sd 2:0:0:0: [sdc] Assuming drive cache: write through
[   29.808613]  sdc: sdc1 < sdc5 >
[   29.833754] sd 2:0:0:0: [sdc] Attached SCSI disk
[   29.833812] sd 2:0:0:0: Attached scsi generic sg4 type 0
[   30.517589] Linux agpgart interface v0.102 (c) Dave Jones
[   30.527162] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   30.553598] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   30.590032] agpgart: Detected SiS chipset - id:1606
[   30.593817] agpgart: AGP aperture is 64M @ 0xd8000000
[   30.752506] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0xe600
[   31.456698] nvidia: module license 'NVIDIA' taints kernel.
[   31.882376] input: PC Speaker as /class/input/input2
[   31.975144] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   31.975464] NVRM: loading NVIDIA UNIX x86 Kernel Module  100.14.19  Wed Sep 12 14:12:24 PDT 2007
[   32.105020] input: PS/2 Logitech Mouse as /class/input/input3
[   32.292782] parport_pc 00:0a: reported by Plug and Play ACPI
[   32.292842] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   32.381817] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 2 if 1 alt 0 proto 2 vid 0x03F0 pid 0x2F11
[   32.381842] usbcore: registered new interface driver usblp
[   32.381846] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[   32.466593] usbcore: registered new interface driver hiddev
[   32.472904] input: USB OpticalWheel Mouse as /class/input/input4
[   32.472979] input: USB HID v1.10 Mouse [USB OpticalWheel Mouse] on usb-0000:00:03.1-3
[   32.472997] usbcore: registered new interface driver usbhid
[   32.473002] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   33.007438] PCI: Enabling device 0000:00:02.7 (0004 -> 0005)
[   33.007454] ACPI: PCI Interrupt 0000:00:02.7[C] -> GSI 18 (level, low) -> IRQ 21
[   33.430105] intel8x0_measure_ac97_clock: measured 52366 usecs
[   33.430109] intel8x0: clocking to 48000
[   34.190633] lp0: using parport0 (interrupt-driven).
[   34.254103] Adding 1646620k swap on /dev/sda5.  Priority:-1 extents:1 across:1646620k
[   34.538328] EXT3 FS on sda1, internal journal
[   35.849839] input: Power Button (FF) as /class/input/input5
[   35.855299] ACPI: Power Button (FF) [PWRF]
[   35.896219] input: Power Button (CM) as /class/input/input6
[   35.901625] ACPI: Power Button (CM) [PWRB]
[   35.936616] No dock devices found.
[   37.458433] Failure registering capabilities with primary security module.
[   37.877427] ppdev: user-space parallel port driver
[   38.387670] audit(1208887631.988:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4827 profile="/usr/sbin/cupsd"
[   38.644637] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   38.644645] apm: overridden by ACPI.
[   39.241753] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   39.241760] vboxdrv: Successfully done.
[   39.616312] eth0: Media Link On 100mbps full-duplex 
[   40.039189] Bluetooth: Core ver 2.11
[   40.039353] NET: Registered protocol family 31
[   40.039356] Bluetooth: HCI device and connection manager initialized
[   40.039360] Bluetooth: HCI socket layer initialized
[   40.111504] Bluetooth: L2CAP ver 2.8
[   40.111509] Bluetooth: L2CAP socket layer initialized
[   40.221100] Bluetooth: RFCOMM socket layer initialized
[   40.221242] Bluetooth: RFCOMM TTY layer initialized
[   40.221245] Bluetooth: RFCOMM ver 1.8
[   42.431174] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[   42.431198] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[   42.431237] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[   44.716232] NET: Registered protocol family 17
[   46.423717] NET: Registered protocol family 10
[   46.423946] lo: Disabled Privacy Extensions
[   56.896484] eth0: no IPv6 routers present



and 

sudo fdisk =l

> 

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x418b418b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4660    37431418+  83  Linux
/dev/sda2            4661        4865     1646662+   5  Extended
/dev/sda5            4661        4865     1646631   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd447915c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           2        6043    48532365    f  W95 Ext'd (LBA)
/dev/sdb2            6044        6225     1461915   82  Linux swap / Solaris
/dev/sdb3            6226        9729    28145880   83  Linux
/dev/sdb5               2        6043    48532333+   7  HPFS/NTFS

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdc6ca795

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               2       19457   156280320    f  W95 Ext'd (LBA)
/dev/sdc5               2       19457   156280288+   7  HPFS/NTFS



---

### Post by handband2 on 2008-04-22
I found this in the [manual]("http://support.rcaaudiovideo.com/manual.aspx?product=384"):
> • What is MTP mode?
– MTP (Media Transfer Protocol) mode is essential if you want to transfer DRM content to
  your player. In MTP mode your player will no longer show up as a drive letter. So programs
  that were designed to work with a player that shows up as a drive letter will not be able to
  work directly with the player.

I would try turning off the **MTP** mode and see if that fixes the problem since the computer does see the device.

---

### Post by dcstar on 2008-04-23
> **handband2 said:**
> I found this in the [manual]("http://support.rcaaudiovideo.com/manual.aspx?product=384"):


I would try turning off the **MTP** mode and see if that fixes the problem since the computer does see the device.

Don't ya just love DRM.....   ** not!**       :mad:

---

