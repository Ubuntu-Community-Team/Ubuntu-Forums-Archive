---
title: "ubuntu won't load, stuck at splash screen"
date: 2006-07-31
forum: General Help
---

### Post by modafokaxx on 2006-07-31
[problem solved, see last post for solution]


Hi all!
this is my first post here, as so far I've managed to make my way with wikis and google searches, as well as with the great ubuntu guide site ([http://ubuntuguide.org/wiki/Dapper)](http://ubuntuguide.org/wiki/Dapper)).
But this time, I think I'm stuck.

I'm running Ubuntu 6.06.
Today, I started my computer, and after the login window asking me for my name/password, the splash screen displaying the loading processes (windows, gnome taskbar, Nautilus file browser) started and just stopped right there.
I rebooted, this time it went to the GNOME desktop, but didn't manage to load it completely. I just had an empty top and bottom bar, no icons, no background, nothing.
Neither ctrl + alt + backspace, ctrl + alt + del or ctrl + alt + F1 do anything at that point. It's just stuck. I tried waiting and doing something else, but after a good half an hour, it's obvious it won't do anything more than that.
I tried booting up on the live CD to make sure, but the same thing happens.

I think I read somewhere that it might be related to the xorg.conf file.. would that make sense?
I **can** boot recovery mode to a terminal, so I should be able to edit stuff.

well if anyone has an idea, it would be great! thanks!

---

### Post by zxee on 2006-07-31
Did you do any recent upgrades, changes , etc, prior to this happening?
To me what you've described sounds like a freeze i.e nothing is working-the system is locked up. While that could be caused by inappropriate changes to your xorg.conf a freeze or lock up isn't the general result of that.
Can you do > linux rescue from the live or install cd and if you do what results from that?
And if you can as you say get into your system sometimes checking /var/log for recent messages will provide a clue-hope that helps.

---

### Post by modafokaxx on 2006-07-31
well in fact, the install/live cd won't load anymore than my actual install..
and when I said I could boot, I mean using the second option in the GRUB boot-up menu "Ubuntu, Kernel blablabla, recovery mode". This leads me to a command prompt. When I exit it, it loads GNOME and then gets stuck, same as the problem I was describing in the first place.
So I can really only enter commands at the terminal.
I'll try [HTML]linux rescue[/HTML] at that point.
By the way, I might add that booting any of the two versions of the kernel I have do the same thing, ie: not work.

To answer your other question, I can't think of anything that I would have installed in particular. This Ubuntu install is really fresh, considering it's about a week old, and it's my frist attempt at linux. So I've been adding stuff around a bit everyday. But the last time I used Ubuntu, I don't recall doing anything appart from browsing with Opera, reading mails with Thunderbird and listening to music with Amarok.
Nothing crazy..
thanks for your help anyway, much appreciated!

---

### Post by modafokaxx on 2006-07-31
ok, small update

I am able to get to a working GNOME session using the "Ubuntu, recovery" option during the GRUB list of choices. Starting GNOME with "startx" at the prompt works, and I get to a working Ubuntu as root.

Thing is, it's nice to be in a useable environment, but I still don't know how to make my default GNOME session using my usual username work..

I also tried opening a failsafe GNOME session as normal user, it got me to the desktop and had me believing it was working, but got stuck as soon as I tried to launch an application (Opera 9 web browser in this case). In this case too, ctrl + alt + backspace or whatever does not work.

Ideas?

---

### Post by zxee on 2006-07-31
Well it's good that you can get to a desktop, but not good that you can't get the live or install cd's to run. I wonder if there was a problem with those images did you run a md5sum check to see if the iso images were good before burning? 
I know I'm asking a lot of questions but there are unknowns here-what hardware do you have? (specifically hard drive partition space and amount of ram) and then there's this > So I've been adding stuff around a bit everydayupgrades can cause problems if apt has to upgrade a desktop component. Besides checking /var/log for messages you might take a look at the output of dmesg. If there's anything odd there post it. Hope that helps.

---

### Post by modafokaxx on 2006-08-02
hey thanks for trying to help out
sorry for not coming back earlier too..

the md5 sum, I didn't check as I borrowed the install disk from a friend who installed Ubuntu a few weeks earlier (he hasn't had any problems as far as I know).
I tried removing all the ~/.gconf* and ~/.gnome* files as someone over at the GNOME forum suggested, but as much as it did give me a clean GNOME session (I could see the things were different on the toolbars for instance), the desktop still froze at the same point, before anything had appeared.
Also, it appears that as soon as I press a key, any key, the mouse freezes too.

