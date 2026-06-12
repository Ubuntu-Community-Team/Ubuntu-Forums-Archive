---
title: "Edgy and Dapper freeze a few minutes after booting"
date: 2006-10-28
forum: General Help
---

### Post by adamzap on 2006-10-28
I posted this same problem when Dapper was released and no one could help me, so let's try again.

Literally 4 or 5 minutes, maybe less maybe more, after booting, it just locks up. My sound get stuck in a short loop, and my video it totally frozen. I cannot kill X or switch to a console (one time I could, but that could have been a different problem.) Also, this even happens on the live cd, I had to try several times to get through the installation. The amount of time before it freezes seems quite random. It also happens if I boot into Ubuntu and go straight to a console on ctrl+alt+F1.

This does not happen on opensuse, knoppix, slackware, winblows etc. Therefore, I do no think it is a hardware issue, unless Ubuntu is telling my hardware to commit suicide on boot or something.

Hardware:
Pentium 4 2.8Ghz (Northwood)
1gb OCZ PC3200 RAM
Radeon 9500 Pro Video Card
ASUS P4P800 Deluxe Motherboard

I tried the few fixes I found on these forums, but none worked.

It's pretty difficult to write free software on Ubuntu when it freezes after 5 minutes :-|

Thanks in advance

---

### Post by tronica on 2006-10-28
if you do ctrl+alt+F1 and let it sit there does it freeze then.

---

### Post by Peter Sommer-Larsen on 2006-10-28
What if you shutdown X ? Does it then freeze ?

---

### Post by galileon on 2006-10-28
try to squeeze out some info for us just after the boot,

eg: lspci, lsusb, dmesg, etc... also try to hunt a bit thru /var/logs/ they may have some interesting stuff.....try to boot in single user mode, ie "recovery mode" or safe mode or whatver-its-called in grub, and see if it hangs in the same way...

---

### Post by adamzap on 2006-10-28
Here's a few things that were asked for, I appreciate the help.

This is a fresh install, so I haven't cleaned out my init scrips yet (bluetooth, etc.)

There was nothing obvious in my logs, but im no expert

I have to pass ide=nodma to the live cd, just thought I'd throw that out there.

Also, it did not freeze in recovery mode, even after i started X! Interesting!

lsusb
```

Bus 001 Device 004: ID 046d:c501 Logitech, Inc. Cordless Mouse Receiver
Bus 001 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  

```

lspci
```

00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R300 NE [Radeon 9500 Pro]
01:00.1 Display controller: ATI Technologies Inc Radeon R300 [Radeon 9500 Pro] (Secondary)
02:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46)
02:04.0 RAID bus controller: VIA Technologies, Inc. VT6410 ATA133 RAID controller (rev 06)
02:05.0 Ethernet controller: 3Com Corporation 3c940 10/100/1000Base-T [Marvell] (rev 12)
02:0c.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 08)
02:0c.1 Input device controller: Creative Labs SB Live! MIDI/Game Port (rev 08)

```

