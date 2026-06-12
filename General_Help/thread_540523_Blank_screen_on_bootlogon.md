---
title: "Blank screen on boot/logon"
date: 2007-09-01
forum: General Help
---

### Post by NoSmokingBandit on 2007-09-01
I just had a dimension 2350 given to me so i decided to make a dedicated linux box. It has a 30gb maxtor drive, 1.8ghz intel processor, and 768mb ram, so its a decent machine. I popped my 7.04 live cd in it and ubuntu installed just fine. After the install the window shows up asking if you want to reboot or keep using the live cd, so i chose to reboot and the screen went black, no countdown progress bar or anything. I let it go for a minute and eventually the cd tray opened. i took out the cd and hit enter (still a black screen, mind you) and my machine beeped and rebooted. Every time i go to boot up ubuntu, i see no progress bar and no logon screen. If i let it sit for about 2 minutes and hit ctrl (other buttons might work, i just bumped it on my way to ctrl-alt-del) the screen gets all glitchy then the logon screen shows up. Once i log in its fine, and im actually typing this from my new install, but the blank screen makes me think something is way off somewhere in the install.

---

### Post by taurus on 2007-09-01
After you log in, edit /boot/grub/menu.lst and remove the last two words, **quiet splash** from a kernel entry to see the boot up message.

```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by NoSmokingBandit on 2007-09-01
Thanks for the quick reply. I did what you said and rebooted.
As it booted up everything went smooth until one line where it stalled for about 30 seconds. This is what it said.

ata 2.00: configured for UMDA/33
ata 2.01: qc timeout (cmd 0xef)
ata 2.01: failed to set xfermode (err_mask=0x4)
ata2: failed to recover some devices, retrying in 5s

It goes through that twice then continues just fine until i get the glitchy screen. The logon screen comes on without me hitting a button though.
Hope this helps.

---

### Post by taurus on 2007-09-01
Can you post the complete output of this command from a terminal?

Applications -> Accessories -> Terminal
```
dmesg
```

---

### Post by NoSmokingBandit on 2007-09-01
```

