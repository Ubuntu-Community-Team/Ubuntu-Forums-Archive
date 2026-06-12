---
title: "Desperate - 100% cpu usage while browsing internet"
date: 2007-03-24
forum: General Help
---

### Post by mich_r on 2007-03-24
Hi ubuntu people,

I am suffering from very bad performance problem under ubuntu while .... browsing internet pages (not only the "fat" ones, almost every one, even google).
When I put the url and press Enter the cpu usage jumps to almost 100% and it stays at this level until the page is completly rendered. What's interesting, the cpu hogging starts just with the moment the request is sent - that means if the web site is responding slowly or even if it is not responding at all , the CPU usage is still 100%. 
I have read almost hundred of threads here and at linuxquestions, I spend plenty of hours with different tries, tried almost everything (replacing video driver, disabling ipv6, etc. ) - no change. I don't know if it is related, but I also have 100% cpu usageduring scrolling windows or moving them around, switching tabs in firefox etc.
I have Windows as the second OS on my machine and both internet and scrolling here is fast as a lighting bolt! Please help, what should I check, where the problem could be ? For now using ubuntu is real pain, I am dealing with it but my patience starting to exhause.

My PC: Athlon 900 MHz, 512 RAM, Soltek mainboard, 2x ADMtek network card (tulip driver) , GeForce MX200 64Mb video (tried nv and nvidia drivers - no difference)

top while sending request:
```
top - 20:13:07 up  1:48,  2 users,  load average: 1.47, 0.65, 0.33
Tasks: 113 total,   3 running, 110 sleeping,   0 stopped,   0 zombie
Cpu(s): 91.7%us,  7.3%sy,  0.0%ni,  0.3%id,  0.0%wa,  0.3%hi,  0.3%si,  0.0%st
Mem:    514852k total,   508308k used,     6544k free,    12456k buffers
Swap:   522104k total,      220k used,   521884k free,   333676k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 4157 root      25   0  107m  20m 8972 R 67.7  4.0   4:45.63 Xorg               
 7717 my        15   0  135m  38m  19m S 24.2  7.6   0:46.12 firefox-bin        
 9338 my        15   0 50088  14m 9936 S  3.3  2.9   0:01.11 gnome-terminal     
 9315 my        15   0 32120  14m  10m S  2.7  2.8   0:07.50 gnome-system-mo    
 9361 my        16   0  2248 1136  840 R  0.7  0.2   0:00.04 top                
 4395 my        16   0  6824 4268 2012 S  0.3  0.8   0:01.69 gconfd-2           
 4566 my        18   0 56788 9376 7752 S  0.3  1.8   0:26.03 gnome-cups-icon    
    1 root      16   0  1628  532  448 S  0.0  0.1   0:01.97 init               
    2 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    3 root      34  19     0    0    0 S  0.0  0.0   0:00.18 ksoftirqd/0        
    4 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.13 events/0           
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khelper            
    7 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread            
    9 root      10  -5     0    0    0 S  0.0  0.0   0:00.03 kblockd/0          
   10 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid             
   11 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify    
```

lspci:
```
00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 03)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)
00:07.4 Bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
00:09.0 USB Controller: Silicon Image, Inc. USB0673 (rev 05)
00:0a.0 Ethernet controller: Linksys NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
00:0b.0 Ethernet controller: Linksys NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
00:0c.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 08)
01:00.0 VGA compatible controller: nVidia Corporation NV11DDR [GeForce2 MX 100 DDR/200 DDR] (rev b2)
```