dmesg
```

[17179569.184000] Linux version 2.6.17-10-generic (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct 13 18:45:35 UTC 2006 (Ubuntu 2.6.17-10.33-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000e8000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000003ff30000 (usable)
[17179569.184000]  BIOS-e820: 000000003ff30000 - 000000003ff40000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000003ff40000 - 000000003fff0000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000003fff0000 - 0000000040000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ffb80000 - 0000000100000000 (reserved)
[17179569.184000] 127MB HIGHMEM available.
[17179569.184000] 896MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000ff780
[17179569.184000] On node 0 totalpages: 261936
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 225280 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 32560 pages, LIFO batch:7
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 ACPIAM                                ) @ 0x000f9e30
[17179569.184000] ACPI: RSDT (v001 A M I  OEMRSDT  0x01000428 MSFT 0x00000097) @ 0x3ff30000
[17179569.184000] ACPI: FADT (v002 A M I  OEMFACP  0x01000428 MSFT 0x00000097) @ 0x3ff30200
[17179569.184000] ACPI: MADT (v001 A M I  OEMAPIC  0x01000428 MSFT 0x00000097) @ 0x3ff30390
[17179569.184000] ACPI: OEMB (v001 A M I  OEMBIOS  0x01000428 MSFT 0x00000097) @ 0x3ff40040
[17179569.184000] ACPI: DSDT (v001  P4P81 P4P81094 0x00000094 INTL 0x02002026) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x808
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 15:2 APIC version 20
[17179569.184000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[17179569.184000] Processor #1 15:2 APIC version 20
[17179569.184000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 50000000 (gap: 40000000:bfb80000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda6 ro quiet splash ide=nodma
[17179569.184000] ide_setup: ide=nodma : Prevented DMA
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[17179569.184000] Detected 2798.974 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179571.056000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179571.056000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179571.080000] Memory: 1029008k/1047744k available (1910k kernel code, 18060k reserved, 1070k data, 308k init, 130240k highmem)
[17179571.080000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179571.160000] Calibrating delay using timer specific routine.. 5603.25 BogoMIPS (lpj=11206507)
[17179571.160000] Security Framework v1.0.0 initialized
[17179571.160000] SELinux:  Disabled at boot.
[17179571.160000] Mount-cache hash table entries: 512
[17179571.160000] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
[17179571.160000] CPU: After vendor identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
[17179571.160000] CPU: Trace cache: 12K uops, L1 D cache: 8K
[17179571.160000] CPU: L2 cache: 512K
[17179571.160000] CPU: Hyper-Threading is disabled
[17179571.160000] CPU: After all inits, caps: bfebfbff 00000000 00000000 00000080 00004400 00000000 00000000
[17179571.160000] Checking 'hlt' instruction... OK.
[17179571.176000] SMP alternatives: switching to UP code
[17179571.176000] checking if image is initramfs... it is
[17179571.600000] Freeing initrd memory: 5254k freed
[17179571.600000] ACPI: Core revision 20060707
[17179571.600000] ACPI: Looking for DSDT ... not found!
[17179572.016000] CPU0: Intel(R) Pentium(R) 4 CPU 2.80GHz stepping 05
[17179572.016000] SMP alternatives: switching to SMP code
[17179572.016000] Booting processor 1/1 eip 3000
[17179572.028000] Initializing CPU#1
[17179572.108000] Calibrating delay using timer specific routine.. 5597.67 BogoMIPS (lpj=11195353)
[17179572.108000] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
[17179572.108000] CPU: After vendor identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
[17179572.108000] CPU: Trace cache: 12K uops, L1 D cache: 8K
[17179572.108000] CPU: L2 cache: 512K
[17179572.108000] CPU: Hyper-Threading is disabled
[17179572.108000] CPU: After all inits, caps: bfebfbff 00000000 00000000 00000080 00004400 00000000 00000000
[17179572.108000] CPU1: Intel(R) Pentium(R) 4 CPU 2.80GHz stepping 05
[17179572.108000] Total of 2 processors activated (11200.93 BogoMIPS).
[17179572.108000] ENABLING IO-APIC IRQs
[17179572.108000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179572.252000] checking TSC synchronization across 2 CPUs: passed.
[17179572.256000] Brought up 2 CPUs
[17179572.336000] migration_cost=4000
[17179572.336000] NET: Registered protocol family 16
[17179572.336000] EISA bus registered
[17179572.336000] ACPI: bus type pci registered
[17179572.336000] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=2
[17179572.336000] PCI: Using configuration type 1
[17179572.336000] Setting up standard PCI resources
[17179572.348000] ACPI: Interpreter enabled
[17179572.348000] ACPI: Using IOAPIC for interrupt routing
[17179572.348000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179572.348000] PCI: Probing PCI hardware (bus 00)
[17179572.352000] PCI quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
[17179572.352000] PCI quirk: region 0480-04bf claimed by ICH4 GPIO
[17179572.352000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[17179572.352000] Boot video device is 0000:01:00.0
[17179572.352000] PCI: Transparent bridge - 0000:00:1e.0
[17179572.352000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179572.360000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[17179572.368000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[17179572.368000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[17179572.368000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[17179572.368000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[17179572.368000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[17179572.368000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179572.368000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[17179572.368000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[17179572.368000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179572.368000] pnp: PnP ACPI init
[17179572.372000] pnp: PnP ACPI: found 14 devices
[17179572.372000] ASUS P4P800 detected. Disabling PnPBIOS
[17179572.372000] PnPBIOS: Disabled
[17179572.372000] PCI: Using ACPI for IRQ routing
[17179572.372000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179572.380000] pnp: 00:0a: ioport range 0x680-0x6ff has been reserved
[17179572.380000] pnp: 00:0a: ioport range 0x290-0x297 has been reserved
[17179572.380000] PCI: Bridge: 0000:00:01.0
[17179572.380000]   IO window: c000-cfff
[17179572.380000]   MEM window: fe900000-fe9fffff
[17179572.380000]   PREFETCH window: d7f00000-f7efffff
[17179572.380000] PCI: Bridge: 0000:00:1e.0
[17179572.380000]   IO window: d000-dfff
[17179572.380000]   MEM window: fea00000-feafffff
[17179572.380000]   PREFETCH window: disabled.
[17179572.380000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179572.380000] NET: Registered protocol family 2
[17179572.416000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179572.416000] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[17179572.416000] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[17179572.416000] TCP: Hash tables configured (established 131072 bind 65536)
[17179572.416000] TCP reno registered
[17179572.416000] audit: initializing netlink socket (disabled)
[17179572.416000] audit(1162044778.416:1): initialized
[17179572.416000] highmem bounce pool size: 64 pages
[17179572.416000] VFS: Disk quotas dquot_6.5.1
[17179572.416000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179572.416000] Initializing Cryptographic API
[17179572.416000] io scheduler noop registered
[17179572.416000] io scheduler anticipatory registered
[17179572.416000] io scheduler deadline registered
[17179572.416000] io scheduler cfq registered (default)
[17179572.416000] isapnp: Scanning for PnP cards...
[17179572.772000] isapnp: No Plug & Play device found
[17179572.796000] Real Time Clock Driver v1.12ac
[17179572.796000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179572.796000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179572.796000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179572.796000] 00:06: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179572.796000] 00:07: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179572.796000] mice: PS/2 mouse device common for all mice
[17179572.796000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179572.796000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179572.796000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179572.796000] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[17179572.796000] PNP: PS/2 controller doesn't have AUX irq; using default 12
[17179572.800000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179572.800000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179572.800000] EISA: Probing bus 0 at eisa.0
[17179572.800000] EISA: Detected 0 cards.
[17179572.800000] TCP bic registered
[17179572.800000] NET: Registered protocol family 1
[17179572.800000] NET: Registered protocol family 8
[17179572.800000] NET: Registered protocol family 20
[17179572.800000] Starting balanced_irq
[17179572.800000] Using IPI No-Shortcut mode
[17179572.800000] ACPI: (supports S0 S1 S3 S4 S5)
[17179572.800000] Freeing unused kernel memory: 308k freed
[17179573.068000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179573.904000] Capability LSM initialized
[17179574.692000] ICH5: IDE controller at PCI slot 0000:00:1f.1
[17179574.692000] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[17179574.692000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 169
[17179574.692000] ICH5: chipset revision 2
[17179574.692000] ICH5: not 100% native mode: will probe irqs later
[17179574.692000]     ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:DMA, hdb:DMA
[17179574.692000]     ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: hdc:DMA, hdd:pio
[17179574.692000] Probing IDE interface ide0...
[17179574.988000] hda: ST320413A, ATA DISK drive
[17179575.272000] hdb: WDC WD800BB-00CAA1, ATA DISK drive
[17179575.332000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179575.352000] Probing IDE interface ide1...
[17179576.092000] hdc: TSSTcorpCD/DVDW SH-S162L, ATAPI CD/DVD-ROM drive
[17179576.764000] ide1 at 0x170-0x177,0x376 on irq 15
[17179576.792000] hda: max request size: 128KiB
[17179576.792000] hda: 39102336 sectors (20020 MB) w/512KiB Cache, CHS=38792/16/63
[17179576.792000] hda: cache flushes not supported
[17179576.792000]  hda: hda1 hda2 < hda5 hda6 >
[17179576.856000] hdb: max request size: 128KiB
[17179576.856000] hdb: 156301488 sectors (80026 MB) w/2048KiB Cache, CHS=65535/16/63
[17179576.856000] hdb: cache flushes not supported
[17179576.856000]  hdb: hdb1
[17179576.876000] hdc: ATAPI 63X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache
[17179576.876000] Uniform CD-ROM driver Revision: 3.20
[17179577.608000] VP_IDE: IDE controller at PCI slot 0000:02:04.0
[17179577.608000] ACPI: PCI Interrupt 0000:02:04.0[A] -> GSI 23 (level, low) -> IRQ 177
[17179577.608000] PCI: Via IRQ fixup for 0000:02:04.0, from 11 to 1
[17179577.608000] VP_IDE: chipset revision 6
[17179577.608000] VP_IDE: VIA vt6410 (rev 06) IDE UDMA133 controller on pci0000:02:04.0
[17179577.608000] VP_IDE: 100% native mode on irq 177
[17179577.608000]     ide2: BM-DMA at 0xdf80-0xdf87, BIOS settings: hde:pio, hdf:pio
[17179577.608000]     ide3: BM-DMA at 0xdf88-0xdf8f, BIOS settings: hdg:pio, hdh:pio
[17179577.608000] Probing IDE interface ide2...
[17179578.176000] Probing IDE interface ide3...
[17179578.804000] usbcore: registered new driver usbfs
[17179578.804000] usbcore: registered new driver hub
[17179578.812000] USB Universal Host Controller Interface driver v3.0
[17179578.812000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 185
[17179578.812000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17179578.812000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[17179578.812000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[17179578.812000] uhci_hcd 0000:00:1d.0: irq 185, io base 0x0000ef00
[17179578.816000] usb usb1: configuration #1 chosen from 1 choice
[17179578.816000] hub 1-0:1.0: USB hub found
[17179578.816000] hub 1-0:1.0: 2 ports detected
[17179578.860000] Probing IDE interface ide2...
[17179578.880000] ieee1394: Initialized config rom entry `ip1394'
[17179578.924000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 193
[17179578.924000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[17179578.924000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[17179578.924000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[17179578.924000] uhci_hcd 0000:00:1d.1: irq 193, io base 0x0000ef20
[17179578.924000] usb usb2: configuration #1 chosen from 1 choice
[17179578.924000] hub 2-0:1.0: USB hub found
[17179578.924000] hub 2-0:1.0: 2 ports detected
[17179579.032000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 169
[17179579.032000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[17179579.032000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[17179579.032000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[17179579.032000] uhci_hcd 0000:00:1d.2: irq 169, io base 0x0000ef40
[17179579.032000] usb usb3: configuration #1 chosen from 1 choice
[17179579.032000] hub 3-0:1.0: USB hub found
[17179579.032000] hub 3-0:1.0: 2 ports detected
[17179579.140000] ACPI: PCI Interrupt 0000:00:1d.3[A] -> GSI 16 (level, low) -> IRQ 185
[17179579.140000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[17179579.140000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[17179579.140000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[17179579.140000] uhci_hcd 0000:00:1d.3: irq 185, io base 0x0000ef80
[17179579.140000] usb usb4: configuration #1 chosen from 1 choice
[17179579.140000] hub 4-0:1.0: USB hub found
[17179579.140000] hub 4-0:1.0: 2 ports detected
[17179579.164000] usb 1-2: new low speed USB device using uhci_hcd and address 2
[17179579.248000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 177
[17179579.248000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[17179579.248000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[17179579.248000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[17179579.248000] ehci_hcd 0000:00:1d.7: debug port 1
[17179579.248000] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[17179579.248000] ehci_hcd 0000:00:1d.7: irq 177, io mem 0xfebffc00
[17179579.252000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179579.252000] usb usb5: configuration #1 chosen from 1 choice
[17179579.252000] hub 5-0:1.0: USB hub found
[17179579.252000] hub 5-0:1.0: 8 ports detected
[17179579.360000] ACPI: PCI Interrupt 0000:02:03.0[A] -> GSI 20 (level, low) -> IRQ 201
[17179579.360000] PCI: Via IRQ fixup for 0000:02:03.0, from 10 to 9
[17179579.412000] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[201]  MMIO=[feaff800-feafffff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[17179579.428000] BUG: warning at kernel/irq/manage.c:126/enable_irq()
[17179579.428000]  <c014993a> enable_irq+0x9a/0xe0  <c02563e9> probe_hwif+0x639/0x820
[17179579.428000]  <c0256f80> ideprobe_init+0x70/0x150  <c011bde0> default_wake_function+0x0/0x10
[17179579.428000]  <f8863005> ide_generic_init+0x5/0xd [ide_generic]  <c013cda8> sys_init_module+0x148/0x19c0
[17179579.428000]  <c0256f10> ideprobe_init+0x0/0x150  <c0103027> syscall_call+0x7/0xb
[17179579.432000] Probing IDE interface ide3...
[17179579.700000] usb 1-2: device not accepting address 2, error -71
[17179580.000000] Probing IDE interface ide4...
[17179580.180000] usb 1-2: new low speed USB device using uhci_hcd and address 4
[17179580.364000] usb 1-2: configuration #1 chosen from 1 choice
[17179580.376000] usbcore: registered new driver hiddev
[17179580.396000] input: Logitech USB Receiver as /class/input/input1
[17179580.396000] input: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.0-2
[17179580.396000] usbcore: registered new driver usbhid
[17179580.396000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179580.564000] Probing IDE interface ide5...
[17179580.696000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00e018000028c4ff]
[17179581.176000] Attempting manual resume
[17179581.212000] EXT3-fs: INFO: recovery required on readonly filesystem.
[17179581.212000] EXT3-fs: write access will be enabled during recovery.
[17179585.620000] kjournald starting.  Commit interval 5 seconds
[17179585.620000] EXT3-fs: recovery complete.
[17179585.652000] EXT3-fs: mounted filesystem with ordered data mode.
[17179612.776000] Linux agpgart interface v0.101 (c) Dave Jones
[17179612.788000] agpgart: Detected an Intel 865 Chipset.
[17179612.792000] agpgart: AGP aperture is 64M @ 0xf8000000
[17179612.828000] Floppy drive(s): fd0 is 1.44M
[17179612.852000] FDC 0 is a post-1991 82077
[17179613.316000] parport: PnPBIOS parport detected.
[17179613.316000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[17179613.412000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179613.440000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179613.472000] input: PC Speaker as /class/input/input2
[17179613.596000] hw_random hardware driver 1.0.0 loaded
[17179613.700000] ts: Compaq touchscreen protocol output
[17179613.796000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 209
[17179613.796000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[17179614.224000] intel8x0_measure_ac97_clock: measured 59214 usecs
[17179614.224000] intel8x0: clocking to 48000
[17179614.244000] gameport: EMU10K1 is pci0000:02:0c.1/gameport0, io 0xdfe0, speed 1084kHz
[17179614.244000] ACPI: PCI Interrupt 0000:02:05.0[A] -> GSI 22 (level, low) -> IRQ 217
[17179614.244000] skge 1.5 addr 0xfeaf8000 irq 217 chip Yukon rev 1
[17179614.244000] skge eth0: addr 00:0e:a6:2f:29:9c
[17179614.256000] ACPI: PCI Interrupt 0000:02:0c.0[A] -> GSI 20 (level, low) -> IRQ 201
[17179614.364000] skge eth0: enabling interface
[17179614.676000] lp0: using parport0 (interrupt-driven).
[17179614.776000] SCSI subsystem initialized
[17179614.796000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[17179614.796000] ieee1394: sbp2: Try serialize_io=0 for better performance
[17179614.844000] Adding 1020088k swap on /dev/disk/by-uuid/a676e82b-30f2-48d9-a25b-10223490ad6c.  Priority:-1 extents:1 across:1020088k
[17179615.024000] EXT3 FS on hda6, internal journal
[17179615.460000] NET: Registered protocol family 17
[17179616.056000] skge eth0: Link is up at 100 Mbps, full duplex, flow control tx and rx
[17179630.700000] ReiserFS: hdb1: found reiserfs format "3.6" with standard journal
[17179635.248000] ReiserFS: hdb1: using ordered data mode
[17179635.268000] ReiserFS: hdb1: journal params: device hdb1, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[17179635.272000] ReiserFS: hdb1: checking transaction log (hdb1)
[17179635.316000] ReiserFS: hdb1: Using r5 hash to sort names
[17179640.992000] ACPI: Power Button (FF) [PWRF]
[17179640.992000] ACPI: Power Button (CM) [PWRB]
[17179641.184000] ibm_acpi: ec object not found
[17179641.236000] pcc_acpi: loading...
[17179643.936000] [drm] Initialized drm 1.0.1 20051102
[17179643.984000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 185
[17179643.984000] [drm] Initialized radeon 1.25.0 20060524 on minor 0
[17179644.580000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179644.580000] apm: disabled - APM is not SMP safe.
[17179645.380000] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[17179645.380000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 4x mode
[17179645.380000] agpgart: Putting AGP V3 device at 0000:01:00.0 into 4x mode
[17179645.760000] [drm] Setting GART location based on new memory map
[17179645.760000] [drm] Loading R300 Microcode
[17179645.760000] [drm] writeback test succeeded in 1 usecs
[17179649.852000] Bluetooth: Core ver 2.8
[17179649.852000] NET: Registered protocol family 31
[17179649.852000] Bluetooth: HCI device and connection manager initialized
[17179649.852000] Bluetooth: HCI socket layer initialized
[17179649.876000] Bluetooth: L2CAP ver 2.8
[17179649.876000] Bluetooth: L2CAP socket layer initialized
[17179649.904000] Bluetooth: RFCOMM socket layer initialized
[17179649.904000] Bluetooth: RFCOMM TTY layer initialized
[17179649.904000] Bluetooth: RFCOMM ver 1.7
[17179661.500000] NET: Registered protocol family 10
[17179661.500000] lo: Disabled Privacy Extensions
[17179661.500000] IPv6 over IPv4 tunneling driver
[17179668.440000] ISO 9660 Extensions: Microsoft Joliet Level 3
[17179668.924000] ISOFS: changing to secondary root
[17179672.004000] eth0: no IPv6 routers present

```

---

### Post by adamzap on 2006-10-30
well, thanks guys

I guess I'll wait and try the next major release

---

### Post by galileon on 2006-10-30
given your single user mode works, you could now try this:

boot up normally, press ctrl-alt-f1 to get a console, login there, then issue this command:

sudo /etc/init.d/gdm stop

this will shut down x-server, and leave it for some time, and see if it still locks up...

---

### Post by jadt on 2006-10-30
Hi guys,

I've just recently installed Ubuntu 6.10 and it appears to behave the same, a couple of mins after start-up it just freezes everything (the cursor, the time, ctrl+alt+f1 doesn't even work)...

Well the little time I could spend on Ubuntu, it really looks great! On one of my other PC's it works without freezing, so it has to be something with the HW...

Thanks

P.S. if any ubuntu expert wants me to post logs, please let me know...

---

### Post by galileon on 2006-10-30
hello, im far from being expert, but your logs would be interesting, we might find something...

lspci, lsusb, dmesg, cat /var/log/syslog, etc...

---

### Post by cwalk on 2006-10-31
I am experiencing the same thing. Exactly as adamzap described. I think it might have something to do with the video card. I have a 9550se and it has never worked quit right with Ubuntu. I did a fresh i386 install of Edgy. I have an AMD64 3200+. The thing is, i never installed any 'extra' video drivers and i tested the 3d accel. on a few games and it works great. Just freezes up sometimes. Then repeatedly shuts down when you try to reboot. I think the poor thing is overheating? When i let the computer sit off for a while then turn it back on it will usually last at least a few hours. Any ideas?

---

### Post by David Corrales on 2006-10-31
> **cwalk said:**
> I am experiencing the same thing. Exactly as adamzap described. I think it might have something to do with the video card. I have a 9550se and it has never worked quit right with Ubuntu. I did a fresh i386 install of Edgy. I have an AMD64 3200+. The thing is, i never installed any 'extra' video drivers and i tested the 3d accel. on a few games and it works great. Just freezes up sometimes. Then repeatedly shuts down when you try to reboot. I think the poor thing is overheating? When i let the computer sit off for a while then turn it back on it will usually last at least a few hours. Any ideas?

It does sound a lot like overheating. Check the fans. Add some if possible or buy a replacement (something like a cheap Nvidia).

---

### Post by David Corrales on 2006-10-31
> **adamzap said:**
> I posted this same problem when Dapper was released and no one could help me, so let's try again.

Literally 4 or 5 minutes, maybe less maybe more, after booting, it just locks up. My sound get stuck in a short loop, and my video it totally frozen. I cannot kill X or switch to a console (one time I could, but that could have been a different problem.) Also, this even happens on the live cd, I had to try several times to get through the installation. The amount of time before it freezes seems quite random. It also happens if I boot into Ubuntu and go straight to a console on ctrl+alt+F1.

This does not happen on opensuse, knoppix, slackware, winblows etc. Therefore, I do no think it is a hardware issue, unless Ubuntu is telling my hardware to commit suicide on boot or something.

Hardware:
Pentium 4 2.8Ghz (Northwood)
1gb OCZ PC3200 RAM
Radeon 9500 Pro Video Card
ASUS P4P800 Deluxe Motherboard

I tried the few fixes I found on these forums, but none worked.

It's pretty difficult to write free software on Ubuntu when it freezes after 5 minutes :-|

Thanks in advance

Long ago, when I used Mandrake (yuck KDE now lol) I had to pass the following cheat codes when booting up or I'd get random lockups:
**noapic nolapic**
Try and see if those help you out. If those don't work, maybe your HD doesn't like having DMA enabled so just add that cheat code to the kernel boot line and use it for a few days. If you don't any lockups, it'll be time to file a bug.

---

### Post by adamzap on 2006-11-01
Thanks guys...

I'm glad to hear someone else is having this problem!

It doesnt freeze when X isnt running. (I did the gdm stop thing)

Could it really be overheating when it works fine in other distros and winblows?

I'll do more testing tomorrow...hopefully we can get to the bottom of this, cwalk

(I have a vid card i could use, but i dual boot, and it would suck to have to switch vid cards every time i go into winblows)

thanks guys

---

### Post by adamzap on 2006-11-02
I installed the ATI drivers from their site, and I also took out a lot of unneeded startup script.

It didn't freeze all day yesterday.

I did the exact same thing for dapper, and it didn't help, so I'm guessing the ATI drivers fixed our bug, but I still have to do a lot more testing.

Will someone else who is having this problem try this?

I'll give the exact details of how I did all this soon, (I'm at work).

---

### Post by cwalk on 2006-11-02
Count me in adam. I would love to get this card working. I dusted it a little(fan wasnt really very dirty) and installed an additional fan but I am still having the freezes, which means that my overheating hypothesis is probably wrong. I checked out the ati site and there were a few things in the instructions i did not know how to do. Mainly, how to uninstall my previous drivers first, and how do i know if i have POSIX shared memory(my /dev/shm folder is empty). Also, I will post some lspci dmseg stuff if it will help.
-cheers

---

### Post by cwalk on 2006-11-02
dmesg:
```
[17179569.184000] Linux version 2.6.17-10-generic (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct 13 18:45:35 UTC 2006 (Ubuntu 2.6.17-10.33-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[17179569.184000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000003fef0000 (usable)
[17179569.184000]  BIOS-e820: 000000003fef0000 - 000000003fef3000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000003fef3000 - 000000003ff00000 (ACPI data)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[17179569.184000] 126MB HIGHMEM available.
[17179569.184000] 896MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000f5050
[17179569.184000] On node 0 totalpages: 261872
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 225280 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 32496 pages, LIFO batch:7
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 VIAK8M                                ) @ 0x000f9130
[17179569.184000] ACPI: RSDT (v001 VIAK8M AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x3fef3040
[17179569.184000] ACPI: FADT (v001 VIAK8M AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x3fef30c0
[17179569.184000] ACPI: MADT (v001 VIAK8M AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x3fef81c0
[17179569.184000] ACPI: DSDT (v001 VIAK8M AWRDACPI 0x00001000 MSFT 0x0100000e) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x4008
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 15:12 APIC version 16
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 40000000 (gap: 3ff00000:bed00000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda1 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[17179569.184000] Detected 2200.055 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179570.484000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179570.484000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179570.500000] Memory: 1028500k/1047488k available (1910k kernel code, 18336k reserved, 1070k data, 308k init, 129984k highmem)
[17179570.500000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179570.580000] Calibrating delay using timer specific routine.. 4405.98 BogoMIPS (lpj=8811965)
[17179570.580000] Security Framework v1.0.0 initialized
[17179570.580000] SELinux:  Disabled at boot.
[17179570.580000] Mount-cache hash table entries: 512
[17179570.580000] CPU: After generic identify, caps: 078bfbff e1d3fbff 00000000 00000000 00000000 00000000 00000000
[17179570.580000] CPU: After vendor identify, caps: 078bfbff e1d3fbff 00000000 00000000 00000000 00000000 00000000
[17179570.580000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[17179570.580000] CPU: L2 Cache: 512K (64 bytes/line)
[17179570.580000] CPU: After all inits, caps: 078bfbff e1d3fbff 00000000 00000410 00000000 00000000 00000000
[17179570.580000] Checking 'hlt' instruction... OK.
[17179570.596000] SMP alternatives: switching to UP code
[17179570.596000] Freeing SMP alternatives: 16k freed
[17179570.596000] checking if image is initramfs... it is
[17179571.020000] Freeing initrd memory: 5564k freed
[17179571.020000] ACPI: Core revision 20060707
[17179571.024000] ACPI: Looking for DSDT ... not found!
[17179571.044000] CPU0: AMD Athlon(tm) 64 Processor 3200+ stepping 00
[17179571.044000] Total of 1 processors activated (4405.98 BogoMIPS).
[17179571.044000] ENABLING IO-APIC IRQs
[17179571.044000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=0 pin2=0
[17179571.188000] Brought up 1 CPUs
[17179571.188000] migration_cost=0
[17179571.188000] NET: Registered protocol family 16
[17179571.188000] EISA bus registered
[17179571.188000] ACPI: bus type pci registered
[17179571.192000] PCI: PCI BIOS revision 2.10 entry at 0xfb7c0, last bus=1
[17179571.192000] PCI: Using configuration type 1
[17179571.192000] Setting up standard PCI resources
[17179571.200000] ACPI: Interpreter enabled
[17179571.200000] ACPI: Using IOAPIC for interrupt routing
[17179571.200000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179571.200000] PCI: Probing PCI hardware (bus 00)
[17179571.200000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:0f.1
[17179571.200000] PCI: Quirk-MSI-K8T Soundcard On
[17179571.200000] PCI: Unexpected Value in PCI-Register: no Change!
[17179571.204000] Boot video device is 0000:01:00.0
[17179571.204000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179571.244000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 *10 11 12)
[17179571.244000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 6 7 10 *11 12)
[17179571.244000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 11 12) *5
[17179571.244000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[17179571.244000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[17179571.244000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[17179571.244000] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[17179571.244000] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[17179571.244000] ACPI: PCI Interrupt Link [ALKA] (IRQs *20)
[17179571.244000] ACPI: PCI Interrupt Link [ALKB] (IRQs *21)
[17179571.248000] ACPI: PCI Interrupt Link [ALKC] (IRQs *22)
[17179571.248000] ACPI: PCI Interrupt Link [ALKD] (IRQs *23)
[17179571.248000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179571.248000] pnp: PnP ACPI init
[17179571.252000] pnp: PnP ACPI: found 13 devices
[17179571.252000] PnPBIOS: Disabled by ACPI PNP
[17179571.252000] PCI: Using ACPI for IRQ routing
[17179571.252000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179571.280000] pnp: 00:02: ioport range 0x4000-0x407f could not be reserved
[17179571.280000] pnp: 00:02: ioport range 0x5000-0x500f has been reserved
[17179571.280000] PCI: Bridge: 0000:00:01.0
[17179571.280000]   IO window: d000-dfff
[17179571.280000]   MEM window: f8000000-f80fffff
[17179571.280000]   PREFETCH window: d0000000-efffffff
[17179571.280000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[17179571.280000] NET: Registered protocol family 2
[17179571.312000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179571.312000] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[17179571.312000] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[17179571.312000] TCP: Hash tables configured (established 131072 bind 65536)
[17179571.312000] TCP reno registered
[17179571.312000] audit: initializing netlink socket (disabled)
[17179571.312000] audit(1162515281.312:1): initialized
[17179571.312000] highmem bounce pool size: 64 pages
[17179571.312000] VFS: Disk quotas dquot_6.5.1
[17179571.312000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179571.312000] Initializing Cryptographic API
[17179571.312000] io scheduler noop registered
[17179571.312000] io scheduler anticipatory registered
[17179571.312000] io scheduler deadline registered
[17179571.312000] io scheduler cfq registered (default)
[17179571.312000] isapnp: Scanning for PnP cards...
[17179571.668000] isapnp: No Plug & Play device found
[17179571.680000] Real Time Clock Driver v1.12ac
[17179571.680000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179571.684000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179571.684000] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179571.684000] mice: PS/2 mouse device common for all mice
[17179571.684000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179571.684000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179571.684000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179571.684000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[17179571.684000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179571.684000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179571.684000] EISA: Probing bus 0 at eisa.0
[17179571.684000] Cannot allocate resource for EISA slot 4
[17179571.684000] Cannot allocate resource for EISA slot 5
[17179571.684000] EISA: Detected 0 cards.
[17179571.684000] TCP bic registered
[17179571.684000] NET: Registered protocol family 1
[17179571.684000] NET: Registered protocol family 8
[17179571.684000] NET: Registered protocol family 20
[17179571.684000] Using IPI No-Shortcut mode
[17179571.684000] ACPI: (supports S0 S1 S4 S5)
[17179571.684000] Freeing unused kernel memory: 308k freed
[17179571.708000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179572.756000] Capability LSM initialized
[17179572.784000] ACPI: Fan [FAN] (on)
[17179572.788000] ACPI: Thermal Zone [THRM] (29 C)
[17179573.120000] SCSI subsystem initialized
[17179573.124000] libata version 1.20 loaded.
[17179573.124000] sata_via 0000:00:0f.0: version 1.1
[17179573.124000] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 20
[17179573.124000] ACPI: PCI Interrupt 0000:00:0f.0[B] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 169
[17179573.124000] PCI: Via IRQ fixup for 0000:00:0f.0, from 11 to 9
[17179573.124000] sata_via 0000:00:0f.0: routed to hard irq line 9
[17179573.124000] ata1: SATA max UDMA/133 cmd 0xE000 ctl 0xE102 bmdma 0xE400 irq 169
[17179573.124000] ata2: SATA max UDMA/133 cmd 0xE200 ctl 0xE302 bmdma 0xE408 irq 169
[17179573.292000] scsi0 : sata_via
[17179573.460000] scsi1 : sata_via
[17179573.472000] VP_IDE: IDE controller at PCI slot 0000:00:0f.1
[17179573.472000] ACPI: PCI Interrupt 0000:00:0f.1[A] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 169
[17179573.472000] PCI: Via IRQ fixup for 0000:00:0f.1, from 255 to 9
[17179573.472000] VP_IDE: chipset revision 6
[17179573.472000] VP_IDE: not 100% native mode: will probe irqs later
[17179573.472000] VP_IDE: VIA vt8237 (rev 00) IDE UDMA133 controller on pci0000:00:0f.1
[17179573.472000]     ide0: BM-DMA at 0xe600-0xe607, BIOS settings: hda:DMA, hdb:pio
[17179573.472000]     ide1: BM-DMA at 0xe608-0xe60f, BIOS settings: hdc:DMA, hdd:pio
[17179573.472000] Probing IDE interface ide0...
[17179573.888000] hda: WDC WD2000BB-22GUA0, ATA DISK drive
[17179574.564000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179574.584000] Probing IDE interface ide1...
[17179575.448000] hdc: OPTORITEDVD RW DD0405, ATAPI CD/DVD-ROM drive
[17179575.788000] ide1 at 0x170-0x177,0x376 on irq 15
[17179575.792000] hda: max request size: 512KiB
[17179575.920000] hda: 390721968 sectors (200049 MB) w/2048KiB Cache, CHS=24321/255/63, UDMA(100)
[17179575.920000] hda: cache flushes supported
[17179575.920000]  hda: hda1 hda2 < hda5 >
[17179575.984000] hdc: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179575.984000] Uniform CD-ROM driver Revision: 3.20
[17179576.252000] usbcore: registered new driver usbfs
[17179576.252000] usbcore: registered new driver hub
[17179576.252000] USB Universal Host Controller Interface driver v3.0
[17179576.252000] ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 21
[17179576.252000] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 177
[17179576.252000] PCI: Via IRQ fixup for 0000:00:10.0, from 10 to 1
[17179576.252000] uhci_hcd 0000:00:10.0: UHCI Host Controller
[17179576.252000] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[17179576.252000] uhci_hcd 0000:00:10.0: irq 177, io base 0x0000e700
[17179576.252000] usb usb1: configuration #1 chosen from 1 choice
[17179576.252000] hub 1-0:1.0: USB hub found
[17179576.252000] hub 1-0:1.0: 2 ports detected
[17179576.356000] ACPI: PCI Interrupt 0000:00:10.4[C] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 177
[17179576.356000] PCI: Via IRQ fixup for 0000:00:10.4, from 5 to 1
[17179576.356000] ehci_hcd 0000:00:10.4: EHCI Host Controller
[17179576.356000] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 2
[17179576.356000] ehci_hcd 0000:00:10.4: irq 177, io mem 0xf8100000
[17179576.356000] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179576.356000] usb usb2: configuration #1 chosen from 1 choice
[17179576.360000] hub 2-0:1.0: USB hub found
[17179576.360000] hub 2-0:1.0: 8 ports detected
[17179576.476000] ACPI: PCI Interrupt 0000:00:10.1[A] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 177
[17179576.476000] PCI: Via IRQ fixup for 0000:00:10.1, from 10 to 1
[17179576.476000] uhci_hcd 0000:00:10.1: UHCI Host Controller
[17179576.476000] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 3
[17179576.476000] uhci_hcd 0000:00:10.1: irq 177, io base 0x0000e800
[17179576.476000] usb usb3: configuration #1 chosen from 1 choice
[17179576.476000] hub 3-0:1.0: USB hub found
[17179576.476000] hub 3-0:1.0: 2 ports detected
[17179576.580000] ACPI: PCI Interrupt 0000:00:10.2[B] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 177
[17179576.580000] PCI: Via IRQ fixup for 0000:00:10.2, from 11 to 1
[17179576.580000] uhci_hcd 0000:00:10.2: UHCI Host Controller
[17179576.580000] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 4
[17179576.580000] uhci_hcd 0000:00:10.2: irq 177, io base 0x0000e900
[17179576.580000] usb usb4: configuration #1 chosen from 1 choice
[17179576.580000] hub 4-0:1.0: USB hub found
[17179576.580000] hub 4-0:1.0: 2 ports detected
[17179576.684000] ACPI: PCI Interrupt 0000:00:10.3[B] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 177
[17179576.684000] PCI: Via IRQ fixup for 0000:00:10.3, from 11 to 1
[17179576.684000] uhci_hcd 0000:00:10.3: UHCI Host Controller
[17179576.684000] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 5
[17179576.684000] uhci_hcd 0000:00:10.3: irq 177, io base 0x0000ea00
[17179576.684000] usb usb5: configuration #1 chosen from 1 choice
[17179576.684000] hub 5-0:1.0: USB hub found
[17179576.684000] hub 5-0:1.0: 2 ports detected
[17179576.868000] Attempting manual resume
[17179576.924000] EXT3-fs: INFO: recovery required on readonly filesystem.
[17179576.924000] EXT3-fs: write access will be enabled during recovery.
[17179577.036000] usb 3-1: new full speed USB device using uhci_hcd and address 2
[17179577.236000] usb 3-1: configuration #1 chosen from 1 choice
[17179580.472000] kjournald starting.  Commit interval 5 seconds
[17179580.472000] EXT3-fs: recovery complete.
[17179580.476000] EXT3-fs: mounted filesystem with ordered data mode.
[17179588.476000] input: PC Speaker as /class/input/input1
[17179588.740000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179588.744000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179588.800000] Linux agpgart interface v0.101 (c) Dave Jones
[17179588.804000] agpgart: Detected AGP bridge 0
[17179588.808000] agpgart: AGP aperture is 128M @ 0xf0000000
[17179588.900000] Floppy drive(s): fd0 is 1.44M
[17179588.952000] FDC 0 is a post-1991 82077
[17179589.180000] logips2pp: Detected unknown logitech mouse model 62
[17179589.204000] via-rhine.c:v1.10-LK1.2.0-2.6 June-10-2004 Written by Donald Becker
[17179589.204000] ACPI: PCI Interrupt Link [ALKD] enabled at IRQ 23
[17179589.204000] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [ALKD] -> GSI 23 (level, low) -> IRQ 185
[17179589.204000] PCI: Via IRQ fixup for 0000:00:12.0, from 10 to 9
[17179589.208000] eth0: VIA Rhine II at 0x1ed00, 00:e0:4c:d6:40:87, IRQ 185.
[17179589.212000] eth0: MII PHY found at address 1, status 0x7869 advertising 05e1 Link 41e1.
[17179589.268000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[17179589.304000] parport: PnPBIOS parport detected.
[17179589.304000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[17179589.524000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 2 if 0 alt 0 proto 2 vid 0x043D pid 0x0078
[17179589.524000] usbcore: registered new driver usblp
[17179589.524000] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[17179589.656000] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
[17179589.656000] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [ALKC] -> GSI 22 (level, low) -> IRQ 193
[17179589.656000] PCI: Via IRQ fixup for 0000:00:11.5, from 5 to 1
[17179589.656000] PCI: Setting latency timer of device 0000:00:11.5 to 64
[17179589.672000] input: ImExPS/2 Logitech Explorer Mouse as /class/input/input2
[17179589.696000] ts: Compaq touchscreen protocol output
[17179590.316000] NET: Registered protocol family 17
[17179590.392000] lp0: using parport0 (interrupt-driven).
[17179590.420000] Adding 3028212k swap on /dev/disk/by-uuid/8a66e64a-2502-4b41-b3c4-f819f30547d7.  Priority:-1 extents:1 across:3028212k
[17179590.492000] EXT3 FS on hda1, internal journal
[17179595.868000] ACPI: Power Button (FF) [PWRF]
[17179595.868000] ACPI: Power Button (CM) [PWRB]
[17179595.868000] ACPI: Sleep Button (CM) [SLPB]
[17179595.968000] ibm_acpi: ec object not found
[17179595.996000] pcc_acpi: loading...
[17179596.264000] powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (version 1.60.2)
[17179596.264000] powernow-k8:    0 : fid 0xe (2200 MHz), vid 0x2 (1500 mV)
[17179596.264000] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0x6 (1400 mV)
[17179596.264000] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0xa (1300 mV)
[17179596.264000] powernow-k8:    3 : fid 0x2 (1000 MHz), vid 0x12 (1100 mV)
[17179596.264000] cpu_init done, current fid 0xe, vid 0x2
[17179596.812000] NET: Registered protocol family 10
[17179596.812000] lo: Disabled Privacy Extensions
[17179596.812000] IPv6 over IPv4 tunneling driver
[17179597.788000] [drm] Initialized drm 1.0.1 20051102
[17179597.804000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 201
[17179597.804000] [drm] Initialized radeon 1.25.0 20060524 on minor 0
[17179598.356000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[17179598.356000] apm: overridden by ACPI.
[17179599.260000] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[17179599.260000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 4x mode
[17179599.260000] agpgart: Putting AGP V3 device at 0000:01:00.0 into 4x mode
[17179601.548000] Bluetooth: Core ver 2.8
[17179601.548000] NET: Registered protocol family 31
[17179601.548000] Bluetooth: HCI device and connection manager initialized
[17179601.548000] Bluetooth: HCI socket layer initialized
[17179601.576000] Bluetooth: L2CAP ver 2.8
[17179601.576000] Bluetooth: L2CAP socket layer initialized
[17179601.604000] Bluetooth: RFCOMM socket layer initialized
[17179601.604000] Bluetooth: RFCOMM TTY layer initialized
[17179601.604000] Bluetooth: RFCOMM ver 1.7
[17179607.544000] [drm] Setting GART location based on new memory map
[17179607.544000] [drm] Loading R300 Microcode
[17179607.544000] [drm] writeback test succeeded in 1 usecs
[17179607.772000] eth0: no IPv6 routers present
[17179623.608000] ISO 9660 Extensions: Microsoft Joliet Level 1
[17179623.692000] ISOFS: changing to secondary root

```

lsusb:
```
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 043d:0078 Lexmark International, Inc. 
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
```

lspci:
```
00:00.0 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AS [Radeon 9550]
01:00.1 Display controller: ATI Technologies Inc RV350 ?? [Radeon 9550] (Secondary)
```

---

### Post by francisco_athens on 2006-11-05
I have a P4P800 (not deluxe) with a 3ghz HT p4 and I could barely get through the motherboard initialization in Ubuntu (Hoary-Edgy) without disabling apic and lapic in BIOS (or on the bootline "nolapic" "noapic") and adding acpi=ht to the bootline.  Now it works well.

If you want to debug you boot, when you get to the grub menu, hit the key to edit the command line and remove the "quiet" and "splash" parts.  You can then get a better idea of whats happening at boot in real time.

Francisco

---

### Post by kyfho23 on 2006-11-06
i've been having the same problems of system freezes after a few minutes. i was thinking originally that it was a problem with the file browser or the owner permissions of some critical file or folder.

but....i am (reluctantly) going back to the onboard graphics (sys specs at the bottom), and i'll let you all know.

one other thought: i'm using an older dell (latiude L800r, i810 chipset, the video card i'm NOT using right now is an NVIDIA GeForce2 MX/MX400 on a pci slot. MAYBE we have a power problem, as in it's drawing too much?

i'll post more devlopments as they occur...

chris

---

### Post by kyfho23 on 2006-11-06
following up...after a few hours of surfing and email....no freezes.

i'm calling this one a hardware problem. time for a new vid card, if i can ever figure out how much power the comp puts out.

---

### Post by marx2k on 2006-11-06
My GNOME desktop was freezing when I plug in my PS2 -> PC HID USB device.  It requires a reboot and to NOT have that device in the USB port.  Im hoping I can solve this error soon with some drivers

---

### Post by ububaba on 2006-11-11
Freezing problem annoyed me so much that I upgraded from Dapper to Edgy. 
The computer became more unstable. Back to Dapper was not much help. 
Now I have retrograded to Breezy. It is better. The problem however
persists. Can one ever get out of this quagmire?](*,) ](*,) ](*,)

---

### Post by cwalk on 2006-11-11
Update: Well, it has been a little while now, and I can report that, without upgrading my video driver from the ATI website, my system has stopped this freezing problem. That is not to say that it will not come back (maybe as soon as I send this message if I know my luck). What I did to make it stop freezing:

1. Cleaned all dust from box.
2. Removed an unnecessary modem from a slot very near the video card, in hopes of creating more air flow.
3. Installed a new 120mm exhaust fan relatively close to my video card. I installed this fan along the back panel where where are a lot of (PCI?) slots, kinda where the modem was.(yes, i ghetto rigged it with some pliers).
4. Voila! no troubles for a week now =)

I will continue to keep you posted if there are any other developments.
Cheers,
Charlie

---

### Post by rev_b on 2006-11-14
Just want to share my "freeze" issues. My (k)ubuntu installation was rock stable, but sometimes (1 out of 3, maybe), it didn't shutdown for itself, I had to press the power button to power off the computer.

I searched a bit, and I tried this solution: adding "acpi=force" in /boot/menu.lst . It indeed solved the shutdown problem, but I started to notice that the computer would freeze completely from time to time, mainly when accessing a file in a hard-disk: starting nautilus or disk manager.

So I started to undo some customizations I had made, and removing that "acpi=force" did fix the freeze problem.

So those freezing issues may be ACPI related.

---

### Post by ububaba on 2006-11-14
> **rev_b said:**
> Just want to share my "freeze" issues. My (k)ubuntu installation was rock stable, but sometimes (1 out of 3, maybe), it didn't shutdown for itself, I had to press the power button to power off the computer.

I searched a bit, and I tried this solution: adding "acpi=force" in /boot/menu.lst . It indeed solved the shutdown problem, but I started to notice that the computer would freeze completely from time to time, mainly when accessing a file in a hard-disk: starting nautilus or disk manager.

So I started to undo some customizations I had made, and removing that "acpi=force" did fix the freeze problem.

So those freezing issues may be ACPI related.

Thanks for the reply. I got so frustrated that I formated the HD
and have 'started' once again to  install Dapper. There I am stuck too.
My install never gets completed. I have to re-start the process of
installing of Dapper from scratch. So, right now I am going in
circles. Help!!!](*,) ](*,) ](*,)

---

### Post by rev_b on 2006-11-14
I don't know exactly how to do it, but maybe trying to do an install without ACPI could help. If you dont't mind to press the on/off button to turn off the computer, you don't really need ACPI too much in a non-laptop computer.

---

### Post by rev_b on 2006-11-15
Also you can try to go system -> administration -> services and disable the Power management services. See if that helps.

---

### Post by sureinlux on 2007-03-24
My laptop has the same problem of random freezes. I wanted to try ```
acpi=ht
``` at boot time, but sadly my audio does not work after that :(


```
ALSA lib pcm_direct.c:819:(snd_pcm_direct_initialize_slave) snd_pcm_hw_params_any failed
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to initialize slave
ALSA snd_pcm_open error: Invalid argument
libao - OSS cannot set channels to 2
ALSA lib pcm_direct.c:819:(snd_pcm_direct_initialize_slave) snd_pcm_hw_params_any failed
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to initialize slave
Creating link /home/me/.kde/socket-mylappy.
can't create mcop directory
```

---

### Post by kyfho23 on 2007-03-24
On this whole general issue...watch the permissions. As far as I can remember, part of my problem was the read/write permissions in the temporary (/tmp/) folder. Often, other freezes stem from the creation and use of files in the /tmp folder.

Part of these problems stem from using sudo when you don't need to, and something being installed/configured as root, which the user can't write to.

Something to put on your debugging checklist, anyway.


ctw

---

