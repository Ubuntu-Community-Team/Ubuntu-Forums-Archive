---
title: "Serious Dsplay problem"
date: 2008-06-04
forum: General Help
---

### Post by CZ-82 on 2008-06-04
Linux Mint [screen resolution problems]


Had problems with this install after a few weeks of use.

One day it came up with too high resolution, and the output did not fill the screen as set up.  Attempted 3 times to reset the screen 
resolution.  The selected resolution did not seem to take.

The next time I booted and forever more, it would not load the X Windows, or desktop manager, or do much else for that matter.

Asked for help elsewhere, and they wanted more info.  Hope I have supplied enough info for you this time.

---------------------------------------------------------------


	From Grub menu:

Linux Mint XFCE, Kernel 2.6.22-14-generic
-------------
	
		After the end of boot attempt:

Modprobe: WARNING: Not loading blacklisted module ipv6

Failed to start the x server (Your graphical interface). It is likely that it is not set up correctly. Would you like to view the x server output to diagnose the problem?  Yes No

	[Selected YES]:


X Window System Version 1.3.0
Real??? Date: 19 April 2007
XProtocol Version ii, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-Server 2:1.3.00fsq-12 Ubuntu)
Current Operating System: Linux xxx-desktop 2.6.22-14-generic #1 SMP SU
Build Date: 29 September 2007
	Yada yada...

(EE) NV(0): Virtual width ( 2048 ) is too large for hardware (Max 2032)
<Reloading daemond ...
Fatal Server Error:
No Server Found  			100%




---------------------------------------------------------------

	Was able to capture dmesg output and here it is:




