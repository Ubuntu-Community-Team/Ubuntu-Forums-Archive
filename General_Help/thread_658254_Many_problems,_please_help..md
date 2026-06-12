---
title: "Many problems, please help."
date: 2008-01-04
forum: General Help
---

### Post by Preyor on 2008-01-04
I am having many problems, any and all help would be appreciated.
I recently installed xubuntu on my compaq 7110US (factory specs, im soon going to upgrade the ram and video card, advice on this would also be appreciated.) and i love it, with a few problems. first is my apparent lack of any 3d capability whatsoever, I installed several games via both synaptic and add/remove programs and it seems only the 2d ones work. Having researched this problem, i thought i'd found i needed legacy drivers, but when i downloaded them and finally worked through the ridiculous settings it put my monitor in, i still had no 3d, and only one desktop to play with. Next is wine, one of the main selling points it seemed when i was first downloading linux, it seems unwilling to work at all, ive gotten virtually no programs to run in it, they all seem to have errors attached, The programs ive tried to run are MapleStory, ForexTrainer, imvu, and various mmo's and various zip crackers, to name a few. (though pico zip recovery tool works fine, if that means anything to you) My usb devices dont seem to work either, i plug in my phone, and it recognizes it is there, but i seem to be unable to access the filesystem. I plug in my scanner, which, on a previous installation (ubuntu) worked fine, now isnt even recognized. Also, i got the game the mana world to work once when i first installed it, but now when i click it nothing happens, i tried un/reinstalling, using add/remove, and synaptic, but it didnt work.

Any and all help is greatly appreciated.

---

### Post by dannyboy79 on 2008-01-04
ok, one issue at a time. first the video card

please post the output of this command

lspci

that'll show me which video card you're using. then I can help you get the proper graphics card module loaded so you can then play games in wine. please also post your /etc/X11/xorg.conf contents here as well. or paste them at pastebin.org and then paste teh link here.

---

### Post by Preyor on 2008-01-04
the output of the command is:

00:00.0 Host bridge: Advanced Micro Devices [AMD] AMD-760 [IGD4-1P] System Controller (rev 12)
00:01.0 PCI bridge: Advanced Micro Devices [AMD] AMD-760 [IGD4-1P] AGP Bridge
00:06.0 FireWire (IEEE 1394): Texas Instruments TSB12LV26 IEEE-1394 Controller (Link)
00:07.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 09)
00:09.0 Ethernet controller: Accton Technology Corporation SMC2-1211TX (rev 10)
00:0a.0 Modem: PCTel Inc HSP MicroModem 56 (rev 02)
00:14.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
00:14.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:14.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)
00:14.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)
00:14.4 Bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
01:05.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev a1)

and i cant seem to copy/paste xorg.conf.

---

### Post by dannyboy79 on 2008-01-04
here's some tips that'll help:

[http://ubuntuforums.org/showthread.php?t=596469](http://ubuntuforums.org/showthread.php?t=596469)

or also here:
[http://ubuntuforums.org/showthread.php?t=194955](http://ubuntuforums.org/showthread.php?t=194955)

---

### Post by Preyor on 2008-01-05
Thank you, that worked wonderfully, and ive even got a few programs running in wine. now if you could just help me with the fact that none of my executables work (i have to download either via synaptic, or add/remove) it said somewhere that it needed g++ but downloading this hasn't helped me at all. this very appreciated. and i'm looking forward to having a fully functional system.

---

### Post by dannyboy79 on 2008-01-05
well I need to know exactly what program you're trying to run and you're referring to programs when you say executables right? do you mean that you're trying to complile programs and they aren't compiling? if that's the case issue this command

sudo aptitude install build-essential

that will install the compiling tools needed.

---

### Post by Preyor on 2008-01-05
well, that command seemed to remove quite a few programs i had installed but never used, but it didnt install anything, and i still cant run executable programs. the programs i was trying to install are regnum online, and planeshift. regnum online gives me something called rolauncher, and all that is says is its an executable, planeshift gives me a .bin, but xubuntu asks me what i want to open it with. This is greatly appreciated, and if i can download my own programs (not depend on synaptic, or add/remove) and get my usb devices working, this will be more than worth the switch. Once again, thank you for your help.

---

### Post by dannyboy79 on 2008-01-05
I am using feisty fawn and able to play regnum. when you're in the command line, and downloaded and extracted the linux installer from regnum online, you should see a file called rolauncher. to open that issue this command frmo the command line when you cd to that directory that it's in

./rolauncher

that should start the game. if you just issue rolauncher it doesn't know what to do because bash probably isn't listed as the default shell within the exectable rolauncher file. regnum online is FUN! i can't speak for planeshift

now, the next issue, your usb devices. what version of ubuntu are you using again? when you enter this command

dmesg

after booting up and having the devices connected, do you see anything about them within the output of dmesg?

---

### Post by Preyor on 2008-01-05
I double-click rolauncher, but it doesn't do anything. and this is the output of the command, i didnt see anything pertaining to my usb scanner (currently plugged in after reboot) but im not too good at deciphering the meaning of these huge blocks lol.

[    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Dec 18 08:02:57 UTC 2007 (Ubuntu 2.6.22-14.47-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000ec000 - 00000000000f0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000010000000 (usable)
[    0.000000]  BIOS-e820: 00000000fffc0000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 256MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 65536) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->    65536
[    0.000000]   HighMem     65536 ->    65536
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->    65536
[    0.000000] On node 0 totalpages: 65536
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 480 pages used for memmap
[    0.000000]   Normal zone: 60960 pages, LIFO batch:15
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00EC010 checksum 0
[    0.000000] ACPI: RSDP 000EC010, 0014 (r0 COMPAQ)
[    0.000000] ACPI: RSDT 000EC080, 002C (r1 COMPAQ HAWA7K21    10503             0)
[    0.000000] ACPI: FACP 000EC0CC, 0074 (r1 COMPAQ HAWA7K21    10503             0)
[    0.000000] ACPI: DSDT 000EC140, 006B (r1 COMPAQ DSDTTBL         1 MSFT  100000C)
[    0.000000] ACPI: FACS 000EC040, 0040
[    0.000000] ACPI: SSDT 000EC223, 2356 (r1 COMPAQ HAWA7K2         1 MSFT  100000C)
[    0.000000] ACPI: PM-Timer IO Port: 0xee08
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 10000000:effc0000)
[    0.000000] Built 1 zonelists.  Total pages: 65024
[    0.000000] Kernel command line: root=UUID=9e822b5c-745c-42dd-8e70-127a0d666fe8 ro quiet splash
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffd000 (0120c000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 1024 (order: 10, 4096 bytes)
[    0.000000] Detected 1325.579 MHz processor.
[   12.500563] Console: colour VGA+ 80x25
[   12.500889] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[   12.501105] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[   12.514570] Memory: 248460k/262144k available (2015k kernel code, 13200k reserved, 916k data, 364k init, 0k highmem)
[   12.514587] virtual kernel memory layout:
[   12.514589]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   12.514591]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   12.514593]     vmalloc : 0xd0800000 - 0xff7fe000   ( 751 MB)
[   12.514596]     lowmem  : 0xc0000000 - 0xd0000000   ( 256 MB)
[   12.514598]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   12.514600]       .data : 0xc02f7de6 - 0xc03dce84   ( 916 kB)
[   12.514602]       .text : 0xc0100000 - 0xc02f7de6   (2015 kB)
[   12.514608] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   12.514675] SLUB: Genslabs=22, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   12.594645] Calibrating delay using timer specific routine.. 2653.36 BogoMIPS (lpj=5306730)
[   12.594690] Security Framework v1.0.0 initialized
[   12.594701] SELinux:  Disabled at boot.
[   12.594730] Mount-cache hash table entries: 512
[   12.594932] CPU: After generic identify, caps: 0183f9ff c1c7f9ff 00000000 00000000 00000000 00000000 00000000
[   12.594946] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   12.594951] CPU: L2 Cache: 256K (64 bytes/line)
[   12.594955] CPU: After all inits, caps: 0183f9ff c1c7f9ff 00000000 00000420 00000000 00000000 00000000
[   12.594972] Compat vDSO mapped to ffffe000.
[   12.594991] Checking 'hlt' instruction... OK.
[   12.610685] SMP alternatives: switching to UP code
[   12.611059] Freeing SMP alternatives: 11k freed
[   12.611589] Early unpacking initramfs... done
[   13.092327] ACPI: Core revision 20070126
[   13.092418] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   13.095664] ACPI: setting ELCR to 0200 (from 0c08)
[   13.096576] CPU0: AMD Athlon(tm) Processor stepping 04
[   13.096584] SMP motherboard not detected.
[   13.096588] Local APIC not detected. Using dummy APIC emulation.
[   13.096657] Brought up 1 CPUs
[   13.096870] Booting paravirtualized kernel on bare hardware
[   13.096986] Time: 18:42:34  Date: 00/05/108
[   13.097029] NET: Registered protocol family 16
[   13.097181] EISA bus registered
[   13.097199] ACPI: bus type pci registered
[   13.113520] PCI: PCI BIOS revision 2.10 entry at 0xfa164, last bus=1
[   13.113525] PCI: Using configuration type 1
[   13.113527] Setting up standard PCI resources
[   13.120291] ACPI: EC: Look up EC in DSDT
[   13.121650] ACPI: Interpreter enabled
[   13.121655] ACPI: (supports S0 S1 S4 S5)
[   13.121674] ACPI: Using PIC for interrupt routing
[   13.126739] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   13.126751] PCI: Probing PCI hardware (bus 00)
[   13.127237] PCI quirk: region ec00-ec0f claimed by vt82c686 SMB
[   13.127379] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   13.128140] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGPB._PRT]
[   13.130746] ACPI: PCI Interrupt Link [LNKA] (IRQs *3 4 5 6 7 10 11 15)
[   13.130904] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11 15) *0, disabled.
[   13.131055] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *10 11 15)
[   13.131203] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 *11 15)
[   13.131324] Linux Plug and Play Support v0.97 (c) Adam Belay
[   13.131352] pnp: PnP ACPI init
[   13.131365] ACPI: bus type pnp registered
[   13.134112] pnp: PnP ACPI: found 13 devices
[   13.134116] ACPI: ACPI bus type pnp unregistered
[   13.134122] PnPBIOS: Disabled by ACPI PNP
[   13.134216] PCI: Using ACPI for IRQ routing
[   13.134221] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   13.159264] NET: Registered protocol family 8
[   13.159268] NET: Registered protocol family 20
[   13.159376] pnp: 00:00: iomem range 0x0-0x9ffff could not be reserved
[   13.159381] pnp: 00:00: iomem range 0xe0000-0xfffff could not be reserved
[   13.159386] pnp: 00:00: iomem range 0x100000-0xfffffff could not be reserved
[   13.159391] pnp: 00:00: iomem range 0xfff80000-0xffffffff could not be reserved
[   13.159406] pnp: 00:0c: ioport range 0x4d0-0x4d1 has been reserved
[   13.159410] pnp: 00:0c: ioport range 0xee00-0xee7f has been reserved
[   13.159415] pnp: 00:0c: ioport range 0xee80-0xeeff has been reserved
[   13.162238] Time: tsc clocksource has been installed.
[   13.189863] PCI: Failed to allocate mem resource #6:10000@90000000 for 0000:01:05.0
[   13.189920] PCI: Bridge: 0000:00:01.0
[   13.189922]   IO window: disabled.
[   13.189928]   MEM window: 80000000-80ffffff
[   13.189933]   PREFETCH window: 88000000-8fffffff
[   13.189960] NET: Registered protocol family 2
[   13.226293] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[   13.226369] TCP established hash table entries: 8192 (order: 4, 98304 bytes)
[   13.226621] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[   13.226823] TCP: Hash tables configured (established 8192 bind 8192)
[   13.226827] TCP reno registered
[   13.238369] checking if image is initramfs... it is
[   13.689896] Switched to high resolution mode on CPU 0
[   14.157476] Freeing initrd memory: 7071k freed
[   14.158107] audit: initializing netlink socket (disabled)
[   14.158129] audit(1199558554.152:1): initialized
[   14.161004] VFS: Disk quotas dquot_6.5.1
[   14.161086] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   14.161251] io scheduler noop registered
[   14.161255] io scheduler anticipatory registered
[   14.161258] io scheduler deadline registered
[   14.161279] io scheduler cfq registered (default)
[   14.161305] PCI: Disabling Via external APIC routing
[   14.161340] Boot video device is 0000:01:05.0
[   14.161617] isapnp: Scanning for PnP cards...
[   14.515408] isapnp: No Plug & Play device found
[   14.564330] Real Time Clock Driver v1.12ac
[   14.564463] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   14.564614] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   14.565880] 00:03: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   14.566298] PCI: Enabling device 0000:00:0a.0 (0000 -> 0001)
[   14.566669] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 3
[   14.566675] PCI: setting IRQ 3 as level-triggered
[   14.566681] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNKA] -> GSI 3 (level, low) -> IRQ 3
[   14.570400] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   14.570763] input: Macintosh mouse button emulation as /class/input/input0
[   14.570893] PNP: PS/2 Controller [PNP0303:KBD,PNP0f0e:PS2M] at 0x60,0x64 irq 1,12
[   14.571273] serio: i8042 KBD port at 0x60,0x64 irq 1
[   14.571281] serio: i8042 AUX port at 0x60,0x64 irq 12
[   14.571533] mice: PS/2 mouse device common for all mice
[   14.571702] EISA: Probing bus 0 at eisa.0
[   14.571716] Cannot allocate resource for EISA slot 1
[   14.571753] EISA: Detected 0 cards.
[   14.572047] TCP cubic registered
[   14.572063] NET: Registered protocol family 1
[   14.572093] Using IPI No-Shortcut mode
[   14.572337]   Magic number: 8:935:745
[   14.573410] Freeing unused kernel memory: 364k freed
[   14.609385] input: AT Translated Set 2 keyboard as /class/input/input1
[   15.865872] AppArmor: AppArmor initialized<5>audit(1199558556.152:2):  type=1505 info="AppArmor initialized" pid=1117
[   15.875758] fuse init (API version 7.8)
[   15.883108] Failure registering capabilities with primary security module.
[   16.705062] ACPI: PCI Interrupt 0000:00:06.0[A] -> Link [LNKA] -> GSI 3 (level, low) -> IRQ 3
[   16.778769] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[3]  MMIO=[81100000-811007ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   16.793434] 8139too Fast Ethernet driver 0.9.28
[   16.793501] PCI: Enabling device 0000:00:09.0 (0004 -> 0007)
[   16.793873] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[   16.793879] PCI: setting IRQ 11 as level-triggered
[   16.793885] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   16.794182] eth0: RealTek RTL8139 at 0xd0830000, 00:10:b5:ef:02:10, IRQ 11
[   16.794187] eth0:  Identified 8139 chip type 'RTL-8139C'
[   16.830232] SCSI subsystem initialized
[   16.838016] libata version 2.21 loaded.
[   16.847505] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   16.847515] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   16.848588] VP_IDE: IDE controller at PCI slot 0000:00:14.1
[   16.848617] VP_IDE: chipset revision 6
[   16.848621] VP_IDE: not 100% native mode: will probe irqs later
[   16.848635] VP_IDE: VIA vt82c686b (rev 40) IDE UDMA100 controller on pci0000:00:14.1
[   16.848646]     ide0: BM-DMA at 0x14c0-0x14c7, BIOS settings: hda:DMA, hdb:pio
[   16.848663]     ide1: BM-DMA at 0x14c8-0x14cf, BIOS settings: hdc:DMA, hdd:DMA
[   16.848673] Probing IDE interface ide0...
[   16.877770] usbcore: registered new interface driver usbfs
[   16.877811] usbcore: registered new interface driver hub
[   16.877847] usbcore: registered new device driver usb
[   16.932535] USB Universal Host Controller Interface driver v3.0
[   17.164012] Floppy drive(s): fd0 is 1.44M
[   17.181570] FDC 0 is a post-1991 82077
[   17.291579] hda: WDC WD600AB-60BVA0, ATA DISK drive
[   17.965019] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   17.965485] Probing IDE interface ide1...
[   18.051007] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0010b50000006ec3]
[   18.826516] hdc: Memorex DVD+R/RW 2.4x8AA, ATAPI CD/DVD-ROM drive
[   19.609973] hdd: LG CD-RW CED-8080B, ATAPI CD/DVD-ROM drive
[   19.610841] ide1 at 0x170-0x177,0x376 on irq 15
[   19.611657] ACPI: Invalid index 3
[   19.611663] ACPI: Invalid IRQ link routing entry
[   19.611667] ACPI: Unable to derive IRQ for device 0000:00:14.2
[   19.611670] ACPI: PCI Interrupt 0000:00:14.2[D]: no GSI - using IRQ 11
[   19.611687] uhci_hcd 0000:00:14.2: UHCI Host Controller
[   19.612127] uhci_hcd 0000:00:14.2: new USB bus registered, assigned bus number 1
[   19.612162] uhci_hcd 0000:00:14.2: irq 11, io base 0x00001480
[   19.612813] usb usb1: configuration #1 chosen from 1 choice
[   19.613022] hub 1-0:1.0: USB hub found
[   19.613035] hub 1-0:1.0: 2 ports detected
[   19.624038] hda: max request size: 128KiB
[   19.645501] hda: 117231408 sectors (60022 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
[   19.645515] hda: cache flushes not supported
[   19.645599]  hda: hda1 hda2 < hda5 >
[   19.714027] ACPI: Invalid index 3
[   19.714035] ACPI: Invalid IRQ link routing entry
[   19.714039] ACPI: Unable to derive IRQ for device 0000:00:14.3
[   19.714043] ACPI: PCI Interrupt 0000:00:14.3[D]: no GSI - using IRQ 11
[   19.714060] uhci_hcd 0000:00:14.3: UHCI Host Controller
[   19.714112] uhci_hcd 0000:00:14.3: new USB bus registered, assigned bus number 2
[   19.714142] uhci_hcd 0000:00:14.3: irq 11, io base 0x000014a0
[   19.714307] usb usb2: configuration #1 chosen from 1 choice
[   19.714358] hub 2-0:1.0: USB hub found
[   19.714373] hub 2-0:1.0: 2 ports detected
[   19.716925] hdc: ATAPI 32X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[   19.716939] Uniform CD-ROM driver Revision: 3.20
[   19.719711] hdd: ATAPI 32X CD-ROM CD-R/RW drive, 2048kB Cache, DMA
[   20.017444] Attempting manual resume
[   20.017451] swsusp: Resume From Partition 3:5
[   20.017454] PM: Checking swsusp image.
[   20.017778] PM: Resume from disk failed.
[   20.081457] usb 1-2: new full speed USB device using uhci_hcd and address 2
[   20.081478] kjournald starting.  Commit interval 5 seconds
[   20.081494] EXT3-fs: mounted filesystem with ordered data mode.
[   20.249791] usb 1-2: configuration #1 chosen from 1 choice
[   30.756935] Linux agpgart interface v0.102 (c) Dave Jones
[   30.765468] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   30.819461] shpchp: HPC vendor_id 1022 device_id 700f ss_vid 0 ss_did 0
[   30.819472] shpchp: shpc_init: cannot reserve MMIO region
[   30.819502] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   31.450171] parport_pc: VIA 686A/8231 detected
[   31.450178] parport_pc: probing current configuration
[   31.450197] parport_pc: Current parallel port base: 0x378
[   31.450271] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[   31.553425] agpgart: Detected AMD 761 chipset
[   31.562541] agpgart: AGP aperture is 64M @ 0x90000000
[   31.566986] parport_pc: VIA parallel port: io=0x378, irq=7
[   31.600768] input: PC Speaker as /class/input/input2
[   31.651836] via686a 0000:00:14.4: base address not set - upgrade BIOS or use force_addr=0xaddr
[   31.669931] vt596_smbus 0000:00:14.4: SMBUS: Error: Host SMBus controller not enabled! - upgrade BIOS or use force=1
[   31.786257] nvidia: module license 'NVIDIA' taints kernel.
[   32.134786] ACPI: PCI Interrupt 0000:01:05.0[A] -> Link [LNKA] -> GSI 3 (level, low) -> IRQ 3
[   32.135820] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9639  Mon Apr 16 20:20:06 PDT 2007
[   32.543064] input: ImPS/2 Generic Wheel Mouse as /class/input/input3
[   33.097348] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10
[   33.097358] PCI: setting IRQ 10 as level-triggered
[   33.097364] ACPI: PCI Interrupt 0000:00:07.0[A] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[   34.833625] lp0: using parport0 (interrupt-driven).
[   34.926898] Adding 746980k swap on /dev/hda5.  Priority:-1 extents:1 across:746980k
[   35.405243] EXT3 FS on hda1, internal journal
[   36.991058] No dock devices found.
[   37.106594] input: Power Button (FF) as /class/input/input4
[   37.113559] ACPI: Power Button (FF) [PWRF]
[   37.170390] input: Power Button (CM) as /class/input/input5
[   37.177313] ACPI: Power Button (CM) [PBTN]
[   37.684754] powernow: No powernow capabilities detected
[   39.573162] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   40.062622] NET: Registered protocol family 10
[   40.062893] lo: Disabled Privacy Extensions
[   40.346717] ppdev: user-space parallel port driver
[   40.656880] audit(1199558581.976:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4572 profile="/usr/sbin/cupsd"
[   40.758876] apm: BIOS not found.
[   41.707248] Failure registering capabilities with primary security module.
[   44.442282] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[   44.442460] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[   44.442623] agpgart: Putting AGP V2 device at 0000:01:05.0 into 4x mode
[   46.706336] NET: Registered protocol family 17
[   59.585974] eth0: no IPv6 routers present
[ 2430.233929] usb 1-2: USB disconnect, address 2
[ 2431.848807] usb 1-2: new full speed USB device using uhci_hcd and address 3
[ 2432.017393] usb 1-2: configuration #1 chosen from 1 choice

---

### Post by Preyor on 2008-01-05
i downloaded the xsane image scanner and it works perfectly now. all i need is whatever is keeping executables from, well, executing. thank you again lol, this has been a tremendous help.

---

### Post by dannyboy79 on 2008-01-07
ok, the problem is that you can't double click on it. it doesn't know what to run it with, so please do as I suggested and try to run it from the command line.

./rolauncher

this tells rolauncher to run it using bash.

you can thank me by hitting the ribbon with the star, that will add to my "thanked" stats.

---