dmesg:
```
[17179569.184000] Linux version 2.6.17-11-generic (root@terranova) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Thu Feb 1 19:52:28 UTC 2007 (Ubuntu 2.6.17-11.35-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 0000000000f00000 (usable)
[17179569.184000]  BIOS-e820: 0000000000f00000 - 0000000001000000 (reserved)
[17179569.184000]  BIOS-e820: 0000000001000000 - 000000001fff0000 (usable)
[17179569.184000]  BIOS-e820: 000000001fff0000 - 000000001fff3000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000001fff3000 - 0000000020000000 (ACPI data)
[17179569.184000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 511MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 131056
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 126960 pages, LIFO batch:31
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 VIA694                                ) @ 0x000f73a0
[17179569.184000] ACPI: RSDT (v001 VIA694 AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x1fff3000
[17179569.184000] ACPI: FADT (v001 VIA694 AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x1fff3040
[17179569.184000] ACPI: DSDT (v001 VIA694 AWRDACPI 0x00001000 MSFT 0x0100000c) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x4008
[17179569.184000] Allocating PCI resources starting at 30000000 (gap: 20000000:dfff0000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=UUID=fe15627e-3def-4626-a378-6cbd94310d68 ro quiet splash
[17179569.184000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[17179569.184000] mapped APIC to ffffd000 (0140a000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[17179569.184000] Detected 906.228 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179572.188000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179572.188000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179572.224000] Memory: 507324k/524224k available (1911k kernel code, 15364k reserved, 1073k data, 308k init, 0k highmem)
[17179572.224000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179572.304000] Calibrating delay using timer specific routine.. 1814.39 BogoMIPS (lpj=3628785)
[17179572.304000] Security Framework v1.0.0 initialized
[17179572.304000] SELinux:  Disabled at boot.
[17179572.304000] Mount-cache hash table entries: 512
[17179572.304000] CPU: After generic identify, caps: 0183f9ff c1c7f9ff 00000000 00000000 00000000 00000000 00000000
[17179572.304000] CPU: After vendor identify, caps: 0183f9ff c1c7f9ff 00000000 00000000 00000000 00000000 00000000
[17179572.304000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[17179572.304000] CPU: L2 Cache: 256K (64 bytes/line)
[17179572.304000] CPU: After all inits, caps: 0183f9ff c1c7f9ff 00000000 00000420 00000000 00000000 00000000
[17179572.304000] Checking 'hlt' instruction... OK.
[17179572.320000] SMP alternatives: switching to UP code
[17179572.320000] Freeing SMP alternatives: 16k freed
[17179572.320000] checking if image is initramfs... it is
[17179573.652000] Freeing initrd memory: 7075k freed
[17179573.652000] ACPI: Core revision 20060707
[17179573.716000] ACPI: Looking for DSDT ... not found!
[17179573.716000] ACPI: setting ELCR to 0200 (from 1e80)
[17179573.760000] CPU0: AMD Athlon(tm) processor stepping 02
[17179573.760000] SMP motherboard not detected.
[17179573.760000] Local APIC not detected. Using dummy APIC emulation.
[17179573.760000] Brought up 1 CPUs
[17179573.760000] migration_cost=0
[17179573.760000] NET: Registered protocol family 16
[17179573.760000] EISA bus registered
[17179573.760000] ACPI: bus type pci registered
[17179573.792000] PCI: PCI BIOS revision 2.10 entry at 0xfb480, last bus=1
[17179573.792000] PCI: Using configuration type 1
[17179573.792000] Setting up standard PCI resources
[17179573.816000] ACPI: Interpreter enabled
[17179573.816000] ACPI: Using PIC for interrupt routing
[17179573.816000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179573.816000] PCI: Probing PCI hardware (bus 00)
[17179573.816000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[17179573.820000] Disabling VIA memory write queue (PCI ID 0305, rev 03): [55] 89 & 1f -> 09
[17179573.820000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:07.1
[17179573.820000] PCI quirk: region 6000-607f claimed by vt82c686 HW-mon
[17179573.820000] PCI quirk: region 5000-500f claimed by vt82c686 SMB
[17179573.820000] Boot video device is 0000:01:00.0
[17179573.820000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179573.848000] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 11 *12 14 15)
[17179573.852000] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 *7 10 11 12 14 15)
[17179573.852000] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 *11 12 14 15)
[17179573.852000] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 *10 11 12 14 15)
[17179573.856000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179573.856000] pnp: PnP ACPI init
[17179573.860000] pnp: PnP ACPI: found 11 devices
[17179573.860000] PnPBIOS: Disabled by ACPI PNP
[17179573.860000] PCI: Using ACPI for IRQ routing
[17179573.860000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179573.888000] PCI: Bridge: 0000:00:01.0
[17179573.888000]   IO window: disabled.
[17179573.888000]   MEM window: ec000000-edffffff
[17179573.888000]   PREFETCH window: e0000000-e7ffffff
[17179573.888000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[17179573.888000] NET: Registered protocol family 2
[17179573.928000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[17179573.928000] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[17179573.928000] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[17179573.928000] TCP: Hash tables configured (established 16384 bind 8192)
[17179573.928000] TCP reno registered
[17179573.928000] audit: initializing netlink socket (disabled)
[17179573.928000] audit(1174760710.928:1): initialized
[17179573.928000] VFS: Disk quotas dquot_6.5.1
[17179573.928000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179573.928000] Initializing Cryptographic API
[17179573.928000] io scheduler noop registered
[17179573.928000] io scheduler anticipatory registered
[17179573.928000] io scheduler deadline registered
[17179573.928000] io scheduler cfq registered (default)
[17179573.928000] Applying VIA southbridge workaround.
[17179573.928000] PCI: Disabling Via external APIC routing
[17179573.928000] isapnp: Scanning for PnP cards...
[17179574.284000] isapnp: No Plug & Play device found
[17179574.332000] Real Time Clock Driver v1.12ac
[17179574.332000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179574.332000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179574.332000] serial8250: ttyS3 at I/O 0x2e8 (irq = 3) is a 16550A
[17179574.332000] 00:08: ttyS3 at I/O 0x2e8 (irq = 3) is a 16550A
[17179574.332000] mice: PS/2 mouse device common for all mice
[17179574.336000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179574.336000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179574.336000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179574.336000] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[17179574.336000] PNP: PS/2 controller doesn't have AUX irq; using default 12
[17179574.336000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179574.336000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179574.336000] EISA: Probing bus 0 at eisa.0
[17179574.336000] Cannot allocate resource for EISA slot 4
[17179574.336000] Cannot allocate resource for EISA slot 5
[17179574.336000] Cannot allocate resource for EISA slot 6
[17179574.336000] EISA: Detected 0 cards.
[17179574.336000] TCP bic registered
[17179574.336000] NET: Registered protocol family 1
[17179574.336000] NET: Registered protocol family 8
[17179574.336000] NET: Registered protocol family 20
[17179574.336000] Using IPI No-Shortcut mode
[17179574.336000] ACPI: (supports S0 S1 S5)
[17179574.336000] Freeing unused kernel memory: 308k freed
[17179574.384000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179575.508000] Capability LSM initialized
[17179575.584000] ACPI: CPU0 (power states: C1[C1] C2[C2])
[17179575.584000] ACPI: Processor [CPU0] (supports 2 throttling states)
[17179576.568000] VP_IDE: IDE controller at PCI slot 0000:00:07.1
[17179576.568000] PCI: Via IRQ fixup for 0000:00:07.1, from 255 to 0
[17179576.568000] VP_IDE: chipset revision 6
[17179576.568000] VP_IDE: not 100% native mode: will probe irqs later
[17179576.568000] VP_IDE: VIA vt82c686b (rev 40) IDE UDMA100 controller on pci0000:00:07.1
[17179576.568000]     ide0: BM-DMA at 0xd000-0xd007, BIOS settings: hda:DMA, hdb:pio
[17179576.568000]     ide1: BM-DMA at 0xd008-0xd00f, BIOS settings: hdc:pio, hdd:DMA
[17179576.568000] Probing IDE interface ide0...
[17179576.984000] hda: SAMSUNG SP1213N, ATA DISK drive
[17179577.656000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179577.656000] Probing IDE interface ide1...
[17179578.796000] hdd: BENQ DVD LS DW1655, ATAPI CD/DVD-ROM drive
[17179578.852000] ide1 at 0x170-0x177,0x376 on irq 15
[17179578.864000] hda: max request size: 512KiB
[17179578.876000] hda: 234493056 sectors (120060 MB) w/8192KiB Cache, CHS=16383/255/63, UDMA(100)
[17179578.884000] hda: cache flushes supported
[17179578.884000]  hda: hda1 hda2 hda3
[17179578.920000] hdd: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179578.920000] Uniform CD-ROM driver Revision: 3.20
[17179579.216000] usbcore: registered new driver usbfs
[17179579.216000] usbcore: registered new driver hub
[17179579.220000] USB Universal Host Controller Interface driver v3.0
[17179579.220000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 10
[17179579.220000] PCI: setting IRQ 10 as level-triggered
[17179579.220000] ACPI: PCI Interrupt 0000:00:07.2[D] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
[17179579.220000] uhci_hcd 0000:00:07.2: UHCI Host Controller
[17179579.220000] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[17179579.220000] uhci_hcd 0000:00:07.2: irq 10, io base 0x0000d400
[17179579.220000] usb usb1: configuration #1 chosen from 1 choice
[17179579.220000] hub 1-0:1.0: USB hub found
[17179579.220000] hub 1-0:1.0: 2 ports detected
[17179579.248000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[17179579.344000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 7
[17179579.344000] PCI: setting IRQ 7 as level-triggered
[17179579.344000] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LNKB] -> GSI 7 (level, low) -> IRQ 7
[17179579.344000] ohci_hcd 0000:00:09.0: OHCI Host Controller
[17179579.344000] ohci_hcd 0000:00:09.0: new USB bus registered, assigned bus number 2
[17179579.344000] ohci_hcd 0000:00:09.0: irq 7, io mem 0xef001000
[17179579.904000] usb usb2: configuration #1 chosen from 1 choice
[17179579.904000] hub 2-0:1.0: USB hub found
[17179579.904000] hub 2-0:1.0: 2 ports detected
[17179580.048000] usb 1-1: new full speed USB device using uhci_hcd and address 2
[17179580.236000] usb 1-1: configuration #1 chosen from 1 choice
[17179580.480000] usb 1-2: new full speed USB device using uhci_hcd and address 3
[17179580.656000] usb 1-2: configuration #1 chosen from 1 choice
[17179580.772000] kjournald starting.  Commit interval 5 seconds
[17179580.772000] EXT3-fs: mounted filesystem with ordered data mode.
[17179580.960000] usb 2-2: new low speed USB device using ohci_hcd and address 2
[17179581.172000] usb 2-2: configuration #1 chosen from 1 choice
[17179593.528000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179593.600000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179593.748000] FDC 0 is a post-1991 82077
[17179593.920000] Linux Tulip driver version 1.1.14 (May 6, 2006)
[17179593.924000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[17179593.924000] PCI: setting IRQ 11 as level-triggered
[17179593.924000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[17179593.924000] tulip0:  MII transceiver #1 config 3100 status 7869 advertising 05e1.
[17179593.924000] tulip0:  MII transceiver #2 config 1000 status 7849 advertising 05e1.
[17179593.924000] tulip0:  MII transceiver #3 config 1000 status 7849 advertising 05e1.
[17179593.928000] tulip0:  MII transceiver #4 config 1000 status 7849 advertising 05e1.
[17179593.928000] eth0: ADMtek Comet rev 17 at Port 0xdc00, 00:0A:CD:07:EA:A2, IRQ 11.
[17179593.928000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
[17179593.928000] tulip1:  MII transceiver #1 config 3100 status 7849 advertising 05e1.
[17179593.928000] tulip1:  MII transceiver #2 config 1000 status 7849 advertising 05e1.
[17179593.928000] tulip1:  MII transceiver #3 config 1000 status 7849 advertising 05e1.
[17179593.928000] tulip1:  MII transceiver #4 config 1000 status 7849 advertising 05e1.
[17179593.928000] eth1: ADMtek Comet rev 17 at Port 0xe000, 00:0A:CD:07:E8:9E, IRQ 10.
[17179593.972000] parport_pc: VIA 686A/8231 detected
[17179593.972000] parport_pc: probing current configuration
[17179593.972000] parport_pc: Current parallel port base: 0x0
[17179593.972000] parport_pc: VIA parallel port disabled in BIOS
[17179593.996000] Linux agpgart interface v0.101 (c) Dave Jones
[17179594.016000] agpgart: Detected VIA Twister-K/KT133x/KM133 chipset
[17179594.024000] agpgart: AGP aperture is 64M @ 0xe8000000
[17179594.408000] irda_init()
[17179594.408000] NET: Registered protocol family 23
[17179594.480000] input: PC Speaker as /class/input/input1
[17179594.988000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 12
[17179594.988000] PCI: setting IRQ 12 as level-triggered
[17179594.988000] ACPI: PCI Interrupt 0000:00:0c.0[A] -> Link [LNKA] -> GSI 12 (level, low) -> IRQ 12
[17179595.284000] usbcore: registered new driver hiddev
[17179595.292000] input: Logitech USB-PS/2 Optical Mouse as /class/input/input2
[17179595.296000] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:09.0-2
[17179595.296000] usbcore: registered new driver usbhid
[17179595.296000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179595.824000] ts: Compaq touchscreen protocol output
[17179595.848000] Linux video capture interface: v1.00
[17179595.868000] quickcam [30.476822]: ----------LOADING QUICKCAM MODULE------------
[17179595.868000] quickcam [30.476838]: struct quickcam size: 4148
[17179595.868000] quickcam: QuickCam USB camera found (driver version QuickCam Messenger/Communicate USB 1.5 $Date: 2006/11/05 00:00:00 $)
[17179595.868000] quickcam: Kernel:2.6.17-11-generic bus:1 class:FF subclass:FF vendor:046D product:08F6
[17179595.868000] quickcam [30.476959]: poisoning qc in qc_usb_init
[17179595.984000] quickcam [30.590111]: E00A contains 08F6
[17179595.984000] quickcam: Sensor VV6450 detected
[17179595.984000] input: Quickcam snapshot button as /class/input/input3
[17179595.984000] quickcam [30.591410]: Quickcam snapshot button registered on usb-0000:00:07.2-2/input0
[17179595.984000] quickcam: Registered device: /dev/video0
[17179595.984000] usbcore: registered new driver quickcam
[17179596.204000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 2 if 0 alt 0 proto 2 vid 0x03F0 pid 0x7104
[17179596.204000] usbcore: registered new driver usblp
[17179596.204000] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[17179596.344000] NET: Registered protocol family 17
[17179596.648000] usbcore: registered new driver snd-usb-audio
[17179596.952000] lp: driver loaded but no devices found
[17179597.072000] Adding 522104k swap on /dev/disk/by-uuid/ad296884-973e-4659-8fb0-923817dcc9e2.  Priority:-1 extents:1 across:522104k
[17179597.184000] EXT3 FS on hda2, internal journal
[17179597.460000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179597.460000] md: bitmap version 4.39
[17179597.816000] device-mapper: 4.6.0-ioctl (2006-02-17) initialised: dm-devel@redhat.com
[17179598.212000] 0000:00:0a.0: tulip_stop_rxtx() failed (CSR5 0xfc664010 CSR6 0xff972113)
[17179598.212000] eth0: Setting full-duplex based on MII#1 link partner capability of 45e1.
[17179620.496000] ACPI: Power Button (FF) [PWRF]
[17179620.496000] ACPI: Power Button (CM) [PWRB]
[17179621.248000] ibm_acpi: ec object not found
[17179621.304000] pcc_acpi: loading...
[17179621.980000] powernow: No powernow capabilities detected
[17179626.840000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[17179626.840000] apm: overridden by ACPI.
[17179638.892000] ip_tables: (C) 2000-2006 Netfilter Core Team
[17179639.420000] Netfilter messages via NETLINK v0.30.
[17179639.624000] ip_conntrack version 2.4 (4095 buckets, 32760 max) - 224 bytes per conntrack
[17179653.740000] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[17179654.372000] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[17179654.380000] NFSD: starting 90-second grace period
[17179666.008000] Bluetooth: Core ver 2.8
[17179666.008000] NET: Registered protocol family 31
[17179666.008000] Bluetooth: HCI device and connection manager initialized
[17179666.008000] Bluetooth: HCI socket layer initialized
[17179666.160000] Bluetooth: L2CAP ver 2.8
[17179666.160000] Bluetooth: L2CAP socket layer initialized
[17179666.392000] Bluetooth: HIDP (Human Interface Emulation) ver 1.1-mh1
[17179666.540000] Bluetooth: RFCOMM socket layer initialized
[17179666.540000] Bluetooth: RFCOMM TTY layer initialized
[17179666.540000] Bluetooth: RFCOMM ver 1.7
[17179843.560000] usb 2-1: new full speed USB device using ohci_hcd and address 3
[17179843.776000] usb 2-1: configuration #1 chosen from 1 choice
[17179844.044000] usbcore: registered new driver libusual
[17179844.188000] SCSI subsystem initialized
[17179844.204000] Initializing USB Mass Storage driver...
[17179844.204000] scsi0 : SCSI emulation for USB Mass Storage devices
[17179844.204000] usbcore: registered new driver usb-storage
[17179844.204000] USB Mass Storage support registered.
[17179844.204000] usb-storage: device found at 3
[17179844.204000] usb-storage: waiting for device to settle before scanning
[17179849.204000] usb-storage: device scan complete
[17179849.212000]   Vendor: NIKON     Model: DSC COOLPIX L3    Rev: 1.00
[17179849.212000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[17179849.388000] SCSI device sda: 2012160 512-byte hdwr sectors (1030 MB)
[17179849.392000] sda: Write Protect is off
[17179849.392000] sda: Mode Sense: 18 00 00 08
[17179849.392000] sda: assuming drive cache: write through
[17179849.412000] SCSI device sda: 2012160 512-byte hdwr sectors (1030 MB)
[17179849.420000] sda: Write Protect is off
[17179849.420000] sda: Mode Sense: 18 00 00 08
[17179849.420000] sda: assuming drive cache: write through
[17179849.420000]  sda: sda1
[17179849.436000] sd 0:0:0:0: Attached scsi removable disk sda
[17179849.464000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17179851.048000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17180126.756000] usb 2-1: USB disconnect, address 3
[17183808.276000] usb 2-1: new full speed USB device using ohci_hcd and address 4
[17183808.488000] usb 2-1: configuration #1 chosen from 1 choice
[17183808.492000] scsi1 : SCSI emulation for USB Mass Storage devices
[17183808.492000] usb-storage: device found at 4
[17183808.492000] usb-storage: waiting for device to settle before scanning
[17183813.492000] usb-storage: device scan complete
[17183813.500000]   Vendor: NIKON     Model: DSC COOLPIX L3    Rev: 1.00
[17183813.500000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[17183813.540000] SCSI device sda: 2012160 512-byte hdwr sectors (1030 MB)
[17183813.548000] sda: Write Protect is off
[17183813.548000] sda: Mode Sense: 18 00 00 08
[17183813.548000] sda: assuming drive cache: write through
[17183813.568000] SCSI device sda: 2012160 512-byte hdwr sectors (1030 MB)
[17183813.576000] sda: Write Protect is off
[17183813.576000] sda: Mode Sense: 18 00 00 08
[17183813.576000] sda: assuming drive cache: write through
[17183813.576000]  sda: sda1
[17183813.592000] sd 1:0:0:0: Attached scsi removable disk sda
[17183813.592000] sd 1:0:0:0: Attached scsi generic sg0 type 0
[17183815.884000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17183849.432000] usb 2-1: reset full speed USB device using ohci_hcd and address 4
[17183849.612000] usb 2-1: device descriptor read/64, error -110
[17183850.008000] usb 2-1: USB disconnect, address 4
[17183850.012000]  1:0:0:0: rejecting I/O to dead device
[17183850.012000]  1:0:0:0: rejecting I/O to dead device
[17183850.012000]  1:0:0:0: rejecting I/O to dead device
[17183850.012000]  1:0:0:0: rejecting I/O to dead device
[17183850.016000] sda : READ CAPACITY failed.
[17183850.016000] sda : status=0, message=00, host=1, driver=00 
[17183850.016000] sda : sense not available. 
[17183850.016000]  1:0:0:0: rejecting I/O to dead device
[17183850.016000] sda: Write Protect is off
[17183850.016000] sda: Mode Sense: 00 00 00 00
[17183850.016000] sda: assuming drive cache: write through
[17183850.016000]  1:0:0:0: rejecting I/O to dead device
[17183850.016000]  1:0:0:0: rejecting I/O to dead device
[17183850.016000]  1:0:0:0: rejecting I/O to dead device
[17183850.016000]  1:0:0:0: rejecting I/O to dead device
[17183850.016000]  1:0:0:0: rejecting I/O to dead device
[17183850.016000] sda : READ CAPACITY failed.
[17183850.016000] sda : status=0, message=00, host=1, driver=00 
[17183850.016000] sda : sense not available. 
[17183850.016000]  1:0:0:0: rejecting I/O to dead device
[17183850.016000] sda: Write Protect is off
[17183850.016000] sda: Mode Sense: 00 00 00 00
[17183850.016000] sda: assuming drive cache: write through
[17183850.016000]  sda:<3> 1:0:0:0: rejecting I/O to dead device
[17183850.016000] Buffer I/O error on device sda, logical block 0
[17183850.016000]  1:0:0:0: rejecting I/O to dead device
[17183850.016000] Buffer I/O error on device sda, logical block 0
[17183850.016000]  unable to read partition table
[17183850.016000]  1:0:0:0: rejecting I/O to dead device

```