[    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Fri Aug 31 00:55:27 UTC 2007 (Ubuntu 2.6.20-16.31-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009fc00 end: 000000000009fc00 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009fc00 size: 0000000000000400 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000f0000 size: 0000000000010000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000002fdf0000 end: 000000002fef0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000002fef0000 size: 0000000000003000 end: 000000002fef3000 type: 4
[    0.000000] copy_e820_map() start: 000000002fef3000 size: 000000000000d000 end: 000000002ff00000 type: 3
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000001000 end: 00000000fec01000 type: 2
[    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000001000 end: 00000000fee01000 type: 2
[    0.000000] copy_e820_map() start: 00000000ffb00000 size: 0000000000500000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000002fef0000 (usable)
[    0.000000]  BIOS-e820: 000000002fef0000 - 000000002fef3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000002fef3000 - 000000002ff00000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 766MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f4ba0
[    0.000000] Entering add_active_range(0, 0, 196336) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   196336
[    0.000000]   HighMem    196336 ->   196336
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   196336
[    0.000000] On node 0 totalpages: 196336
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1501 pages used for memmap
[    0.000000]   Normal zone: 190739 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 IntelR                                ) @ 0x000f6d40
[    0.000000] ACPI: RSDT (v001 IntelR AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x2fef3000
[    0.000000] ACPI: FADT (v001 IntelR AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x2fef3040
[    0.000000] ACPI: BOOT (v001 IntelR AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x2fef6640
[    0.000000] ACPI: MADT (v001 IntelR AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x2fef6680
[    0.000000] ACPI: DSDT (v001 INTELR AWRDACPI 0x00001000 MSFT 0x0100000c) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:2 APIC version 20
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 2ff00000:ced00000)
[    0.000000] Detected 1794.219 MHz processor.
[   10.440182] Built 1 zonelists.  Total pages: 194803
[   10.440190] Kernel command line: root=UUID=0157a0c9-2605-4aa1-ba2d-21ce427167bc ro
[   10.440407] mapped APIC to ffffd000 (fee00000)
[   10.440411] mapped IOAPIC to ffffc000 (fec00000)
[   10.440416] Enabling fast FPU save and restore... done.
[   10.440421] Enabling unmasked SIMD FPU exception support... done.
[   10.440442] Initializing CPU#0
[   10.440562] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   10.442345] Console: colour VGA+ 80x25
[   10.446147] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   10.447292] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   10.470040] Memory: 767288k/785344k available (1993k kernel code, 17416k reserved, 900k data, 328k init, 0k highmem)
[   10.470130] virtual kernel memory layout:
[   10.470131]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   10.470133]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   10.470134]     vmalloc : 0xf0800000 - 0xff7fe000   ( 239 MB)
[   10.470136]     lowmem  : 0xc0000000 - 0xefef0000   ( 766 MB)
[   10.470138]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[   10.470139]       .data : 0xc02f2434 - 0xc03d36d4   ( 900 kB)
[   10.470141]       .text : 0xc0100000 - 0xc02f2434   (1993 kB)
[   10.470566] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   10.548436] Calibrating delay using timer specific routine.. 3592.04 BogoMIPS (lpj=7184092)
[   10.548602] Security Framework v1.0.0 initialized
[   10.548665] SELinux:  Disabled at boot.
[   10.548740] Mount-cache hash table entries: 512
[   10.549007] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00000400 00000000 00000000
[   10.549026] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   10.549119] CPU: L2 cache: 512K
[   10.549172] CPU: Hyper-Threading is disabled
[   10.549226] CPU: After all inits, caps: bfebfbff 00000000 00000000 00003080 00000400 00000000 00000000
[   10.549242] Compat vDSO mapped to ffffe000.
[   10.549298] Remapping vsyscall page to ffffe000
[   10.549367] Checking 'hlt' instruction... OK.
[   10.564600] SMP alternatives: switching to UP code
[   10.564906] Freeing SMP alternatives: 11k freed
[   10.565252] Early unpacking initramfs... done
[   10.991515] ACPI: Core revision 20060707
[   10.998081] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   11.132618] CPU0: Intel(R) Pentium(R) 4 CPU 1.80GHz stepping 07
[   11.132804] Total of 1 processors activated (3592.04 BogoMIPS).
[   11.133006] ENABLING IO-APIC IRQs
[   11.133267] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   11.279598] Brought up 1 CPUs
[   11.280012] Booting paravirtualized kernel on bare hardware
[   11.280163] Time: 21:14:07  Date: 08/01/107
[   11.280259] NET: Registered protocol family 16
[   11.280458] EISA bus registered
[   11.280515] ACPI: bus type pci registered
[   11.310005] PCI: PCI BIOS revision 2.10 entry at 0xfaea0, last bus=1
[   11.310062] PCI: Using configuration type 1
[   11.310115] Setting up standard PCI resources
[   11.330073] ACPI: Interpreter enabled
[   11.330133] ACPI: Using IOAPIC for interrupt routing
[   11.331004] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   11.331067] PCI: Probing PCI hardware (bus 00)
[   11.331522] Boot video device is 0000:00:02.0
[   11.331871] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
[   11.331873] * this clock source is slow. If you are sure your timer does not have
[   11.331875] * this bug, please use "acpi_pm_good" to disable the workaround
[   11.332119] PCI quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
[   11.332178] PCI quirk: region 0480-04bf claimed by ICH4 GPIO
[   11.332724] PCI: Transparent bridge - 0000:00:1e.0
[   11.332808] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   11.358325] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   11.360009] ACPI: PCI Interrupt Link [LNKA] (IRQs *3 4 5 7 9 10 11 12 14 15)
[   11.360855] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *9 10 11 12 14 15)
[   11.361691] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   11.362525] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[   11.363360] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   11.364293] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   11.365217] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   11.366132] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   11.369586] Linux Plug and Play Support v0.97 (c) Adam Belay
[   11.369661] pnp: PnP ACPI init
[   11.373975] pnp: PnP ACPI: found 13 devices
[   11.374037] PnPBIOS: Disabled by ACPI PNP
[   11.374171] PCI: Using ACPI for IRQ routing
[   11.374227] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   11.387887] NET: Registered protocol family 8
[   11.387942] NET: Registered protocol family 20
[   11.388547] pnp: 00:02: ioport range 0x400-0x4bf could not be reserved
[   11.389073] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[   11.389144] PCI: Bridge: 0000:00:1e.0
[   11.389198]   IO window: c000-cfff
[   11.389255]   MEM window: ec000000-edffffff
[   11.389312]   PREFETCH window: 30000000-300fffff
[   11.389382] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   11.389425] NET: Registered protocol family 2
[   11.427482] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   11.427859] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   11.429407] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   11.430441] TCP: Hash tables configured (established 131072 bind 65536)
[   11.430507] TCP reno registered
[   11.439601] checking if image is initramfs... it is
[   12.287662] Freeing initrd memory: 6772k freed
[   12.288049] Simple Boot Flag at 0x59 set to 0x1
[   12.288462] audit: initializing netlink socket (disabled)
[   12.288538] audit(1188681247.800:1): initialized
[   12.288806] VFS: Disk quotas dquot_6.5.1
[   12.288887] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   12.289018] io scheduler noop registered
[   12.289108] io scheduler anticipatory registered
[   12.289197] io scheduler deadline registered
[   12.289298] io scheduler cfq registered (default)
[   12.289809] isapnp: Scanning for PnP cards...
[   12.643933] isapnp: No Plug & Play device found
[   12.681660] Real Time Clock Driver v1.12ac
[   12.681796] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   12.682065] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   12.683166] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   12.683614] mice: PS/2 mouse device common for all mice
[   12.684575] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   12.685020] input: Macintosh mouse button emulation as /class/input/input0
[   12.685137] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   12.685198] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   12.685582] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   12.689744] serio: i8042 KBD port at 0x60,0x64 irq 1
[   12.689816] serio: i8042 AUX port at 0x60,0x64 irq 12
[   12.690120] EISA: Probing bus 0 at eisa.0
[   12.690217] EISA: Detected 0 cards.
[   12.720377] TCP cubic registered
[   12.720441] NET: Registered protocol family 1
[   12.720529] Using IPI No-Shortcut mode
[   12.720678] ACPI: (supports S0 S1 S3 S4 S5)
[   12.721009]   Magic number: 7:488:246
[   12.721125]   hash matches device ttyw2
[   12.721761] Time: tsc clocksource has been installed.
[   12.721935] Freeing unused kernel memory: 328k freed
[   12.735766] input: AT Translated Set 2 keyboard as /class/input/input1
[   12.998799] Capability LSM initialized
[   13.060356] ACPI: Processor [CPU0] (supports 2 throttling states)
[   13.812510] usbcore: registered new interface driver usbfs
[   13.812613] usbcore: registered new interface driver hub
[   13.812703] usbcore: registered new device driver usb
[   13.814103] USB Universal Host Controller Interface driver v3.0
[   13.814242] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
[   13.814360] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   13.814366] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   13.814629] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   13.814729] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000d800
[   13.814947] usb usb1: configuration #1 chosen from 1 choice
[   13.815041] hub 1-0:1.0: USB hub found
[   13.815103] hub 1-0:1.0: 2 ports detected
[   13.916568] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 17
[   13.916696] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   13.916702] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   13.916791] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   13.916889] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000d000
[   13.917089] usb usb2: configuration #1 chosen from 1 choice
[   13.917181] hub 2-0:1.0: USB hub found
[   13.917242] hub 2-0:1.0: 2 ports detected
[   14.020446] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   14.020570] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   14.020576] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   14.020669] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   14.020770] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d400
[   14.020966] usb usb3: configuration #1 chosen from 1 choice
[   14.021058] hub 3-0:1.0: USB hub found
[   14.021124] hub 3-0:1.0: 2 ports detected
[   14.040315] Floppy drive(s): fd0 is 1.44M
[   14.075571] Linux Tulip driver version 1.1.14 (December 15, 2004)
[   14.110387] FDC 0 is a post-1991 82077
[   14.136634] SCSI subsystem initialized
[   14.144976] libata version 2.20 loaded.
[   14.150460] ata_piix 0000:00:1f.1: version 2.10ac1
[   14.150486] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[   14.150619] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   14.150704] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001f000 irq 14
[   14.150823] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001f008 irq 15
[   14.150921] scsi0 : ata_piix
[   14.312236] ata1.00: ata_hpa_resize 1: sectors = 60058656, hpa_sectors = 60058656
[   14.312318] ata1.00: ATA-7: Maxtor 6E030L0, NAR61590, max UDMA/133
[   14.312375] ata1.00: 60058656 sectors, multi 16: LBA 
[   14.320214] ata1.00: ata_hpa_resize 1: sectors = 60058656, hpa_sectors = 60058656
[   14.320283] ata1.00: configured for UDMA/100
[   14.320352] scsi1 : ata_piix
[   14.803965] ata2.00: ATAPI, max UDMA/33
[   14.804026] ata2.01: ATAPI, max UDMA/33
[   14.983901] ata2.00: configured for UDMA/33
[   44.946684] ata2.01: qc timeout (cmd 0xef)
[   44.946756] ata2.01: failed to set xfermode (err_mask=0x4)
[   44.946813] ata2: failed to recover some devices, retrying in 5 secs
[   50.592498] ata2.00: configured for UDMA/33
[   80.555435] ata2.01: qc timeout (cmd 0xef)
[   80.555504] ata2.01: failed to set xfermode (err_mask=0x4)
[   80.555564] ata2.01: limiting speed to UDMA/33:PIO3
[   80.555619] ata2: failed to recover some devices, retrying in 5 secs
[   86.201251] ata2.00: configured for UDMA/33
[  116.164188] ata2.01: qc timeout (cmd 0xef)
[  116.164257] ata2.01: failed to set xfermode (err_mask=0x4)
[  116.164315] ata2.01: disabled
[  116.164369] ata2: failed to recover some devices, retrying in 5 secs
[  121.162124] ata2.00: failed to set xfermode (err_mask=0x40)
[  121.162187] ata2: failed to recover some devices, retrying in 5 secs
[  126.648128] ata2.00: configured for UDMA/33
[  126.648382] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 6E030L0   NAR6 PQ: 0 ANSI: 5
[  126.652031] scsi 1:0:0:0: CD-ROM            HL-DT-ST CD-ROM GCR-8481B 1.06 PQ: 0 ANSI: 5
[  126.653020] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 19
[  126.653146] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[  126.653152] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[  126.653455] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[  126.653572] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[  126.653587] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xee080000
[  126.657526] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[  126.658281] usb usb4: configuration #1 chosen from 1 choice
[  126.658621] hub 4-0:1.0: USB hub found
[  126.658690] hub 4-0:1.0: 6 ports detected
[  126.678820] SCSI device sda: 60058656 512-byte hdwr sectors (30750 MB)
[  126.678914] sda: Write Protect is off
[  126.678968] sda: Mode Sense: 00 3a 00 00
[  126.678996] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  126.679156] SCSI device sda: 60058656 512-byte hdwr sectors (30750 MB)
[  126.679227] sda: Write Protect is off
[  126.679281] sda: Mode Sense: 00 3a 00 00
[  126.679307] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  126.679380]  sda:<6>ACPI: PCI Interrupt 0000:01:06.0[A] -> GSI 18 (level, low) -> IRQ 18
[  126.764460] tulip0:  MII transceiver #1 config 1000 status 786d advertising 01e1.
[  126.771881] eth0: ADMtek Comet rev 17 at Port 0xc800, 00:04:5A:7E:25:CF, IRQ 18.
[  127.384110]  sda1 sda2 < sda5 >
[  127.406990] sd 0:0:0:0: Attached scsi disk sda
[  127.414272] sd 0:0:0:0: Attached scsi generic sg0 type 0
[  127.414536] sr 1:0:0:0: Attached scsi generic sg1 type 5
[  127.434302] sr0: scsi3-mmc drive: 48x/48x cd/rw xa/form2 cdda tray
[  127.434371] Uniform CD-ROM driver Revision: 3.20
[  127.434531] sr 1:0:0:0: Attached scsi CD-ROM sr0
[  127.621143] Attempting manual resume
[  127.621199] swsusp: Resume From Partition 8:5
[  127.621202] PM: Checking swsusp image.
[  127.621482] PM: Resume from disk failed.
[  127.679654] kjournald starting.  Commit interval 5 seconds
[  127.679732] EXT3-fs: mounted filesystem with ordered data mode.
[  140.149416] NET: Registered protocol family 17
[  140.855052] i810_smbus 0000:00:02.0: i810/i815 i2c device found.
[  140.901218] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[  140.904780] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[  141.103216] intel_rng: FWH not detected
[  141.149271] Linux agpgart interface v0.102 (c) Dave Jones
[  141.150415] iTCO_vendor_support: vendor-support=0
[  141.152016] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[  141.152213] iTCO_wdt: Found a ICH4 TCO device (Version=1, TCOBASE=0x0460)
[  141.152323] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[  141.155708] agpgart: Detected an Intel 845G Chipset.
[  141.155916] agpgart: Detected 892K stolen memory.
[  141.174432] agpgart: AGP aperture is 128M @ 0xe0000000
[  141.783163] 0000:01:06.0: tulip_stop_rxtx() failed (CSR5 0xfc664010 CSR6 0xff972113)
[  141.783177] eth0: Setting full-duplex based on MII#1 link partner capability of 45e1.
[  141.894131] gameport: EMU10K1 is pci0000:01:04.1/gameport0, io 0xc400, speed 932kHz
[  142.265325] input: PC Speaker as /class/input/input2
[  142.278616] parport: PnPBIOS parport detected.
[  142.278707] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[  142.534617] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 20
[  142.534763] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[  142.587414] input: ImPS/2 Generic Wheel Mouse as /class/input/input3
[  142.855754] intel8x0_measure_ac97_clock: measured 58084 usecs
[  142.855821] intel8x0: clocking to 48000
[  142.857690] ACPI: PCI Interrupt 0000:01:04.0[A] -> GSI 16 (level, low) -> IRQ 16
[  143.191087] fuse init (API version 7.8)
[  143.228703] lp0: using parport0 (interrupt-driven).
[  143.274702] Adding 1277128k swap on /dev/disk/by-uuid/228bf93f-0d66-4327-97f7-77c44304110a.  Priority:-1 extents:1 across:1277128k
[  143.419695] EXT3 FS on sda1, internal journal
[  143.651182] NET: Registered protocol family 10
[  143.651322] lo: Disabled Privacy Extensions
[  150.430478] ibm_acpi: ec object not found
[  150.469614] Using specific hotkey driver
[  150.601806] No dock devices found.
[  150.686313] input: Power Button (FF) as /class/input/input4
[  150.686672] ACPI: Power Button (FF) [PWRF]
[  150.710265] input: Power Button (CM) as /class/input/input5
[  150.710581] ACPI: Power Button (CM) [PWRB]
[  150.787561] pcc_acpi: loading...
[  154.617460] eth0: no IPv6 routers present
[  156.602752] ppdev: user-space parallel port driver
[  157.058779] [drm] Initialized drm 1.1.0 20060810
[  157.206097] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[  157.210147] [drm] Initialized i915 1.6.0 20060119 on minor 0
[  158.711603] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[  158.711611] apm: overridden by ACPI.
[  159.040595] Bluetooth: Core ver 2.11
[  159.040689] NET: Registered protocol family 31
[  159.040692] Bluetooth: HCI device and connection manager initialized
[  159.040697] Bluetooth: HCI socket layer initialized
[  159.101363] Bluetooth: L2CAP ver 2.8
[  159.101370] Bluetooth: L2CAP socket layer initialized
[  159.225980] Bluetooth: RFCOMM socket layer initialized
[  159.226001] Bluetooth: RFCOMM TTY layer initialized
[  159.226004] Bluetooth: RFCOMM ver 1.8
[  176.450951] eth0: no IPv6 routers present

```

---

### Post by pt123 on 2007-09-28
If you are getting failed to set xfermode on older CD drives try this solution:
[http://fak3r.com/2007/06/22/failed-to-set-xfermode-solved/](http://fak3r.com/2007/06/22/failed-to-set-xfermode-solved/)

In grub, “…at the end of this new menu item add it as an argument to the line:
```

# defoptions=quiet splash irqpoll

```


You just need to ad `irqpoll` to your grub line. So in so in /boot/grub/menu.lst I added irqpoll to the kernel line:
```

kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=495b ro quiet splash irqpoll

```

---

