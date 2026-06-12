---
title: "Swinging back to Microsoft after repeated Ubuntu hangs."
date: 2007-01-23
forum: General Help
---

### Post by Dmole on 2007-01-23
my little server ran smoothly with server2003 for years
I installed xubuntu and now it hangs every few days.
I've asked for help on this subject twice before but no useful replies were posted.
[http://www.ubuntuforums.org/showthread.php?t=330867](http://www.ubuntuforums.org/showthread.php?t=330867)
[http://www.ubuntuforums.org/showthread.php?t=331603](http://www.ubuntuforums.org/showthread.php?t=331603)

I'm giving it one more shot before I write off Ubuntu as intolerant of my system.
Help I want to believe in Linux!
How do I stop it from hanging?

---

### Post by Shatrat on 2007-01-23
What video card do you have and what drivers are you using?
Also, the command dmesg can sometimes yield useful information about errors.

---

### Post by Dmole on 2007-01-23
thanks for the command.:)

My Matrox G400 works fine as far as i can see

dmesg gives this:
  [17179569.184000 ] Linux version 2.6.15-27-386  (buildd@terranova )  (gcc version 4.0.3  (Ubuntu 4.0.3-1ubuntu5 ) ) #1 PREEMPT Fri Dec 8 17: 51: 56 UTC 2006
 [17179569.184000 ] BIOS-provided physical RAM map: 
 [17179569.184000 ]  BIOS-e820:  0000000000000000 - 00000000000a0000  (usable )
 [17179569.184000 ]  BIOS-e820:  00000000000f0000 - 0000000000100000  (reserved )
 [17179569.184000 ]  BIOS-e820:  0000000000100000 - 000000001fffd000  (usable )
 [17179569.184000 ]  BIOS-e820:  000000001fffd000 - 000000001ffff000  (ACPI data )
 [17179569.184000 ]  BIOS-e820:  000000001ffff000 - 0000000020000000  (ACPI NVS )
 [17179569.184000 ]  BIOS-e820:  00000000ffff0000 - 0000000100000000  (reserved )
 [17179569.184000 ] 0MB HIGHMEM available.
 [17179569.184000 ] 511MB LOWMEM available.
 [17179569.184000 ] On node 0 totalpages:  131069
 [17179569.184000 ]   DMA zone:  4096 pages, LIFO batch: 0
 [17179569.184000 ]   DMA32 zone:  0 pages, LIFO batch: 0
 [17179569.184000 ]   Normal zone:  126973 pages, LIFO batch: 31
 [17179569.184000 ]   HighMem zone:  0 pages, LIFO batch: 0
 [17179569.184000 ] DMI 2.0 present.
 [17179569.184000 ] ACPI:  RSDP  (v000 ASUS                                   ) @ 0x000f8020
 [17179569.184000 ] ACPI:  RSDT  (v001 ASUS   P2B-F    0x58582e31 ASUS 0x31303030 ) @ 0x1fffd000
 [17179569.184000 ] ACPI:  FADT  (v001 ASUS   P2B-F    0x58582e31 ASUS 0x31303030 ) @ 0x1fffd080
 [17179569.184000 ] ACPI:  BOOT  (v001 ASUS   P2B-F    0x58582e31 ASUS 0x31303030 ) @ 0x1fffd040
 [17179569.184000 ] ACPI:  DSDT  (v001   ASUS P2B-F    0x00001000 MSFT 0x01000001 ) @ 0x00000000
 [17179569.184000 ] ACPI:  PM-Timer IO Port:  0xe408
 [17179569.184000 ] Allocating PCI resources starting at 30000000  (gap:  20000000: dfff0000 )
 [17179569.184000 ] Built 1 zonelists
 [17179569.184000 ] Kernel command line:  root=/dev/hda6 ro quiet splash
 [17179569.184000 ] Local APIC disabled by BIOS  (or by default ) -- you can enable it with "lapic"
 [17179569.184000 ] mapped APIC to ffffd000  (01402000 )
 [17179569.184000 ] Initializing CPU#0
 [17179569.184000 ] PID hash table entries:  2048  (order:  11, 32768 bytes )
 [17179569.184000 ] Detected 501.212 MHz processor.
 [17179569.184000 ] Using pmtmr for high-res timesource
 [17179569.184000 ] Console:  colour VGA+ 80x25
 [17179573.148000 ] Dentry cache hash table entries:  131072  (order:  7, 524288 bytes )
 [17179573.152000 ] Inode-cache hash table entries:  65536  (order:  6, 262144 bytes )
 [17179573.224000 ] Memory:  508856k/524276k available  (1976k kernel code, 14808k reserved, 606k data, 288k init, 0k highmem )
 [17179573.224000 ] Checking if this processor honours the WP bit even in supervisor mode... Ok.
 [17179573.304000 ] Calibrating delay using timer specific routine.. 1003.29 BogoMIPS  (lpj=2006590 )
 [17179573.304000 ] Security Framework v1.0.0 initialized
 [17179573.304000 ] SELinux:   Disabled at boot.
 [17179573.304000 ] Mount-cache hash table entries:  512
 [17179573.304000 ] CPU:  After generic identify, caps:  0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
 [17179573.304000 ] CPU:  After vendor identify, caps:  0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
 [17179573.304000 ] CPU:  L1 I cache:  16K, L1 D cache:  16K
 [17179573.304000 ] CPU:  L2 cache:  512K
 [17179573.304000 ] CPU:  After all inits, caps:  0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000
 [17179573.304000 ] mtrr:  v2.0  (20020519 )
 [17179573.304000 ] CPU:  Intel Pentium III  (Katmai ) stepping 02
 [17179573.304000 ] Enabling fast FPU save and restore... done.
 [17179573.304000 ] Enabling unmasked SIMD FPU exception support... done.
 [17179573.304000 ] Checking 'hlt' instruction... OK.
 [17179573.320000 ] checking if image is initramfs... it is
 [17179576.396000 ] Freeing initrd memory:  6617k freed
 [17179576.440000 ] ACPI:  Looking for DSDT ... not found!
 [17179576.444000 ] ACPI:  setting ELCR to 0200  (from 1c20 )
 [17179576.444000 ] NET:  Registered protocol family 16
 [17179576.444000 ] EISA bus registered
 [17179576.444000 ] ACPI:  bus type pci registered
 [17179576.448000 ] PCI:  PCI BIOS revision 2.10 entry at 0xf0720, last bus=1
 [17179576.448000 ] PCI:  Using configuration type 1
 [17179576.448000 ] ACPI:  Subsystem revision 20051216
 [17179576.452000 ] ACPI:  Interpreter enabled
 [17179576.452000 ] ACPI:  Using PIC for interrupt routing
 [17179576.456000 ] ACPI:  PCI Interrupt Link  [LNKA ]  (IRQs 3 4 5 6 7 9 10 *11 12 14 15 )
 [17179576.456000 ] ACPI:  PCI Interrupt Link  [LNKB ]  (IRQs 3 4 5 6 7 9 *10 11 12 14 15 )
 [17179576.456000 ] ACPI:  PCI Interrupt Link  [LNKC ]  (IRQs 3 4 5 6 7 9 10 11 *12 14 15 )
 [17179576.460000 ] ACPI:  PCI Interrupt Link  [LNKD ]  (IRQs 3 4 *5 6 7 9 10 11 12 14 15 )
 [17179576.460000 ] ACPI:  PCI Root Bridge  [PCI0 ]  (0000: 00 )
 [17179576.460000 ] PCI:  Probing PCI hardware  (bus 00 )
 [17179576.460000 ] ACPI:  Assume root bridge  [\_SB_.PCI0 ] bus is 0
 [17179576.464000 ] PCI quirk:  region e400-e43f claimed by PIIX4 ACPI
 [17179576.468000 ] PCI quirk:  region e800-e80f claimed by PIIX4 SMB
 [17179576.468000 ] PIIX4 devres B PIO at 0290-0297
 [17179576.468000 ] Boot video device is 0000: 01: 00.0
 [17179576.468000 ] ACPI:  PCI Interrupt Routing Table  [\_SB_.PCI0._PRT ]
 [17179576.484000 ] Linux Plug and Play Support v0.97  (c ) Adam Belay
 [17179576.484000 ] pnp:  PnP ACPI init
 [17179576.496000 ] pnp:  PnP ACPI:  found 11 devices
 [17179576.496000 ] PnPBIOS:  Disabled by ACPI PNP
 [17179576.496000 ] PCI:  Using ACPI for IRQ routing
 [17179576.496000 ] PCI:  If a device doesn't work, try "pci=routeirq".  If it helps, post a report
 [17179576.528000 ] pnp:  00: 01:  ioport range 0xe400-0xe43f could not be reserved
 [17179576.528000 ] pnp:  00: 01:  ioport range 0xe800-0xe80f has been reserved
 [17179576.528000 ] pnp:  00: 01:  ioport range 0x290-0x297 has been reserved
 [17179576.532000 ] PCI:  Bridge:  0000: 00: 01.0
 [17179576.532000 ]   IO window:  disabled.
 [17179576.532000 ]   MEM window:  e2000000-e2ffffff
 [17179576.532000 ]   PREFETCH window:  e3f00000-e6ffffff
 [17179576.532000 ] Simple Boot Flag at 0x46 set to 0x1
 [17179576.532000 ] audit:  initializing netlink socket  (disabled )
 [17179576.532000 ] audit (1169571233.532: 1 ):  initialized
 [17179576.532000 ] VFS:  Disk quotas dquot_6.5.1
 [17179576.532000 ] Dquot-cache hash table entries:  1024  (order 0, 4096 bytes )
 [17179576.532000 ] Initializing Cryptographic API
 [17179576.532000 ] io scheduler noop registered
 [17179576.532000 ] io scheduler anticipatory registered
 [17179576.532000 ] io scheduler deadline registered
 [17179576.532000 ] io scheduler cfq registered
 [17179576.532000 ] Limiting direct PCI/PCI transfers.
 [17179576.536000 ] isapnp:  Scanning for PnP cards...
 [17179576.888000 ] isapnp:  No Plug & Play device found
 [17179576.964000 ] PNP:  PS/2 Controller  [PNP0303: PS2K ] at 0x60,0x64 irq 1
 [17179576.964000 ] PNP:  PS/2 controller doesn't have AUX irq; using default 12
 [17179576.968000 ] serio:  i8042 AUX port at 0x60,0x64 irq 12
 [17179576.968000 ] serio:  i8042 KBD port at 0x60,0x64 irq 1
 [17179576.968000 ] Serial:  8250/16550 driver $Revision:  1.90 $ 48 ports, IRQ sharing enabled
 [17179576.968000 ] serial8250:  ttyS0 at I/O 0x3f8  (irq = 4 ) is a 16550A
 [17179576.968000 ] serial8250:  ttyS1 at I/O 0x2f8  (irq = 3 ) is a 16550A
 [17179576.980000 ] 00: 08:  ttyS0 at I/O 0x3f8  (irq = 4 ) is a 16550A
 [17179576.980000 ] 00: 09:  ttyS1 at I/O 0x2f8  (irq = 3 ) is a 16550A
 [17179576.980000 ] RAMDISK driver initialized:  16 RAM disks of 65536K size 1024 blocksize
 [17179576.980000 ] Uniform Multi-Platform E-IDE driver Revision:  7.00alpha2
 [17179576.980000 ] ide:  Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
 [17179576.980000 ] mice:  PS/2 mouse device common for all mice
 [17179576.984000 ] EISA:  Probing bus 0 at eisa.0
 [17179576.984000 ] EISA:  Detected 0 cards.
 [17179576.984000 ] NET:  Registered protocol family 2
 [17179577.020000 ] IP route cache hash table entries:  8192  (order:  3, 32768 bytes )
 [17179577.020000 ] TCP established hash table entries:  32768  (order:  5, 131072 bytes )
 [17179577.020000 ] TCP bind hash table entries:  32768  (order:  5, 131072 bytes )
 [17179577.020000 ] TCP:  Hash tables configured  (established 32768 bind 32768 )
 [17179577.020000 ] TCP reno registered
 [17179577.020000 ] TCP bic registered
 [17179577.020000 ] NET:  Registered protocol family 1
 [17179577.020000 ] NET:  Registered protocol family 8
 [17179577.020000 ] NET:  Registered protocol family 20
 [17179577.020000 ] Using IPI Shortcut mode
 [17179577.020000 ] ACPI wakeup devices:  
 [17179577.020000 ] PCI0 UAR1 UAR2 USB0 
 [17179577.020000 ] ACPI:   (supports S0 S1 S4 S5 )
 [17179577.020000 ] Freeing unused kernel memory:  288k freed
 [17179577.224000 ] vga16fb:  initializing
 [17179577.224000 ] vga16fb:  mapped to 0xc00a0000
 [17179577.284000 ] Console:  switching to colour frame buffer device 80x25
 [17179577.284000 ] fb0:  VGA16 VGA frame buffer device
 [17179577.296000 ] input:  AT Translated Set 2 keyboard as /class/input/input0
 [17179578.416000 ] Capability LSM initialized
 [17179578.544000 ] ACPI:  CPU0  (power states:  C1 [C1 ] C2 [C2 ] )
 [17179580.076000 ] PIIX4:  IDE controller at PCI slot 0000: 00: 04.1
 [17179580.076000 ] PIIX4:  chipset revision 1
 [17179580.076000 ] PIIX4:  not 100% native mode:  will probe irqs later
 [17179580.076000 ]     ide0:  BM-DMA at 0xd800-0xd807, BIOS settings:  hda: DMA, hdb: pio
 [17179580.076000 ]     ide1:  BM-DMA at 0xd808-0xd80f, BIOS settings:  hdc: DMA, hdd: pio
 [17179580.076000 ] Probing IDE interface ide0...
 [17179580.364000 ] hda:  Maxtor 98196H8, ATA DISK drive
 [17179581.036000 ] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
 [17179581.036000 ] Probing IDE interface ide1...
 [17179581.772000 ] hdc:  ATAPI CD-ROM DRIVE 40X MAXIMUM, ATAPI CD/DVD-ROM drive
 [17179582.108000 ] hdc:  Disabling  (U )DMA for ATAPI CD-ROM DRIVE 40X MAXIMUM  (blacklisted )
 [17179582.108000 ] ide1 at 0x170-0x177,0x376 on irq 15
 [17179582.132000 ] hda:  max request size:  128KiB
 [17179582.152000 ] hda:  160086528 sectors  (81964 MB ) w/2048KiB Cache, CHS=65535/16/63, UDMA (33 )
 [17179582.152000 ] hda:  cache flushes not supported
 [17179582.152000 ]  hda:  hda1 hda2 hda3 < hda5 hda6 hda7 >
 [17179582.240000 ] hdc:  ATAPI 40X CD-ROM drive, 128kB Cache
 [17179582.240000 ] Uniform CD-ROM driver Revision:  3.20
 [17179583.244000 ] usbcore:  registered new driver usbfs
 [17179583.248000 ] usbcore:  registered new driver hub
 [17179583.256000 ] USB Universal Host Controller Interface driver v2.3
 [17179583.256000 ] **** SET:  Misaligned resource pointer:  dfb605e2 Type 07 Len 0
 [17179583.256000 ] ACPI:  PCI Interrupt Link  [LNKD ] enabled at IRQ 5
 [17179583.256000 ] PCI:  setting IRQ 5 as level-triggered
 [17179583.256000 ] ACPI:  PCI Interrupt 0000: 00: 04.2 [D ] -> Link  [LNKD ] -> GSI 5  (level, low ) -> IRQ 5
 [17179583.256000 ] uhci_hcd 0000: 00: 04.2:  UHCI Host Controller
 [17179583.256000 ] uhci_hcd 0000: 00: 04.2:  new USB bus registered, assigned bus number 1
 [17179583.256000 ] uhci_hcd 0000: 00: 04.2:  irq 5, io base 0x0000d400
 [17179583.260000 ] hub 1-0: 1.0:  USB hub found
 [17179583.260000 ] hub 1-0: 1.0:  2 ports detected
 [17179583.376000 ] ieee1394:  Initialized config rom entry `ip1394'
 [17179583.384000 ] ohci1394:  $Rev:  1313 $ Ben Collins <bcollins@debian.org>
 [17179583.384000 ] **** SET:  Misaligned resource pointer:  dfb600e2 Type 07 Len 0
 [17179583.384000 ] ACPI:  PCI Interrupt Link  [LNKA ] enabled at IRQ 11
 [17179583.384000 ] PCI:  setting IRQ 11 as level-triggered
 [17179583.384000 ] ACPI:  PCI Interrupt 0000: 00: 09.2 [B ] -> Link  [LNKA ] -> GSI 11  (level, low ) -> IRQ 11
 [17179583.504000 ] ohci1394:  fw-host0:  OHCI-1394 1.1  (PCI ):  IRQ= [11 ]  MMIO= [e1800000-e18007ff ]  Max Packet= [2048 ]
 [17179583.604000 ] usb 1-2:  new low speed USB device using uhci_hcd and address 2
 [17179583.736000 ] Attempting manual resume
 [17179583.824000 ] usbcore:  registered new driver hiddev
 [17179583.860000 ] EXT3-fs:  INFO:  recovery required on readonly filesystem.
 [17179583.860000 ] EXT3-fs:  write access will be enabled during recovery.
 [17179583.876000 ] input:  Gyration GyroPoint RF Technology Receiver as /class/input/input1
 [17179583.876000 ] input:  USB HID v1.00 Keyboard  [Gyration GyroPoint RF Technology Receiver ] on usb-0000: 00: 04.2-2
 [17179583.904000 ] input:  Gyration GyroPoint RF Technology Receiver as /class/input/input2
 [17179583.904000 ] input,hiddev96:  USB HID v1.00 Mouse  [Gyration GyroPoint RF Technology Receiver ] on usb-0000: 00: 04.2-2
 [17179583.904000 ] usbcore:  registered new driver usbhid
 [17179583.904000 ] drivers/usb/input/hid-core.c:  v2.6: USB HID core driver
 [17179584.776000 ] ieee1394:  Host added:  ID: BUS [0-00: 1023 ]  GUID [00023c00910173b4 ]
 [17179591.876000 ] EXT3-fs:  hda6:  orphan cleanup on readonly fs
 [17179591.876000 ] kjournald starting.  Commit interval 5 seconds
 [17179591.920000 ] ext3_orphan_cleanup:  deleting unreferenced inode 1119704
 [17179591.940000 ] ext3_orphan_cleanup:  deleting unreferenced inode 1119703
 [17179591.940000 ] ext3_orphan_cleanup:  deleting unreferenced inode 1119702
 [17179591.940000 ] ext3_orphan_cleanup:  deleting unreferenced inode 1119700
 [17179591.940000 ] ext3_orphan_cleanup:  deleting unreferenced inode 1119697
 [17179591.948000 ] ext3_orphan_cleanup:  deleting unreferenced inode 1119696
 [17179591.960000 ] ext3_orphan_cleanup:  deleting unreferenced inode 1119695
 [17179591.964000 ] ext3_orphan_cleanup:  deleting unreferenced inode 1119694
 [17179591.964000 ] ext3_orphan_cleanup:  deleting unreferenced inode 1119687
 [17179591.976000 ] ext3_orphan_cleanup:  deleting unreferenced inode 1119686
 [17179591.976000 ] ext3_orphan_cleanup:  deleting unreferenced inode 1119685
 [17179591.976000 ] ext3_orphan_cleanup:  deleting unreferenced inode 1119681
 [17179591.984000 ] ext3_orphan_cleanup:  deleting unreferenced inode 1119679
 [17179591.992000 ] ext3_orphan_cleanup:  deleting unreferenced inode 1119676
 [17179591.992000 ] ext3_orphan_cleanup:  deleting unreferenced inode 1119675
 [17179591.992000 ] ext3_orphan_cleanup:  deleting unreferenced inode 1119674
 [17179592.000000 ] ext3_orphan_cleanup:  deleting unreferenced inode 1119672
 [17179592.020000 ] ext3_orphan_cleanup:  deleting unreferenced inode 974190
 [17179592.048000 ] ext3_orphan_cleanup:  deleting unreferenced inode 973727
 [17179592.060000 ] ext3_orphan_cleanup:  deleting unreferenced inode 973725
 [17179592.064000 ] ext3_orphan_cleanup:  deleting unreferenced inode 973723
 [17179592.064000 ] ext3_orphan_cleanup:  deleting unreferenced inode 974694
 [17179592.072000 ] ext3_orphan_cleanup:  deleting unreferenced inode 973583
 [17179592.072000 ] ext3_orphan_cleanup:  deleting unreferenced inode 973582
 [17179592.080000 ] ext3_orphan_cleanup:  deleting unreferenced inode 974692
 [17179592.096000 ] ext3_orphan_cleanup:  deleting unreferenced inode 975536
 [17179592.096000 ] ext3_orphan_cleanup:  deleting unreferenced inode 975535
 [17179592.100000 ] ext3_orphan_cleanup:  deleting unreferenced inode 975533
 [17179592.100000 ] ext3_orphan_cleanup:  deleting unreferenced inode 973840
 [17179592.128000 ] ext3_orphan_cleanup:  deleting unreferenced inode 1249539
 [17179592.152000 ] ext3_orphan_cleanup:  deleting unreferenced inode 373306
 [17179592.152000 ] EXT3-fs:  hda6:  31 orphan inodes deleted
 [17179592.152000 ] EXT3-fs:  recovery complete.
 [17179592.256000 ] EXT3-fs:  mounted filesystem with ordered data mode.
 [17179603.728000 ] ts:  Compaq touchscreen protocol output
 [17179605.540000 ] Linux agpgart interface v0.101  (c ) Dave Jones
 [17179605.548000 ] agpgart:  Detected an Intel 440BX Chipset.
 [17179605.552000 ] agpgart:  AGP aperture is 16M @ 0xe7000000
 [17179605.680000 ] pci_hotplug:  PCI Hot Plug PCI Core version:  0.5
 [17179605.688000 ] shpchp:  Standard Hot Plug PCI Controller Driver version:  0.4
 [17179607.012000 ] piix4_smbus 0000: 00: 04.3:  Found 0000: 00: 04.3 device
 [17179607.032000 ] gameport:  EMU10K1 is pci0000: 00: 09.1/gameport0, io 0xb800, speed 1242kHz
 [17179607.220000 ] Linux Tulip driver version 1.1.13  (December 15, 2004 )
 [17179607.220000 ] **** SET:  Misaligned resource pointer:  dfb4da22 Type 07 Len 0
 [17179607.224000 ] ACPI:  PCI Interrupt Link  [LNKC ] enabled at IRQ 12
 [17179607.224000 ] PCI:  setting IRQ 12 as level-triggered
 [17179607.224000 ] ACPI:  PCI Interrupt 0000: 00: 0a.0 [A ] -> Link  [LNKC ] -> GSI 12  (level, low ) -> IRQ 12
 [17179607.224000 ] tulip0:   MII transceiver #1 config 3100 status 7869 advertising 05e1.
 [17179607.224000 ] tulip0:   MII transceiver #2 config 1000 status 7849 advertising 05e1.
 [17179607.224000 ] tulip0:   MII transceiver #3 config 1000 status 7849 advertising 05e1.
 [17179607.224000 ] tulip0:   MII transceiver #4 config 1000 status 7849 advertising 05e1.
 [17179607.224000 ] eth0:  ADMtek Comet rev 17 at 0001b400, 00: 04: 5A: 84: 69: FD, IRQ 12.
 [17179607.340000 ] Linux video capture interface:  v1.00
 [17179607.428000 ] bttv:  driver version 0.9.16 loaded
 [17179607.428000 ] bttv:  using 8 buffers with 2080k  (520 pages ) each for capture
 [17179607.428000 ] bttv:  Host bridge needs ETBF enabled.
 [17179607.428000 ] bttv:  Bt8xx card found  (0 ).
 [17179607.428000 ] **** SET:  Misaligned resource pointer:  dfb4da22 Type 07 Len 0
 [17179607.432000 ] ACPI:  PCI Interrupt Link  [LNKB ] enabled at IRQ 10
 [17179607.432000 ] PCI:  setting IRQ 10 as level-triggered
 [17179607.432000 ] ACPI:  PCI Interrupt 0000: 00: 0b.0 [A ] -> Link  [LNKB ] -> GSI 10  (level, low ) -> IRQ 10
 [17179607.432000 ] bttv0:  Bt848  (rev 18 ) at 0000: 00: 0b.0, irq:  10, latency:  32, mmio:  0xe3000000
 [17179607.432000 ] bttv0:  using:   *** UNKNOWN/GENERIC ***   [card=0,autodetected ]
 [17179607.432000 ] bttv0:  enabling ETBF  (430FX/VP3 compatibilty )
 [17179607.432000 ] bttv0:  gpio:  en=00000000, out=00000000 in=00fffffb  [init ]
 [17179607.524000 ] bttv0:  detected by eeprom:  Hauppauge  (bt848 )  [card=2 ]
 [17179607.620000 ] tveeprom 1-0050:  Hauppauge model 56101, rev E M2, serial# 475602
 [17179607.620000 ] tveeprom 1-0050:  tuner model is Philips FI1236 MK2  (idx 10, type 2 )
 [17179607.620000 ] tveeprom 1-0050:  TV standards NTSC (M )  (eeprom 0x08 )
 [17179607.620000 ] tveeprom 1-0050:  audio processor is None  (idx 0 )
 [17179607.620000 ] tveeprom 1-0050:  has no radio
 [17179607.620000 ] bttv0:  using tuner=2
 [17179607.620000 ] bttv0:  i2c:  checking for MSP34xx @ 0x80... not found
 [17179607.620000 ] bttv0:  i2c:  checking for TDA9875 @ 0xb0... not found
 [17179607.624000 ] bttv0:  i2c:  checking for TDA7432 @ 0x8a... not found
 [17179607.688000 ] bttv0:  i2c:  checking for TDA9887 @ 0x86... not found
 [17179607.728000 ] Driver for 1-wire Dallas network protocol.
 [17179607.756000 ] tuner 1-0061:  chip found @ 0xc2  (bt848 #0  [sw ] )
 [17179607.756000 ] tuner 1-0061:  type set to 2  (Philips NTSC  (FI1236,FM1236 and compatibles ) )
 [17179607.788000 ] bttv0:  registered device video0
 [17179607.788000 ] bttv0:  registered device vbi0
 [17179607.796000 ] matrox_w1 0000: 01: 00.0:  Matrox G400 GPIO transport layer for 1-wire.
 [17179608.404000 ] Real Time Clock Driver v1.12
 [17179608.724000 ] ACPI:  PCI Interrupt 0000: 00: 09.0 [A ] -> Link  [LNKD ] -> GSI 5  (level, low ) -> IRQ 5
 [17179608.728000 ] Installing spdif_bug patch:  Audigy 2 Platinum  [SB0240P ]
 [17179609.324000 ] input:  PC Speaker as /class/input/input3
 [17179609.368000 ] FDC 0 is a post-1991 82077
 [17179609.876000 ] parport:  PnPBIOS parport detected.
 [17179609.876000 ] parport0:  PC-style at 0x378  (0x778 ), irq 7, dma 3  [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA ]
 [17179611.792000 ] lp0:  using parport0  (interrupt-driven ).
 [17179611.936000 ] SCSI subsystem initialized
 [17179611.956000 ] sbp2:  $Rev:  1306 $ Ben Collins <bcollins@debian.org>
 [17179611.956000 ] ieee1394:  sbp2:  Driver forced to serialize I/O  (serialize_io=1 )
 [17179611.956000 ] ieee1394:  sbp2:  Try serialize_io=0 for better performance
 [17179612.168000 ] Adding 1028152k swap on /dev/hda2.  Priority: -1 extents: 1 across: 1028152k
 [17179612.352000 ] EXT3 FS on hda6, internal journal
 [17179612.476000 ] NET:  Registered protocol family 17
 [17179612.796000 ] md:  md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
 [17179612.796000 ] md:  bitmap version 4.39
 [17179613.764000 ] device-mapper:  4.4.0-ioctl  (2005-01-12 ) initialised:  [email]dm-devel@redhat.com[/email]
 [17179614.400000 ] 0000: 00: 0a.0:  tulip_stop_rxtx ( ) failed  (CSR5 0xfc664010 CSR6 0xff972113 )
 [17179614.400000 ] eth0:  Setting full-duplex based on MII#1 link partner capability of 41e1.
 [17179615.304000 ] cdrom:  open failed.
 [17179615.708000 ] NET:  Registered protocol family 10
 [17179615.708000 ] lo:  Disabled Privacy Extensions
 [17179615.708000 ] IPv6 over IPv4 tunneling driver
 [17179620.816000 ] NTFS driver 2.1.25  [Flags:  R/O MODULE ].
 [17179620.892000 ] NTFS volume version 1.2.
 [17179620.892000 ] NTFS-fs warning  (device hda1 ):  load_system_files ( ):  Disabling sparse support due to NTFS volume version 1.2  (need at least version 3.0 ).
 [17179620.940000 ] NTFS volume version 1.2.
 [17179620.940000 ] NTFS-fs warning  (device hda5 ):  load_system_files ( ):  Disabling sparse support due to NTFS volume version 1.2  (need at least version 3.0 ).
 [17179625.844000 ] eth0:  no IPv6 routers present
 [17179629.524000 ] ACPI:  Power Button  (FF )  [PWRF ]
 [17179629.524000 ] ACPI:  Power Button  (CM )  [PWRB ]
 [17179629.888000 ] ibm_acpi:  ec object not found
 [17179629.968000 ] pcc_acpi:  loading...
 [17179643.608000 ]  [drm ] Initialized drm 1.0.1 20051102
 [17179643.668000 ] ACPI:  PCI Interrupt 0000: 01: 00.0 [A ] -> Link  [LNKA ] -> GSI 11  (level, low ) -> IRQ 11
 [17179643.672000 ]  [drm ] Initialized mga 3.2.1 20051102 on minor 0
 [17179643.676000 ] agpgart:  Found an AGP 1.0 compliant device at 0000: 00: 00.0.
 [17179643.676000 ] agpgart:  Putting AGP V2 device at 0000: 00: 00.0 into 1x mode
 [17179643.676000 ] agpgart:  Putting AGP V2 device at 0000: 01: 00.0 into 1x mode
 [17179645.764000 ] ppdev:  user-space parallel port driver
 [17179646.292000 ] apm:  BIOS version 1.2 Flags 0x03  (Driver version 1.16ac )
 [17179646.292000 ] apm:  overridden by ACPI.
 [17179647.152000 ] ip_tables:   (C ) 2000-2002 Netfilter core team
 [17179647.436000 ] Netfilter messages via NETLINK v0.30.
 [17179647.580000 ] ip_conntrack version 2.4  (4095 buckets, 32760 max ) - 232 bytes per conntrack

---

### Post by danbh on 2007-04-04
run this command:
free

Whats that say?

---

### Post by yabbadabbadont on 2007-04-04
> **danbh said:**
> run this command:
free

Whats that say?

Holy Thread Resurrection Batman!  Did you realize that the thread was two months old?  :D

---

### Post by danbh on 2007-04-04
hehehehe, no i didn't.  O well.  I still hope the guy gets the message.  It sounds like he is having trouble with some sort of power saving feature.

---

### Post by Dmole on 2008-04-20
SOLVED: I found it was a File System driver bug but thanks for the input guys!

---