Here is the result of dmesg, now you'll know everything about my computer!
I couldn't see anything odd about it, but then, I'm not sure I would know how to.
About my computer: it's an old AMD 1.33 ghz Athlon Thunderbird CPU with 384 mo of RAM, a GE Force 2 MX handling graphics duty and 2 physical hard drives, one of 160 go and one of 40, partitionned for the first one into a primary 10 go NTFS (hda1) and an extended partition containing a ext3 partition of about 15 go (hda5) a 256 mo linux swap (hda6 I think), and two fat32 partitions, one of 93 go (hda7) and one of 21 go (hda8). The second hard drive has a primary fat 32 partition (hdb1) and an extended partition containing a 256 mo linux swap (hdb3) and another fat 32 partition (hdb5).
So that's twice 256 mo of swap and 384 of ram.

```
[17179569.184000] Linux version 2.6.15-26-386 (buildd@terranova) (gcc version 4. 0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Mon Jul 17 19:52:53 UTC 2006
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 0000000017fec000 (usable)
[17179569.184000]  BIOS-e820: 0000000017fec000 - 0000000017fef000 (ACPI data)
[17179569.184000]  BIOS-e820: 0000000017fef000 - 0000000017fff000 (reserved)
[17179569.184000]  BIOS-e820: 0000000017fff000 - 0000000018000000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 383MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 98284
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 94188 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 0 pages, LIFO batch:0
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 ASUS                                  ) @ 0x0 00f6da0
[17179569.184000] ACPI: RSDT (v001 ASUS   A7V266   0x30303031 MSFT 0x31313031) @  0x17fec000
[17179569.184000] ACPI: FADT (v001 ASUS   A7V266   0x30303031 MSFT 0x31313031) @  0x17fec080
[17179569.184000] ACPI: BOOT (v001 ASUS   A7V266   0x30303031 MSFT 0x31313031) @  0x17fec040
[17179569.184000] ACPI: DSDT (v001   ASUS A7V266   0x00001000 MSFT 0x0100000b) @  0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0xe408
[17179569.184000] Allocating PCI resources starting at 20000000 (gap: 18000000:e 7ff0000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda5 ro single
[17179569.184000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[17179569.184000] mapped APIC to ffffd000 (01302000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 2048 (order: 11, 32768 bytes)
[17179569.184000] Detected 1343.232 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179569.500000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes )
[17179569.500000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179569.516000] Memory: 379188k/393136k available (1976k kernel code, 13400k r eserved, 606k data, 288k init, 0k highmem)
[17179569.516000] Checking if this processor honours the WP bit even in supervis or mode... Ok.
[17179569.600000] Calibrating delay using timer specific routine.. 2688.95 BogoM IPS (lpj=5377919)
[17179569.600000] Security Framework v1.0.0 initialized
[17179569.600000] SELinux:  Disabled at boot.
[17179569.600000] Mount-cache hash table entries: 512
[17179569.600000] CPU: After generic identify, caps: 0183f9ff c1c7f9ff 00000000 00000000 00000000 00000000 00000000
[17179569.600000] CPU: After vendor identify, caps: 0183f9ff c1c7f9ff 00000000 0 0000000 00000000 00000000 00000000
[17179569.600000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/li ne)
[17179569.600000] CPU: L2 Cache: 256K (64 bytes/line)
[17179569.600000] CPU: After all inits, caps: 0183f9ff c1c7f9ff 00000000 0000042 0 00000000 00000000 00000000
[17179569.600000] mtrr: v2.0 (20020519)
[17179569.600000] CPU: AMD Athlon(TM)Processor stepping 04
[17179569.600000] Enabling fast FPU save and restore... done.
[17179569.600000] Checking 'hlt' instruction... OK.
[17179569.616000] checking if image is initramfs... it is
[17179570.420000] Freeing initrd memory: 6617k freed
[17179570.436000] ACPI: Looking for DSDT ... not found!
[17179570.436000] ACPI: setting ELCR to 0200 (from 0c20)
[17179570.460000] NET: Registered protocol family 16
[17179570.460000] EISA bus registered
[17179570.460000] ACPI: bus type pci registered
[17179570.464000] PCI: PCI BIOS revision 2.10 entry at 0xf0ed0, last bus=1
[17179570.464000] PCI: Using configuration type 1
[17179570.464000] ACPI: Subsystem revision 20051216
[17179570.468000] ACPI: Interpreter enabled
[17179570.468000] ACPI: Using PIC for interrupt routing
[17179570.468000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14  15)
[17179570.468000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[17179570.468000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 *10 11 12 14  15)
[17179570.468000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 9 10 11 12 14  15)
[17179570.472000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179570.472000] PCI: Probing PCI hardware (bus 00)
[17179570.472000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[17179570.476000] Boot video device is 0000:01:00.0
[17179570.476000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179570.480000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[17179570.488000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179570.488000] pnp: PnP ACPI init
[17179570.492000] pnp: PnP ACPI: found 13 devices
[17179570.492000] PnPBIOS: Disabled by ACPI PNP
[17179570.492000] PCI: Using ACPI for IRQ routing
[17179570.492000] PCI: If a device doesn't work, try "pci=routeirq".  If it help s, post a report
[17179570.500000] pnp: 00:02: ioport range 0xe400-0xe47f could not be reserved
[17179570.500000] pnp: 00:02: ioport range 0xe800-0xe80f has been reserved
[17179570.500000] pnp: 00:02: ioport range 0x290-0x291 has been reserved
[17179570.500000] pnp: 00:02: ioport range 0x370-0x373 has been reserved
[17179570.500000] PCI: Bridge: 0000:00:01.0
[17179570.500000]   IO window: disabled.
[17179570.500000]   MEM window: ee000000-efefffff
[17179570.500000]   PREFETCH window: eff00000-fbffffff
[17179570.500000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[17179570.500000] Simple Boot Flag at 0x3a set to 0x1
[17179570.500000] audit: initializing netlink socket (disabled)
[17179570.504000] audit(1154552939.504:1): initialized
[17179570.504000] VFS: Disk quotas dquot_6.5.1
[17179570.504000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179570.504000] Initializing Cryptographic API
[17179570.504000] io scheduler noop registered
[17179570.504000] io scheduler anticipatory registered
[17179570.504000] io scheduler deadline registered
[17179570.504000] io scheduler cfq registered
[17179570.504000] isapnp: Scanning for PnP cards...
[17179570.856000] isapnp: No Plug & Play device found
[17179570.876000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[17179570.880000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179570.880000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179570.880000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ shar ing enabled
[17179570.880000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179570.880000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179570.884000] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179570.884000] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179570.884000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 b locksize
[17179570.884000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179570.884000] ide: Assuming 33MHz system bus speed for PIO modes; override w ith idebus=xx
[17179570.884000] mice: PS/2 mouse device common for all mice
[17179570.892000] EISA: Probing bus 0 at eisa.0
[17179570.892000] EISA: Detected 0 cards.
[17179570.892000] NET: Registered protocol family 2
[17179570.936000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179570.936000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes )
[17179570.936000] TCP established hash table entries: 16384 (order: 4, 65536 byt es)
[17179570.936000] TCP bind hash table entries: 16384 (order: 4, 65536 bytes)
[17179570.936000] TCP: Hash tables configured (established 16384 bind 16384)
[17179570.936000] TCP reno registered
[17179570.936000] TCP bic registered
[17179570.936000] NET: Registered protocol family 1
[17179570.936000] NET: Registered protocol family 8
[17179570.936000] NET: Registered protocol family 20
[17179570.936000] Using IPI Shortcut mode
[17179570.936000] ACPI wakeup devices:
[17179570.936000] PCI0 PCI1 UAR1 UAR2 USB0 USB1 USB2
[17179570.936000] ACPI: (supports S0 S1 S4 S5)
[17179570.936000] Freeing unused kernel memory: 288k freed
[17179571.004000] Capability LSM initialized
[17179571.664000] VP_IDE: IDE controller at PCI slot 0000:00:11.1
[17179571.664000] VP_IDE: chipset revision 6
[17179571.664000] VP_IDE: not 100% native mode: will probe irqs later
[17179571.664000] VP_IDE: VIA vt8233 (rev 00) IDE UDMA100 controller on pci0000: 00:11.1
[17179571.664000]     ide0: BM-DMA at 0xb800-0xb807, BIOS settings: hda:DMA, hdb :DMA
[17179571.664000]     ide1: BM-DMA at 0xb808-0xb80f, BIOS settings: hdc:DMA, hdd :DMA
[17179571.664000] Probing IDE interface ide0...
[17179572.080000] hda: ST3160023A, ATA DISK drive
[17179572.360000] hdb: WDC WD400BB-00CFC0, ATA DISK drive
[17179572.416000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179572.436000] Probing IDE interface ide1...
[17179573.304000] hdc: LG CD-ROM CRD-8522B, ATAPI CD/DVD-ROM drive
[17179574.088000] hdd: HL-DT-ST DVDRAM GSA-4082B, ATAPI CD/DVD-ROM drive
[17179574.144000] ide1 at 0x170-0x177,0x376 on irq 15
[17179574.160000] hda: max request size: 1024KiB
[17179574.184000] hda: 312581808 sectors (160041 MB) w/8192KiB Cache, CHS=19457/ 255/63, UDMA(100)
[17179574.188000] hda: cache flushes supported
[17179574.188000]  hda: hda1 hda2 < hda5 hda6 hda7 hda8 >
[17179574.248000] hdb: max request size: 128KiB
[17179574.248000] hdb: 78165360 sectors (40020 MB) w/2048KiB Cache, CHS=65535/16 /63, UDMA(100)
[17179574.248000] hdb: cache flushes not supported
[17179574.248000]  hdb: hdb1 hdb2 < hdb5 > hdb3
[17179574.304000] hdc: ATAPI 52X CD-ROM drive, 128kB Cache, DMA
[17179574.304000] Uniform CD-ROM driver Revision: 3.20
[17179574.316000] hdd: ATAPI 63X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179574.836000] usbcore: registered new driver usbfs
[17179574.840000] usbcore: registered new driver hub
[17179574.840000] USB Universal Host Controller Interface driver v2.3
[17179574.840000] **** SET: Misaligned resource pointer: d7d9d2e2 Type 07 Len 0
[17179574.840000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 5
[17179574.840000] PCI: setting IRQ 5 as level-triggered
[17179574.840000] ACPI: PCI Interrupt 0000:00:11.2[D] -> Link [LNKD] -> GSI 5 (l evel, low) -> IRQ 5
[17179574.840000] uhci_hcd 0000:00:11.2: UHCI Host Controller
[17179574.844000] uhci_hcd 0000:00:11.2: new USB bus registered, assigned bus nu mber 1
[17179574.844000] uhci_hcd 0000:00:11.2: irq 5, io base 0x0000b400
[17179574.844000] hub 1-0:1.0: USB hub found
[17179574.844000] hub 1-0:1.0: 2 ports detected
[17179574.948000] ACPI: PCI Interrupt 0000:00:11.3[D] -> Link [LNKD] -> GSI 5 (l evel, low) -> IRQ 5
[17179574.948000] uhci_hcd 0000:00:11.3: UHCI Host Controller
[17179574.948000] uhci_hcd 0000:00:11.3: new USB bus registered, assigned bus nu mber 2
[17179574.948000] uhci_hcd 0000:00:11.3: irq 5, io base 0x0000b000
[17179574.948000] hub 2-0:1.0: USB hub found
[17179574.948000] hub 2-0:1.0: 2 ports detected
[17179575.052000] ACPI: PCI Interrupt 0000:00:11.4[D] -> Link [LNKD] -> GSI 5 (l evel, low) -> IRQ 5
[17179575.052000] uhci_hcd 0000:00:11.4: UHCI Host Controller
[17179575.052000] uhci_hcd 0000:00:11.4: new USB bus registered, assigned bus nu mber 3
[17179575.052000] uhci_hcd 0000:00:11.4: irq 5, io base 0x0000a800
[17179575.052000] hub 3-0:1.0: USB hub found
[17179575.052000] hub 3-0:1.0: 2 ports detected
[17179575.312000] Attempting manual resume
[17179575.328000] EXT3-fs: INFO: recovery required on readonly filesystem.
[17179575.328000] EXT3-fs: write access will be enabled during recovery.
[17179576.496000] EXT3-fs: recovery complete.
[17179576.496000] kjournald starting.  Commit interval 5 seconds
[17179576.508000] EXT3-fs: mounted filesystem with ordered data mode.
[17179585.724000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179585.744000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179585.796000] irda_init()
[17179585.796000] NET: Registered protocol family 23
[17179585.832000] Linux agpgart interface v0.101 (c) Dave Jones
[17179585.872000] agpgart: Detected VIA KT266/KY266x/KT333 chipset
[17179585.876000] agpgart: AGP aperture is 32M @ 0xfc000000
[17179585.976000] **** SET: Misaligned resource pointer: d781a722 Type 07 Len 0
[17179585.976000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10
[17179585.976000] PCI: setting IRQ 10 as level-triggered
[17179585.976000] ACPI: PCI Interrupt 0000:00:0f.0[A] -> Link [LNKC] -> GSI 10 ( level, low) -> IRQ 10
[17179586.256000] nvidia: module license 'NVIDIA' taints kernel.
[17179586.264000] **** SET: Misaligned resource pointer: d21852c2 Type 07 Len 0
[17179586.264000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[17179586.264000] PCI: setting IRQ 11 as level-triggered
[17179586.264000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 ( level, low) -> IRQ 11
[17179586.264000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8762  Mon Ma y 15 13:06:38 PDT 2006
[17179587.520000] gameport: EMU10K1 is pci0000:00:0f.1/gameport0, io 0xd400, spe ed 1217kHz
[17179587.524000] Real Time Clock Driver v1.12
[17179587.536000] Floppy drive(s): fd0 is 1.44M
[17179587.544000] input: PC Speaker as /class/input/input1
[17179587.552000] FDC 0 is a post-1991 82077
[17179587.660000] 8139too Fast Ethernet driver 0.9.27
[17179587.660000] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [LNKD] -> GSI 5 (l evel, low) -> IRQ 5
[17179587.660000] eth0: RealTek RTL8139 at 0xd892e000, 00:80:ad:86:71:21, IRQ 5
[17179587.660000] eth0:  Identified 8139 chip type 'RTL-8139C'
[17179587.684000] parport: PnPBIOS parport detected.
[17179587.684000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRIST ATE,COMPAT,EPP,ECP,DMA]
[17179587.700000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[17179588.092000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[17179588.504000] input: ImPS/2 Logitech Wheel Mouse as /class/input/input2
[17179588.568000] ts: Compaq touchscreen protocol output
[17179588.804000] NET: Registered protocol family 10
[17179588.804000] lo: Disabled Privacy Extensions
[17179588.804000] IPv6 over IPv4 tunneling driver
[17179588.844000] lp0: using parport0 (interrupt-driven).
[17179588.936000] Adding 265032k swap on /dev/hda6.  Priority:-1 extents:1 acros s:265032k
[17179588.936000] Adding 265064k swap on /dev/hdb3.  Priority:-2 extents:1 acros s:265064k
[17179599.236000] eth0: no IPv6 routers present
[17179635.396000] EXT3 FS on hda5, internal journal
[17179635.652000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179635.652000] md: bitmap version 4.39
[17179636.268000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@ redhat.com
[17179676.980000] NTFS driver 2.1.25 [Flags: R/O MODULE].
[17179677.024000] NTFS volume version 3.1.
[17179679.096000] NET: Registered protocol family 17

```

