---
title: "Can't boot into my Ubuntu 7.10"
date: 2008-04-01
forum: General Help
---

### Post by dukemaru on 2008-04-01
This is a bit of a complicated senario.
First one of my hard drives crashed, so I had to reinstall everything over to a new hd.
As I run both 32 bit Gutsy and 64 bit + XP a certain series of odd events occured that I didn't forsee.
First I installed XP. Then I installed 32bit ubuntu and finally 64 bit ubuntu. As my ubuntu's both share the same home folder the FSTAB settings for my 32bit are not accurate now so I can't boot into that account with a proper xorg setup. Anyway, more on that later.

After installing my ubuntus, I went back into xp and installed all the drivers and so on and so forth but unfortunately, something went wrong while installing a driver and I got the bluescreen of death. After that XP would no longer boot, so I had to reinstall XP, which aside from a lot of time consumption was no problem as far as I was concerned because I can always reinstall grub later from a live cd and I was on vacation.

The problem is this, after I installed xp and when back and reinstalled grub, my 64 bit ubuntu would no longer complete a boot up. It was fine on the grub menu and would start the boot process and get most of the way through it but then it just stops and pauses on a blinking cursor...

So now for some odd reason my 64 bit ubuntu is out of sorts. It does the same thing when I boot into recovery, so i can't  get to a command line.

Now, there is a fairly quick and simple solution to this which is to reinstall my 64 bit gutsy and that would at least get it up and going and I can then easily go in and update my fstab for my 32bit gutsy from within 64 bit ubuntu, HOWEVER, and here is where things start looking really bad. When I go into my live cd and look at the partition editor it shows my drive as completely raw and unpartitioned - it doesn't see my partitions at all, so if i do attempt to install gutsy again, it will overwrite my other two working OS (XP and 32bit gutsy).

So here are my questions:
1. Is there anyway I can repair my 64bit Ubuntu without having to reinstall it?
2. How can I get the partition editor to recognize my partitions?
3. Should the above all fail to pan out properly, I would at least like to be able to get into my 32bit properly, so I will need to get my fstab settings sorted out, how do I go about doing that when I can't get into 64bit ubuntu right now?

I sure don't want to have to reinstall all three operating systems from scratch and waste another whole day or more :(

---

### Post by cdenley on 2008-04-01
What is the output of these commands while running the livecd?
```

sudo dmesg -c
sudo fdisk -l
sudo gparted
dmesg

```

Grub settings are in the file /boot/grub/menu.lst on the partition you last installed grub from.

---

### Post by forrestcupp on 2008-04-01
So, you have already tried restoring GRUB, right?  And you can't even get to recovery mode?

If you end up having to reinstall, it sounds to me like 32-bit is more important to you than 64-bit.  If I were you, I would install 64-bit Ubuntu in a virtual machine to make things a lot simpler.

---

### Post by dukemaru on 2008-04-01
Thanks for the reply.
I will start up the live disk and check out what the output is for those commands.
These color schemes sure do make it tough for color-blind people to read the help forums.
The font and the background almost appear as one color...

P.S. I reloaded grub to my 32 bit ubuntu partition because I couldn't boot into my 64bit, so the menu is not on my last installed partition :)

---

### Post by cdenley on 2008-04-01
Yeah, kind of a stupid april fool's joke. The theme can be changed with the select box on the bottom left.

---