---

### Post by jeffathehutt on 2007-03-24
Have you tried a different web browser?  This sounds like a problem with either firefox or Xorg.

You might want to try epiphany just to see if it makes a difference.  If your cpu still spikes, it is most likely a problem with the video drivers.  I have that same video card in my other computer, and I haven't noticed this problem (I'm using the official nVidia drivers)

---

### Post by mich_r on 2007-03-25
I just tried Epiphany - it behavies a little different : there is no 100% cpu when browser just waits for the site response , but as soon as the response is received it starts to hog almost 100% cpu until the page is fully rendered (it is very clear especially for slow answering web pages).

The 100% cpu during scroll symptom is the same in epiphany, but I can see it also in the Nautilus, when scrolling folder windows.

I also tried to replace my video card with the very old one - that is nvidia vanta 16Mb - the symptoms were exactly the same.

Any suggestions what to do with it ? Should I post my xorg.conf here ?

---

### Post by jeffathehutt on 2007-03-25
The only suggestion I have is to install the nVidia drivers again.  While unlikely, it is possible they weren't installed correctly before.  The only time my machine ever lags like that is when the official drivers aren't installed.  Once I install them, the lag goes away.

---

### Post by Benchrest on 2007-03-25
I have the same symptoms as you with the exception mine occurs infrequently. May work ok for a week and then fail several times in a day. Only recently have I ran TOP when it happens. System monitor shows 100% but doesn't show the culprit. I'll keep monitoring this site for resolution. Meanwhile I need to see if I have the same video drivers as you. I have just blamed mine previously on my laptop being 11 years old.

---

### Post by mich_r on 2007-03-25
Thank you for the answers.

I have used nvidia-glx drivers from the official packages (tried both "legacy" and "non-legacy"). Now I am running on the nv driver, makes no difference to me and I do not need 3D.

jeffathehutt: I will try to reinstall some drivers tommorow, just after finishing my current ugly work task (urgent of course)

---

### Post by mich_r on 2007-03-26
Hello again

I have done a lot of testing. Reinstalled nvidia drivers, tried different kernels, tied official firefox from mozilla.com... etc. etc. and finally I discovered something! 
Disabling custom theme (I used to use Ubuntu Tango theme) firefox behavies the same as epiphany - that means no cpu hogging during web site searchig (dns resolution or something - maybe the little animation in the corner was causing it) . 100% cpu usage starts during page rendering or scrolling.

Now I am almost sure that the problem is on the graphics card driver. But the bad news are I am really out of ideas what to with it :(

---