[    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000000ffc0000 (usable)
[    0.000000]  BIOS-e820: 000000000ffc0000 - 000000000fff8000 (ACPI data)
[    0.000000]  BIOS-e820: 000000000fff8000 - 0000000010000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000ffb80000 - 00000000ffc00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 255MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 65472) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->    65472
[    0.000000]   HighMem     65472 ->    65472
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->    65472
[    0.000000] On node 0 totalpages: 65472
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 479 pages used for memmap
[    0.000000]   Normal zone: 60897 pages, LIFO batch:15
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00FF980 checksum 0
[    0.000000] ACPI: RSDP 000FF980, 0014 (r0 AMI   )
[    0.000000] ACPI: RSDT 0FFF0000, 002C (r1 DELL   ZUUL     20020611 MSFT     1011)
[    0.000000] ACPI: FACP 0FFF1000, 0074 (r1 DELL   ZUUL     20020611 MSFT     1011)
[    0.000000] ACPI: DSDT 0FFE0000, 2D8B (r1 D815EA EA81510A       13 MSFT  100000B)
[    0.000000] ACPI: FACS 0FFF8000, 0040
[    0.000000] ACPI: BOOT 0FFF4000, 002B (r1 DELL   ZUUL     20020611 MSFT     1011)
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 10000000:efb80000)
[    0.000000] Built 1 zonelists.  Total pages: 64961
[    0.000000] Kernel command line: root=/dev/sda2 ro single
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffd000 (0120c000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 1024 (order: 10, 4096 bytes)
[    0.000000] Detected 930.347 MHz processor.
[  183.978225] Console: colour VGA+ 80x25
[  183.981767] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[  183.982198] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[  184.003696] Memory: 246284k/261888k available (2015k kernel code, 15140k reserved, 916k data, 364k init, 0k highmem)
[  184.003823] virtual kernel memory layout:
[  184.003825]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[  184.003829]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[  184.003832]     vmalloc : 0xd0800000 - 0xff7fe000   ( 751 MB)
[  184.003835]     lowmem  : 0xc0000000 - 0xcffc0000   ( 255 MB)
[  184.003838]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[  184.003841]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
[  184.003844]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
[  184.004561] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[  184.004817] SLUB: Genslabs=22, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[  184.084897] Calibrating delay using timer specific routine.. 1862.20 BogoMIPS (lpj=3724403)
[  184.085127] Security Framework v1.0.0 initialized
[  184.085231] SELinux:  Disabled at boot.
[  184.085352] Mount-cache hash table entries: 512
[  184.085687] CPU: After generic identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[  184.085710] CPU: L1 I cache: 16K, L1 D cache: 16K
[  184.085885] CPU: L2 cache: 256K
[  184.085980] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[  184.086001] Compat vDSO mapped to ffffe000.
[  184.086117] Checking 'hlt' instruction... OK.
[  184.101168] SMP alternatives: switching to UP code
[  184.101589] Freeing SMP alternatives: 11k freed
[  184.102268] Early unpacking initramfs... done
[  184.926630] ACPI: Core revision 20070126
[  184.926930] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[  184.930269] ACPI: setting ELCR to 0200 (from 0e08)
[  184.931409] CPU0: Intel Pentium III (Coppermine) stepping 03
[  184.931746] SMP motherboard not detected.
[  184.931839] Local APIC not detected. Using dummy APIC emulation.
[  184.932021] Brought up 1 CPUs
[  184.932428] Booting paravirtualized kernel on bare hardware
[  184.932639] Time: 10:13:06  Date: 05/04/108
[  184.932792] NET: Registered protocol family 16
[  184.933120] EISA bus registered
[  184.933230] ACPI: bus type pci registered
[  184.933916] PCI: PCI BIOS revision 2.10 entry at 0xfda95, last bus=2
[  184.934011] PCI: Using configuration type 1
[  184.934103] Setting up standard PCI resources
[  184.937830] ACPI: EC: Look up EC in DSDT
[  184.945807] ACPI: Interpreter enabled
[  184.945913] ACPI: (supports S0 S1 S4 S5)
[  184.946428] ACPI: Using PIC for interrupt routing
[  184.955975] ACPI: PCI Root Bridge [PCI0] (0000:00)
[  184.956113] PCI: Probing PCI hardware (bus 00)
[  184.956427] PCI quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
[  184.956528] PCI quirk: region 0500-053f claimed by ICH4 GPIO
[  184.957192] PCI: Transparent bridge - 0000:00:1e.0
[  184.957323] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[  184.957575] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[  184.960032] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12)
[  184.961295] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *9 10 11 12)
[  184.962451] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 11 12) *0, disabled.
[  184.963769] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 *10 11 12)
[  184.964957] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12) *0, disabled.
[  184.966276] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12) *0, disabled.
[  184.967595] ACPI: PCI Interrupt Link [LNKG] (IRQs *3 4 5 6 7 9 10 11 12)
[  184.968760] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11 12)
[  184.969971] ACPI: Power Resource [URP1] (off)
[  184.970127] ACPI: Power Resource [URP2] (off)
[  184.970281] ACPI: Power Resource [FDDP] (off)
[  184.970436] ACPI: Power Resource [LPTP] (off)
[  184.970550] Linux Plug and Play Support v0.97 (c) Adam Belay
[  184.970665] pnp: PnP ACPI init
[  184.970790] ACPI: bus type pnp registered
[  184.976452] pnp: PnP ACPI: found 12 devices
[  184.976556] ACPI: ACPI bus type pnp unregistered
[  184.976654] PnPBIOS: Disabled by ACPI PNP
[  184.976868] PCI: Using ACPI for IRQ routing
[  184.976965] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[  184.979937] NET: Registered protocol family 8
[  184.980030] NET: Registered protocol family 20
[  184.980281] pnp: 00:0b: iomem range 0x0-0x9ffff could not be reserved
[  184.980386] Time: tsc clocksource has been installed.
[  184.980544] pnp: 00:0b: iomem range 0xe0000-0xfffff could not be reserved
[  184.980643] pnp: 00:0b: iomem range 0x100000-0xfffffff could not be reserved
[  184.980739] pnp: 00:0b: iomem range 0x0-0x0 could not be reserved
[  185.011505] PCI: Bridge: 0000:00:01.0
[  185.011599]   IO window: disabled.
[  185.011695]   MEM window: fc900000-fe9fffff
[  185.011789]   PREFETCH window: f0600000-f46fffff
[  185.011891] PCI: Bridge: 0000:00:1e.0
[  185.011983]   IO window: d000-dfff
[  185.012079]   MEM window: fea00000-feafffff
[  185.012173]   PREFETCH window: f4700000-f47fffff
[  185.012285] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[  185.012315] NET: Registered protocol family 2
[  185.052447] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[  185.052644] TCP established hash table entries: 8192 (order: 4, 98304 bytes)
[  185.052998] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[  185.053285] TCP: Hash tables configured (established 8192 bind 8192)
[  185.053382] TCP reno registered
[  185.064655] checking if image is initramfs...<6>Switched to high resolution mode on CPU 0
[  185.775854]  it is
[  186.642745] Freeing initrd memory: 9008k freed
[  186.643140] Simple Boot Flag at 0x7a set to 0x1
[  186.643794] audit: initializing netlink socket (disabled)
[  186.643923] audit(1212574387.480:1): initialized
[  186.649312] VFS: Disk quotas dquot_6.5.1
[  186.649618] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[  186.649978] io scheduler noop registered
[  186.650075] io scheduler anticipatory registered
[  186.650168] io scheduler deadline registered
[  186.650312] io scheduler cfq registered (default)
[  186.650457] Boot video device is 0000:01:00.0
[  186.650795] isapnp: Scanning for PnP cards...
[  187.004687] isapnp: No Plug & Play device found
[  187.082185] Real Time Clock Driver v1.12ac
[  187.082468] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[  187.082695] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[  187.084632] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[  187.086428] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[  187.087152] input: Macintosh mouse button emulation as /class/input/input0
[  187.087437] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[  187.090787] serio: i8042 KBD port at 0x60,0x64 irq 1
[  187.090892] serio: i8042 AUX port at 0x60,0x64 irq 12
[  187.091421] mice: PS/2 mouse device common for all mice
[  187.091770] EISA: Probing bus 0 at eisa.0
[  187.091910] EISA: Detected 0 cards.
[  187.092213] TCP cubic registered
[  187.092338] NET: Registered protocol family 1
[  187.092487] Using IPI No-Shortcut mode
[  187.092897]   Magic number: 12:525:223
[  187.093044]   hash matches device ttyu7
[  187.093148]   hash matches device ttyra
[  187.094405] Freeing unused kernel memory: 364k freed
[  187.127061] input: AT Translated Set 2 keyboard as /class/input/input1
[  187.537317] fuse init (API version 7.8)
[  187.551902] Capability LSM initialized
[  188.924308] SCSI subsystem initialized
[  188.947688] libata version 2.21 loaded.
[  188.954587] ata_piix 0000:00:1f.1: version 2.11
[  188.954703] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[  188.954940] scsi0 : ata_piix
[  188.955133] scsi1 : ata_piix
[  188.955463] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001ffa0 irq 14
[  188.955570] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001ffa8 irq 15
[  189.014594] usbcore: registered new interface driver usbfs
[  189.014748] usbcore: registered new interface driver hub
[  189.014897] usbcore: registered new device driver usb
[  189.018533] USB Universal Host Controller Interface driver v3.0
[  189.055419] Linux Tulip driver version 1.1.15 (Feb 27, 2007)
[  189.118064] ata1.00: ATA-5: ST340016A, 3.05, max UDMA/100
[  189.118171] ata1.00: 78165360 sectors, multi 16: LBA 
[  189.125952] ata1.00: configured for UDMA/100
[  189.365640] Floppy drive(s): fd0 is 1.44M
[  189.434767] FDC 0 is a post-1991 82077
[  189.610659] ata2.00: ATAPI: Lite-On LTN483S 48x Max, PD02, max UDMA/33, CDB intr
[  189.610784] ata2.01: ATAPI: SONY    CD-RW  CRX140E, 1.0n, max UDMA/33
[  189.782332] ata2.00: configured for UDMA/33
[  189.953293] ata2.01: configured for UDMA/33
[  189.953651] scsi 0:0:0:0: Direct-Access     ATA      ST340016A        3.05 PQ: 0 ANSI: 5
[  189.958653] scsi 1:0:0:0: CD-ROM            Lite-On  LTN483S 48x Max  PD02 PQ: 0 ANSI: 5
[  189.961959] scsi 1:0:1:0: CD-ROM            SONY     CD-RW  CRX140E   1.0n PQ: 0 ANSI: 5
[  189.970892] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 10
[  189.971001] PCI: setting IRQ 10 as level-triggered
[  189.971007] ACPI: PCI Interrupt 0000:00:1f.2[D] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
[  189.971284] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[  189.971292] uhci_hcd 0000:00:1f.2: UHCI Host Controller
[  189.971677] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
[  189.971817] uhci_hcd 0000:00:1f.2: irq 10, io base 0x0000ef80
[  189.972220] usb usb1: configuration #1 chosen from 1 choice
[  189.972393] hub 1-0:1.0: USB hub found
[  189.972502] hub 1-0:1.0: 2 ports detected
[  190.019510] sd 0:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[  190.019696] sd 0:0:0:0: [sda] Write Protect is off
[  190.019792] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  190.019831] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  190.020058] sd 0:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[  190.020173] sd 0:0:0:0: [sda] Write Protect is off
[  190.020268] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  190.020304] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  190.020415]  sda: sda1 sda2 sda3 < sda5 >
[  190.063826] sd 0:0:0:0: [sda] Attached SCSI disk
[  190.075263] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 3
[  190.075371] PCI: setting IRQ 3 as level-triggered
[  190.075377] ACPI: PCI Interrupt 0000:02:0a.0[A] -> Link [LNKG] -> GSI 3 (level, low) -> IRQ 3
[  190.076179] tulip0:  MII transceiver #1 config 1000 status 786d advertising 01e1.
[  190.081811] eth0: ADMtek Comet rev 17 at Port 0xd800, 00:0C:41:1B:28:B7, IRQ 3.
[  190.082777] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
[  190.082873] PCI: setting IRQ 11 as level-triggered
[  190.082879] ACPI: PCI Interrupt 0000:02:0b.0[A] -> Link [LNKH] -> GSI 11 (level, low) -> IRQ 11
[  190.083149] 3c59x: Donald Becker and others.
[  190.083250] 0000:02:0b.0: 3Com PCI 3c905B Cyclone 100baseTx at d08e8800.
[  190.111891] sd 0:0:0:0: Attached scsi generic sg0 type 0
[  190.112420] sr 1:0:0:0: Attached scsi generic sg1 type 5
[  190.112948] scsi 1:0:1:0: Attached scsi generic sg2 type 5
[  190.141538] sr0: scsi3-mmc drive: 48x/48x cd/rw xa/form2 cdda tray
[  190.141653] Uniform CD-ROM driver Revision: 3.20
[  190.142519] sr 1:0:0:0: Attached scsi CD-ROM sr0
[  190.212281] sr1: scsi3-mmc drive: 32x/32x writer cd/rw xa/form2 cdda tray
[  190.212986] sr 1:0:1:0: Attached scsi CD-ROM sr1
[  190.312927] usb 1-1: new low speed USB device using uhci_hcd and address 2
[  190.481806] usb 1-1: configuration #1 chosen from 1 choice
[  190.553678] Attempting manual resume
[  190.553776] swsusp: Resume From Partition 8:5
[  190.553780] PM: Checking swsusp image.
[  190.554245] PM: Resume from disk failed.
[  190.627655] kjournald starting.  Commit interval 5 seconds
[  190.627779] EXT3-fs: mounted filesystem with ordered data mode.
[  190.724626] usb 1-2: new full speed USB device using uhci_hcd and address 3
[  190.899464] usb 1-2: configuration #1 chosen from 1 choice
[  190.902503] usbcore: registered new interface driver hiddev
[  190.917992] input: USB Optical Mouse as /class/input/input2
[  190.918142] input: USB HID v1.10 Mouse [USB Optical Mouse] on usb-0000:00:1f.2-1
[  190.918434] usbcore: registered new interface driver usbhid
[  190.918533] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[  199.491340] eth1:  setting half-duplex.
[  201.092861] NET: Registered protocol family 17
[  202.390757] 0000:02:0a.0: tulip_stop_rxtx() failed (CSR5 0xfc664010 CSR6 0xff972113)
[  202.390775] eth0: Setting full-duplex based on MII#1 link partner capability of 45e1.
[  202.650973] Linux agpgart interface v0.102 (c) Dave Jones
[  202.659787] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[  202.687436] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[  202.915809] intel_rng: Firmware space is locked read-only. <4>intel_rng: If you can't or
[  202.915816]  don't want to <4>intel_rng: disable this in firmware setup, and <4>intel_rng: if
[  202.915820]  you are certain that your <4>intel_rng: system has a functional
[  202.915824]  RNG, try<4>intel_rng: using the 'no_fwh_detect' option.
[  202.943793] agpgart: Detected an Intel i815 Chipset.
[  202.948085] agpgart: AGP aperture is 64M @ 0xf8000000
[  202.985729] iTCO_vendor_support: vendor-support=0
[  202.989026] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[  202.989276] iTCO_wdt: Found a ICH2 TCO device (Version=1, TCOBASE=0x0460)
[  202.989483] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[  203.588959] input: PC Speaker as /class/input/input3
[  204.772151] parport_pc 00:09: reported by Plug and Play ACPI
[  204.772337] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[  205.209423] usbcore: registered new interface driver libusual
[  205.375236] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[  205.376782] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[  205.496319] Initializing USB Mass Storage driver...
[  205.501166] scsi2 : SCSI emulation for USB Mass Storage devices
[  205.504199] usb-storage: device found at 3
[  205.504208] usb-storage: waiting for device to settle before scanning
[  205.504257] usbcore: registered new interface driver usb-storage
[  205.504363] USB Mass Storage support registered.
[  205.872656] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 9
[  205.872765] PCI: setting IRQ 9 as level-triggered
[  205.872770] ACPI: PCI Interrupt 0000:02:0c.0[A] -> Link [LNKB] -> GSI 9 (level, low) -> IRQ 9
[  207.959769] lp0: using parport0 (interrupt-driven).
[  208.044939] Adding 746980k swap on /dev/sda5.  Priority:-1 extents:1 across:746980k
[  208.405302] EXT3 FS on sda2, internal journal
[  210.501521] usb-storage: device scan complete
[  210.504523] scsi 2:0:0:0: Direct-Access              USB FLASH DRIVE  PMAP PQ: 0 ANSI: 0 CCS
[  213.203297] sd 2:0:0:0: [sdb] 4030464 512-byte hardware sectors (2064 MB)
[  213.206283] sd 2:0:0:0: [sdb] Write Protect is off
[  213.206290] sd 2:0:0:0: [sdb] Mode Sense: 23 00 00 00
[  213.206296] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  213.218277] sd 2:0:0:0: [sdb] 4030464 512-byte hardware sectors (2064 MB)
[  213.221270] sd 2:0:0:0: [sdb] Write Protect is off
[  213.221276] sd 2:0:0:0: [sdb] Mode Sense: 23 00 00 00
[  213.221282] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  213.221385]  sdb: sdb1
[  213.227428] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[  213.227533] sd 2:0:0:0: Attached scsi generic sg3 type 0
[  394.579415] No dock devices found.
[  394.946132] input: Power Button (FF) as /class/input/input4
[  394.954657] ACPI: Power Button (FF) [PWRF]
[  395.020244] input: Power Button (CM) as /class/input/input5
[  395.020772] ACPI: Power Button (CM) [PBTN]
[  397.902598] ppdev: user-space parallel port driver
[  398.404550] Dell Dimension 4100 machine detected. Disabling APM.
[  398.404593] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[  398.404599] apm: disabled on user request.
[  399.152530] Bluetooth: Core ver 2.11
[  399.152757] NET: Registered protocol family 31
[  399.152764] Bluetooth: HCI device and connection manager initialized
[  399.152772] Bluetooth: HCI socket layer initialized
[  399.196473] Bluetooth: L2CAP ver 2.8
[  399.196483] Bluetooth: L2CAP socket layer initialized
[  399.209539] Bluetooth: RFCOMM socket layer initialized
[  399.209728] Bluetooth: RFCOMM TTY layer initialized
[  399.209734] Bluetooth: RFCOMM ver 1.8

=================
Thank you for your support,

---

