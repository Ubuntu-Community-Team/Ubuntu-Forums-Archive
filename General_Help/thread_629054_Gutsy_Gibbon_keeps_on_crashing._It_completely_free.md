---
title: "Gutsy Gibbon keeps on crashing. It completely freezes and locks up."
date: 2007-12-01
forum: General Help
---

### Post by mahasmb on 2007-12-01
Here are my specs

==Desktop==
3.0 Ghz (with Hyper-Threading) Intel Pentium IV Processor
512 MB RAM
120 GB Maxtor HDD (80 GB Ubuntu Ultimate 1.4 (Feisty Fawn), 40 GB Windows XP)
40 GB Seagate HDD (No OS, Just stored files with NTFS filesystem)
128 Integrated Graphics Card

===========

The computer used to lock up about once every two days or so, but it's done so almost ten times today!

I can't move the mouse or type anything and I have to press my reset button. This can happen while I'm on the computer (i.e. watching something, browsing the web) or even when I haven't touched the computer for hours (thus it would freeze in the middle of a screensaver).

I don't use Compiz, Beryl or Compiz fusion at all.

Is there any way I can fix this problem?

---

### Post by mahasmb on 2007-12-03
Right in the middle of watching a video, I was logged out. When I locked back in, all I saw was my mouse and nothing else loaded. So I restarted. The computer froze in the middle of the Ubuntu load up splash screen. So I had to restart again. I had to do this at least five times before I could finally reach my login screen and now everything seems to be working alright.

I don't know what's going on, but this is scary. I don't want to be unable to use my computer anymore.

Any idea what's wrong here?

---

### Post by -grubby on 2007-12-03
I'm guessing maybe something to do with your graphics, but who knows, I could be wrong. Another thing could be broken RAM modules or DIMM slots (the slots where RAM is held)

---

### Post by mahasmb on 2007-12-04
I just had to restart [SIZE="4"]**[COLOR="Red"]THIRTY (30)[/COLOR]**[/SIZE] times before I could even log in!

What's going on? I don't know what to do to fix this.

Edit: Two hours later my computer freezes again and I'm forced to reboot. I have to restart more than ten times before I can login again. This time I copied down the last line of the words I saw when booting failed. Each is from a different boot.

> [   69.102369] agpgart: AGP aperture is 128M @ 0xd0000000 udved-event [3708] : run_program: '/sbin/modprobe' abnormal exit


> [ 25.011753] hdd: hdd1

> [ 40.630919] hub 2-0:1.0: 2 ports detected

> [36.764422] pci_hotplug: PCI Hot Plug PCI Core version: 0.5

> *Loading hardware drivers...                [OK]

> [ 49.143380] input: PC Speaker  as /class/input/input2 udved-event[3893]: run_program: '/sbin/modprobe' abnormal exit


> [46.045559] Linux agpgart interface v0.102 (c) Dave Jones

> Begin: Waiting for root file system...

> [19.035220] USB Universal Host Controller Interface driver v3.0

---

### Post by mahasmb on 2007-12-04
I'm also unable to login to my Windows XP...

I guess this is a hardware problem?? What can I do though? I can't use my computer for longer than an hour...

---

### Post by onion221 on 2007-12-04
I don't know, but if this happened to me I would completely wipe my hard drive. Reinstall Windows then install Ubuntu. The computer I am using right now is basically the same specs as yours and I am fine. Save all your music etc and try that maybe. Except I have a 256 card.

---

### Post by mahasmb on 2007-12-04
I don't know about that. What if this continues to happen again? Especially if it's a hardware issue. Then I'd go through all that trouble for nothing. I don't like shooting in the dark.

