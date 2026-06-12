---
title: "Long boot time"
date: 2007-05-07
forum: General Help
---

### Post by redraider0807 on 2007-05-07
I just installed Feisty, and it takes forever to boot up, I tried commenting out the extras in the networking interfaces but that didn't do anything.  Here's my bootchart because I have no idea how to read it, I'm fairly new to linux and have been using this more then windows but when it takes 145 seconds to boot up thats a pain in the ***.  Thanks for any help you can give

---

### Post by ld50 on 2007-05-07
Post the contents of dmesg, use, 
  

```
 gedit /var/log/dmesg
```

---

### Post by RedSquirrel on 2007-05-07
You might want to see if something is failing during boot. Try this in a terminal:

```
dmesg | grep -i failed
```

---

### Post by johnnymac on 2007-05-07
If you want to see what's going on during boot....do this:

Process A:
Modify your /boot/grub/menu.lst and remove quiet splash from the kernel line

or

Process B:
Catch grub before it boots and then manually edit and remove those entries at boot

You'll be able to visually look and see where the hang is.  I'm betting your having an issue with a service starting or just taking a long time to start (perhaps something to do with reverse lookup stuff)

---

### Post by redraider0807 on 2007-05-08
Here is the dmesg

[    0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f800 end: 000000000009f800 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009f800 size: 0000000000000800 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000f0000 size: 0000000000010000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000003fef0000 end: 000000003fff0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000003fff0000 size: 0000000000003000 end: 000000003fff3000 type: 4
[    0.000000] copy_e820_map() start: 000000003fff3000 size: 000000000000d000 end: 0000000040000000 type: 3
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000001000 end: 00000000fec01000 type: 2
[    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000001000 end: 00000000fee01000 type: 2
[    0.000000] copy_e820_map() start: 00000000ffff0000 size: 0000000000010000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fff0000 (usable)
[    0.000000]  BIOS-e820: 000000003fff0000 - 000000003fff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003fff3000 - 0000000040000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] 127MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f5520
[    0.000000] Entering add_active_range(0, 0, 262128) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   262128
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   262128
[    0.000000] On node 0 totalpages: 262128
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 255 pages used for memmap
[    0.000000]   HighMem zone: 32497 pages, LIFO batch:7
[    0.000000] DMI 2.2 present.
[    0.000000] ACPI: RSDP (v000 AWARD                                 ) @ 0x000f6f00
[    0.000000] ACPI: RSDT (v001 AWARD  AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x3fff3000
[    0.000000] ACPI: FADT (v001 AWARD  AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x3fff3040
[    0.000000] ACPI: MADT (v001 AWARD  AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x3fff6b80
[    0.000000] ACPI: DSDT (v001 AWARD  AWRDACPI 0x00001000 MSFT 0x0100000e) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:12 APIC version 16
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 20, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 dfl dfl)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bec00000)
[    0.000000] Detected 2199.371 MHz processor.
[   28.195268] Built 1 zonelists.  Total pages: 260081
[   28.195272] Kernel command line: root=UUID=9741535b-8ae0-4940-b0c8-a068578829c0 ro quiet splash
[   28.195390] mapped APIC to ffffd000 (fee00000)
[   28.195392] mapped IOAPIC to ffffc000 (fec00000)
[   28.195395] Enabling fast FPU save and restore... done.
[   28.195397] Enabling unmasked SIMD FPU exception support... done.
[   28.195405] Initializing CPU#0
[   28.195450] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   28.196905] Console: colour VGA+ 80x25
[   28.197362] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   28.197788] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   28.217256] Memory: 1028316k/1048512k available (1992k kernel code, 19456k reserved, 893k data, 328k init, 131008k highmem)
[   28.217265] virtual kernel memory layout:
[   28.217266]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   28.217267]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   28.217268]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   28.217269]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   28.217271]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB)
[   28.217272]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB)
[   28.217273]       .text : 0xc0100000 - 0xc02f2264   (1992 kB)
[   28.217275] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   28.295333] Calibrating delay using timer specific routine.. 4400.85 BogoMIPS (lpj=8801715)
[   28.295370] Security Framework v1.0.0 initialized
[   28.295377] SELinux:  Disabled at boot.
[   28.295390] Mount-cache hash table entries: 512
[   28.295517] CPU: After generic identify, caps: 078bfbff e1d3fbff 00000000 00000000 00000000 00000000 00000000
[   28.295524] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   28.295526] CPU: L2 Cache: 512K (64 bytes/line)
[   28.295528] CPU: After all inits, caps: 078bfbff e1d3fbff 00000000 00000410 00000000 00000000 00000000
[   28.295538] Compat vDSO mapped to ffffe000.
[   28.295542] Remapping vsyscall page to ffffe000
[   28.295551] Checking 'hlt' instruction... OK.
[   28.311443] SMP alternatives: switching to UP code
[   28.311655] Freeing SMP alternatives: 11k freed
[   28.311832] Early unpacking initramfs... done
[   28.567379] ACPI: Core revision 20060707
[   28.573643] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   28.712864] CPU0: AMD Athlon(tm) 64 Processor 3200+ stepping 00
[   28.712879] Total of 1 processors activated (4400.85 BogoMIPS).
[   28.712968] ENABLING IO-APIC IRQs
[   28.713123] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   28.858689] Brought up 1 CPUs
[   28.858859] Booting paravirtualized kernel on bare hardware
[   28.858917] Time: 18:46:59  Date: 04/07/107
[   28.858940] NET: Registered protocol family 16
[   28.859007] EISA bus registered
[   28.859010] ACPI: bus type pci registered
[   28.894674] PCI: PCI BIOS revision 2.10 entry at 0xfb4e0, last bus=1
[   28.894676] PCI: Using configuration type 1
[   28.894678] Setting up standard PCI resources
[   28.906947] ACPI: Interpreter enabled
[   28.906951] ACPI: Using IOAPIC for interrupt routing
[   28.907393] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   28.907396] PCI: Probing PCI hardware (bus 00)
[   28.907447] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[   28.907975] Boot video device is 0000:01:00.0
[   28.908029] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   28.931021] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[   28.931194] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   28.931365] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[   28.931539] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[   28.931711] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[   28.931886] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[   28.932062] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   28.932236] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[   28.933770] Linux Plug and Play Support v0.97 (c) Adam Belay
[   28.933777] pnp: PnP ACPI init
[   28.935992] pnp: PnP ACPI: found 10 devices
[   28.935995] PnPBIOS: Disabled by ACPI PNP
[   28.936034] PCI: Using ACPI for IRQ routing
[   28.936036] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   28.941338] NET: Registered protocol family 8
[   28.941340] NET: Registered protocol family 20
[   28.941755] PCI: Bridge: 0000:00:01.0
[   28.941757]   IO window: d000-dfff
[   28.941761]   MEM window: e8000000-e80fffff
[   28.941764]   PREFETCH window: d0000000-dfffffff
[   28.941792] NET: Registered protocol family 2
[   28.966600] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   28.966769] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   28.967796] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   28.968352] TCP: Hash tables configured (established 131072 bind 65536)
[   28.968355] TCP reno registered
[   28.978623] checking if image is initramfs... it is
[   29.482620] Freeing initrd memory: 6772k freed
[   29.482967] audit: initializing netlink socket (disabled)
[   29.482980] audit(1178563619.232:1): initialized
[   29.483029] highmem bounce pool size: 64 pages
[   29.483076] VFS: Disk quotas dquot_6.5.1
[   29.483091] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   29.483132] io scheduler noop registered
[   29.483135] io scheduler anticipatory registered
[   29.483136] io scheduler deadline registered
[   29.483142] io scheduler cfq registered (default)
[   29.569954] isapnp: Scanning for PnP cards...
[   29.922832] isapnp: No Plug & Play device found
[   29.938962] Real Time Clock Driver v1.12ac
[   29.938997] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   29.939097] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   29.939509] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   29.939643] mice: PS/2 mouse device common for all mice
[   29.940022] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   29.940204] input: Macintosh mouse button emulation as /class/input/input0
[   29.940226] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   29.940229] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   29.940421] PNP: No PS/2 controller found. Probing ports directly.
[   29.940593] serio: i8042 KBD port at 0x60,0x64 irq 1
[   29.940597] serio: i8042 AUX port at 0x60,0x64 irq 12
[   29.940673] EISA: Probing bus 0 at eisa.0
[   29.940680] Cannot allocate resource for EISA slot 1
[   29.940688] Cannot allocate resource for EISA slot 4
[   29.940702] EISA: Detected 0 cards.
[   29.970802] TCP cubic registered
[   29.970811] NET: Registered protocol family 1
[   29.970827] Using IPI No-Shortcut mode
[   29.970876] ACPI: (supports S0 S1 S4 S5)
[   29.970909]   Magic number: 7:663:796
[   29.970910]   hash matches drivers/base/power/resume.c:61
[   29.971003]   hash matches device ptyr4
[   29.971301] Freeing unused kernel memory: 328k freed
[   29.973312] Time: tsc clocksource has been installed.
[   31.193382] Capability LSM initialized
[   31.224156] ACPI: Fan [FAN] (on)
[   31.228010] ACPI: Thermal Zone [THRM] (40 C)
[   31.666996] SCSI subsystem initialized
[   31.670586] libata version 2.20 loaded.
[   31.672677] pata_sis 0000:00:02.5: version 0.5.1
[   31.672744] ata1: PATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00014000 irq 14
[   31.672769] ata2: PATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x00014008 irq 15
[   31.672783] scsi0 : pata_sis
[   31.688575] usbcore: registered new interface driver usbfs
[   31.688594] usbcore: registered new interface driver hub
[   31.688611] usbcore: registered new device driver usb
[   31.710088] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   31.717566] sis900.c: v1.08.10 Apr. 2 2006
[   31.844798] ata1.00: ata_hpa_resize 1: sectors = 398297088, hpa_sectors = 398297088
[   31.844803] ata1.00: ATA-7: Maxtor 6L200R0, BAH41G10, max UDMA/133
[   31.844805] ata1.00: 398297088 sectors, multi 16: LBA48 
[   31.857606] ata1.00: ata_hpa_resize 1: sectors = 398297088, hpa_sectors = 398297088
[   31.857611] ata1.00: configured for UDMA/133
[   31.857622] scsi1 : pata_sis
[   31.858514] Floppy drive(s): fd0 is 1.44M
[   31.893454] FDC 0 is a post-1991 82077
[   32.354548] ata2.00: ATAPI, max UDMA/33
[   32.354551] ata2.01: ATAPI, max UDMA/33
[   62.321296] ata2.00: qc timeout (cmd 0xef)
[   62.321302] ata2.00: failed to set xfermode (err_mask=0x4)
[   62.321306] ata2: failed to recover some devices, retrying in 5 secs
[   97.765467] ata2.00: qc timeout (cmd 0xef)
[   97.765472] ata2.00: failed to set xfermode (err_mask=0x4)
[   97.765477] ata2.00: limiting speed to UDMA/33:PIO3
[   97.765479] ata2: failed to recover some devices, retrying in 5 secs
[  133.209637] ata2.00: qc timeout (cmd 0xef)
[  133.209643] ata2.00: failed to set xfermode (err_mask=0x4)
[  133.209646] ata2.00: disabled
[  133.209649] ata2: failed to recover some devices, retrying in 5 secs
[  138.207458] ata2.01: failed to set xfermode (err_mask=0x40)
[  138.207463] ata2: failed to recover some devices, retrying in 5 secs
[  143.689110] ata2.01: configured for UDMA/33
[  143.689215] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 6L200R0   BAH4 PQ: 0 ANSI: 5
[  143.691126] scsi 1:0:1:0: CD-ROM            SONY     DVD RW DRU-810A  1.0f PQ: 0 ANSI: 5
[  143.692397] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 20 (level, low) -> IRQ 16
[  143.692408] ohci_hcd 0000:00:03.0: OHCI Host Controller
[  143.692525] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
[  143.692540] ohci_hcd 0000:00:03.0: irq 16, io mem 0xe8124000
[  143.750678] usb usb1: configuration #1 chosen from 1 choice
[  143.750699] hub 1-0:1.0: USB hub found
[  143.750709] hub 1-0:1.0: 3 ports detected
[  143.852571] ACPI: PCI Interrupt 0000:00:03.1[B] -> GSI 21 (level, low) -> IRQ 17
[  143.852584] ohci_hcd 0000:00:03.1: OHCI Host Controller
[  143.852603] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 2
[  143.852617] ohci_hcd 0000:00:03.1: irq 17, io mem 0xe8120000
[  143.910459] usb usb2: configuration #1 chosen from 1 choice
[  143.910480] hub 2-0:1.0: USB hub found
[  143.910490] hub 2-0:1.0: 3 ports detected
[  144.012365] ACPI: PCI Interrupt 0000:00:03.2[C] -> GSI 22 (level, low) -> IRQ 18
[  144.012378] ohci_hcd 0000:00:03.2: OHCI Host Controller
[  144.012395] ohci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 3
[  144.012409] ohci_hcd 0000:00:03.2: irq 18, io mem 0xe8121000
[  144.070264] usb usb3: configuration #1 chosen from 1 choice
[  144.070286] hub 3-0:1.0: USB hub found
[  144.070295] hub 3-0:1.0: 2 ports detected
[  144.172164] ACPI: PCI Interrupt 0000:00:0c.0[A] -> GSI 16 (level, low) -> IRQ 19
[  144.172178] ohci_hcd 0000:00:0c.0: OHCI Host Controller
[  144.172194] ohci_hcd 0000:00:0c.0: new USB bus registered, assigned bus number 4
[  144.172207] ohci_hcd 0000:00:0c.0: irq 19, io mem 0xe8125000
[  144.257844] usb usb4: configuration #1 chosen from 1 choice
[  144.257868] hub 4-0:1.0: USB hub found
[  144.257877] hub 4-0:1.0: 3 ports detected
[  144.315893] usb 2-1: new low speed USB device using ohci_hcd and address 2
[  144.359923] ACPI: PCI Interrupt 0000:00:0c.1[B] -> GSI 17 (level, low) -> IRQ 20
[  144.359935] ohci_hcd 0000:00:0c.1: OHCI Host Controller
[  144.359952] ohci_hcd 0000:00:0c.1: new USB bus registered, assigned bus number 5
[  144.359965] ohci_hcd 0000:00:0c.1: irq 20, io mem 0xe8126000
[  144.445593] usb usb5: configuration #1 chosen from 1 choice
[  144.445616] hub 5-0:1.0: USB hub found
[  144.445625] hub 5-0:1.0: 2 ports detected
[  144.539565] usb 2-1: configuration #1 chosen from 1 choice
[  144.547783] ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 19 (level, low) -> IRQ 21
[  144.548826] 0000:00:04.0: Realtek RTL8201 PHY transceiver found at address 1.
[  144.557291] 0000:00:04.0: Using transceiver found at address 1 as default
[  144.557873] eth0: SiS 900 PCI Fast Ethernet at 0xe200, IRQ 21, 00:11:5b:8c:9c:44.
[  144.557941] ACPI: PCI Interrupt 0000:00:03.3[D] -> GSI 23 (level, low) -> IRQ 22
[  144.557949] ehci_hcd 0000:00:03.3: EHCI Host Controller
[  144.557968] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 6
[  144.557995] PCI: cache line size of 64 is not supported by device 0000:00:03.3
[  144.558003] ehci_hcd 0000:00:03.3: irq 22, io mem 0xe8122000
[  144.558011] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[  144.558028] usb 2-1: USB disconnect, address 2
[  144.558174] usb usb6: configuration #1 chosen from 1 choice
[  144.558192] hub 6-0:1.0: USB hub found
[  144.558198] hub 6-0:1.0: 8 ports detected
[  144.659563] ACPI: PCI Interrupt 0000:00:0c.2[C] -> GSI 18 (level, low) -> IRQ 23
[  144.659577] ehci_hcd 0000:00:0c.2: EHCI Host Controller
[  144.659594] ehci_hcd 0000:00:0c.2: new USB bus registered, assigned bus number 7
[  144.683482] ehci_hcd 0000:00:0c.2: irq 23, io mem 0xe8127000
[  144.683489] ehci_hcd 0000:00:0c.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[  144.683558] usb usb7: configuration #1 chosen from 1 choice
[  144.683582] hub 7-0:1.0: USB hub found
[  144.683590] hub 7-0:1.0: 5 ports detected
[  144.788051] sata_sis 0000:00:05.0: version 0.7
[  144.788070] ACPI: PCI Interrupt 0000:00:05.0[A] -> GSI 17 (level, low) -> IRQ 20
[  144.788080] sata_sis 0000:00:05.0: Detected SiS 180/181/964 chipset in SATA mode
[  144.788113] ata3: SATA max UDMA/133 cmd 0x0001e300 ctl 0x0001e402 bmdma 0x0001e700 irq 20
[  144.788134] ata4: SATA max UDMA/133 cmd 0x0001e500 ctl 0x0001e602 bmdma 0x0001e708 irq 20
[  144.788144] scsi2 : sata_sis
[  144.798384] SCSI device sda: 398297088 512-byte hdwr sectors (203928 MB)
[  144.798395] sda: Write Protect is off
[  144.798397] sda: Mode Sense: 00 3a 00 00
[  144.798407] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  144.798446] SCSI device sda: 398297088 512-byte hdwr sectors (203928 MB)
[  144.798452] sda: Write Protect is off
[  144.798454] sda: Mode Sense: 00 3a 00 00
[  144.798463] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  144.798466]  sda: sda1 sda2 sda3
[  144.844942] sd 0:0:0:0: Attached scsi disk sda
[  144.848960] sd 0:0:0:0: Attached scsi generic sg0 type 0
[  144.849053] sr 1:0:1:0: Attached scsi generic sg1 type 5
[  144.862997] sr0: scsi3-mmc drive: 125x/94x writer cd/rw xa/form2 cdda tray
[  144.863002] Uniform CD-ROM driver Revision: 3.20
[  144.863182] sr 1:0:1:0: Attached scsi CD-ROM sr0
[  144.867286] usbcore: registered new interface driver hiddev
[  145.088305] Attempting manual resume
[  145.088308] swsusp: Resume From Partition 8:3
[  145.088309] PM: Checking swsusp image.
[  145.088477] PM: Resume from disk failed.
[  145.094950] ReiserFS: sda2: found reiserfs format "3.6" with standard journal
[  145.094959] ReiserFS: sda2: using ordered data mode
[  145.098934] ata3: SATA link down (SStatus 0 SControl 300)
[  145.109399] ATA: abnormal status 0x7F on port 0x0001e307
[  145.109423] scsi3 : sata_sis
[  145.109635] ReiserFS: sda2: journal params: device sda2, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[  145.110319] ReiserFS: sda2: checking transaction log (sda2)
[  145.153453] ReiserFS: sda2: Using r5 hash to sort names
[  145.174836] usb 2-1: new low speed USB device using ohci_hcd and address 3
[  145.390336] usb 2-1: configuration #1 chosen from 1 choice
[  145.400343] input: Microsft Microsoft Wireless Desktop Receiver 3.1 as /class/input/input1
[  145.400354] input: USB HID v1.11 Keyboard [Microsft Microsoft Wireless Desktop Receiver 3.1] on usb-0000:00:03.1-1
[  145.418543] ata4: SATA link down (SStatus 0 SControl 300)
[  145.429010] ATA: abnormal status 0x7F on port 0x0001e507
[  145.441301] input: Microsft Microsoft Wireless Desktop Receiver 3.1 as /class/input/input2
[  145.441320] input: USB HID v1.11 Mouse [Microsft Microsoft Wireless Desktop Receiver 3.1] on usb-0000:00:03.1-1
[  145.441328] usbcore: registered new interface driver usbhid
[  145.441331] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[  153.886838] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[  154.043191] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[  154.063439] Linux agpgart interface v0.102 (c) Dave Jones
[  154.064531] agpgart: Detected AGP bridge 0
[  154.068360] agpgart: AGP aperture is 128M @ 0xe0000000
[  154.635090] usbcore: registered new interface driver xpad
[  154.635094] drivers/usb/input/xpad.c: driver for Xbox controllers v0.1.6
[  154.832656] input: PC Speaker as /class/input/input3
[  154.988929] parport: PnPBIOS parport detected.
[  154.988994] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[  155.043261] ACPI: PCI Interrupt 0000:00:02.7[C] -> GSI 18 (level, low) -> IRQ 23
[  155.366229] intel8x0_measure_ac97_clock: measured 58893 usecs
[  155.366232] intel8x0: clocking to 48000
[  155.540084] fuse init (API version 7.8)
[  155.562870] lp0: using parport0 (interrupt-driven).
[  155.591056] Adding 1638620k swap on /dev/disk/by-uuid/85b12368-8c13-45fa-8af7-10b05992c881.  Priority:-1 extents:1 across:1638620k

