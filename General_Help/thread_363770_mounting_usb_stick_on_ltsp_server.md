---
title: "mounting usb stick on ltsp server"
date: 2007-02-17
forum: General Help
---

### Post by namelessone on 2007-02-17
I have an ltsp server running xubuntu that works great, except for one thing. Ever since I ran ltsp-build-client, I have been unable to mount usb sticks. The device sda does not appear in /dev when I stick the usb drive in.

How do I fix this? Any help would be greatly appreciated.

---

### Post by crmanski on 2007-02-20
I'm wondering a couple things.
Dapper or Edgy?

This is on a client, the server or both?

If you type the following on the command line...
```
dmesg
```
...what does the last few lines of it say? 

I got my removable devices working by checking the things mentioned here in the wiki...
[https://wiki.edubuntu.org/EnableLTSP5LocalDevices](https://wiki.edubuntu.org/EnableLTSP5LocalDevices)

> **namelessone said:**
> I have an ltsp server running xubuntu that works great, except for one thing. Ever since I ran ltsp-build-client, I have been unable to mount usb sticks. The device sda does not appear in /dev when I stick the usb drive in.

How do I fix this? Any help would be greatly appreciated.

---

### Post by namelessone on 2007-02-22
I am using Edgy. This problem is on the server.

here is the output of dmesg:
> Linux version 2.6.19custom (root@thin-client-server) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #1 Fri Jan 26 10:41:21 CST 2007
BIOS-provided physical RAM map:
 BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
 BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
 BIOS-e820: 00000000000e7000 - 0000000000100000 (reserved)
 BIOS-e820: 0000000000100000 - 00000000040fd800 (usable)
 BIOS-e820: 00000000040fd800 - 00000000040ff800 (ACPI data)
 BIOS-e820: 00000000040ff800 - 00000000040ffc00 (ACPI NVS)
 BIOS-e820: 00000000040ffc00 - 0000000010000000 (usable)
 BIOS-e820: 00000000fffe7000 - 0000000100000000 (reserved)
256MB LOWMEM available.
Entering add_active_range(0, 0, 65536) 0 entries of 256 used
Zone PFN ranges:
  DMA             0 ->     4096
  Normal       4096 ->    65536
early_node_map[1] active PFN ranges
    0:        0 ->    65536
On node 0 totalpages: 65536
  DMA zone: 32 pages used for memmap
  DMA zone: 0 pages reserved
  DMA zone: 4064 pages, LIFO batch:0
  Normal zone: 480 pages used for memmap
  Normal zone: 60960 pages, LIFO batch:15
DMI 2.1 present.
ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f6ac0
ACPI: RSDT (v001 PTLTD    RSDT   0x00000000 PTL  0x01000000) @ 0x040fda87
ACPI: FADT (v001 GATEWA TABOR II 0x19991217 PTL  0x000f4240) @ 0x040ff78c
ACPI: DSDT (v001 GATEWA TABOR II 0x00000000 MSFT 0x01000004) @ 0x00000000
ACPI: BIOS age (1999) fails cutoff (2000), acpi=force is required to enable ACPI
ACPI: Disabling ACPI support
Allocating PCI resources starting at 20000000 (gap: 10000000:effe7000)
Detected 497.485 MHz processor.
Built 1 zonelists.  Total pages: 65024
Kernel command line: root=/dev/hda1 ro quiet splash
Local APIC disabled by BIOS -- you can enable it with "lapic"
mapped APIC to ffffd000 (01201000)
Enabling fast FPU save and restore... done.
Enabling unmasked SIMD FPU exception support... done.
Initializing CPU#0
PID hash table entries: 1024 (order: 10, 4096 bytes)
Console: colour VGA+ 80x25
Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
Memory: 252760k/262144k available (1908k kernel code, 8764k reserved, 599k data, 304k init, 0k highmem)
virtual kernel memory layout:
    fixmap  : 0xfffb7000 - 0xfffff000   ( 288 kB)
    vmalloc : 0xd0800000 - 0xfffb5000   ( 759 MB)
    lowmem  : 0xc0000000 - 0xd0000000   ( 256 MB)
      .init : 0xc0376000 - 0xc03c2000   ( 304 kB)
      .data : 0xc02dd246 - 0xc037300c   ( 599 kB)
      .text : 0xc0100000 - 0xc02dd246   (1908 kB)
Checking if this processor honours the WP bit even in supervisor mode... Ok.
Calibrating delay using timer specific routine.. 995.70 BogoMIPS (lpj=1991406)
Mount-cache hash table entries: 512
CPU: After generic identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
CPU: L1 I cache: 16K, L1 D cache: 16K
CPU: L2 cache: 512K
CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000
CPU: Intel Pentium III (Katmai) stepping 02
Checking 'hlt' instruction... OK.
checking if image is initramfs... it is
Freeing initrd memory: 3389k freed
NET: Registered protocol family 16
EISA bus registered
PCI: PCI BIOS revision 2.10 entry at 0xfd983, last bus=1
PCI: Using configuration type 1
Setting up standard PCI resources
ACPI: Interpreter disabled.
Linux Plug and Play Support v0.97 (c) Adam Belay
pnp: PnP ACPI: disabled
PnPBIOS: Scanning system for PnP BIOS support...
PnPBIOS: Found PnP BIOS installation structure at 0xc00f6ae0
PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0x9e33, dseg 0x400
PnPBIOS: 15 nodes reported by PnP BIOS; 15 recorded by driver
PCI: Probing PCI hardware
PCI: Probing PCI hardware (bus 00)
* Found PM-Timer Bug on the chipset. Due to workarounds for a bug,
* this clock source is slow. Consider trying other clock sources
PCI quirk: region 8000-803f claimed by PIIX4 ACPI
PCI quirk: region 7000-700f claimed by PIIX4 SMB
Boot video device is 0000:01:00.0
PCI: Using IRQ router PIIX/ICH [8086/7110] at 0000:00:07.0
pnp: 00:00: ioport range 0x370-0x371 has been reserved
pnp: 00:0a: ioport range 0x4d0-0x4d1 has been reserved
pnp: 00:0a: ioport range 0x8000-0x803f has been reserved
pnp: 00:0a: ioport range 0x7000-0x700f has been reserved
PCI: Bridge: 0000:00:01.0
  IO window: disabled.
  MEM window: f1000000-f1ffffff
  PREFETCH window: f8000000-fc0fffff
NET: Registered protocol family 2
IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
TCP established hash table entries: 8192 (order: 3, 32768 bytes)
TCP bind hash table entries: 4096 (order: 2, 16384 bytes)
TCP: Hash tables configured (established 8192 bind 4096)
TCP reno registered
audit: initializing netlink socket (disabled)
audit(1172152702.576:1): initialized
VFS: Disk quotas dquot_6.5.1
Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Installing knfsd (copyright (C) 1996 [email]okir@monad.swb.de[/email]).
io scheduler noop registered
io scheduler cfq registered (default)
Limiting direct PCI/PCI transfers.
isapnp: Scanning for PnP cards...
isapnp: No Plug & Play device found
Real Time Clock Driver v1.12ac
Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
00:0e: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
serio: i8042 KBD port at 0x60,0x64 irq 1
serio: i8042 AUX port at 0x60,0x64 irq 12
mice: PS/2 mouse device common for all mice
EISA: Probing bus 0 at eisa.0
Cannot allocate resource for EISA slot 1
Cannot allocate resource for EISA slot 7
Cannot allocate resource for EISA slot 8
EISA: Detected 0 cards.
TCP cubic registered
NET: Registered protocol family 1
NET: Registered protocol family 8
NET: Registered protocol family 20
Using IPI Shortcut mode
Freeing unused kernel memory: 304k freed
Time: tsc clocksource has been installed.
input: AT Translated Set 2 keyboard as /class/input/input0
PIIX4: IDE controller at PCI slot 0000:00:07.1
PIIX4: chipset revision 1
PIIX4: not 100% native mode: will probe irqs later
    ide0: BM-DMA at 0x1000-0x1007, BIOS settings: hda:DMA, hdb:pio
    ide1: BM-DMA at 0x1008-0x100f, BIOS settings: hdc:DMA, hdd:pio
Probing IDE interface ide0...
hda: IBM-DPTA-371020, ATA DISK drive
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Probing IDE interface ide1...
hdc: PLEXTOR CD-R PX-W4012A, ATAPI CD/DVD-ROM drive
ide1 at 0x170-0x177,0x376 on irq 15
hda: max request size: 128KiB
hda: 20028960 sectors (10254 MB) w/1961KiB Cache, CHS=19870/16/63, UDMA(33)
hda: cache flushes not supported
 hda: hda1 hda2 < hda5 >
hdc: ATAPI 40X CD-ROM CD-R/RW drive, 4096kB Cache, UDMA(33)
Uniform CD-ROM driver Revision: 3.20
usbcore: registered new interface driver usbfs
usbcore: registered new interface driver hub
usbcore: registered new device driver usb
USB Universal Host Controller Interface driver v3.0
PCI: setting IRQ 9 as level-triggered
PCI: Found IRQ 9 for device 0000:00:07.2
PCI: Sharing IRQ 9 with 0000:00:10.0
uhci_hcd 0000:00:07.2: UHCI Host Controller
uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
uhci_hcd 0000:00:07.2: irq 9, io base 0x00001020
usb usb1: configuration #1 chosen from 1 choice
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 2 ports detected
Attempting manual resume
kjournald starting.  Commit interval 5 seconds
EXT3-fs: mounted filesystem with ordered data mode.
PCI: Enabling device 0000:00:11.0 (0114 -> 0117)
PCI: setting IRQ 10 as level-triggered
PCI: Found IRQ 10 for device 0000:00:11.0
3c59x: Donald Becker and others. [www.scyld.com/network/vortex.html](www.scyld.com/network/vortex.html)
0000:00:11.0: 3Com PCI 3c905B Cyclone 100baseTx at d082c000.
natsemi dp8381x driver, version 2.1, Sept 11, 2006
  originally by Donald Becker <becker@scyld.com>
  [http://www.scyld.com/network/natsemi.html](http://www.scyld.com/network/natsemi.html)
  2.4.x kernel port by Jeff Garzik, Tjeerd Mulder
PCI: Enabling device 0000:00:10.0 (0104 -> 0107)
PCI: Found IRQ 9 for device 0000:00:10.0
PCI: Sharing IRQ 9 with 0000:00:07.2
natsemi eth1: NatSemi DP8381[56] at 0xf0000000 (0000:00:10.0), 00:02:e3:02:e8:a5, IRQ 9, port TP.
Linux agpgart interface v0.101 (c) Dave Jones
agpgart: Detected an Intel 440BX Chipset.
agpgart: AGP aperture is 64M @ 0xf4000000
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
PCI: Enabling device 0000:00:0e.1 (0104 -> 0105)
gameport: EMU10K1 is pci0000:00:0e.1/gameport0, io 0x1010, speed 1193kHz
input: PC Speaker as /class/input/input1
piix4_smbus 0000:00:07.3: Found 0000:00:07.3 device
parport: PnPBIOS parport detected.
parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
input: ImPS/2 Generic Wheel Mouse as /class/input/input2
eth0: DSPCFG accepted after 0 usec.
eth2:  setting half-duplex.
Adding 441748k swap on /dev/disk/by-uuid/e3c8dddf-6de4-4b18-8980-d08e63ec6ebc.  Priority:-1 extents:1 across:441748k
EXT3 FS on hda1, internal journal
NET: Registered protocol family 17
NET: Registered protocol family 10
lo: Disabled Privacy Extensions
ADDRCONF(NETDEV_UP): eth0: link is not ready
eth2: no IPv6 routers present
apm: BIOS not found.
NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
NFSD: starting 90-second grace period
eth0: Autonegotiation advertising 0x5e1  partner 0x45e1.
eth0: link up.
eth0: Setting full-duplex based on negotiated link capability.
eth0: Link wake-up event 0x40020b
ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
eth0: no IPv6 routers present


---

### Post by crmanski on 2007-02-22
That is really odd. When I put a USB storage device into my machine I get something like this...
```
[18027096.712000] usb 5-8: new high speed USB device using ehci_hcd and address 4
[18027096.848000] usb 5-8: configuration #1 chosen from 2 choices
[18027097.260000] usbcore: registered new driver libusual
[18027097.272000] Initializing USB Mass Storage driver...
[18027097.272000] scsi2 : SCSI emulation for USB Mass Storage devices
[18027097.272000] usbcore: registered new driver usb-storage
[18027097.272000] USB Mass Storage support registered.
[18027097.272000] usb-storage: device found at 4
[18027097.272000] usb-storage: waiting for device to settle before scanning
[18027102.272000] usb-storage: device scan complete
[18027102.272000]   Vendor: Apple     Model: iPod              Rev: 1.62
[18027102.272000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[18027102.276000] SCSI device sdb: 1999871 512-byte hdwr sectors (1024 MB)
[18027102.276000] sdb: Write Protect is off
[18027102.276000] sdb: Mode Sense: 68 00 00 08
[18027102.276000] sdb: assuming drive cache: write through
[18027102.280000] SCSI device sdb: 1999871 512-byte hdwr sectors (1024 MB)
[18027102.280000] sdb: Write Protect is off
[18027102.280000] sdb: Mode Sense: 68 00 00 08
[18027102.280000] sdb: assuming drive cache: write through
[18027102.280000]  sdb: sdb1 sdb2
[18027102.284000] sd 2:0:0:0: Attached scsi removable disk sdb
[18027102.284000] sd 2:0:0:0: Attached scsi generic sg1 type 0

```

Since you do not have any mention in dmesg when you put a USB device in I think that the USB port is either bad, the USB device is incompatible (2.0 device->1.0 port). Have you tried other devices (Printer maybe) and do these work?

---

### Post by namelessone on 2007-02-22
Oh. I'm sorry. I didn't know you wanted me to have a usb stick in my drive when i typed dmesg. It should be noted that I have used this same usb stick on this same computer with this same operating system and it worked...it only stopped working after I did the ltsp-build-client thingy.

I'll get back to you with a new dmesg output...I'm away from that computer right now.

---

### Post by namelessone on 2007-02-28
Hey! I figured it out!

I forgot to mention that I custom compiled a new kernel for my computer...and somehow I custom compiled it without the usb-storage module. I booted with the old generic kernel and the usb drive worked fine.

Is it possible to get this module into my custom kernel now, or is it too late?

---