dmesg
```
dmesg
[    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001bff0000 (usable)
[    0.000000]  BIOS-e820: 000000001bff0000 - 000000001bff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001bff3000 - 000000001c000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 447MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f5490
[    0.000000] Entering add_active_range(0, 0, 114672) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   114672
[    0.000000]   HighMem    114672 ->   114672
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   114672
[    0.000000] On node 0 totalpages: 114672
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 863 pages used for memmap
[    0.000000]   Normal zone: 109713 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.2 present.
[    0.000000] Intel MultiProcessor Specification v1.4
[    0.000000]     Virtual Wire compatibility mode.
[    0.000000] OEM ID: OEM00000 Product ID: PROD00000000 APIC at: 0xFEE00000
[    0.000000] Processor #0 15:3 APIC version 17
[    0.000000] I/O APIC #2 Version 17 at 0xFEC00000.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Processors: 1
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 1c000000:e2c00000)
[    0.000000] Built 1 zonelists.  Total pages: 113777
[    0.000000] Kernel command line: root=UUID=334b9d01-776c-4441-b944-ffdac0fb08d9 ro acpi=off
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 2995.063 MHz processor.
[   23.412037] Console: colour VGA+ 80x25
[   23.413886] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   23.414205] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   23.421752] Memory: 442892k/458688k available (2015k kernel code, 15172k reserved, 916k data, 364k init, 0k highmem)
[   23.421825] virtual kernel memory layout:
[   23.421826]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   23.421827]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   23.421829]     vmalloc : 0xdc800000 - 0xff7fe000   ( 559 MB)
[   23.421830]     lowmem  : 0xc0000000 - 0xdbff0000   ( 447 MB)
[   23.421831]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   23.421832]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
[   23.421833]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
[   23.422219] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   23.422351] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   23.502226] Calibrating delay using timer specific routine.. 5997.32 BogoMIPS (lpj=11994644)
[   23.502346] Security Framework v1.0.0 initialized
[   23.502399] SELinux:  Disabled at boot.
[   23.502458] Mount-cache hash table entries: 512
[   23.502635] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000041d 00000000 00000000
[   23.502645] monitor/mwait feature present.
[   23.502694] using mwait in idle threads.
[   23.502748] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   23.502835] CPU: L2 cache: 1024K
[   23.502883] CPU: Physical Processor ID: 0
[   23.502932] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b180 0000041d 00000000 00000000
[   23.502943] Compat vDSO mapped to ffffe000.
[   23.503005] Checking 'hlt' instruction... OK.
[   23.518319] SMP alternatives: switching to UP code
[   23.518511] Freeing SMP alternatives: 11k freed
[   23.518826] Early unpacking initramfs... done
[   23.812282] CPU0: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 03
[   23.812445] Total of 1 processors activated (5997.32 BogoMIPS).
[   23.812764] ExtINT not setup in hardware but reported by MP table
[   23.813295] ENABLING IO-APIC IRQs
[   23.813691] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=0 pin2=0
[   24.068787] Brought up 1 CPUs
[   24.068992] Booting paravirtualized kernel on bare hardware
[   24.069129] Time: 17:50:40  Date: 11/04/107
[   24.069200] NET: Registered protocol family 16
[   24.069338] EISA bus registered
[   24.077656] PCI: PCI BIOS revision 2.10 entry at 0xfbb30, last bus=1
[   24.077707] PCI: Using configuration type 1
[   24.077755] Setting up standard PCI resources
[   24.084232] ACPI: Interpreter disabled.
[   24.084282] Linux Plug and Play Support v0.97 (c) Adam Belay
[   24.084338] pnp: PnP ACPI: disabled
[   24.084388] PnPBIOS: Scanning system for PnP BIOS support...
[   24.084948] PnPBIOS: Found PnP BIOS installation structure at 0xc00fc5f0
[   24.085007] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xc620, dseg 0xf0000
[   24.086296] PnPBIOS: 14 nodes reported by PnP BIOS; 14 recorded by driver
[   24.086391] PCI: Probing PCI hardware
[   24.086454] PCI: Probing PCI hardware (bus 00)
[   24.087200] PCI: MSI-K8T-Neo2Fir, attempting to turn soundcard ON
[   24.087253] PCI: MSI-K8T-Neo2Fir, soundcard on
[   24.088899] PCI: Using IRQ router VIA [1106/3227] at 0000:00:11.0
[   24.088964] PCI->APIC IRQ transform: 0000:00:08.0[A] -> IRQ 16
[   24.089017] PCI->APIC IRQ transform: 0000:00:10.0[A] -> IRQ 21
[   24.089068] PCI->APIC IRQ transform: 0000:00:10.1[A] -> IRQ 21
[   24.089119] PCI->APIC IRQ transform: 0000:00:10.2[B] -> IRQ 21
[   24.089171] PCI->APIC IRQ transform: 0000:00:10.3[B] -> IRQ 21
[   24.089222] PCI->APIC IRQ transform: 0000:00:10.4[C] -> IRQ 21
[   24.089275] PCI->APIC IRQ transform: 0000:00:11.5[C] -> IRQ 22
[   24.089326] PCI->APIC IRQ transform: 0000:00:12.0[A] -> IRQ 23
[   24.089377] PCI->APIC IRQ transform: 0000:01:00.0[A] -> IRQ 16
[   24.131884] NET: Registered protocol family 8
[   24.131933] NET: Registered protocol family 20
[   24.132043] pnp: 00:07: iomem range 0x0-0x9ffff could not be reserved
[   24.132096] pnp: 00:07: iomem range 0xfffe0000-0xffffffff could not be reserved
[   24.132155] pnp: 00:07: iomem range 0xfec00000-0xfec0ffff could not be reserved
[   24.132214] pnp: 00:07: iomem range 0xfee00000-0xfee0ffff could not be reserved
[   24.132275] pnp: 00:08: iomem range 0xf0000-0xf3fff could not be reserved
[   24.132327] pnp: 00:08: iomem range 0xf4000-0xf7fff could not be reserved
[   24.132378] pnp: 00:08: iomem range 0xf8000-0xfffff could not be reserved
[   24.132430] pnp: 00:08: iomem range 0xd0000-0xd3fff has been reserved
[   24.132585] Time: tsc clocksource has been installed.
[   24.132856] PCI: Bridge: 0000:00:01.0
[   24.132905]   IO window: disabled.
[   24.132957]   MEM window: dc000000-ddffffff
[   24.133008]   PREFETCH window: d8000000-dbffffff
[   24.133073] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   24.133084] NET: Registered protocol family 2
[   24.160555] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   24.160644] TCP established hash table entries: 16384 (order: 5, 196608 bytes)
[   24.160834] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   24.160961] TCP: Hash tables configured (established 16384 bind 16384)
[   24.161013] TCP reno registered
[   24.172605] checking if image is initramfs... it is
[   24.748610] Freeing initrd memory: 7313k freed
[   24.749128] audit: initializing netlink socket (disabled)
[   24.749193] audit(1196790640.108:1): initialized
[   24.751330] VFS: Disk quotas dquot_6.5.1
[   24.751438] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   24.751622] io scheduler noop registered
[   24.751671] io scheduler anticipatory registered
[   24.751720] io scheduler deadline registered
[   24.751782] io scheduler cfq registered (default)
[   24.751844] PCI: VIA PCI bridge detected. Disabling DAC.
[   24.751958] PCI: Bypassing VIA 8237 APIC De-Assert Message
[   24.752015] Boot video device is 0000:01:00.0
[   24.752145] isapnp: Scanning for PnP cards...
[   25.105610] isapnp: No Plug & Play device found
[   25.131625] Real Time Clock Driver v1.12ac
[   25.131759] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   25.131911] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   25.132729] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   25.133543] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   25.133831] input: Macintosh mouse button emulation as /class/input/input0
[   25.134020] PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
[   25.134520] serio: i8042 KBD port at 0x60,0x64 irq 1
[   25.134573] serio: i8042 AUX port at 0x60,0x64 irq 12
[   25.134797] mice: PS/2 mouse device common for all mice
[   25.134962] EISA: Probing bus 0 at eisa.0
[   25.135048] EISA: Detected 0 cards.
[   25.135261] TCP cubic registered
[   25.135320] NET: Registered protocol family 1
[   25.135391] Using IPI No-Shortcut mode
[   25.135526]   Magic number: 3:926:844
[   25.135711]   hash matches device ptyrd
[   25.136076] Freeing unused kernel memory: 364k freed
[   25.210609] input: AT Translated Set 2 keyboard as /class/input/input1
[   25.317771] AppArmor: AppArmor initialized<5>audit(1196790640.608:2):  type=1505 info="AppArmor initialized" pid=1110
[   25.326674] fuse init (API version 7.8)
[   25.331617] Failure registering capabilities with primary security module.
[   25.361926] thermal: Unknown symbol acpi_processor_set_thermal_limit
[   25.877038] 3c59x: Donald Becker and others.
[   25.877097] 0000:00:08.0: 3Com PCI 3c905B Cyclone 100baseTx at dc80e000.
[   25.911856] SCSI subsystem initialized
[   25.917361] libata version 2.21 loaded.
[   25.923491] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   25.923548] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   25.936594] usbcore: registered new interface driver usbfs
[   25.936678] usbcore: registered new interface driver hub
[   25.936750] usbcore: registered new device driver usb
[   25.937636] USB Universal Host Controller Interface driver v3.0
[   25.937768] uhci_hcd 0000:00:10.0: UHCI Host Controller
[   25.937975] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[   25.938063] uhci_hcd 0000:00:10.0: irq 21, io base 0x0000c800
[   25.938221] usb usb1: configuration #1 chosen from 1 choice
[   25.938299] hub 1-0:1.0: USB hub found
[   25.938353] hub 1-0:1.0: 2 ports detected
[   26.016546] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[   26.016606] via-rhine: Broken BIOS detected, avoid_D3 enabled.
[   26.039764] uhci_hcd 0000:00:10.1: UHCI Host Controller
[   26.039843] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[   26.039925] uhci_hcd 0000:00:10.1: irq 21, io base 0x0000cc00
[   26.040073] usb usb2: configuration #1 chosen from 1 choice
[   26.040151] hub 2-0:1.0: USB hub found
[   26.040205] hub 2-0:1.0: 2 ports detected
[   26.141283] Floppy drive(s): fd0 is 1.44M
[   26.143421] uhci_hcd 0000:00:10.2: UHCI Host Controller
[   26.143499] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[   26.143579] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000d000
[   26.143731] usb usb3: configuration #1 chosen from 1 choice
[   26.143808] hub 3-0:1.0: USB hub found
[   26.143863] hub 3-0:1.0: 2 ports detected
[   26.162296] FDC 0 is a post-1991 82077
[   26.247139] uhci_hcd 0000:00:10.3: UHCI Host Controller
[   26.247220] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[   26.247302] uhci_hcd 0000:00:10.3: irq 21, io base 0x0000d400
[   26.247449] usb usb4: configuration #1 chosen from 1 choice
[   26.247531] hub 4-0:1.0: USB hub found
[   26.247584] hub 4-0:1.0: 2 ports detected
[   26.351738] VP_IDE: IDE controller at PCI slot 0000:00:0f.0
[   26.351817] VP_IDE: chipset revision 6
[   26.351865] VP_IDE: not 100% native mode: will probe irqs later
[   26.351926] VP_IDE: VIA vt8237 (rev 00) IDE UDMA133 controller on pci0000:00:0f.0
[   26.351990]     ide0: BM-DMA at 0xc400-0xc407, BIOS settings: hda:DMA, hdb:DMA
[   26.352130]     ide1: BM-DMA at 0xc408-0xc40f, BIOS settings: hdc:DMA, hdd:DMA
[   26.352266] Probing IDE interface ide0...
[   26.877434] hda: HL-DT-ST DVDRAM GSA-4167B, ATAPI CD/DVD-ROM drive
[   27.172559] usb 4-2: new full speed USB device using uhci_hcd and address 2
[   27.319406] usb 4-2: configuration #1 chosen from 1 choice
[   27.659367] hdb: CD-ROM CDU701-F, ATAPI CD/DVD-ROM drive
[   27.716171] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   27.716320] Probing IDE interface ide1...
[   28.130123] hdc: Maxtor 6Y120L0, ATA DISK drive
[   28.409385] hdd: ST340810A, ATA DISK drive
[   28.471045] ide1 at 0x170-0x177,0x376 on irq 15
[   28.471561] ehci_hcd 0000:00:10.4: EHCI Host Controller
[   28.471745] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
[   28.471842] ehci_hcd 0000:00:10.4: irq 21, io mem 0xdf001000
[   28.471897] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   28.472272] usb usb5: configuration #1 chosen from 1 choice
[   28.472458] hub 5-0:1.0: USB hub found
[   28.472512] hub 5-0:1.0: 8 ports detected
[   28.494670] hda: ATAPI 79X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
[   28.495032] Uniform CD-ROM driver Revision: 3.20
[   28.512476] hdb: ATAPI 32X CD-ROM drive, 128kB Cache, DMA
[   28.531222] hdc: max request size: 128KiB
[   28.546105] hdc: 240121728 sectors (122942 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(33)
[   28.546476] hdc: cache flushes supported
[   28.546577]  hdc: hdc1 hdc2 hdc3
[   28.556401] hdd: max request size: 128KiB
[   28.557420] hdd: 78165360 sectors (40020 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(33)
[   28.557628] hdd: cache flushes not supported
[   28.557706]  hdd: hdd1
[   28.577136] eth1: VIA Rhine II at 0x1e000, 00:11:5b:1b:ce:b5, IRQ 23.
[   28.578122] eth1: MII PHY found at address 1, status 0x7849 advertising 01e1 Link 0000.
[   28.812228] usb 5-8: new high speed USB device using ehci_hcd and address 2
[   28.944344] usb 5-8: configuration #1 chosen from 1 choice
[   28.944635] usb 4-2: USB disconnect, address 2
[   38.489803] Attempting manual resume
[   38.489856] swsusp: Resume From Partition 22:1
[   38.489858] PM: Checking swsusp image.
[   38.507877] PM: Resume from disk failed.
[   38.527317] EXT3-fs: INFO: recovery required on readonly filesystem.
[   38.527376] EXT3-fs: write access will be enabled during recovery.
[   45.580509] kjournald starting.  Commit interval 5 seconds
[   45.580580] EXT3-fs: hdc2: orphan cleanup on readonly fs
[   45.580636] ext3_orphan_cleanup: deleting unreferenced inode 1688216
[   45.580664] ext3_orphan_cleanup: deleting unreferenced inode 1654806
[   45.580673] ext3_orphan_cleanup: deleting unreferenced inode 1654805
[   45.580679] ext3_orphan_cleanup: deleting unreferenced inode 1654802
[   45.580685] ext3_orphan_cleanup: deleting unreferenced inode 1654801
[   45.580691] ext3_orphan_cleanup: deleting unreferenced inode 1654795
[   45.580696] EXT3-fs: hdc2: 6 orphan inodes deleted
[   45.580746] EXT3-fs: recovery complete.
[   45.673991] EXT3-fs: mounted filesystem with ordered data mode.
[   57.987912] input: PC Speaker as /class/input/input2
[   58.958675] input: ImPS/2 Logitech Wheel Mouse as /class/input/input3
[   60.348493] parport_pc 00:0e: reported by Plug and Play BIOS
[   60.348630] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   61.157004] Linux agpgart interface v0.102 (c) Dave Jones
[   61.191725] agpgart: Detected VIA PM800/PN800/PM880/PN880 chipset
[   61.199715] agpgart: AGP aperture is 128M @ 0xd0000000
[   61.222319] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   61.225189] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   66.476763] PCI: Setting latency timer of device 0000:00:11.5 to 64
[   67.376431] lp0: using parport0 (interrupt-driven).
[   67.413612] ndiswrapper version 1.45 loaded (smp=yes)
[   67.581803] usb 5-8: reset high speed USB device using ehci_hcd and address 2
[   67.739222] ndiswrapper: driver sis163u (TRENDnet,11/02/2005,5.1.1039.1050) loaded
[   68.160952] wlan0: ethernet device 00:40:f4:e0:10:4a using NDIS driver: sis163u, version: 0x1000000, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 0457:0163.F.conf
[   68.162225] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   68.162341] usbcore: registered new interface driver ndiswrapper
[   68.205835] Adding 746980k swap on /dev/hdc1.  Priority:-1 extents:1 across:746980k
[  358.569627] EXT3 FS on hdc2, internal journal
[  364.538679] acpi_cpufreq: Unknown symbol acpi_processor_notify_smm
[  364.538725] acpi_cpufreq: Unknown symbol acpi_processor_unregister_performance
[  364.538846] acpi_cpufreq: Unknown symbol acpi_processor_preregister_performance
[  364.538904] acpi_cpufreq: Unknown symbol acpi_processor_register_performance
[  371.346159] NET: Registered protocol family 10
[  371.346245] lo: Disabled Privacy Extensions
[  372.646287] [drm] Initialized drm 1.1.0 20060810
[  372.686013] [drm] Initialized via 2.11.1 20070202 on minor 0
[  372.764203] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[  372.764224] agpgart: Device is in legacy mode, falling back to 2.x
[  372.764231] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[  372.764300] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[  378.949592] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[  390.667040] UDF-fs: Partition marked readonly; forcing readonly mount
[  390.708055] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'ARJUNA_6_TO_13_WOLFS_RAIN_1__1', timestamp 2005/03/22 09:42 (1ed4)
[  409.259137] rpcbind: server localhost not responding, timed out
[  409.259166] RPC: failed to contact local rpcbind server (errno 5).
[  416.427982] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  434.677282] eth0: link down
[  434.677545] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  439.326552] rpcbind: server localhost not responding, timed out
[  439.326587] RPC: failed to contact local rpcbind server (errno 5).
[  446.944931] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  448.590360] NET: Registered protocol family 17
[  448.727020] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

```

