---
title: "How do I connect a Moto V323i using USB"
date: 2007-07-06
forum: General Help
---

### Post by Eddie Wilson on 2007-07-06
Good Day All,
Well I had to reinstall Xp to connect to my cell phone. Its a Motoroal V323i. I'm using the Phone Tools 4 that runs under MS Window. It will not run under wine. I would rather use nothing but my Ubuntu but I can't seem to get it to connect. I tried Moto4Lin and can't connect through that. I don't want to have to buy a Bluetooth adapter when I can just use my usb. Does anybody know of a way in which I can connect to my cell and also upload and download files? Thank you in advance and any help you can give.
Eddie

---

### Post by Eddie Wilson on 2007-07-06
Any takers?

---

### Post by hikaricore on 2007-07-06
check the output of:

```
dmesg
```

About 30 seconds after you plug in the phone.

Paste the output here.  I can tell you for sure if you have any chance of getting it working at the very least.

---

### Post by Eddie Wilson on 2007-07-06
Thank You,
I'll do that as soon as I get home.

---

### Post by Eddie Wilson on 2007-07-07
Here is the output of dmesg


[    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Thu Jun 7 20:19:32 UTC 2007 (Ubuntu 2.6.20-16.29-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009fc00 end: 000000000009fc00 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009fc00 size: 0000000000000400 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000f0000 size: 0000000000010000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000001fefb000 end: 000000001fffb000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000001fffb000 size: 0000000000004000 end: 000000001ffff000 type: 3
[    0.000000] copy_e820_map() start: 000000001ffff000 size: 0000000000001000 end: 0000000020000000 type: 4
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000001000 end: 00000000fec01000 type: 2
[    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000001000 end: 00000000fee01000 type: 2
[    0.000000] copy_e820_map() start: 00000000ffff0000 size: 0000000000010000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001fffb000 (usable)
[    0.000000]  BIOS-e820: 000000001fffb000 - 000000001ffff000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001ffff000 - 0000000020000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 511MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 131067) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   131067
[    0.000000]   HighMem    131067 ->   131067
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   131067
[    0.000000] On node 0 totalpages: 131067
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 991 pages used for memmap
[    0.000000]   Normal zone: 125980 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 ASUS                                  ) @ 0x000f5e30
[    0.000000] ACPI: RSDT (v001 ASUS   A7V600   0x42302e31 MSFT 0x31313031) @ 0x1fffb000
[    0.000000] ACPI: FADT (v001 ASUS   A7V600   0x42302e31 MSFT 0x31313031) @ 0x1fffb0b2
[    0.000000] ACPI: BOOT (v001 ASUS   A7V600   0x42302e31 MSFT 0x31313031) @ 0x1fffb030
[    0.000000] ACPI: MADT (v001 ASUS   A7V600   0x42302e31 MSFT 0x31313031) @ 0x1fffb058
[    0.000000] ACPI: DSDT (v001   ASUS A7V600   0x00001000 MSFT 0x0100000b) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0xe408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:10 APIC version 16
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
[    0.000000] Detected 2000.257 MHz processor.
[   15.659228] Built 1 zonelists.  Total pages: 130044
[   15.659232] Kernel command line: root=UUID=3a9bd4f2-7c34-4cd5-9326-bfccfe7eedf9 ro quiet splash
[   15.659405] mapped APIC to ffffd000 (fee00000)
[   15.659408] mapped IOAPIC to ffffc000 (fec00000)
[   15.659412] Enabling fast FPU save and restore... done.
[   15.659414] Enabling unmasked SIMD FPU exception support... done.
[   15.659428] Initializing CPU#0
[   15.659514] PID hash table entries: 2048 (order: 11, 8192 bytes)
[   15.660737] Console: colour VGA+ 80x25
[   15.661244] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   15.661608] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   15.679290] Memory: 508728k/524268k available (1992k kernel code, 14968k reserved, 900k data, 328k init, 0k highmem)
[   15.679301] virtual kernel memory layout:
[   15.679302]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   15.679304]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   15.679305]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
[   15.679306]     lowmem  : 0xc0000000 - 0xdfffb000   ( 511 MB)
[   15.679307]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[   15.679309]       .data : 0xc02f2374 - 0xc03d36d4   ( 900 kB)
[   15.679310]       .text : 0xc0100000 - 0xc02f2374   (1992 kB)
[   15.679313] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   15.755342] Calibrating delay using timer specific routine.. 4003.85 BogoMIPS (lpj=8007705)
[   15.755392] Security Framework v1.0.0 initialized
[   15.755402] SELinux:  Disabled at boot.
[   15.755421] Mount-cache hash table entries: 512
[   15.755599] CPU: After generic identify, caps: 0383fbff c1c3fbff 00000000 00000000 00000000 00000000 00000000
[   15.755610] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   15.755612] CPU: L2 Cache: 256K (64 bytes/line)
[   15.755615] CPU: After all inits, caps: 0383fbff c1c3fbff 00000000 00000420 00000000 00000000 00000000
[   15.755627] Compat vDSO mapped to ffffe000.
[   15.755634] Remapping vsyscall page to ffffe000
[   15.755645] Checking 'hlt' instruction... OK.
[   15.771465] SMP alternatives: switching to UP code
[   15.771777] Freeing SMP alternatives: 11k freed
[   15.772093] Early unpacking initramfs... done
[   16.085251] ACPI: Core revision 20060707
[   16.085994] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   16.090077] CPU0: AMD Athlon(TM) XP 2400+ stepping 00
[   16.090103] Total of 1 processors activated (4003.85 BogoMIPS).
[   16.090870] ENABLING IO-APIC IRQs
[   16.091189] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   16.238511] Brought up 1 CPUs
[   16.238839] Booting paravirtualized kernel on bare hardware
[   16.238943] Time: 12:49:10  Date: 06/07/107
[   16.238988] NET: Registered protocol family 16
[   16.239115] EISA bus registered
[   16.239120] ACPI: bus type pci registered
[   16.240390] PCI: PCI BIOS revision 2.10 entry at 0xf1970, last bus=1
[   16.240393] PCI: Using configuration type 1
[   16.240395] Setting up standard PCI resources
[   16.254059] ACPI: Interpreter enabled
[   16.254066] ACPI: Using IOAPIC for interrupt routing
[   16.254810] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12)
[   16.255016] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 12)
[   16.255213] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 *7 9 10 11 12)
[   16.255414] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 11 12) *0, disabled.
[   16.255720] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *9 10 11 12)
[   16.255981] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *9 10 11 12)
[   16.256259] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 *11 12)
[   16.256472] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12) *15, disabled.
[   16.256574] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   16.256581] PCI: Probing PCI hardware (bus 00)
[   16.256959] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[   16.257735] PCI: enabled onboard AC97/MC97 devices
[   16.257921] Boot video device is 0000:01:00.0
[   16.257965] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   16.260666] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[   16.265412] Linux Plug and Play Support v0.97 (c) Adam Belay
[   16.265431] pnp: PnP ACPI init
[   16.269667] pnp: PnP ACPI: found 13 devices
[   16.269673] PnPBIOS: Disabled by ACPI PNP
[   16.269741] PCI: Using ACPI for IRQ routing
[   16.269746] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   16.277288] NET: Registered protocol family 8
[   16.277290] NET: Registered protocol family 20
[   16.277572] pnp: 00:02: ioport range 0xe400-0xe47f could not be reserved
[   16.277576] pnp: 00:02: ioport range 0xe800-0xe81f has been reserved
[   16.277589] pnp: 00:0c: ioport range 0x290-0x297 has been reserved
[   16.277592] pnp: 00:0c: ioport range 0x370-0x375 has been reserved
[   16.277915] PCI: Bridge: 0000:00:01.0
[   16.277917]   IO window: disabled.
[   16.277922]   MEM window: e6000000-e7efffff
[   16.277926]   PREFETCH window: e7f00000-efffffff
[   16.277947] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   16.277985] NET: Registered protocol family 2
[   16.314430] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   16.314546] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   16.314806] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[   16.314941] TCP: Hash tables configured (established 16384 bind 8192)
[   16.314944] TCP reno registered
[   16.326452] checking if image is initramfs... it is
[   16.913207] Freeing initrd memory: 6774k freed
[   16.913466] Simple Boot Flag at 0x3a set to 0x1
[   16.913834] audit: initializing netlink socket (disabled)
[   16.913853] audit(1183812551.336:1): initialized
[   16.913992] VFS: Disk quotas dquot_6.5.1
[   16.914019] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   16.914086] io scheduler noop registered
[   16.914089] io scheduler anticipatory registered
[   16.914091] io scheduler deadline registered
[   16.914099] io scheduler cfq registered (default)
[   16.914187] PCI: Bypassing VIA 8237 APIC De-Assert Message
[   16.914474] isapnp: Scanning for PnP cards...
[   17.267435] isapnp: No Plug & Play device found
[   17.302718] Real Time Clock Driver v1.12ac
[   17.302781] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   17.302904] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   17.303156] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   17.303968] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   17.304362] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   17.304804] mice: PS/2 mouse device common for all mice
[   17.305423] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   17.305725] input: Macintosh mouse button emulation as /class/input/input0
[   17.305766] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   17.305770] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   17.306042] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   17.308728] serio: i8042 KBD port at 0x60,0x64 irq 1
[   17.308738] serio: i8042 AUX port at 0x60,0x64 irq 12
[   17.308938] EISA: Probing bus 0 at eisa.0
[   17.308973] Cannot allocate resource for EISA slot 8
[   17.308975] EISA: Detected 0 cards.
[   17.339036] TCP cubic registered
[   17.339044] NET: Registered protocol family 1
[   17.339073] Using IPI No-Shortcut mode
[   17.339148] ACPI: (supports S0 S1 S4 S5)
[   17.339191]   Magic number: 15:589:834
[   17.339346]   hash matches device ptyu0
[   17.339911] Freeing unused kernel memory: 328k freed
[   17.340394] Time: tsc clocksource has been installed.
[   17.357353] input: AT Translated Set 2 keyboard as /class/input/input1
[   18.586405] Capability LSM initialized
[   19.206749] usbcore: registered new interface driver usbfs
[   19.206785] usbcore: registered new interface driver hub
[   19.206813] usbcore: registered new device driver usb
[   19.207759] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   19.207816] ACPI: PCI Interrupt 0000:00:0d.0[A] -> GSI 16 (level, low) -> IRQ 16
[   19.207832] ohci_hcd 0000:00:0d.0: OHCI Host Controller
[   19.208029] ohci_hcd 0000:00:0d.0: new USB bus registered, assigned bus number 1
[   19.208057] ohci_hcd 0000:00:0d.0: irq 16, io mem 0xe5800000
[   19.263837] SCSI subsystem initialized
[   19.269424] libata version 2.20 loaded.
[   19.280527] USB Universal Host Controller Interface driver v3.0
[   19.837972] usb usb1: configuration #1 chosen from 1 choice
[   19.838009] hub 1-0:1.0: USB hub found
[   19.838024] hub 1-0:1.0: 3 ports detected
[   20.351240] ACPI: PCI Interrupt 0000:00:0d.2[C] -> GSI 18 (level, low) -> IRQ 17
[   20.351263] ehci_hcd 0000:00:0d.2: EHCI Host Controller
[   20.351295] ehci_hcd 0000:00:0d.2: new USB bus registered, assigned bus number 2
[   20.375030] ehci_hcd 0000:00:0d.2: irq 17, io mem 0xe4800000
[   20.375040] ehci_hcd 0000:00:0d.2: USB 2.0 started, EHCI 0.95, driver 10 Dec 2004
[   20.375175] usb usb2: configuration #1 chosen from 1 choice
[   20.375206] hub 2-0:1.0: USB hub found
[   20.375218] hub 2-0:1.0: 5 ports detected
[   20.479030] ACPI: PCI Interrupt 0000:00:10.4[C] -> GSI 21 (level, low) -> IRQ 18
[   20.479053] ehci_hcd 0000:00:10.4: EHCI Host Controller
[   20.479082] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 3
[   20.479139] ehci_hcd 0000:00:10.4: irq 18, io mem 0xe4000000
[   20.479146] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   20.479235] usb usb3: configuration #1 chosen from 1 choice
[   20.479264] hub 3-0:1.0: USB hub found
[   20.479276] hub 3-0:1.0: 8 ports detected
[   20.582949] sata_via 0000:00:0f.0: version 2.1
[   20.582987] ACPI: PCI Interrupt 0000:00:0f.0[B] -> GSI 20 (level, low) -> IRQ 19
[   20.583010] sata_via 0000:00:0f.0: routed to hard irq line 0
[   20.583111] ata1: SATA max UDMA/133 cmd 0x0001d000 ctl 0x0001b802 bmdma 0x0001a800 irq 19
[   20.583153] ata2: SATA max UDMA/133 cmd 0x0001b400 ctl 0x0001b002 bmdma 0x0001a808 irq 19
[   20.583171] scsi0 : sata_via
[   20.786269] ata1: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[   20.796701] ATA: abnormal status 0x7F on port 0x0001d007
[   20.796733] scsi1 : sata_via
[   20.997888] ata2: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[   21.008319] ATA: abnormal status 0x7F on port 0x0001b407
[   21.008953] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 21 (level, low) -> IRQ 18
[   21.008969] uhci_hcd 0000:00:10.0: UHCI Host Controller
[   21.009035] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 4
[   21.009063] uhci_hcd 0000:00:10.0: irq 18, io base 0x00009800
[   21.009221] usb usb4: configuration #1 chosen from 1 choice
[   21.009253] hub 4-0:1.0: USB hub found
[   21.009266] hub 4-0:1.0: 2 ports detected
[   21.109887] ACPI: PCI Interrupt 0000:00:10.1[A] -> GSI 21 (level, low) -> IRQ 18
[   21.109904] uhci_hcd 0000:00:10.1: UHCI Host Controller
[   21.109935] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 5
[   21.109962] uhci_hcd 0000:00:10.1: irq 18, io base 0x00009400
[   21.110089] usb usb5: configuration #1 chosen from 1 choice
[   21.110119] hub 5-0:1.0: USB hub found
[   21.110132] hub 5-0:1.0: 2 ports detected
[   21.213673] ACPI: PCI Interrupt 0000:00:10.2[B] -> GSI 21 (level, low) -> IRQ 18
[   21.213689] uhci_hcd 0000:00:10.2: UHCI Host Controller
[   21.213720] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 6
[   21.213748] uhci_hcd 0000:00:10.2: irq 18, io base 0x00009000
[   21.213870] usb usb6: configuration #1 chosen from 1 choice
[   21.213901] hub 6-0:1.0: USB hub found
[   21.213912] hub 6-0:1.0: 2 ports detected
[   21.317489] ACPI: PCI Interrupt 0000:00:10.3[B] -> GSI 21 (level, low) -> IRQ 18
[   21.317505] uhci_hcd 0000:00:10.3: UHCI Host Controller
[   21.317536] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 7
[   21.317564] uhci_hcd 0000:00:10.3: irq 18, io base 0x00008800
[   21.317688] usb usb7: configuration #1 chosen from 1 choice
[   21.317720] hub 7-0:1.0: USB hub found
[   21.317732] hub 7-0:1.0: 2 ports detected
[   21.424661] VP_IDE: IDE controller at PCI slot 0000:00:0f.1
[   21.424689] ACPI: PCI Interrupt 0000:00:0f.1[A] -> GSI 20 (level, low) -> IRQ 19
[   21.424704] VP_IDE: chipset revision 6
[   21.424706] VP_IDE: not 100% native mode: will probe irqs later
[   21.424718] VP_IDE: VIA vt8237 (rev 00) IDE UDMA133 controller on pci0000:00:0f.1
[   21.424727]     ide0: BM-DMA at 0xa000-0xa007, BIOS settings: hda:DMA, hdb:DMA
[   21.424742]     ide1: BM-DMA at 0xa008-0xa00f, BIOS settings: hdc:DMA, hdd:pio
[   21.424749] Probing IDE interface ide0...
[   21.840454] hda: IC35L080AVVA07-0, ATA DISK drive
[   22.119961] hdb: ST340014A, ATA DISK drive
[   22.176794] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   22.192463] Probing IDE interface ide1...
[   22.247652] usb 7-2: new low speed USB device using uhci_hcd and address 2
[   22.426413] usb 7-2: configuration #1 chosen from 1 choice
[   22.442350] usbcore: registered new interface driver hiddev
[   23.054268] hdc: LITE-ON DVDRW SOHW-1693S, ATAPI CD/DVD-ROM drive
[   23.725518] ide1 at 0x170-0x177,0x376 on irq 15
[   23.726385] ACPI: PCI Interrupt 0000:00:0d.1[B] -> GSI 17 (level, low) -> IRQ 20
[   23.726405] ohci_hcd 0000:00:0d.1: OHCI Host Controller
[   23.726560] ohci_hcd 0000:00:0d.1: new USB bus registered, assigned bus number 8
[   23.726584] ohci_hcd 0000:00:0d.1: irq 20, io mem 0xe5000000
[   23.734247] hda: max request size: 128KiB
[   23.749586] hda: 160836480 sectors (82348 MB) w/1863KiB Cache, CHS=65535/16/63, UDMA(100)
[   23.749805] hda: cache flushes supported
[   23.749878]  hda: hda1 hda2 hda3 hda4
[   24.287062] usb usb8: configuration #1 chosen from 1 choice
[   24.287339] hub 8-0:1.0: USB hub found
[   24.287360] hub 8-0:1.0: 2 ports detected
[   24.289890] hdb: max request size: 512KiB
[   24.290137] hdb: 78165360 sectors (40020 MB) w/2048KiB Cache, CHS=16383/255/63, UDMA(100)
[   24.290274] hdb: cache flushes supported
[   24.290320]  hdb:<6>hdc: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(66)
[   24.291016] Uniform CD-ROM driver Revision: 3.20
[   24.316632]  hdb1
[   24.633534] Attempting manual resume
[   24.633539] swsusp: Resume From Partition 3:4
[   24.633541] PM: Checking swsusp image.
[   24.645647] PM: Resume from disk failed.
[   24.682466] kjournald starting.  Commit interval 5 seconds
[   24.682483] EXT3-fs: mounted filesystem with ordered data mode.
[   32.446381] drivers/usb/input/hid-core.c: timeout initializing reports
[   32.446512] input: Logitech Inc. WingMan RumblePad as /class/input/input2
[   32.446520] input: USB HID v1.10 Joystick [Logitech Inc. WingMan RumblePad] on usb-0000:00:10.3-2
[   32.446545] usbcore: registered new interface driver usbhid
[   32.446549] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   35.902060] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   35.904593] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   36.005953] gameport: EMU10K1 is pci0000:00:0e.1/gameport0, io 0xd400, speed 1242kHz
[   36.424190] Linux agpgart interface v0.102 (c) Dave Jones
[   36.821687] agpgart: Detected VIA KT400/KT400A/KT600 chipset
[   36.830591] agpgart: AGP aperture is 128M @ 0xf0000000
[   37.333935] nvidia: module license 'NVIDIA' taints kernel.
[   37.720166] input: PC Speaker as /class/input/input3
[   37.742224] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   37.742750] NVRM: loading NVIDIA UNIX x86 Kernel Module  1.0-9755  Mon Feb 26 23:21:15 PST 2007
[   37.783432] usbcore: registered new interface driver xpad
[   37.783439] drivers/usb/input/xpad.c: driver for Xbox controllers v0.1.6
[   37.825536] PCI: Enabling device 0000:00:11.5 (0000 -> 0001)
[   37.825556] ACPI: PCI Interrupt 0000:00:11.5[C] -> GSI 22 (level, low) -> IRQ 21
[   37.827632] PCI: Setting latency timer of device 0000:00:11.5 to 64
[   38.341053] codec_read: codec 0 is not valid [0xfe0000]
[   38.347230] codec_read: codec 0 is not valid [0xfe0000]
[   38.353445] codec_read: codec 0 is not valid [0xfe0000]
[   38.359620] codec_read: codec 0 is not valid [0xfe0000]
[   38.359705] input: ImExPS/2 Generic Explorer Mouse as /class/input/input4
[   38.378516] ACPI: PCI Interrupt 0000:00:0e.0[A] -> GSI 17 (level, low) -> IRQ 20
[   38.399901] PCI: Enabling device 0000:00:11.6 (0000 -> 0001)
[   38.399914] ACPI: PCI Interrupt 0000:00:11.6[C] -> GSI 22 (level, low) -> IRQ 21
[   39.149207] PCI: Setting latency timer of device 0000:00:11.6 to 64
[   39.652497] ACPI: PCI interrupt for device 0000:00:11.6 disabled
[   39.652510] VIA 82xx Modem: probe of 0000:00:11.6 failed with error -13
[   39.788991] fuse init (API version 7.8)
[   39.873033] lp: driver loaded but no devices found
[   39.919348] Adding 514072k swap on /dev/disk/by-uuid/7431d78a-1f12-4f8d-b4c5-b41d1cacb549.  Priority:-1 extents:1 across:514072k
[   40.077512] EXT3 FS on hda2, internal journal
[   52.849919] NTFS driver 2.1.28 [Flags: R/O MODULE].
[   52.913383] NTFS volume version 3.1.
[   52.947995] kjournald starting.  Commit interval 5 seconds
[   52.948118] EXT3 FS on hda3, internal journal
[   52.948124] EXT3-fs: mounted filesystem with ordered data mode.
[   54.471283] NET: Registered protocol family 17
[   59.825717] Using specific hotkey driver
[   59.900472] ibm_acpi: ec object not found
[   59.964480] No dock devices found.
[   60.102628] input: Power Button (FF) as /class/input/input5
[   60.108309] ACPI: Power Button (FF) [PWRF]
[   60.149568] input: Power Button (CM) as /class/input/input6
[   60.155217] ACPI: Power Button (CM) [PWRB]
[   60.285229] pcc_acpi: loading...
[   63.331694] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[   63.332125] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   63.332413] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[   64.655114] ppdev: user-space parallel port driver
[   65.718425] apm: BIOS version 1.2 Flags 0x0b (Driver version 1.16ac)
[   65.718433] apm: overridden by ACPI.
[   66.315040] Bluetooth: Core ver 2.11
[   66.315145] NET: Registered protocol family 31
[   66.315148] Bluetooth: HCI device and connection manager initialized
[   66.315152] Bluetooth: HCI socket layer initialized
[   66.342626] Bluetooth: L2CAP ver 2.8
[   66.342633] Bluetooth: L2CAP socket layer initialized
[   66.643169] Bluetooth: RFCOMM socket layer initialized
[   66.643193] Bluetooth: RFCOMM TTY layer initialized
[   66.643195] Bluetooth: RFCOMM ver 1.8
[   80.902078] NET: Registered protocol family 10
[   80.902209] lo: Disabled Privacy Extensions
[  252.605890] PPP generic driver version 2.4.2
[  256.032967] PPP BSD Compression module registered
[  256.092655] PPP Deflate Compression module registered
[  767.944843] usb 6-2: new full speed USB device using uhci_hcd and address 2
[  768.068620] usb 6-2: device descriptor read/64, error -71
[  768.296208] usb 6-2: device descriptor read/64, error -71
[  768.511819] usb 6-2: new full speed USB device using uhci_hcd and address 3
[  768.635597] usb 6-2: device descriptor read/64, error -71
[  768.863204] usb 6-2: device descriptor read/64, error -71
[  769.078814] usb 6-2: new full speed USB device using uhci_hcd and address 4
[  769.494050] usb 6-2: device not accepting address 4, error -71
[  769.605849] usb 6-2: new full speed USB device using uhci_hcd and address 5
[  770.021100] usb 6-2: device not accepting address 5, error -71
[  798.501816] usb 6-2: new full speed USB device using uhci_hcd and address 6
[  798.736407] usb 6-2: configuration #1 chosen from 2 choices
[  798.741281] usb 6-2: can't set config #1, error -84
eddie@eddie-desktop:~$ 

Thanks
Eddie

---

### Post by hikaricore on 2007-07-08
You should be seeing something like this:

> [279255.491627] usbcore: registered new interface driver cdc_acm
[279255.491731] drivers/usb/class/cdc-acm.c: v0.25:USB Abstract Control Model driver for USB modems and ISDN adapters
[279255.596022] usb 1-2: new full speed USB device using uhci_hcd and address 3
[279255.835914] usb 1-2: configuration #1 chosen from 1 choice
[279255.838879] cdc_acm 1-2:1.0: ttyACM0: USB ACM device


Which should load cdc_amc to create /dev node such as this:

> [hikaricore@devistate:~ (2735.1 Mb)]$ ls -la /dev/ttyACM0
crw-rw---- 1 root dialout 166, 0 2007-07-08 03:08 **/dev/ttyACM0**

Either your phone isn't supported the kernel module cdc_amc, your phone has a setting in it preventing pcsync, or possibly the cable/usb port is bad/needs the contacts cleaned.

Other than that I'm not too sure.  :/  Atleast it's being recognized.  That's a start.

My Razr v3m isn't even recognized by the system.

---