---

### Post by hasplu on 2007-05-08
same to me! Anyone any ideas pls:)

---

### Post by RedSquirrel on 2007-05-08
redraider0807:

This stuff from your dmesg is the problem:

```
 [   32.354548] ata2.00: ATAPI, max UDMA/33
[   32.354551] ata2.01: ATAPI, max UDMA/33
[   62.321296] ata2.00: qc timeout (cmd 0xef)
[   62.321302] ata2.00: failed to set xfermode (err_mask=0x4)
[   62.321306] ata2: failed to recover some devices, retrying in 5 secs
[   97.765467] ata2.00: qc timeout (cmd 0xef)
[   97.765472] ata2.00: failed to set xfermode (err_mask=0x4)
[   97.765477] ata2.00: limiting speed to UDMA/33:PIO3
[   97.765479] ata2: failed to recover some devices, retrying in 5 secs
[  133.209637] ata2.00: qc timeout (cmd 0xef)
[  133.209643] ata2.00: failed to set xfermode (err_mask=0x4)
[  133.209646] ata2.00: disabled
[  133.209649] ata2: failed to recover some devices, retrying in 5 secs
[  138.207458] ata2.01: failed to set xfermode (err_mask=0x40)
[  138.207463] ata2: failed to recover some devices, retrying in 5 secs
[  143.689110] ata2.01: configured for UDMA/33
[  143.689215] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 6L200R0   BAH4 PQ: 0 ANSI: 5
[  143.691126] scsi 1:0:1:0: CD-ROM            SONY     DVD RW DRU-810A  1.0f PQ: 0 ANSI: 5

```
It's a "known" issue. 

Here is some discussion about it:

[https://answers.launchpad.net/ubuntu/+source/linux-source-2.6.20/+question/5691](https://answers.launchpad.net/ubuntu/+source/linux-source-2.6.20/+question/5691)

Have a look at this for some ideas on how to fix it:

[https://answers.launchpad.net/ubuntu/+question/4995](https://answers.launchpad.net/ubuntu/+question/4995)


In my opinion, when debugging issues with booting, it's best to start by searching for things that are failing in an obvious way. This is why I suggested above you search dmesg for "failed". It's not always a magic bullet, but it's a good start.

After that, try a search for some of the errors you see (ubuntuforums and/or google), such as "ata2: failed to recover some devices, retrying in 5 secs". You might get some interesting results. :)

---

### Post by redraider0807 on 2007-05-10
I already tried disabling most of the things in the networking interface, except the lines containing lo so that doesn't work.  Any other suggestions? and i'll try googling ta2: failed to recover some devices, retrying in 5 secs to see what i find, thanks for the help thus far.

---

### Post by redraider0807 on 2007-05-10
I found out what it was, something with the kernel and my CD-R but i added irqpoll to the boot arguments and boot time is 35 seconds.  Thanks for the help.

---