---

### Post by onion221 on 2007-12-04
Have you recently tried to install any hardware ram etc?

---

### Post by mahasmb on 2007-12-04
Nope. I haven't even opened my case.

---

### Post by -grubby on 2007-12-05
let's hope not but, maybe your motherboard is going?

---

### Post by marvinrichards on 2007-12-05
Sounds like a heat problem.  Check the air vents in the back of the computer- if the vents are dirty, the inside is dirty.   Open the case and clean the inside.  Check the fans and make sure they are running and clean.  Use compressed air to clean and don't touch anything inside unless you know what you are doing.  You won't get shocked but static electricity  will mess up the system.

---

### Post by mahasmb on 2007-12-05
Thanks. I'll do that.

---

### Post by jmate24 on 2007-12-12
mine is a hard drive problem. i have to set tune2fs to check my hard drives at every boot so that i can access my folders and files

```

$sudo fdisk -l
[sudo] password for jmate24:

Disk /dev/hda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbbafbbaf

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       14946   120053713+  83  Linux

Disk /dev/hdd: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbbf1bbf1

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1        9964    80035798+  83  Linux
$ sudo tune2fs -c 1 /dev/hda1
$ sudo tune2fs -c 1 /dev/hdd1
```

where hda1 is my /home and hdd1 is my /.
and make sure that you use the correct drive and partition /dev/hdx1,2,3...n.
where x is the drive letter and 1-n are your partition numbers.:)