I checked /var/log but didn't find any log particularly appealling.. maybe I don't know what to look for?

thanks anyway, I'm starting to think I'm going to have to reinstall Ubuntu.
Or would reinstalling gnome work?
like "apt-get install GNOME" ? or is it not a good idea?

edit: also, here is the details of the /.xsession-errors file, the "critical" and the "failed" part sound interesting;
```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "axx"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/axx-desktop:/tmp/.ICE-unix/4765

(gnome-panel:4833): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `dest_width > 0' failed
Gnome-Message: gnome_execute_async_with_env_fds: returning -1

```

---

### Post by modafokaxx on 2006-08-03
bump?

also, when creating a new user, this new user has no problem login in to a functionnal GNOME session..
If anyone has an idea, I do realise this is a tricky one.. :)

---

### Post by modafokaxx on 2006-08-08
solved.

I compared the ~/.xsession-errors file for my session (te one that was not working) and for a test user I had created (that was working), and saw that my session was trying to access a session manager called: 
SESSION_MANAGER=local/axx-desktop:/tmp/.ICE-unix/4760 
but upon investigation, I saw there was no such file, and that the working session for my test user used a session manager called: 
SESSION_MANAGER=local/axx-desktop:/tmp/.ICE-unix/4761 

so I did what I thought was necessary to give all sessions a clean slate: I deleted all temporary files. 

So the solution to my problem was: ```

sudo rm -Rf /tmp/* /tmp/.* /var/tmp/* /var/tmp/.*
```


now I'm almost sure that some of these directory didn't need to be wiped out, but it worked for me. And, as I thought to myself "well they ARE temporary files, so they can go..".

there you have it.

thanks a bunch zxee for trying to help me out, it was much appreciated! :)

---