### Post by dukemaru on 2008-04-01
T 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] Command line: BOOT_IMAGE=/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000005ffb0000 (usable)
[    0.000000]  BIOS-e820: 000000005ffb0000 - 000000005ffc0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000005ffc0000 - 000000005fff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000005fff0000 - 0000000060000000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff780000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 393136) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xFFFF8100000FA7C0 checksum 0
[    0.000000] ACPI: RSDP 000FA7C0, 0021 (r2 ACPIAM)
[    0.000000] ACPI: XSDT 5FFB0100, 003C (r1 A M I  OEMXSDT   6000530 MSFT       97)
[    0.000000] ACPI: FACP 5FFB0290, 00F4 (r3 A M I  OEMFACP   6000530 MSFT       97)
[    0.000000] ACPI: DSDT 5FFB03F0, 3A3E (r1  A0036 A0036001        1 MSFT  100000D)
[    0.000000] ACPI: FACS 5FFC0000, 0040
[    0.000000] ACPI: APIC 5FFB0390, 0052 (r1 A M I  OEMAPIC   6000530 MSFT       97)
[    0.000000] ACPI: OEMB 5FFC0040, 003F (r1 A M I  OEMBIOS   6000530 MSFT       97)
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000005ffb0000
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 393136) 1 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-000000005ffb0000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      159
[    0.000000]     0:      256 ->   393136
[    0.000000] On node 0 totalpages: 393039
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1126 pages reserved
[    0.000000]   DMA zone: 2817 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 5318 pages used for memmap
[    0.000000]   DMA32 zone: 383722 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled)
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e4000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e4000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 70000000 (gap: 60000000:9f780000)
[    0.000000] SMP: Allowing 2 CPUs, 1 hotplug CPUs
[    0.000000] PERCPU: Allocating 34696 bytes of per cpu data
[    0.000000] Built 1 zonelists.  Total pages: 386539
[    0.000000] Kernel command line: BOOT_IMAGE=/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Extended CMOS year: 2000
[   30.253687] time.c: Detected 2002.601 MHz processor.
[   30.255613] Console: colour VGA+ 80x25
[   30.255628] Checking aperture...
[   30.255631] CPU 0: aperture @ d8000000 size 64 MB
[   30.270158] Memory: 1538252k/1572544k available (2274k kernel code, 33904k reserved, 1181k data, 296k init)
[   30.270206] SLUB: Genslabs=23, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   30.347628] Calibrating delay using timer specific routine.. 4009.77 BogoMIPS (lpj=8019552)
[   30.347658] Security Framework v1.0.0 initialized
[   30.347665] SELinux:  Disabled at boot.
[   30.347817] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[   30.349293] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   30.350033] Mount-cache hash table entries: 256
[   30.350157] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   30.350159] CPU: L2 Cache: 512K (64 bytes/line)
[   30.350162] CPU 0/0 -> Node 0
[   30.350177] SMP alternatives: switching to UP code
[   30.350407] Early unpacking initramfs... done
[   30.657837] ACPI: Core revision 20070126
[   30.657885] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   30.700700] Using local APIC timer interrupts.
[   30.750605] result 12516252
[   30.750607] Detected 12.516 MHz APIC timer.
[   30.751412] Brought up 1 CPUs
[   30.751750] NET: Registered protocol family 16
[   30.751818] ACPI: bus type pci registered
[   30.751824] PCI: Using configuration type 1
[   30.753530] ACPI: EC: Look up EC in DSDT
[   30.756890] ACPI: Interpreter enabled
[   30.756893] ACPI: (supports S0 S1 S3 S4 S5)
[   30.756908] ACPI: Using IOAPIC for interrupt routing
[   30.763275] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   30.763284] PCI: Probing PCI hardware (bus 00)
[   30.764135] PCI: enabled onboard AC97/MC97 devices
[   30.764363] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   30.772915] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 *11 14 15)
[   30.773001] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *10 11 14 15)
[   30.773084] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 7 10 11 14 15)
[   30.773166] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[   30.773253] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[   30.773336] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[   30.773419] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[   30.773501] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[   30.773567] Linux Plug and Play Support v0.97 (c) Adam Belay
[   30.773576] pnp: PnP ACPI init
[   30.773587] ACPI: bus type pnp registered
[   30.776943] pnp: PnP ACPI: found 14 devices
[   30.776946] ACPI: ACPI bus type pnp unregistered
[   30.776994] PCI: Using ACPI for IRQ routing
[   30.776996] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   30.777004] PCI: Cannot allocate resource region 0 of device 0000:00:00.0
[   30.777149] NET: Registered protocol family 8
[   30.777151] NET: Registered protocol family 20
[   30.777205] agpgart: Detected AGP bridge 0
[   30.780177] agpgart: AGP aperture is 64M @ 0xd8000000
[   30.780252] pnp: 00:08: ioport range 0x680-0x6ff has been reserved
[   30.780255] pnp: 00:08: ioport range 0x290-0x297 has been reserved
[   30.780265] pnp: 00:0a: iomem range 0xfec00000-0xfec00fff has been reserved
[   30.780268] pnp: 00:0a: iomem range 0xfee00000-0xfee00fff could not be reserved
[   30.780271] pnp: 00:0a: iomem range 0xfff80000-0xffffffff could not be reserved
[   30.780277] pnp: 00:0d: iomem range 0x0-0x9ffff could not be reserved
[   30.780280] pnp: 00:0d: iomem range 0xc0000-0xdffff has been reserved
[   30.780283] pnp: 00:0d: iomem range 0xe0000-0xfffff could not be reserved
[   30.780286] pnp: 00:0d: iomem range 0x100000-0x5ffeffff could not be reserved
[   30.780521] PCI: Bridge: 0000:00:01.0
[   30.780523]   IO window: disabled.
[   30.780527]   MEM window: f9f00000-fbffffff
[   30.780530]   PREFETCH window: e0000000-f8ffffff
[   30.780545] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   30.780580] NET: Registered protocol family 2
[   30.783351] Time: tsc clocksource has been installed.
[   30.819394] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[   30.820018] TCP established hash table entries: 262144 (order: 10, 6291456 bytes)
[   30.824684] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   30.825415] TCP: Hash tables configured (established 262144 bind 65536)
[   30.825419] TCP reno registered
[   30.835448] checking if image is initramfs... it is
[   31.436437] Freeing initrd memory: 7706k freed
[   31.441763] audit: initializing netlink socket (disabled)
[   31.441774] audit(1207092681.144:1): initialized
[   31.443564] VFS: Disk quotas dquot_6.5.1
[   31.443610] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   31.443692] io scheduler noop registered
[   31.443694] io scheduler anticipatory registered
[   31.443696] io scheduler deadline registered
[   31.443777] io scheduler cfq registered (default)
[   31.443788] PCI: VIA PCI bridge detected. Disabling DAC.
[   31.475005] Boot video device is 0000:01:00.0
[   31.495655] Real Time Clock Driver v1.12ac
[   31.495730] Linux agpgart interface v0.102 (c) Dave Jones
[   31.495733] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   31.495819] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   31.495949] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   31.496383] 00:0b: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   31.496583] 00:0c: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   31.497168] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   31.497354] input: Macintosh mouse button emulation as /class/input/input0
[   31.497412] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   31.497415] PNP: PS/2 controller doesn't have AUX irq; using default 12
[   31.497796] serio: i8042 KBD port at 0x60,0x64 irq 1
[   31.497800] serio: i8042 AUX port at 0x60,0x64 irq 12
[   31.497933] mice: PS/2 mouse device common for all mice
[   31.498108] TCP cubic registered
[   31.498168] NET: Registered protocol family 1
[   31.498378] /build/buildd/linux-source-2.6.22-2.6.22/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   31.498385] Freeing unused kernel memory: 296k freed
[   31.559710] input: AT Translated Set 2 keyboard as /class/input/input1
[   32.664388] AppArmor: AppArmor initialized<5>audit(1207092682.368:2):  type=1505 info="AppArmor initialized" pid=1212
[   32.718366] fuse init (API version 7.8)
[   32.722840] Failure registering capabilities with primary security module.
[   32.737583] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   33.294407] ACPI: PCI Interrupt 0000:00:07.0[A] -> GSI 16 (level, low) -> IRQ 16
[   33.351946] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[16]  MMIO=[f9400000-f94007ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   33.357029] ACPI: PCI Interrupt 0000:00:0c.0[A] -> GSI 17 (level, low) -> IRQ 17
[   33.410622] ohci1394: fw-host1: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[f9c00000-f9c007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[   33.439718] SCSI subsystem initialized
[   33.479560] libata version 2.21 loaded.
[   33.480615] sata_promise 0000:00:08.0: version 2.07
[   33.480635] ACPI: PCI Interrupt 0000:00:08.0[A] -> GSI 18 (level, low) -> IRQ 18
[   33.480737] sata_promise 0000:00:08.0: PATA port found
[   33.498855] usbcore: registered new interface driver usbfs
[   33.498879] usbcore: registered new interface driver hub
[   33.506355] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   33.506361] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   33.508483] usbcore: registered new device driver usb
[   33.509122] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   33.509138] scsi0 : sata_promise
[   33.509183] scsi1 : sata_promise
[   33.509212] scsi2 : sata_promise
[   33.509236] ata1: SATA max UDMA/133 cmd 0xffffc20000326200 ctl 0xffffc20000326238 bmdma 0x0000000000000000 irq 18
[   33.509242] ata2: SATA max UDMA/133 cmd 0xffffc20000326280 ctl 0xffffc200003262b8 bmdma 0x0000000000000000 irq 18
[   33.509246] ata3: PATA max UDMA/133 cmd 0xffffc20000326300 ctl 0xffffc20000326338 bmdma 0x0000000000000000 irq 18
[   33.515750] USB Universal Host Controller Interface driver v3.0
[   33.623539] Floppy drive(s): fd0 is 1.44M
[   33.689574] FDC 0 is a post-1991 82077
[   33.925322] end_request: I/O error, dev fd0, sector 0
[   33.977296] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   34.001807] ata1.00: ATA-6: HDS722525VLSA80, V36OA63A, max UDMA/100
[   34.001810] ata1.00: 488397168 sectors, multi 0: LBA48 
[   34.037788] ata1.00: configured for UDMA/100
[   34.353028] ata2: SATA link down (SStatus 0 SControl 300)
[   34.509038] scsi 0:0:0:0: Direct-Access     ATA      HDS722525VLSA80  V36O PQ: 0 ANSI: 5
[   34.509546] ACPI: PCI Interrupt 0000:00:0a.0[A] -> GSI 17 (level, low) -> IRQ 17
[   34.509558] PCI: Disallowing DAC for device 0000:00:0a.0
[   34.509667] skge 1.11 addr 0xf9800000 irq 17 chip Yukon-Lite rev 7
[   34.510008] skge eth0: addr 00:11:2f:f6:61:c2
[   34.510129] VP_IDE: IDE controller at PCI slot 0000:00:0f.1
[   34.510146] ACPI: PCI Interrupt 0000:00:0f.1[A] -> GSI 20 (level, low) -> IRQ 20
[   34.510157] VP_IDE: chipset revision 6
[   34.510159] VP_IDE: not 100% native mode: will probe irqs later
[   34.510169] VP_IDE: VIA vt8237 (rev 00) IDE UDMA133 controller on pci0000:00:0f.1
[   34.510176]     ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:pio, hdb:pio
[   34.510185]     ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: hdc:DMA, hdd:pio
[   34.510191] Probing IDE interface ide0...
[   34.529128] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   34.529140] sd 0:0:0:0: [sda] Write Protect is off
[   34.529142] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   34.529154] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   34.529203] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   34.529210] sd 0:0:0:0: [sda] Write Protect is off
[   34.529212] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   34.529223] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   34.529228]  sda: sda1 sda2 < sda5 sda6 sda7 > sda3 sda4
[   34.575081] sd 0:0:0:0: [sda] Attached SCSI disk
[   34.578667] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   34.632933] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00e0180000b9bab1]
[   34.904748] ieee1394: Host added: ID:BUS[1-00:1023]  GUID[00c0d000f7108e7d]
[   34.972635] end_request: I/O error, dev fd0, sector 0
[   35.080566] Probing IDE interface ide1...
[   35.345921] kjournald starting.  Commit interval 5 seconds
[   35.345931] EXT3-fs: mounted filesystem with ordered data mode.
[   35.372072] kjournald starting.  Commit interval 5 seconds
[   35.372082] EXT3-fs: mounted filesystem with ordered data mode.
[   35.390051] kjournald starting.  Commit interval 5 seconds
[   35.390061] EXT3-fs: mounted filesystem with ordered data mode.
[   35.960060] hdc: Optiarc DVD RW AD-7173A, ATAPI CD/DVD-ROM drive
[   36.427680] end_request: I/O error, dev fd0, sector 0
[   36.632177] ide1 at 0x170-0x177,0x376 on irq 15
[   36.635541] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 16 (level, low) -> IRQ 16
[   36.635676] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[   36.636049] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 1
[   36.636063] ohci_hcd 0000:00:0b.0: irq 16, io mem 0xf9900000
[   36.645780] hdc: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
[   36.645788] Uniform CD-ROM driver Revision: 3.20
[   37.207572] usb usb1: configuration #1 chosen from 1 choice
[   37.207714] hub 1-0:1.0: USB hub found
[   37.207722] hub 1-0:1.0: 3 ports detected
[   37.352161] kjournald starting.  Commit interval 5 seconds
[   37.352171] EXT3-fs: mounted filesystem with ordered data mode.
[   37.378357] kjournald starting.  Commit interval 5 seconds
[   37.378367] EXT3-fs: mounted filesystem with ordered data mode.
[   37.396340] kjournald starting.  Commit interval 5 seconds
[   37.396350] EXT3-fs: mounted filesystem with ordered data mode.
[   37.727256] ACPI: PCI Interrupt 0000:00:0b.1[B] -> GSI 17 (level, low) -> IRQ 17
[   37.727366] ohci_hcd 0000:00:0b.1: OHCI Host Controller
[   37.727637] ohci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 2
[   37.727651] ohci_hcd 0000:00:0b.1: irq 17, io mem 0xf9a00000
[   38.298684] usb usb2: configuration #1 chosen from 1 choice
[   38.298835] hub 2-0:1.0: USB hub found
[   38.298843] hub 2-0:1.0: 2 ports detected
[   38.434361] end_request: I/O error, dev fd0, sector 0
[   38.538280] usb 1-1: new full speed USB device using ohci_hcd and address 2
[   38.734182] usb 1-1: configuration #1 chosen from 1 choice
[   38.737121] hub 1-1:1.0: USB hub found
[   38.740095] hub 1-1:1.0: 4 ports detected
[   38.818560] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 21 (level, low) -> IRQ 21
[   38.818572] uhci_hcd 0000:00:10.0: UHCI Host Controller
[   38.818730] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 3
[   38.818759] uhci_hcd 0000:00:10.0: irq 21, io base 0x0000d400
[   38.819126] usb usb3: configuration #1 chosen from 1 choice
[   38.819298] hub 3-0:1.0: USB hub found
[   38.819305] hub 3-0:1.0: 2 ports detected
[   38.926135] ACPI: PCI Interrupt 0000:00:10.1[A] -> GSI 21 (level, low) -> IRQ 21
[   38.926147] uhci_hcd 0000:00:10.1: UHCI Host Controller
[   38.926169] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 4
[   38.926189] uhci_hcd 0000:00:10.1: irq 21, io base 0x0000d800
[   38.926285] usb usb4: configuration #1 chosen from 1 choice
[   38.926314] hub 4-0:1.0: USB hub found
[   38.926321] hub 4-0:1.0: 2 ports detected
[   39.004285] ISO 9660 Extensions: Microsoft Joliet Level 3
[   39.034063] ACPI: PCI Interrupt 0000:00:10.2[B] -> GSI 21 (level, low) -> IRQ 21
[   39.034076] uhci_hcd 0000:00:10.2: UHCI Host Controller
[   39.034098] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 5
[   39.034119] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000e000
[   39.034213] usb usb5: configuration #1 chosen from 1 choice
[   39.034239] hub 5-0:1.0: USB hub found
[   39.034246] hub 5-0:1.0: 2 ports detected
[   39.045232] ISO 9660 Extensions: RRIP_1991A
[   39.141999] ACPI: PCI Interrupt 0000:00:10.3[B] -> GSI 21 (level, low) -> IRQ 21
[   39.142011] uhci_hcd 0000:00:10.3: UHCI Host Controller
[   39.142034] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 6
[   39.142055] uhci_hcd 0000:00:10.3: irq 21, io base 0x0000e400
[   39.142158] usb usb6: configuration #1 chosen from 1 choice
[   39.142182] hub 6-0:1.0: USB hub found
[   39.142189] hub 6-0:1.0: 2 ports detected
[   39.165867] usb 1-3: new low speed USB device using ohci_hcd and address 3
[   39.249988] ACPI: PCI Interrupt 0000:00:0b.2[C] -> GSI 18 (level, low) -> IRQ 18
[   39.250108] ehci_hcd 0000:00:0b.2: EHCI Host Controller
[   39.250159] ehci_hcd 0000:00:0b.2: new USB bus registered, assigned bus number 7
[   39.277822] ehci_hcd 0000:00:0b.2: irq 18, io mem 0xf9b00000
[   39.329771] ehci_hcd 0000:00:0b.2: USB 2.0 started, EHCI 0.95, driver 10 Dec 2004
[   39.329877] usb usb7: configuration #1 chosen from 1 choice
[   39.329908] hub 7-0:1.0: USB hub found
[   39.329916] hub 7-0:1.0: 5 ports detected
[   39.387255] Registering unionfs 1.4
[   39.387258] unionfs: debugging is not enabled
[   39.392576] loop: module loaded
[   39.433795] ACPI: PCI Interrupt 0000:00:10.4[C] -> GSI 21 (level, low) -> IRQ 21
[   39.433898] ehci_hcd 0000:00:10.4: EHCI Host Controller
[   39.433955] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 8
[   39.433995] ehci_hcd 0000:00:10.4: irq 21, io mem 0xf9e00000
[   39.434002] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   39.434098] usb usb8: configuration #1 chosen from 1 choice
[   39.434123] hub 8-0:1.0: USB hub found
[   39.434129] hub 8-0:1.0: 8 ports detected
[   39.541790] sata_via 0000:00:0f.0: version 2.2
[   39.541805] ACPI: PCI Interrupt 0000:00:0f.0[B] -> GSI 20 (level, low) -> IRQ 20
[   39.541840] sata_via 0000:00:0f.0: routed to hard irq line 10
[   39.541891] scsi3 : sata_via
[   39.541933] scsi4 : sata_via
[   39.541955] ata4: SATA max UDMA/133 cmd 0x000000000001d000 ctl 0x000000000001c802 bmdma 0x000000000001b800 irq 20
[   39.541958] ata5: SATA max UDMA/133 cmd 0x000000000001c400 ctl 0x000000000001c002 bmdma 0x000000000001b808 irq 20
[   39.745485] usb 1-3: device not accepting address 3, error -62
[   39.749480] ata4: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[   39.809453] usb 1-1: USB disconnect, address 2
[   39.965339] ata5: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[   40.319846] squashfs: version 3.2-UBUNTU (2007/07/26) Phillip Lougher
[   41.340433] usb 7-1: new high speed USB device using ehci_hcd and address 2
[   41.481654] usb 7-1: configuration #1 chosen from 1 choice
[   41.481843] hub 7-1:1.0: USB hub found
[   41.482006] hub 7-1:1.0: 4 ports detected
[   42.259826] usb 1-3: new low speed USB device using ohci_hcd and address 5
[   42.482781] usb 1-3: configuration #1 chosen from 1 choice
[   42.727508] usb 6-2: new low speed USB device using uhci_hcd and address 2
[   42.911978] usb 6-2: configuration #1 chosen from 1 choice
[   42.915596] usbcore: registered new interface driver hiddev
[   42.925501] input: I-O DATA DEVICE,INC. USB-IRUNIT2 as /class/input/input2
[   42.925507] input: USB HID v1.10 Device [I-O DATA DEVICE,INC. USB-IRUNIT2] on usb-0000:00:0b.0-3
[   42.941004] input: Logitech USB-PS/2 Optical Mouse as /class/input/input3
[   42.941019] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:10.3-2
[   42.941029] usbcore: registered new interface driver usbhid
[   42.941032] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   97.960505] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   98.048735] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   99.469849] Linux video capture interface: v2.00
[   99.664042] parport_pc 00:07: reported by Plug and Play ACPI
[   99.664083] parport0: PC-style at 0x378, irq 7 [PCSPP]
[   99.709920] input: PC Speaker as /class/input/input4
[   99.860544] ivtv:  ==================== START INIT IVTV ====================
[   99.860548] ivtv:  version 1.0.0 (2.6.22-14-generic SMP mod_unload ) loading
[   99.860646] ivtv0: Autodetected I/O Data GV-MVP/RX, GV-MVP/RX2W (dual tuner) card (cx23416 based)
[   99.860705] ACPI: PCI Interrupt 0000:00:0d.0[A] -> GSI 18 (level, low) -> IRQ 18
[   99.935316] usbcore: registered new interface driver xpad
[   99.935321] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/joystick/xpad.c: driver for Xbox controllers v0.1.6
[  100.663916] ivtv0: loaded v4l-cx2341x-enc.fw firmware (-139636550660800 bytes)
[  100.881025] ivtv0: Encoder revision: 0x02050032
[  100.881028] ivtv0: Recommended firmware version is 0x02060039.
[  100.897489] tuner 0-0043: chip found @ 0x86 (ivtv i2c driver #0)
[  100.897516] tda9887 0-0043: tda988[5/6/7] found @ 0x43 (tuner)
[  100.901129] tuner 0-0060: All bytes are equal. It is not a TEA5767
[  100.901132] tuner 0-0060: chip found @ 0xc0 (ivtv i2c driver #0)
[  101.026930] saa7115 0-0021: saa7115 found (1f7115d0e100000) @ 0x42 (ivtv i2c driver #0)
[  101.171437] upd64031a 0-0012: chip found @ 0x24 (ivtv i2c driver #0)
[  101.192178] upd64083 0-005c: chip found @ 0xb8 (ivtv i2c driver #0)
[  101.225724] tvaudio 0-005b: tda9850 found @ 0xb6 (ivtv i2c driver #0)
[  101.259487] wm8739 0-001a: chip found @ 0x34 (ivtv i2c driver #0)
[  101.267942] tuner 0-0060: type set to 46 (Panasonic VP27s/ENGE4324D)
[  101.501807] ivtv0: Registered device video0 for encoder MPEG (4 MB)
[  101.501953] ivtv0: Registered device video32 for encoder YUV (2 MB)
[  101.502115] ivtv0: Registered device vbi0 for encoder VBI (1 MB)
[  101.502184] ivtv0: Registered device video24 for encoder PCM audio (1 MB)
[  101.548550] ivtv0: Initialized I/O Data GV-MVP/RX, GV-MVP/RX2W (dual tuner), card #0
[  101.548592] PCI: Enabling device 0000:00:11.6 (0000 -> 0001)
[  101.548601] ACPI: PCI Interrupt 0000:00:11.6[C] -> GSI 22 (level, low) -> IRQ 22
[  102.300077] PCI: Setting latency timer of device 0000:00:11.6 to 64
[  102.803932] ACPI: PCI interrupt for device 0000:00:11.6 disabled
[  102.803938] VIA 82xx Modem: probe of 0000:00:11.6 failed with error -13
[  102.804121] ivtv:  ====================  END INIT IVTV  ====================
[  102.804964] ACPI: PCI Interrupt 0000:00:11.5[C] -> GSI 22 (level, low) -> IRQ 22
[  102.805101] PCI: Setting latency timer of device 0000:00:11.5 to 64
[  104.775518] Adding 2931820k swap on /dev/sda3.  Priority:-1 extents:1 across:2931820k
[  106.731502] No dock devices found.
[  107.025103] input: Power Button (FF) as /class/input/input5
[  107.028966] ACPI: Power Button (FF) [PWRF]
[  107.057396] input: Power Button (CM) as /class/input/input6
[  107.061217] ACPI: Power Button (CM) [PWRB]
[  107.089664] input: Sleep Button (CM) as /class/input/input7
[  107.093507] ACPI: Sleep Button (CM) [SLPB]
[  107.958303] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3200+ processors (version 2.00.00)
[  107.958337] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0x6
[  107.958340] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x8
[  107.958342] powernow-k8:    2 : fid 0x2 (1000 MHz), vid 0x12
[  113.441878] skge eth0: enabling interface
[  113.455957] lp0: using parport0 (interrupt-driven).
[  113.661316] ppdev: user-space parallel port driver
[  115.127518] skge eth0: Link is up at 100 Mbps, full duplex, flow control none
[  116.268904] Failure registering capabilities with primary security module.
[  116.722804] Marking TSC unstable due to cpufreq changes
[  116.725178] Time: acpi_pm clocksource has been installed.
[  117.107926] Bluetooth: Core ver 2.11
[  117.108019] NET: Registered protocol family 31
[  117.108021] Bluetooth: HCI device and connection manager initialized
[  117.108024] Bluetooth: HCI socket layer initialized
[  117.180153] Bluetooth: L2CAP ver 2.8
[  117.180157] Bluetooth: L2CAP socket layer initialized
[  117.511807] Bluetooth: RFCOMM socket layer initialized
[  117.511879] Bluetooth: RFCOMM TTY layer initialized
[  117.511881] Bluetooth: RFCOMM ver 1.8
[  121.034121] NET: Registered protocol family 17
[  124.153930] NET: Registered protocol family 10
[  124.154060] lo: Disabled Privacy Extensions

---

### Post by dukemaru on 2008-04-01
Ah! This FDISK command will sure help me get the fstab sorted out!  With gparted not recognizing it, I could not find out what drives belonged to which uuids.

ubuntu@ubuntu:~$ sudo fdisk -l
omitting empty partition (5)

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x29872986

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4462    35840983+   7  HPFS/NTFS
/dev/sda2            4463       15562    89160750    5  Extended
/dev/sda3            5472        5836     2931831   82  Linux swap / Solaris
/dev/sda4           15563       30401   119194267+   7  HPFS/NTFS
/dev/sda5            4463        5471     8104729+  83  Linux
/dev/sda6            5837        7052     9767488+  83  Linux
/dev/sda7            7053       15562    68356543+  83  Linux

---

### Post by dukemaru on 2008-04-01
ubuntu@ubuntu:~$ sudo gparted
shows unallocated space only
no partitions showing...

---

### Post by dukemaru on 2008-04-01
> **cdenley said:**
> What is the output of these commands while running the livecd?
```

sudo dmesg -c
sudo fdisk -l
sudo gparted
dmesg

```

Grub settings are in the file /boot/grub/menu.lst on the partition you last installed grub from.

Well, I have them both installed so I can get a taste for which I prefer. I have been running 32bit on my 64 bit comp for ages now, and I wanted to see if the 64 bit now had all the software I needed to make use of it. BUT, I see your point. I may as well test it out as a virtual machine first...

However, with this partition table problem I have...unless thats fixable, I am going to have to reinstall every damned thing, which I am really not wanting to do. The reason I say that is that this is going to become a problem the next time I want to partition this drive - like when 8.04 comes out.... I would rather deal with this problem now than when I have my xp system fully loaded.

---

### Post by dukemaru on 2008-04-01
damn, that quote was supposed to be for Forrestcup. Its getting awful late here and I am getting punchy. I had better get some sleep. I will log back on in the morning. Thanks for the help!

---

### Post by cdenley on 2008-04-01
> **dukemaru said:**
> ubuntu@ubuntu:~$ sudo gparted
shows unallocated space only
no partitions showing...
Is that the actual terminal output?

Maybe if you re-write the partition table with fdisk, gparted will suddenly read it correctly.
```

sudo fdisk /dev/sda

```
enter the command "w" to write the partiiton table.

Maybe that "empty" partition is what gparted doesn't like. If it is actually empty, you could try deleting it with fdisk.

---

### Post by forrestcupp on 2008-04-01
If GParted only shows unallocated space, you may be screwed.

Don't worry about 8.04 coming out.  You should be able to just upgrade Gutsy without messing with a new install.  I'm trying out the upgrade for the beta now.

Edit:
I just upgraded Gutsy with very little effort.  I'm not suggesting you go ahead and upgrade to the beta.  I'm just encouraging you that when it is released, it won't be that hard to do an upgrade rather than a clean install.

---

### Post by dukemaru on 2008-04-01
I have found from past experience upgrading that somethings don't get upgraded through the process and I would like to have a complete Heron. I has always seemed to me better to just do a full install, which I have ended up doing in each case after an upgrade anyway in order to get the full system upgraded. 

I will try the writing the partition table, but I am a little hesitant because by your post it sounds like you are guessing at this one as a fix...

cdenly, have you ever run sudo gparted?
There is no terminal output because what it does is run gparted and a gui gparted shows up (the same as if you went to administration tab and clicked on Partition Editor.

I'm getting worried that we're just guessing here. Isn't there anyone who has experience with this kind of problem? Have I stumbled upon new territory here?

---

### Post by dukemaru on 2008-04-01
[QUOTE=forrestcupp;4630320]If GParted only shows unallocated space, you may be screwed.

Here is the thing that's killing me: Fdisk shows the partition table perfectly. Why doesn't gparted show it? I even ran QTparted to see what it would show, and it too doesn't recognize any of my partitions...ODD!

---

### Post by dukemaru on 2008-04-01
Damn, looks like this may well be related to [https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/54211](https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/54211)

This is a long outstanding bug, and if this is my problem...

---

### Post by dukemaru on 2008-04-01
I've been trying to my xorg working properly.
It has me at a tiny resolution and also my mouse is not working at all.

I went to the recovery console and typed in "dpkg-reconfigure -phigh xserver-xorg"
"Xorg not installed" was the output...

Any help on this one?

---

### Post by dukemaru on 2008-04-02
Well, I have made some progress...
I went into XP and just deleted my ubuntu partitions. Since I did not have so much installed on them anyway, it should be easy enough to reinstall. Anyway, since xp could recognize my partitions, I used xp to delete them.

I then loaded up the ubuntu live CD and that recognised the windows partition. So it must have been that one of my ubuntu partitions was messed up on some way. Apparently the Gparted and QTparted wont recognize a partition table if there is any oddity. This is a know bug in the upstream that has been around for several years it looks like...not holding my breath to see it fixed any time soon.

Anyway from here, I guess I will just have to reinstall Ubuntu and go on my merry way. 
Thanks to those of you who replied to my questions.

---

