---
title: "Mounting a Windoze Raid Drive"
date: 2007-02-21
forum: General Help
---

### Post by firekat on 2007-02-21
Greetings all!

I have just finished installing Ubuntu on a AMD 64 machine which has a RAID 0 array for Windows.  I have Ubuntu loaded on a separate SATA hard drive that I bought specifically for the purpose.  Additionally I was able to get GRUB installed on the SATA drive and have the BIOS set so that it boots off that drive so I can dual boot.

The way is sits right now Ubuntu does not see the RAID array.  I have thrashed around and attempted to rectify the situation utilizing what I have seen here and some other locations.  On my last attempt I did the following:


```

firekat@firekat:~$ sudo fdisk -l
Password:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19457   156288321    7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 100.2 GB, 100256292864 bytes
255 heads, 63 sectors/track, 12188 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       11815    94903956   83  Linux
/dev/sdc2           11816       12188     2996122+   5  Extended
/dev/sdc5           11816       12188     2996091   82  Linux swap / Solaris
firekat@firekat:~$ 
```

I then tried this:

```
firekat@firekat:~$ sudo mount /dev/sda1 /mnt/
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```


I did the dmesg and this is what I got:
```

firekat@firekat:~$ dmesg
[    0.000000] Bootdata ok (command line is root=/dev/sdc1 ro quiet splash)
[    0.000000] Linux version 2.6.17-10-generic (root@king) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Tue Dec 5 21:16:35 UTC 2006 (Ubuntu 2.6.17-10.34-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003ffb0000 (usable)
[    0.000000]  BIOS-e820: 000000003ffb0000 - 000000003ffc0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003ffc0000 - 000000003fff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003fff0000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff780000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 ACPIAM                                ) @ 0x00000000000fa7c0
[    0.000000] ACPI: RSDT (v001 A M I  OEMRSDT  0x11000514 MSFT 0x00000097) @ 0x000000003ffb0000
[    0.000000] ACPI: FADT (v001 A M I  OEMFACP  0x11000514 MSFT 0x00000097) @ 0x000000003ffb0200
[    0.000000] ACPI: MADT (v001 A M I  OEMAPIC  0x11000514 MSFT 0x00000097) @ 0x000000003ffb0390
[    0.000000] ACPI: OEMB (v001 A M I  OEMBIOS  0x11000514 MSFT 0x00000097) @ 0x000000003ffc0040
[    0.000000] ACPI: DSDT (v001  A0036 A0036001 0x00000001 MSFT 0x0100000d) @ 0x0000000000000000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] Number of nodes 1
[    0.000000] Node 0 MemBase 0000000000000000 Limit 000000003ffb0000
[    0.000000] NUMA: Using 63 for the hash shift.
[    0.000000] Using node hash shift of 63
[    0.000000] Bootmem setup node 0 0000000000000000-000000003ffb0000
[    0.000000] On node 0 totalpages: 257031
[    0.000000]   DMA zone: 2589 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 254442 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:15 APIC version 16
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled)
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to physical flat
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bf780000)
[    0.000000] Checking aperture...
[    0.000000] CPU 0: aperture @ d0000000 size 256 MB
[    0.000000] SMP: Allowing 2 CPUs, 1 hotplug CPUs
[    0.000000] Built 1 zonelists
[    0.000000] Kernel command line: root=/dev/sdc1 ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] time.c: Using 3.579545 MHz WALL PM GTOD PIT/TSC timer.
[    0.000000] time.c: Detected 2202.898 MHz processor.
[   37.894273] Console: colour VGA+ 80x25
[   37.894980] Dentry cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   37.896071] Inode-cache hash table entries: 65536 (order: 7, 524288 bytes)
[   37.906898] Memory: 1020684k/1048256k available (2129k kernel code, 27184k reserved, 1424k data, 188k init)
[   37.986549] Calibrating delay using timer specific routine.. 4410.72 BogoMIPS (lpj=8821456)
[   37.986600] Security Framework v1.0.0 initialized
[   37.986609] SELinux:  Disabled at boot.
[   37.986629] Mount-cache hash table entries: 256
[   37.986760] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   37.986763] CPU: L2 Cache: 512K (64 bytes/line)
[   37.986766] CPU 0/0(1) -> Node 0 -> Core 0
[   37.986782] SMP alternatives: switching to UP code
[   37.987024] checking if image is initramfs... it is
[   38.445990] Freeing initrd memory: 5751k freed
[   38.449636] ACPI: Core revision 20060707
[   38.450059] ACPI: Looking for DSDT ... not found!
[   38.492573] Using local APIC timer interrupts.
[   38.537888] result 12516468
[   38.537890] Detected 12.516 MHz APIC timer.
[   38.541607] Brought up 1 CPUs
[   38.541730] testing NMI watchdog ... OK.
[   38.581738] migration_cost=0
[   38.581946] NET: Registered protocol family 16
[   38.581969] ACPI: bus type pci registered
[   38.581975] PCI: Using configuration type 1
[   38.586169] ACPI: Interpreter enabled
[   38.586171] ACPI: Using IOAPIC for interrupt routing
[   38.587113] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   38.587116] PCI: Probing PCI hardware (bus 00)
[   38.589892] PCI: Ignoring BAR0-3 of IDE controller 0000:00:0f.1
[   38.590150] PCI: Quirk-MSI-K8T Soundcard On
[   38.590153] PCI: Unexpected Value in PCI-Register: no Change!
[   38.590158] PCI: enabled onboard AC97/MC97 devices
[   38.590351] Boot video device is 0000:01:00.0
[   38.590394] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   38.606772] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 *11 14 15)
[   38.606963] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 7 10 11 14 15)
[   38.607151] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 7 10 11 14 15)
[   38.607338] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 7 10 11 14 15)
[   38.607528] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[   38.607721] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[   38.607911] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[   38.608100] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[   38.608192] Linux Plug and Play Support v0.97 (c) Adam Belay
[   38.608205] pnp: PnP ACPI init
[   38.612796] pnp: PnP ACPI: found 17 devices
[   38.612838] PCI: Using ACPI for IRQ routing
[   38.612841] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   38.613004] agpgart: Detected AGP bridge 0
[   38.623505] agpgart: AGP aperture is 256M @ 0xd0000000
[   38.623525] PCI-DMA: Disabling IOMMU.
[   38.624134] pnp: 00:09: ioport range 0x680-0x6ff has been reserved
[   38.624137] pnp: 00:09: ioport range 0x290-0x297 has been reserved
[   38.624299] PCI: Bridge: 0000:00:01.0
[   38.624301]   IO window: disabled.
[   38.624304]   MEM window: f9f00000-fbffffff
[   38.624308]   PREFETCH window: e0000000-f8ffffff
[   38.624323] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   38.624366] NET: Registered protocol family 2
[   38.661392] IP route cache hash table entries: 32768 (order: 6, 262144 bytes)
[   38.661567] TCP established hash table entries: 131072 (order: 9, 2097152 bytes)
[   38.663061] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   38.663833] TCP: Hash tables configured (established 131072 bind 65536)
[   38.663836] TCP reno registered
[   38.664155] IA32 emulation $Id: sys_ia32.c,v 1.32 2002/03/24 13:02:28 ak Exp $
[   38.664451] audit: initializing netlink socket (disabled)
[   38.664460] audit(1172077045.776:1): initialized
[   38.664588] VFS: Disk quotas dquot_6.5.1
[   38.664607] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   38.664647] Initializing Cryptographic API
[   38.664651] io scheduler noop registered
[   38.664657] io scheduler anticipatory registered
[   38.664664] io scheduler deadline registered
[   38.664677] io scheduler cfq registered (default)
[   38.706201] Real Time Clock Driver v1.12ac
[   38.706238] Linux agpgart interface v0.101 (c) Dave Jones
[   38.706241] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   38.706341] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   38.706452] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   38.706851] 00:0c: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   38.706995] 00:0d: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   38.707107] GSI 16 sharing vector 0xA9 and IRQ 16
[   38.707110] ACPI: PCI Interrupt 0000:00:0e.0[A] -> GSI 19 (level, low) -> IRQ 169
[   38.707805] mice: PS/2 mouse device common for all mice
[   38.708237] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   38.708412] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   38.708415] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   38.708662] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   38.708842] serio: i8042 AUX port at 0x60,0x64 irq 12
[   38.708856] serio: i8042 KBD port at 0x60,0x64 irq 1
[   38.709058] TCP bic registered
[   38.709065] NET: Registered protocol family 1
[   38.709070] NET: Registered protocol family 8
[   38.709072] NET: Registered protocol family 20
[   38.709216] ACPI: (supports S0 S1 S3 S4 S5)
[   38.709288] drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   38.709306] Freeing unused kernel memory: 188k freed
[   38.730309] input: AT Translated Set 2 keyboard as /class/input/input0
[   38.752911] vga16fb: initializing
[   38.752916] vga16fb: mapped to 0xffff8100000a0000
[   38.910258] Console: switching to colour frame buffer device 80x25
[   38.910264] fb0: VGA16 VGA frame buffer device
[   39.948309] Capability LSM initialized
[   39.976142] ACPI Exception (acpi_processor-0693): AE_NOT_FOUND, Processor Device is not present [20060707]
[   39.976148] ACPI: Getting cpuindex for acpiid 0x2
[   40.271792] SCSI subsystem initialized
[   40.274942] libata version 1.20 loaded.
[   40.275770] sata_promise 0000:00:08.0: version 1.04
[   40.275788] GSI 17 sharing vector 0xB1 and IRQ 17
[   40.275791] ACPI: PCI Interrupt 0000:00:08.0[A] -> GSI 18 (level, low) -> IRQ 177
[   40.275906] sata_promise PATA port found
[   40.294417] ata1: SATA max UDMA/133 cmd 0xFFFFC2000003E200 ctl 0xFFFFC2000003E238 bmdma 0x0 irq 177
[   40.294439] ata2: SATA max UDMA/133 cmd 0xFFFFC2000003E280 ctl 0xFFFFC2000003E2B8 bmdma 0x0 irq 177
[   40.294457] ata3: PATA max UDMA/133 cmd 0xFFFFC2000003E300 ctl 0xFFFFC2000003E338 bmdma 0x0 irq 177
[   40.501976] ata1: SATA link up 1.5 Gbps (SStatus 113)
[   40.789767] ata1: dev 0 cfg 49:2f00 82:346b 83:7d01 84:4003 85:3469 86:3c01 87:4003 88:407f
[   40.789771] ata1: dev 0 ATA-6, max UDMA/133, 156301488 sectors: LBA48
[   40.801741] ata1: dev 0 configured for UDMA/133
[   40.801744] scsi0 : sata_promise
[   41.009050] ata2: SATA link up 1.5 Gbps (SStatus 113)
[   41.296836] ata2: dev 0 cfg 49:2f00 82:346b 83:7d01 84:4003 85:3469 86:3c01 87:4003 88:407f
[   41.296840] ata2: dev 0 ATA-6, max UDMA/133, 156301488 sectors: LBA48
[   41.308811] ata2: dev 0 configured for UDMA/133
[   41.308813] scsi1 : sata_promise
[   41.478247] ata3: disabling port
[   41.478249] scsi2 : sata_promise
[   41.478402]   Vendor: ATA       Model: ST380013AS        Rev: 3.18
[   41.478408]   Type:   Direct-Access                      ANSI SCSI revision: 05
[   41.478598]   Vendor: ATA       Model: ST380013AS        Rev: 3.18
[   41.478604]   Type:   Direct-Access                      ANSI SCSI revision: 05
[   41.487473] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[   41.487484] sda: Write Protect is off
[   41.487486] sda: Mode Sense: 00 3a 00 00
[   41.487497] SCSI device sda: drive cache: write back
[   41.487547] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[   41.487554] sda: Write Protect is off
[   41.487556] sda: Mode Sense: 00 3a 00 00
[   41.487566] SCSI device sda: drive cache: write back
[   41.487570]  sda: sda1
[   41.509839] sd 0:0:0:0: Attached scsi disk sda
[   41.510444] SCSI device sdb: 156301488 512-byte hdwr sectors (80026 MB)
[   41.512151] sdb: Write Protect is off
[   41.512155] sdb: Mode Sense: 00 3a 00 00
[   41.512754] SCSI device sdb: drive cache: write back
[   41.512805] SCSI device sdb: 156301488 512-byte hdwr sectors (80026 MB)
[   41.512812] sdb: Write Protect is off
[   41.512814] sdb: Mode Sense: 00 3a 00 00
[   41.512824] SCSI device sdb: drive cache: write back
[   41.512827]  sdb: unknown partition table
[   41.532755] sd 1:0:0:0: Attached scsi disk sdb
[   41.560185] Buffer I/O error on device sda1, logical block 156288256
[   41.560201] Buffer I/O error on device sda1, logical block 156288257
[   41.560205] Buffer I/O error on device sda1, logical block 156288258
[   41.560208] Buffer I/O error on device sda1, logical block 156288259
[   41.560218] Buffer I/O error on device sda1, logical block 156288256
[   41.560221] Buffer I/O error on device sda1, logical block 156288257
[   41.560224] Buffer I/O error on device sda1, logical block 156288258
[   41.560227] Buffer I/O error on device sda1, logical block 156288259
[   41.560242] Buffer I/O error on device sda1, logical block 156288320
[   41.560248] Buffer I/O error on device sda1, logical block 156288320
[   41.626657] sata_via 0000:00:0f.0: version 1.1
[   41.626674] GSI 18 sharing vector 0xB9 and IRQ 18
[   41.626678] ACPI: PCI Interrupt 0000:00:0f.0[B] -> GSI 20 (level, low) -> IRQ 185
[   41.626688] PCI: Via IRQ fixup for 0000:00:0f.0, from 5 to 9
[   41.626718] sata_via 0000:00:0f.0: routed to hard irq line 9
[   41.626745] ata4: SATA max UDMA/133 cmd 0xD400 ctl 0xD002 bmdma 0xC000 irq 185
[   41.626762] ata5: SATA max UDMA/133 cmd 0xC800 ctl 0xC402 bmdma 0xC008 irq 185
[   41.795783] ata4: dev 0 cfg 49:2f00 82:7c6b 83:5b09 84:4673 85:7c69 86:1a21 87:4663 88:407f
[   41.795789] ata4: dev 0 ATA-7, max UDMA/133, 195813072 sectors: LBA
[   41.807762] ata4: dev 0 configured for UDMA/133
[   41.807764] scsi3 : sata_via
[   41.977852] scsi4 : sata_via
[   41.978000]   Vendor: ATA       Model: Maxtor 6L100M0    Rev: BANC
[   41.978007]   Type:   Direct-Access                      ANSI SCSI revision: 05
[   41.978177] SCSI device sdc: 195813072 512-byte hdwr sectors (100256 MB)
[   41.978186] sdc: Write Protect is off
[   41.978188] sdc: Mode Sense: 00 3a 00 00
[   41.978199] SCSI device sdc: drive cache: write back
[   41.978234] SCSI device sdc: 195813072 512-byte hdwr sectors (100256 MB)
[   41.978241] sdc: Write Protect is off
[   41.978243] sdc: Mode Sense: 00 3a 00 00
[   41.978254] SCSI device sdc: drive cache: write back
[   41.978256]  sdc: sdc1 sdc2 < sdc5 >
[   42.013864] sd 3:0:0:0: Attached scsi disk sdc
[   42.241479] VP_IDE: IDE controller at PCI slot 0000:00:0f.1
[   42.241498] ACPI: PCI Interrupt 0000:00:0f.1[A] -> GSI 20 (level, low) -> IRQ 185
[   42.241503] PCI: Via IRQ fixup for 0000:00:0f.1, from 255 to 9
[   42.241528] VP_IDE: chipset revision 6
[   42.241529] VP_IDE: not 100% native mode: will probe irqs later
[   42.241541] VP_IDE: VIA vt8237 (rev 00) IDE UDMA133 controller on pci0000:00:0f.1
[   42.241548]     ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:pio, hdb:pio
[   42.241561]     ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: hdc:DMA, hdd:DMA
[   42.241569] Probing IDE interface ide0...
[   42.809752] Probing IDE interface ide1...
[   43.684240] hdc: SONY DVD-ROM DDU1613, ATAPI CD/DVD-ROM drive
[   44.466803] hdd: SONY DVD RW DW-D22A, ATAPI CD/DVD-ROM drive
[   44.523275] ide1 at 0x170-0x177,0x376 on irq 15
[   44.533220] hdc: ATAPI 40X DVD-ROM drive, 512kB Cache, UDMA(33)
[   44.533228] Uniform CD-ROM driver Revision: 3.20
[   44.535292] hdd: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(66)
[   44.586452] Probing IDE interface ide0...
[   44.633015] ieee1394: Initialized config rom entry `ip1394'
[   44.634158] GSI 19 sharing vector 0xC1 and IRQ 19
[   44.634162] ACPI: PCI Interrupt 0000:00:07.0[A] -> GSI 16 (level, low) -> IRQ 193
[   44.634173] PCI: Via IRQ fixup for 0000:00:07.0, from 11 to 1
[   44.687315] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[193]  MMIO=[f9800000-f98007ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   44.702073] usbcore: registered new driver usbfs
[   44.702094] usbcore: registered new driver hub
[   44.702931] USB Universal Host Controller Interface driver v3.0
[   44.702982] GSI 20 sharing vector 0xC9 and IRQ 20
[   44.702985] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 21 (level, low) -> IRQ 201
[   44.702995] PCI: Via IRQ fixup for 0000:00:10.0, from 11 to 9
[   44.703020] uhci_hcd 0000:00:10.0: UHCI Host Controller
[   44.703143] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[   44.703171] uhci_hcd 0000:00:10.0: irq 201, io base 0x0000d800
[   44.703243] usb usb1: configuration #1 chosen from 1 choice
[   44.703262] hub 1-0:1.0: USB hub found
[   44.703268] hub 1-0:1.0: 2 ports detected
[   44.810289] ACPI: PCI Interrupt 0000:00:10.1[A] -> GSI 21 (level, low) -> IRQ 201
[   44.810295] PCI: Via IRQ fixup for 0000:00:10.1, from 11 to 9
[   44.810321] uhci_hcd 0000:00:10.1: UHCI Host Controller
[   44.810405] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[   44.810427] uhci_hcd 0000:00:10.1: irq 201, io base 0x0000e000
[   44.810563] usb usb2: configuration #1 chosen from 1 choice
[   44.810646] hub 2-0:1.0: USB hub found
[   44.810653] hub 2-0:1.0: 2 ports detected
[   44.917990] ACPI: PCI Interrupt 0000:00:10.2[B] -> GSI 21 (level, low) -> IRQ 201
[   44.917994] PCI: Via IRQ fixup for 0000:00:10.2, from 5 to 9
[   44.918015] uhci_hcd 0000:00:10.2: UHCI Host Controller
[   44.918097] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[   44.918114] uhci_hcd 0000:00:10.2: irq 201, io base 0x0000e400
[   44.918237] usb usb3: configuration #1 chosen from 1 choice
[   44.918323] hub 3-0:1.0: USB hub found
[   44.918329] hub 3-0:1.0: 2 ports detected
[   45.025793] ACPI: PCI Interrupt 0000:00:10.3[B] -> GSI 21 (level, low) -> IRQ 201
[   45.025797] PCI: Via IRQ fixup for 0000:00:10.3, from 5 to 9
[   45.025818] uhci_hcd 0000:00:10.3: UHCI Host Controller
[   45.025903] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[   45.025919] uhci_hcd 0000:00:10.3: irq 201, io base 0x0000e800
[   45.026044] usb usb4: configuration #1 chosen from 1 choice
[   45.026128] hub 4-0:1.0: USB hub found
[   45.026133] hub 4-0:1.0: 2 ports detected
[   45.139769] ACPI: PCI Interrupt 0000:00:10.4[C] -> GSI 21 (level, low) -> IRQ 201
[   45.139776] PCI: Via IRQ fixup for 0000:00:10.4, from 5 to 9
[   45.139924] ehci_hcd 0000:00:10.4: EHCI Host Controller
[   45.139975] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
[   45.140015] ehci_hcd 0000:00:10.4: irq 201, io mem 0xf9e00000
[   45.140022] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   45.140086] usb usb5: configuration #1 chosen from 1 choice
[   45.140108] hub 5-0:1.0: USB hub found
[   45.140114] hub 5-0:1.0: 8 ports detected
[   45.282573] Attempting manual resume
[   45.294946] kjournald starting.  Commit interval 5 seconds
[   45.294956] EXT3-fs: mounted filesystem with ordered data mode.
[   45.968135] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00e0180000c78366]
[   46.359266] usb 5-5: new high speed USB device using ehci_hcd and address 3
[   46.503910] usb 5-5: configuration #1 chosen from 1 choice
[   46.746542] usb 2-1: new low speed USB device using uhci_hcd and address 2
[   46.925238] usb 2-1: configuration #1 chosen from 1 choice
[   52.497514] printk: 22 messages suppressed.
[   52.497519] Buffer I/O error on device sda1, logical block 156288256
[   52.497535] Buffer I/O error on device sda1, logical block 156288257
[   52.645058] GSI 21 sharing vector 0xD1 and IRQ 21
[   52.645062] ACPI: PCI Interrupt 0000:00:0a.0[A] -> GSI 17 (level, low) -> IRQ 209
[   52.645193] skge 1.5 addr 0xf9c00000 irq 209 chip Yukon-Lite rev 7
[   52.645306] skge eth0: addr 00:11:d8:37:86:eb
[   52.759783] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   52.762855] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   52.888975] input: PC Speaker as /class/input/input1
[   53.095463] Floppy drive(s): fd0 is 1.44M
[   53.118770] FDC 0 is a post-1991 82077
[   53.179721] parport: PnPBIOS parport detected.
[   53.179761] parport0: PC-style at 0x378, irq 7 [PCSPP]
[   53.357791] PCI: Enabling device 0000:00:11.6 (0000 -> 0001)
[   53.357800] GSI 22 sharing vector 0xD9 and IRQ 22
[   53.357803] ACPI: PCI Interrupt 0000:00:11.6[C] -> GSI 22 (level, low) -> IRQ 217
[   53.357813] PCI: Via IRQ fixup for 0000:00:11.6, from 0 to 9
[   53.481327] skge eth0: enabling interface
[   53.581637] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   53.581662] sd 1:0:0:0: Attached scsi generic sg1 type 0
[   53.581685] sd 3:0:0:0: Attached scsi generic sg2 type 0
[   53.611179] usbcore: registered new driver libusual
[   53.728290] Initializing USB Mass Storage driver...
[   53.730559] scsi5 : SCSI emulation for USB Mass Storage devices
[   53.730653] usbcore: registered new driver usb-storage
[   53.730656] USB Mass Storage support registered.
[   53.730659] usb-storage: device found at 3
[   53.730661] usb-storage: waiting for device to settle before scanning
[   53.775020] input: Wacom Graphire2 4x5 as /class/input/input2
[   53.781339] usbcore: registered new driver wacom
[   53.781344] drivers/usb/input/wacom.c: v1.45:USB Wacom Graphire and Wacom Intuos tablet driver
[   53.872151] logips2pp: Detected unknown logitech mouse model 127
[   53.960510] nvidia: module license 'NVIDIA' taints kernel.
[   54.216261] PCI: Setting latency timer of device 0000:00:11.6 to 64
[   54.238309] usbcore: registered new driver hiddev
[   54.238325] usbcore: registered new driver usbhid
[   54.238328] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   54.272946] ts: Compaq touchscreen protocol output
[   54.317655] input: ImExPS/2 Logitech Explorer Mouse as /class/input/input3
[   54.536118] NET: Registered protocol family 17
[   54.720155] ACPI: PCI interrupt for device 0000:00:11.6 disabled
[   54.720163] VIA 82xx Modem: probe of 0000:00:11.6 failed with error -13
[   54.720294] PCI: Enabling device 0000:00:11.5 (0000 -> 0001)
[   54.720299] ACPI: PCI Interrupt 0000:00:11.5[C] -> GSI 22 (level, low) -> IRQ 217
[   54.720304] PCI: Via IRQ fixup for 0000:00:11.5, from 0 to 9
[   54.720452] PCI: Setting latency timer of device 0000:00:11.5 to 64
[   55.247739] ACPI: PCI Interrupt 0000:00:0c.0[A] -> GSI 17 (level, low) -> IRQ 209
[   55.293405] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 193
[   55.293561] NVRM: loading NVIDIA Linux x86_64 Kernel Module  1.0-9626  Wed Sep 20 16:36:52 PDT 2006
[   55.320347] skge eth0: Link is up at 100 Mbps, full duplex, flow control none
[   56.259859] lp0: using parport0 (interrupt-driven).
[   56.295053] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[   56.295058] ieee1394: sbp2: Try serialize_io=0 for better performance
[   56.517555] Adding 2996080k swap on /dev/disk/by-uuid/faa1a6b6-c448-46f0-b04f-21f8dce5cd98.  Priority:-1 extents:1 across:2996080k
[   56.604206] EXT3 FS on sdc1, internal journal
[   57.645392] NET: Registered protocol family 10
[   57.645478] lo: Disabled Privacy Extensions
[   57.645597] IPv6 over IPv4 tunneling driver
[   58.725046] usb-storage: device scan complete
[   58.726026]   Vendor: USB2.0    Model: CardReader CF RW  Rev: 0814
[   58.726034]   Type:   Direct-Access                      ANSI SCSI revision: 00
[   58.728611]   Vendor: USB2.0    Model: CardReader Combo  Rev: 0814
[   58.728618]   Type:   Direct-Access                      ANSI SCSI revision: 00
[   58.745299] sd 5:0:0:0: Attached scsi removable disk sdd
[   58.745340] sd 5:0:0:0: Attached scsi generic sg3 type 0
[   58.756607] sd 5:0:0:1: Attached scsi removable disk sde
[   58.756653] sd 5:0:0:1: Attached scsi generic sg4 type 0
[   60.865898] ACPI: Power Button (FF) [PWRF]
[   60.865922] ACPI: Power Button (CM) [PWRB]
[   60.865930] ACPI: Sleep Button (CM) [SLPB]
[   60.930888] ibm_acpi: ec object not found
[   60.957195] pcc_acpi: loading...
[   61.369163] powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (version 1.60.2)
[   61.370149] powernow-k8: BIOS error - no PSB or ACPI _PSS objects
[   64.711656] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[   64.711670] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   64.711737] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[   68.526658] eth0: no IPv6 routers present
[   71.087019] printk: 30 messages suppressed.
[   71.087025] Buffer I/O error on device sda1, logical block 156288256
[   71.087334] Buffer I/O error on device sda1, logical block 156288257
[   71.087338] Buffer I/O error on device sda1, logical block 156288258
[   72.068960] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[   72.175069] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   72.175466] NFSD: starting 90-second grace period
[   73.213343] Bluetooth: Core ver 2.8
[   73.213348] NET: Registered protocol family 31
[   73.213350] Bluetooth: HCI device and connection manager initialized
[   73.213364] Bluetooth: HCI socket layer initialized
[   73.222079] Bluetooth: L2CAP ver 2.8
[   73.222084] Bluetooth: L2CAP socket layer initialized
[   73.265132] Bluetooth: RFCOMM socket layer initialized
[   73.265147] Bluetooth: RFCOMM TTY layer initialized
[   73.265149] Bluetooth: RFCOMM ver 1.7
[ 1046.135703] printk: 27 messages suppressed.
[ 1046.135711] Buffer I/O error on device sda1, logical block 156288256
[ 1046.136039] Buffer I/O error on device sda1, logical block 156288257
[ 1046.136043] Buffer I/O error on device sda1, logical block 156288258
[ 1046.136046] Buffer I/O error on device sda1, logical block 156288259
[ 1046.136233] Buffer I/O error on device sda1, logical block 156288256
[ 1046.136237] Buffer I/O error on device sda1, logical block 156288257
[ 1046.136240] Buffer I/O error on device sda1, logical block 156288258
[ 1046.136243] Buffer I/O error on device sda1, logical block 156288259
[ 1046.136489] Buffer I/O error on device sda1, logical block 156288320
[ 1046.137164] Buffer I/O error on device sda1, logical block 156288320
[ 1083.863069] printk: 22 messages suppressed.
[ 1083.863078] Buffer I/O error on device sda1, logical block 156288256
[ 1083.863419] Buffer I/O error on device sda1, logical block 156288257
[ 1083.863423] Buffer I/O error on device sda1, logical block 156288258
[ 1083.863426] Buffer I/O error on device sda1, logical block 156288259
[ 1083.863615] Buffer I/O error on device sda1, logical block 156288256
[ 1083.863618] Buffer I/O error on device sda1, logical block 156288257
[ 1083.863621] Buffer I/O error on device sda1, logical block 156288258
[ 1083.957717] NTFS driver 2.1.27 [Flags: R/O MODULE].
firekat@firekat:~$ 
```


I am very much a newbie so any help would be greatly appreciated!

---

### Post by tomBorgia on 2007-02-23
> firekat@firekat:~$ sudo mount /dev/sda1 /mnt/
This will work but you need to specify the filesystem type - something like this - 
# sudo mount -t ntfs -o nls=utf8,umask=0222 /dev/sda1 /mnt/windows
:)

---

### Post by firekat on 2007-02-23
I tried this.  First it said that the mount point did not exist so I just changed it to /media.

I got this message:

```
firekat@firekat-desktop:~$ sudo mount -t ntfs -o nls=utf8,umask=0222 /dev/sda1 /media
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