---

### Post by mahasmb on 2007-12-20
The problem seemed to get better. Then it got worse with the computer continually restarting.

I did a memtest (Thank goodness Ubuntu has it at the bootup screen) and I gotat least 14 errors. Does this definitely mean I have bad RAM? Or could it be something else? Or bad RAM plus something else?

---

### Post by mahasmb on 2008-01-03
So... I got some brand new RAM and just installed it. The computer still keeps on restarting. I did another memtest with the new RAM and no errors showed up.

A friend of mine is saying the problem is likely the power supply unit.

I've already spent money on new RAM, what are the chances that even if I do buy a new PSU that it will actually solve my problem?

Also, I have no idea how to figure out what kind of power supply unit my desktop needs.

---

### Post by mahasmb on 2008-01-04
I'm not so sure it's a hardware problem anymore... I've tried two different PSU's but only Ubuntu seems to be giving me some problems.

Ubuntu keeps on restarting, while Windows XP appears to work fine (it's actually working just a little faster because of the memory upgrade).

Any ideas on this? Could it be just a software problem?

---

### Post by amdalex on 2008-01-04
Does your other Ubuntu install work?

---

### Post by mahasmb on 2008-01-04
I only have one Ubuntu installed on the computer. I don't know what you mean.

---

### Post by roachk71 on 2008-01-04
I've scanned through your **dmesg** output, and found one potential issue:
```


[   26.016546] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[   26.016606] via-rhine: Broken BIOS detected, avoid_D3 enabled.

```I have had a look into the forums for a couple of other distributions, and it would appear Mepis and others are having a problem with the latest 2.6 kernels and Via Rhine chipsets and BIOS, as well. If your motherboard's BIOS has an option for a Plug-n-Play (PNP) OS, try enabling that and see if that helps the problem any. This option tells the BIOS to allow the operating system to initialize non-boot devices instead of the bugged MB BIOS.

UPDATE: It would appear to indeed be a kernel bug (in the 2.6.18 - 2.6.22 kernels). Here's a [link]("http://lists.debian.org/debian-kernel/2007/09/msg00285.html") to the Debian lists page regarding poor Via SATA performance with this issue.

My advice, if this solution doesn't work (or there's no supporting BIOS option), is to revert to 6.06 LTS and stick with it until a few months after 8.04 LTS is released in April. The LTS (Long-Term Support) releases have their main focus in the stability department, whereas the others are usually technology preview and non-critical improvement releases, and many have stability issues to boot.

Another option would be using Windows to download and apply a firmware update to your BIOS chip (**WARNING:** This is very risky. If the power goes out or another problem interrupts the BIOS update, your machine could be unusable until the chip's replaced. Proceed with caution.)

---

### Post by mahasmb on 2008-01-06
Alright, the PNP option I don't seem to have, so I'm trying out Live CD's of Gutsy and Dapper Drake. The Dapper Drake Live CD does indeed seem to be more stable. But I'm still wondering, I've been using Gutsy Gibbon since the day it came out. What could possibly have changed recently to make my Gutsy Gibbon less stable?

---

### Post by roachk71 on 2008-01-06
The cause(s) could be any one or more of several factors. In a modular system such as GNU/Linux, these are too numerous to list here (Even Ubuntu's repositories have tens of thousands of packages.)

Could be a bad kernel patch (which seems to be the case here), the latest X server updates, etc...It really is hard to be certain.

I like to compile custom kernels from time to time, and even that seems to go wrong every once-in-a-while, at least until the devs fix certain package issues.

All in all, though, I wouldn't switch my dual-core, 64-bit machine back to an expensive 32-bit Vista if they tried to force me. Ubuntu may have a rather steep learning curve, but it still rocks. :guitar:

---

### Post by Northsider on 2008-01-07
I'm finding that Gusty is locking up on me as well.  I am forced to hard-reset and sometimes during the boot it just shuts down.

---

### Post by union guy on 2008-01-13
I am having a problem with Gutsy (Ubuntu Ultimate 1.6) freezing.  Never happened with earlier editions (was last running UU 1.4).  I am running three year old 2GHZ AMD on cheap board w/ 512 ram.  Usually freezes at point of some application start, but not every time except for Wine.  When I try to start Wine it freezes every time.  I was surprised that this was the only "Gutsy freezing" thread I could find.  Any thoughts anyone?  Are there really so few people having problems with Gutsy freezing?

---

### Post by jmate24 on 2008-02-04
union guy:
          "i am having a problem with Gutsy (Ubuntu Ultimate 1.6) freezing. Never happened with earlier editions (was last running UU 1.4). I am running three year old 2GHZ AMD on cheap board w/ 512 ram."

More RAM if you can afford it.

---

### Post by photismos on 2008-02-22
Think this was one of the threads I'd combed through before trying to find an answer to my freezing problems...  Happy to say I did finally.  I noticed in my BIOS there are ACPI settings as well...wonder if it's related to the freezing; so I'll post this here as a possible solution although my freezes weren't as frequent as described here...but it may be worth a try =)  Here's my cut-paste:  

I'm very new to Linux, but I was having very similar errors....random freezing (even restarts at times) but usually still able to use my mouse, although to no avail since nothing was selectable, and of course the keyboard was completely useless (frozen)...nothing worked. It was happening intermittently, wondered if it was Firefox or my movie player or my NVIDIA driver something I was doing...NOT SO!  

I searched a few threads here and found that editing "/boot/grub/menu.lst" adding just two little words..."noapic nolapic" fixed it COMPLETELY. Since then I've had no freezes at all.

Here's where the those "words" went in the context of my menu.lst, if it helps you to know where to put it:

## ## End Default Options ##

title Ubuntu 7.10, kernel 2.6.22-14-rt
root (hd0,1)
kernel /boot/vmlinuz-2.6.22-14-rt root=UUID=56ef75eb-5ce9-4863-a4ee-2d4d2a167847 ro noapic nolapic quiet splash
initrd /boot/initrd.img-2.6.22-14-rt
quiet

...AND that's it. you put it in that "kernel" line and restart. Hope it helps. If it does, would be nice if you confirmed that for others... =) That's what I'm doing...trying to find the original thread(s) I found this solution in to confirm it works! =D ...well, again...hope it helps!

---

### Post by elnamo on 2008-02-26
I'm facing the same issue where gutsy suddenly freeze. 

Some other intermittent issues

XMMX freezes  
Firefox crashes repeatedly, but since it also crashes a lot on Windows I suspect that it's a Firefox issue.


The problem seems to start about a week ago, right after the system updates. 

Looking forward to try the noapic nolapic solution.

---

### Post by kallek on 2008-03-20
Reply to photismos:

I'm also having problems with freezing, and I tried adding "noapic nolapic" to /boot/grub/menu.lst, but unfortunately, it didn't help.

My computer started freezing just yesterday, after having worked perfectly for 2 weeks (fresh install). It starts freezing a few minutes after I boot and log in. First, the mouse partially freezes, I can move it, but not click, and a minute or so later, the also keyboard freezes. Eventually I cannot move the mouse either. A couple of times, before the keyboard has frozen (only the mouse frozen), I have pressed ctr+alt+F1, or ctr+alt+backspace in order to leave or restart the graphics, but with the only result that the screen and keyboard will freeze completely during the nvidia splash screen.

The computer:
Gutsy 64-bit/xp 32-bit dual boot (xp works fine)
AMD Opteron Processor 250
3.50 GB RAM
Graphics: Nvidia Quadro FX 1400

Any advice is very welcome,
thanks
kallek

---