This is the dmseg:

```

firekat@firekat-desktop:~$ dmesg
[    0.000000] Bootdata ok (command line is root=/dev/sdc1 ro quiet splash)
[    0.000000] Linux version 2.6.17-11-generic (root@king) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Thu Feb 1 18:03:05 UTC 2007 (Ubuntu 2.6.17-11.35-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003ffb0000 (usable)
[    0.000000]  BIOS-e820: 000000003ffb0000 - 000000003ffc0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003ffc0000 - 000000003fff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003fff0000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff780000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 ACPIAM                                ) @ 0x00000000000fa7c0
[    0.000000] ACPI: RSDT (v001 A M I  OEMRSDT  0x11000514 MSFT 0x00000097) @ 0x000000003ffb0000
[    0.000000] ACPI: FADT (v001 A M I  OEMFACP  0x11000514 MSFT 0x00000097) @ 0x000000003ffb0200
[    0.000000] ACPI: MADT (v001 A M I  OEMAPIC  0x11000514 MSFT 0x00000097) @ 0x000000003ffb0390
[    0.000000] ACPI: OEMB (v001 A M I  OEMBIOS  0x11000514 MSFT 0x00000097) @ 0x000000003ffc0040
[    0.000000] ACPI: DSDT (v001  A0036 A0036001 0x00000001 MSFT 0x0100000d) @ 0x0000000000000000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] Number of nodes 1
[    0.000000] Node 0 MemBase 0000000000000000 Limit 000000003ffb0000
[    0.000000] NUMA: Using 63 for the hash shift.
[    0.000000] Using node hash shift of 63
[    0.000000] Bootmem setup node 0 0000000000000000-000000003ffb0000
[    0.000000] On node 0 totalpages: 257031
[    0.000000]   DMA zone: 2589 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 254442 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:15 APIC version 16
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled)
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to physical flat
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bf780000)
[    0.000000] Checking aperture...
[    0.000000] CPU 0: aperture @ d0000000 size 256 MB
[    0.000000] SMP: Allowing 2 CPUs, 1 hotplug CPUs
[    0.000000] Built 1 zonelists
[    0.000000] Kernel command line: root=/dev/sdc1 ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] time.c: Using 3.579545 MHz WALL PM GTOD PIT/TSC timer.
[    0.000000] time.c: Detected 2202.832 MHz processor.
[   38.019786] Console: colour VGA+ 80x25
[   38.020493] Dentry cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   38.021583] Inode-cache hash table entries: 65536 (order: 7, 524288 bytes)
[   38.032438] Memory: 1020684k/1048256k available (2129k kernel code, 27184k reserved, 1424k data, 188k init)
[   38.112076] Calibrating delay using timer specific routine.. 4410.82 BogoMIPS (lpj=8821644)
[   38.112128] Security Framework v1.0.0 initialized
[   38.112136] SELinux:  Disabled at boot.
[   38.112156] Mount-cache hash table entries: 256
[   38.112287] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   38.112290] CPU: L2 Cache: 512K (64 bytes/line)
[   38.112292] CPU 0/0(1) -> Node 0 -> Core 0
[   38.112309] SMP alternatives: switching to UP code
[   38.112550] checking if image is initramfs... it is
[   38.571963] Freeing initrd memory: 5751k freed
[   38.575631] ACPI: Core revision 20060707
[   38.576041] ACPI: Looking for DSDT ... not found!
[   38.618527] Using local APIC timer interrupts.
[   38.663842] result 12516113
[   38.663843] Detected 12.516 MHz APIC timer.
[   38.667130] Brought up 1 CPUs
[   38.667253] testing NMI watchdog ... OK.
[   38.707261] migration_cost=0
[   38.707470] NET: Registered protocol family 16
[   38.707492] ACPI: bus type pci registered
[   38.707499] PCI: Using configuration type 1
[   38.711675] ACPI: Interpreter enabled
[   38.711677] ACPI: Using IOAPIC for interrupt routing
[   38.712601] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   38.712604] PCI: Probing PCI hardware (bus 00)
[   38.715352] PCI: Ignoring BAR0-3 of IDE controller 0000:00:0f.1
[   38.715612] PCI: Quirk-MSI-K8T Soundcard On
[   38.715615] PCI: Unexpected Value in PCI-Register: no Change!
[   38.715620] PCI: enabled onboard AC97/MC97 devices
[   38.715816] Boot video device is 0000:01:00.0
[   38.715858] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   38.732077] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 *11 14 15)
[   38.732264] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 7 10 11 14 15)
[   38.732448] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 7 10 11 14 15)
[   38.732632] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 7 10 11 14 15)
[   38.732818] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[   38.733006] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[   38.733192] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[   38.733385] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[   38.733477] Linux Plug and Play Support v0.97 (c) Adam Belay
[   38.733486] pnp: PnP ACPI init
[   38.737976] pnp: PnP ACPI: found 17 devices
[   38.738021] PCI: Using ACPI for IRQ routing
[   38.738024] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   38.738143] agpgart: Detected AGP bridge 0
[   38.748671] agpgart: AGP aperture is 256M @ 0xd0000000
[   38.748690] PCI-DMA: Disabling IOMMU.
[   38.749279] pnp: 00:09: ioport range 0x680-0x6ff has been reserved
[   38.749282] pnp: 00:09: ioport range 0x290-0x297 has been reserved
[   38.749450] PCI: Bridge: 0000:00:01.0
[   38.749451]   IO window: disabled.
[   38.749455]   MEM window: f9f00000-fbffffff
[   38.749459]   PREFETCH window: e0000000-f8ffffff
[   38.749473] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   38.749517] NET: Registered protocol family 2
[   38.778930] IP route cache hash table entries: 32768 (order: 6, 262144 bytes)
[   38.779112] TCP established hash table entries: 131072 (order: 9, 2097152 bytes)
[   38.780602] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   38.781375] TCP: Hash tables configured (established 131072 bind 65536)
[   38.781378] TCP reno registered
[   38.781693] IA32 emulation $Id: sys_ia32.c,v 1.32 2002/03/24 13:02:28 ak Exp $
[   38.781994] audit: initializing netlink socket (disabled)
[   38.782003] audit(1172221991.768:1): initialized
[   38.782132] VFS: Disk quotas dquot_6.5.1
[   38.782150] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   38.782192] Initializing Cryptographic API
[   38.782195] io scheduler noop registered
[   38.782203] io scheduler anticipatory registered
[   38.782211] io scheduler deadline registered
[   38.782225] io scheduler cfq registered (default)
[   38.823725] Real Time Clock Driver v1.12ac
[   38.823758] Linux agpgart interface v0.101 (c) Dave Jones
[   38.823761] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   38.823863] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   38.823968] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   38.824363] 00:0c: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   38.824507] 00:0d: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   38.824619] GSI 16 sharing vector 0xA9 and IRQ 16
[   38.824622] ACPI: PCI Interrupt 0000:00:0e.0[A] -> GSI 19 (level, low) -> IRQ 169
[   38.825306] mice: PS/2 mouse device common for all mice
[   38.825735] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   38.825904] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   38.825907] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   38.826157] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   38.826339] serio: i8042 AUX port at 0x60,0x64 irq 12
[   38.826352] serio: i8042 KBD port at 0x60,0x64 irq 1
[   38.826557] TCP bic registered
[   38.826564] NET: Registered protocol family 1
[   38.826569] NET: Registered protocol family 8
[   38.826571] NET: Registered protocol family 20
[   38.826715] ACPI: (supports S0 S1 S3 S4 S5)
[   38.826751] drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   38.826769] Freeing unused kernel memory: 188k freed
[   38.847858] input: AT Translated Set 2 keyboard as /class/input/input0
[   38.870974] vga16fb: initializing
[   38.870980] vga16fb: mapped to 0xffff8100000a0000
[   39.027264] Console: switching to colour frame buffer device 80x25
[   39.027269] fb0: VGA16 VGA frame buffer device
[   40.065914] Capability LSM initialized
[   40.094231] ACPI Exception (acpi_processor-0693): AE_NOT_FOUND, Processor Device is not present [20060707]
[   40.094236] ACPI: Getting cpuindex for acpiid 0x2
[   40.387883] SCSI subsystem initialized
[   40.391033] libata version 1.20 loaded.
[   40.391853] sata_promise 0000:00:08.0: version 1.04
[   40.391869] GSI 17 sharing vector 0xB1 and IRQ 17
[   40.391872] ACPI: PCI Interrupt 0000:00:08.0[A] -> GSI 18 (level, low) -> IRQ 177
[   40.392032] sata_promise PATA port found
[   40.411921] ata1: SATA max UDMA/133 cmd 0xFFFFC2000003E200 ctl 0xFFFFC2000003E238 bmdma 0x0 irq 177
[   40.411944] ata2: SATA max UDMA/133 cmd 0xFFFFC2000003E280 ctl 0xFFFFC2000003E2B8 bmdma 0x0 irq 177
[   40.411961] ata3: PATA max UDMA/133 cmd 0xFFFFC2000003E300 ctl 0xFFFFC2000003E338 bmdma 0x0 irq 177
[   40.619475] ata1: SATA link up 1.5 Gbps (SStatus 113)
[   40.903268] ata1: dev 0 cfg 49:2f00 82:346b 83:7d01 84:4003 85:3469 86:3c01 87:4003 88:407f
[   40.903271] ata1: dev 0 ATA-6, max UDMA/133, 156301488 sectors: LBA48
[   40.915243] ata1: dev 0 configured for UDMA/133
[   40.915245] scsi0 : sata_promise
[   41.122544] ata2: SATA link up 1.5 Gbps (SStatus 113)
[   41.406337] ata2: dev 0 cfg 49:2f00 82:346b 83:7d01 84:4003 85:3469 86:3c01 87:4003 88:407f
[   41.406340] ata2: dev 0 ATA-6, max UDMA/133, 156301488 sectors: LBA48
[   41.418309] ata2: dev 0 configured for UDMA/133
[   41.418311] scsi1 : sata_promise
[   41.587742] ata3: disabling port
[   41.587745] scsi2 : sata_promise
[   41.587900]   Vendor: ATA       Model: ST380013AS        Rev: 3.18
[   41.587906]   Type:   Direct-Access                      ANSI SCSI revision: 05
[   41.588097]   Vendor: ATA       Model: ST380013AS        Rev: 3.18
[   41.588103]   Type:   Direct-Access                      ANSI SCSI revision: 05
[   41.597221] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[   41.597232] sda: Write Protect is off
[   41.597234] sda: Mode Sense: 00 3a 00 00
[   41.597245] SCSI device sda: drive cache: write back
[   41.597295] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[   41.597302] sda: Write Protect is off
[   41.597303] sda: Mode Sense: 00 3a 00 00
[   41.597313] SCSI device sda: drive cache: write back
[   41.597316]  sda: sda1
[   41.623221] sd 0:0:0:0: Attached scsi disk sda
[   41.623830] SCSI device sdb: 156301488 512-byte hdwr sectors (80026 MB)
[   41.625649] sdb: Write Protect is off
[   41.625653] sdb: Mode Sense: 00 3a 00 00
[   41.626151] SCSI device sdb: drive cache: write back
[   41.626201] SCSI device sdb: 156301488 512-byte hdwr sectors (80026 MB)
[   41.626208] sdb: Write Protect is off
[   41.626210] sdb: Mode Sense: 00 3a 00 00
[   41.626220] SCSI device sdb: drive cache: write back
[   41.626222]  sdb: unknown partition table
[   41.646086] sd 1:0:0:0: Attached scsi disk sdb
[   41.673571] Buffer I/O error on device sda1, logical block 156288256
[   41.673587] Buffer I/O error on device sda1, logical block 156288257
[   41.673591] Buffer I/O error on device sda1, logical block 156288258
[   41.673593] Buffer I/O error on device sda1, logical block 156288259
[   41.673603] Buffer I/O error on device sda1, logical block 156288256
[   41.673606] Buffer I/O error on device sda1, logical block 156288257
[   41.673608] Buffer I/O error on device sda1, logical block 156288258
[   41.673611] Buffer I/O error on device sda1, logical block 156288259
[   41.673625] Buffer I/O error on device sda1, logical block 156288320
[   41.673631] Buffer I/O error on device sda1, logical block 156288320
[   41.744191] sata_via 0000:00:0f.0: version 1.1
[   41.744209] GSI 18 sharing vector 0xB9 and IRQ 18
[   41.744212] ACPI: PCI Interrupt 0000:00:0f.0[B] -> GSI 20 (level, low) -> IRQ 185
[   41.744222] PCI: Via IRQ fixup for 0000:00:0f.0, from 5 to 9
[   41.744252] sata_via 0000:00:0f.0: routed to hard irq line 9
[   41.744278] ata4: SATA max UDMA/133 cmd 0xD400 ctl 0xD002 bmdma 0xC000 irq 185
[   41.744295] ata5: SATA max UDMA/133 cmd 0xC800 ctl 0xC402 bmdma 0xC008 irq 185
[   41.913257] ata4: dev 0 cfg 49:2f00 82:7c6b 83:5b09 84:4673 85:7c69 86:1a21 87:4663 88:407f
[   41.913262] ata4: dev 0 ATA-7, max UDMA/133, 195813072 sectors: LBA
[   41.925234] ata4: dev 0 configured for UDMA/133
[   41.925237] scsi3 : sata_via
[   42.095540] scsi4 : sata_via
[   42.095692]   Vendor: ATA       Model: Maxtor 6L100M0    Rev: BANC
[   42.095699]   Type:   Direct-Access                      ANSI SCSI revision: 05
[   42.095867] SCSI device sdc: 195813072 512-byte hdwr sectors (100256 MB)
[   42.095876] sdc: Write Protect is off
[   42.095878] sdc: Mode Sense: 00 3a 00 00
[   42.095889] SCSI device sdc: drive cache: write back
[   42.095924] SCSI device sdc: 195813072 512-byte hdwr sectors (100256 MB)
[   42.095931] sdc: Write Protect is off
[   42.095932] sdc: Mode Sense: 00 3a 00 00
[   42.095942] SCSI device sdc: drive cache: write back
[   42.095944]  sdc: sdc1 sdc2 < sdc5 >
[   42.131434] sd 3:0:0:0: Attached scsi disk sdc
[   42.303103] VP_IDE: IDE controller at PCI slot 0000:00:0f.1
[   42.303121] ACPI: PCI Interrupt 0000:00:0f.1[A] -> GSI 20 (level, low) -> IRQ 185
[   42.303126] PCI: Via IRQ fixup for 0000:00:0f.1, from 255 to 9
[   42.303151] VP_IDE: chipset revision 6
[   42.303153] VP_IDE: not 100% native mode: will probe irqs later
[   42.303164] VP_IDE: VIA vt8237 (rev 00) IDE UDMA133 controller on pci0000:00:0f.1
[   42.303171]     ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:pio, hdb:pio
[   42.303184]     ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: hdc:DMA, hdd:DMA
[   42.303192] Probing IDE interface ide0...
[   42.871309] Probing IDE interface ide1...
[   43.737791] hdc: SONY DVD-ROM DDU1613, ATAPI CD/DVD-ROM drive
[   44.520344] hdd: SONY DVD RW DW-D22A, ATAPI CD/DVD-ROM drive
[   44.576807] ide1 at 0x170-0x177,0x376 on irq 15
[   44.586936] hdc: ATAPI 40X DVD-ROM drive, 512kB Cache, UDMA(33)
[   44.586943] Uniform CD-ROM driver Revision: 3.20
[   44.589003] hdd: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(66)
[   44.647952] Probing IDE interface ide0...
[   44.694485] ieee1394: Initialized config rom entry `ip1394'
[   44.695623] GSI 19 sharing vector 0xC1 and IRQ 19
[   44.695627] ACPI: PCI Interrupt 0000:00:07.0[A] -> GSI 16 (level, low) -> IRQ 193
[   44.695637] PCI: Via IRQ fixup for 0000:00:07.0, from 11 to 1
[   44.748783] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[193]  MMIO=[f9800000-f98007ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   44.763644] usbcore: registered new driver usbfs
[   44.763664] usbcore: registered new driver hub
[   44.764510] USB Universal Host Controller Interface driver v3.0
[   44.764559] GSI 20 sharing vector 0xC9 and IRQ 20
[   44.764563] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 21 (level, low) -> IRQ 201
[   44.764573] PCI: Via IRQ fixup for 0000:00:10.0, from 11 to 9
[   44.764599] uhci_hcd 0000:00:10.0: UHCI Host Controller
[   44.764723] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[   44.764751] uhci_hcd 0000:00:10.0: irq 201, io base 0x0000d800
[   44.764824] usb usb1: configuration #1 chosen from 1 choice
[   44.764843] hub 1-0:1.0: USB hub found
[   44.764849] hub 1-0:1.0: 2 ports detected
[   44.871807] ACPI: PCI Interrupt 0000:00:10.1[A] -> GSI 21 (level, low) -> IRQ 201
[   44.871814] PCI: Via IRQ fixup for 0000:00:10.1, from 11 to 9
[   44.871839] uhci_hcd 0000:00:10.1: UHCI Host Controller
[   44.871923] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[   44.871945] uhci_hcd 0000:00:10.1: irq 201, io base 0x0000e000
[   44.872079] usb usb2: configuration #1 chosen from 1 choice
[   44.872164] hub 2-0:1.0: USB hub found
[   44.872170] hub 2-0:1.0: 2 ports detected
[   44.979505] ACPI: PCI Interrupt 0000:00:10.2[B] -> GSI 21 (level, low) -> IRQ 201
[   44.979509] PCI: Via IRQ fixup for 0000:00:10.2, from 5 to 9
[   44.979529] uhci_hcd 0000:00:10.2: UHCI Host Controller
[   44.979607] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[   44.979625] uhci_hcd 0000:00:10.2: irq 201, io base 0x0000e400
[   44.979752] usb usb3: configuration #1 chosen from 1 choice
[   44.979838] hub 3-0:1.0: USB hub found
[   44.979843] hub 3-0:1.0: 2 ports detected
[   45.087308] ACPI: PCI Interrupt 0000:00:10.3[B] -> GSI 21 (level, low) -> IRQ 201
[   45.087313] PCI: Via IRQ fixup for 0000:00:10.3, from 5 to 9
[   45.087333] uhci_hcd 0000:00:10.3: UHCI Host Controller
[   45.087415] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[   45.087432] uhci_hcd 0000:00:10.3: irq 201, io base 0x0000e800
[   45.087553] usb usb4: configuration #1 chosen from 1 choice
[   45.087640] hub 4-0:1.0: USB hub found
[   45.087645] hub 4-0:1.0: 2 ports detected
[   45.201385] ACPI: PCI Interrupt 0000:00:10.4[C] -> GSI 21 (level, low) -> IRQ 201
[   45.201392] PCI: Via IRQ fixup for 0000:00:10.4, from 5 to 9
[   45.201539] ehci_hcd 0000:00:10.4: EHCI Host Controller
[   45.201596] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
[   45.201632] ehci_hcd 0000:00:10.4: irq 201, io mem 0xf9e00000
[   45.201638] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   45.201701] usb usb5: configuration #1 chosen from 1 choice
[   45.201720] hub 5-0:1.0: USB hub found
[   45.201726] hub 5-0:1.0: 8 ports detected
[   45.342038] Attempting manual resume
[   45.354430] kjournald starting.  Commit interval 5 seconds
[   45.354440] EXT3-fs: mounted filesystem with ordered data mode.
[   46.029617] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00e0180000c78366]
[   46.412768] usb 5-5: new high speed USB device using ehci_hcd and address 3
[   46.557387] usb 5-5: configuration #1 chosen from 1 choice
[   46.800043] usb 2-1: new low speed USB device using uhci_hcd and address 2
[   46.977778] usb 2-1: configuration #1 chosen from 1 choice
[   53.781233] GSI 21 sharing vector 0xD1 and IRQ 21
[   53.781238] ACPI: PCI Interrupt 0000:00:0a.0[A] -> GSI 17 (level, low) -> IRQ 209
[   53.781383] skge 1.5 addr 0xf9c00000 irq 209 chip Yukon-Lite rev 7
[   53.781525] skge eth0: addr 00:11:d8:37:86:eb
[   53.797610] printk: 22 messages suppressed.
[   53.797614] Buffer I/O error on device sda1, logical block 156288256
[   53.797631] Buffer I/O error on device sda1, logical block 156288257
[   53.865455] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   53.933797] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   54.173210] Floppy drive(s): fd0 is 1.44M
[   54.194848] FDC 0 is a post-1991 82077
[   54.223648] parport: PnPBIOS parport detected.
[   54.223689] parport0: PC-style at 0x378, irq 7 [PCSPP]
[   54.295989] input: PC Speaker as /class/input/input1
[   54.543140] PCI: Enabling device 0000:00:11.6 (0000 -> 0001)
[   54.543149] GSI 22 sharing vector 0xD9 and IRQ 22
[   54.543152] ACPI: PCI Interrupt 0000:00:11.6[C] -> GSI 22 (level, low) -> IRQ 217
[   54.543162] PCI: Via IRQ fixup for 0000:00:11.6, from 0 to 9
[   54.572405] usbcore: registered new driver libusual
[   54.612634] Initializing USB Mass Storage driver...
[   54.613028] scsi5 : SCSI emulation for USB Mass Storage devices
[   54.785396] usbcore: registered new driver usb-storage
[   54.785402] USB Mass Storage support registered.
[   54.785406] usb-storage: device found at 3
[   54.785408] usb-storage: waiting for device to settle before scanning
[   54.855343] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   54.855367] sd 1:0:0:0: Attached scsi generic sg1 type 0
[   54.855391] sd 3:0:0:0: Attached scsi generic sg2 type 0
[   55.016785] logips2pp: Detected unknown logitech mouse model 127
[   55.098837] nvidia: module license 'NVIDIA' taints kernel.
[   55.233669] input: Wacom Graphire2 4x5 as /class/input/input2
[   55.241577] skge eth0: enabling interface
[   55.281746] usbcore: registered new driver wacom
[   55.281751] drivers/usb/input/wacom.c: v1.45:USB Wacom Graphire and Wacom Intuos tablet driver
[   55.288926] usbcore: registered new driver hiddev
[   55.289944] usbcore: registered new driver usbhid
[   55.289949] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   55.296341] PCI: Setting latency timer of device 0000:00:11.6 to 64
[   55.325662] ts: Compaq touchscreen protocol output
[   55.471666] input: ImExPS/2 Logitech Explorer Mouse as /class/input/input3
[   55.799591] ACPI: PCI interrupt for device 0000:00:11.6 disabled
[   55.799598] VIA 82xx Modem: probe of 0000:00:11.6 failed with error -13
[   55.799707] PCI: Enabling device 0000:00:11.5 (0000 -> 0001)
[   55.799712] ACPI: PCI Interrupt 0000:00:11.5[C] -> GSI 22 (level, low) -> IRQ 217
[   55.799717] PCI: Via IRQ fixup for 0000:00:11.5, from 0 to 9
[   55.799865] PCI: Setting latency timer of device 0000:00:11.5 to 64
[   56.289971] NET: Registered protocol family 17
[   56.323132] ACPI: PCI Interrupt 0000:00:0c.0[A] -> GSI 17 (level, low) -> IRQ 209
[   56.369558] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 193
[   56.369727] NVRM: loading NVIDIA Linux x86_64 Kernel Module  1.0-8776  Mon Oct 16 21:53:43 PDT 2006
[   56.907026] skge eth0: Link is up at 100 Mbps, full duplex, flow control none
[   57.451728] lp0: using parport0 (interrupt-driven).
[   57.482124] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[   57.482128] ieee1394: sbp2: Try serialize_io=0 for better performance
[   57.721126] Adding 2996080k swap on /dev/disk/by-uuid/ac05f818-e02e-4b07-81df-928ea09a28b5.  Priority:-1 extents:1 across:2996080k
[   57.831561] EXT3 FS on sdc1, internal journal
[   59.776536] usb-storage: device scan complete
[   59.777522]   Vendor: USB2.0    Model: CardReader CF RW  Rev: 0814
[   59.777529]   Type:   Direct-Access                      ANSI SCSI revision: 00
[   59.778507]   Vendor: USB2.0    Model: CardReader Combo  Rev: 0814
[   59.778513]   Type:   Direct-Access                      ANSI SCSI revision: 00
[   59.782292] sd 5:0:0:0: Attached scsi removable disk sdd
[   59.782333] sd 5:0:0:0: Attached scsi generic sg3 type 0
[   59.785777] sd 5:0:0:1: Attached scsi removable disk sde
[   59.785820] sd 5:0:0:1: Attached scsi generic sg4 type 0
[   60.456769] NET: Registered protocol family 10
[   60.456857] lo: Disabled Privacy Extensions
[   60.456971] IPv6 over IPv4 tunneling driver
[   65.559501] ACPI: Power Button (FF) [PWRF]
[   65.559523] ACPI: Power Button (CM) [PWRB]
[   65.559531] ACPI: Sleep Button (CM) [SLPB]
[   65.631794] ibm_acpi: ec object not found
[   65.658075] pcc_acpi: loading...
[   66.025708] powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (version 1.60.2)
[   66.026698] powernow-k8: BIOS error - no PSB or ACPI _PSS objects
[   69.492357] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[   69.492370] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   69.492438] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[   70.548071] eth0: no IPv6 routers present
[   75.283984] printk: 30 messages suppressed.
[   75.283990] Buffer I/O error on device sda1, logical block 156288256
[   75.284294] Buffer I/O error on device sda1, logical block 156288257
[   75.284298] Buffer I/O error on device sda1, logical block 156288258
[   75.284301] Buffer I/O error on device sda1, logical block 156288259
[   76.222467] Bluetooth: Core ver 2.8
[   76.222472] NET: Registered protocol family 31
[   76.222473] Bluetooth: HCI device and connection manager initialized
[   76.222487] Bluetooth: HCI socket layer initialized
[   76.283418] Bluetooth: L2CAP ver 2.8
[   76.283422] Bluetooth: L2CAP socket layer initialized
[   76.320558] Bluetooth: RFCOMM socket layer initialized
[   76.320572] Bluetooth: RFCOMM TTY layer initialized
[   76.320574] Bluetooth: RFCOMM ver 1.7
[  414.474348] NTFS driver 2.1.27 [Flags: R/O MODULE].
[  414.521038] printk: 26 messages suppressed.
[  414.521044] NTFS-fs error (device sda1): ntfs_attr_find(): Inode is corrupt.  Run chkdsk.
[  414.521048] NTFS-fs error (device sda1): ntfs_read_inode_mount(): Failed to lookup attribute list attribute. You should run chkdsk.
[  414.521051] NTFS-fs error (device sda1): ntfs_read_inode_mount(): Failed. Marking inode as bad.
[  414.521055] NTFS-fs error (device sda1): ntfs_fill_super(): Failed to load essential metadata.
firekat@firekat-desktop:~$ 
```

I did see on another thread that updating a edgy broken dmraid would fix the problem.  It referenced this [https://launchpad.net/ubuntu/+source/dmraid/+bug/54246]("https://launchpad.net/ubuntu/+source/dmraid/+bug/54246")

The thing is that this was built for the i386 and I am on a AMD machine.  I don't know how I would source an updated dmraid compiled for the AMD.

Thanx!

---

