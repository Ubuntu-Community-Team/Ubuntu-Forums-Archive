---
title: "Random freezes"
date: 2006-07-24
forum: General Help
---

### Post by Carlsson on 2006-07-24
My computer seems to hate linux. After i log in the computer runs fine for a minute and then freezes. Ctrl+Alt+Backspace/Ctrl+Alt+F1 doesnt work. The only thing that works on the screen is the mouse. I use Ubuntu 5.10

At first i thought it was my graphics card(I use a ATI Radeon 9200SE) so i tried some of the advice i found in this forum. Nothing works!

Im a Linux newbie, but i love it. so please help me!

My computer:
CPU: Intel Celeron 2.60GHz
GC: ATI Radeon 9200SE

if there is anything else you need to know, tell me what.

Thanks

---

### Post by jordilin on 2006-07-24
Take a look at the file /var/log/messages and tell us what it says. This file logs all the activity of your computer. Most probably is a hardware problem

---

### Post by Carlsson on 2006-07-24
I noticed some of it is in swedish, will that matter?
*Edit: Translated.*

> Jul 25 00:59:12 localhost syslogd 1.4.1#17ubuntu3: restart.
Jul 25 00:59:13 localhost kernel: Inspecting /boot/System.map-2.6.12-10-686
Jul 25 00:59:13 localhost kernel: Loaded 28233 symbols from /boot/System.map-2.6.12-10-686.
Jul 25 00:59:13 localhost kernel: Symbols match kernel version 2.6.12.
Jul 25 00:59:13 localhost kernel: No module symbols loaded - kernel modules not enabled.
Jul 25 00:59:13 localhost kernel: fec00000)
Jul 25 00:59:13 localhost kernel: [4294667.296000] Initializing CPU#0
Jul 25 00:59:13 localhost kernel: [4294667.296000] PID hash table entries: 2048 (order: 11, 32768 bytes)
Jul 25 00:59:13 localhost kernel: [4294667.296000] Detected 2600.430 MHz processor.
Jul 25 00:59:13 localhost kernel: [4294667.296000] Using pmtmr for high-res timesource
Jul 25 00:59:13 localhost kernel: [4294667.296000] Console: colour VGA+ 80x25
Jul 25 00:59:13 localhost kernel: [4294667.678000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Jul 25 00:59:13 localhost kernel: [4294667.679000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Jul 25 00:59:13 localhost kernel: [4294667.690000] Memory: 510476k/524272k available (1623k kernel code, 13188k reserved, 730k data, 168k init, 0k highmem)
Jul 25 00:59:13 localhost kernel: [4294667.690000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Jul 25 00:59:13 localhost kernel: [4294667.713000] Security Framework v1.0.0 initialized
Jul 25 00:59:13 localhost kernel: [4294667.713000] SELinux: Disabled at boot.
Jul 25 00:59:13 localhost kernel: [4294667.713000] Mount-cache hash table entries: 512
Jul 25 00:59:13 localhost kernel: [4294667.713000] CPU: Trace cache: 12K uops, L1 D cache: 8K
Jul 25 00:59:13 localhost kernel: [4294667.713000] CPU: L2 cache: 128K
Jul 25 00:59:13 localhost kernel: [4294667.713000] Intel machine check architecture supported.
Jul 25 00:59:13 localhost kernel: [4294667.713000] Intel machine check reporting enabled on CPU#0.
Jul 25 00:59:13 localhost kernel: [4294667.713000] CPU0: Intel P4/Xeon Extended MCE MSRs (12) available
Jul 25 00:59:13 localhost kernel: [4294667.713000] CPU0: Thermal monitoring enabled
Jul 25 00:59:13 localhost kernel: [4294667.713000] CPU: Intel(R) Celeron(R) CPU 2.60GHz stepping 09
Jul 25 00:59:13 localhost kernel: [4294667.713000] Enabling fast FPU save and restore... done.
Jul 25 00:59:13 localhost kernel: [4294667.713000] Enabling unmasked SIMD FPU exception support... done.
Jul 25 00:59:13 localhost kernel: [4294667.713000] Checking 'hlt' instruction... OK.
Jul 25 00:59:13 localhost kernel: [4294667.717000] checking if image is initramfs... it is
Jul 25 00:59:13 localhost kernel: [4294668.224000] Freeing initrd memory: 5498k freed
Jul 25 00:59:13 localhost kernel: [4294668.225000] ACPI: Looking for DSDT in initrd... not found!
Jul 25 00:59:13 localhost kernel: [4294668.274000] not found!
Jul 25 00:59:13 localhost kernel: [4294668.278000] ENABLING IO-APIC IRQs
Jul 25 00:59:13 localhost kernel: [4294668.278000] ..TIMER: vector=0x31 pin1=2 pin2=-1
Jul 25 00:59:13 localhost kernel: [4294668.389000] NET: Registered protocol family 16
Jul 25 00:59:13 localhost kernel: [4294668.389000] ACPI: bus type pci registered
Jul 25 00:59:13 localhost kernel: [4294668.390000] PCI: PCI BIOS revision 2.10 entry at 0xf10f0, last bus=1
Jul 25 00:59:13 localhost kernel: [4294668.390000] PCI: Using configuration type 1
Jul 25 00:59:13 localhost kernel: [4294668.390000] mtrr: v2.0 (20020519)
Jul 25 00:59:13 localhost kernel: [4294668.390000] ACPI: Subsystem revision 20050729
Jul 25 00:59:13 localhost kernel: [4294668.398000] ACPI: Interpreter enabled
Jul 25 00:59:13 localhost kernel: [4294668.398000] ACPI: Using IOAPIC for interrupt routing
Jul 25 00:59:13 localhost kernel: [4294668.399000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
Jul 25 00:59:13 localhost kernel: [4294668.400000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
Jul 25 00:59:13 localhost kernel: [4294668.400000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *10 11 12 14 15)
Jul 25 00:59:13 localhost kernel: [4294668.400000] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 6 7 10 11 12 14 15)
Jul 25 00:59:13 localhost kernel: [4294668.401000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 6 7 10 11 12 14 15)
Jul 25 00:59:13 localhost kernel: [4294668.401000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *9
Jul 25 00:59:13 localhost kernel: [4294668.401000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
Jul 25 00:59:13 localhost kernel: [4294668.402000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 12 14 15) *9
Jul 25 00:59:13 localhost kernel: [4294668.402000] ACPI: PCI Root Bridge [PCI0] (0000:00)
Jul 25 00:59:13 localhost kernel: [4294668.402000] PCI: Probing PCI hardware (bus 00)
Jul 25 00:59:13 localhost kernel: [4294668.402000] ACPI: Assume root bridge [\_SB_.PCI0] segment is 0
Jul 25 00:59:13 localhost kernel: [4294668.402000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
Jul 25 00:59:13 localhost kernel: [4294668.405000] Enabling SiS 96x SMBus.
Jul 25 00:59:13 localhost kernel: [4294668.405000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:02.5
Jul 25 00:59:13 localhost kernel: [4294668.413000] Linux Plug and Play Support v0.97 (c) Adam Belay
Jul 25 00:59:13 localhost kernel: [4294668.413000] pnp: PnP ACPI init
Jul 25 00:59:13 localhost kernel: [4294668.418000] pnp: PnP ACPI: found 15 devices
Jul 25 00:59:13 localhost kernel: [4294668.418000] PnPBIOS: Disabled by ACPI PNP
Jul 25 00:59:13 localhost kernel: [4294668.418000] PCI: Using ACPI for IRQ routing
Jul 25 00:59:13 localhost kernel: [4294668.418000] PCI: If a device doesn't work, try "pci=routeirq". If it helps, post a report
Jul 25 00:59:13 localhost kernel: [4294668.426000] pnp: 00:01: ioport range 0xe400-0xe47f could not be reserved
Jul 25 00:59:13 localhost kernel: [4294668.426000] pnp: 00:01: ioport range 0xe480-0xe4ff has been reserved
Jul 25 00:59:13 localhost kernel: [4294668.426000] pnp: 00:01: ioport range 0xe600-0xe61f has been reserved
Jul 25 00:59:13 localhost kernel: [4294668.426000] pnp: 00:01: ioport range 0x480-0x48f has been reserved
Jul 25 00:59:13 localhost kernel: [4294668.426000] pnp: 00:0e: ioport range 0x295-0x296 has been reserved
Jul 25 00:59:13 localhost kernel: [4294668.427000] Simple Boot Flag at 0x3a set to 0x1
Jul 25 00:59:13 localhost kernel: [4294668.427000] audit: initializing netlink socket (disabled)
Jul 25 00:59:13 localhost kernel: [4294668.427000] audit: initialized
Jul 25 00:59:13 localhost kernel: [4294668.427000] VFS: Disk quotas dquot_6.5.1
Jul 25 00:59:13 localhost kernel: [4294668.427000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Jul 25 00:59:13 localhost kernel: [4294668.427000] devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
Jul 25 00:59:13 localhost kernel: [4294668.427000] devfs: boot_options: 0x0
Jul 25 00:59:13 localhost kernel: [4294668.427000] Initializing Cryptographic API
Jul 25 00:59:13 localhost kernel: [4294668.428000] isapnp: Scanning for PnP cards...
Jul 25 00:59:13 localhost kernel: [4294668.782000] isapnp: No Plug & Play device found
Jul 25 00:59:13 localhost kernel: [4294668.834000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Jul 25 00:59:13 localhost kernel: [4294669.508000] serio: i8042 AUX port at 0x60,0x64 irq 12
Jul 25 00:59:13 localhost kernel: [4294669.508000] serio: i8042 KBD port at 0x60,0x64 irq 1
Jul 25 00:59:13 localhost kernel: [4294669.508000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
Jul 25 00:59:13 localhost kernel: [4294669.508000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jul 25 00:59:13 localhost kernel: [4294669.513000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jul 25 00:59:13 localhost kernel: [4294669.514000] io scheduler noop registered
Jul 25 00:59:13 localhost kernel: [4294669.514000] io scheduler anticipatory registered
Jul 25 00:59:13 localhost kernel: [4294669.514000] io scheduler deadline registered
Jul 25 00:59:13 localhost kernel: [4294669.514000] io scheduler cfq registered
Jul 25 00:59:13 localhost kernel: [4294669.514000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Jul 25 00:59:13 localhost kernel: [4294669.515000] NET: Registered protocol family 2
Jul 25 00:59:13 localhost kernel: [4294669.524000] IP: routing cache hash table of 4096 buckets, 32Kbytes
Jul 25 00:59:13 localhost kernel: [4294669.524000] TCP established hash table entries: 32768 (order: 6, 262144 bytes)
Jul 25 00:59:13 localhost kernel: [4294669.524000] TCP bind hash table entries: 32768 (order: 5, 131072 bytes)
Jul 25 00:59:13 localhost kernel: [4294669.524000] TCP: Hash tables configured (established 32768 bind 3276
Jul 25 00:59:13 localhost kernel: [4294669.525000] NET: Registered protocol family 8
Jul 25 00:59:13 localhost kernel: [4294669.525000] NET: Registered protocol family 20
Jul 25 00:59:13 localhost kernel: [4294669.525000] ACPI wakeup devices:
Jul 25 00:59:13 localhost kernel: [4294669.525000] PCI0 PCI1 PS2K PS2M USB3 USB1
Jul 25 00:59:13 localhost kernel: [4294669.525000] ACPI: (supports S0 S1 S4 S5)
Jul 25 00:59:13 localhost kernel: [4294669.525000] Freeing unused kernel memory: 168k freed
Jul 25 00:59:13 localhost kernel: [4294669.565000] input: AT Translated Set 2 keyboard on isa0060/serio0
Jul 25 00:59:13 localhost kernel: [4294669.578000] vga16fb: mapped to 0xc00a0000
Jul 25 00:59:13 localhost kernel: [4294669.683000] Console: switching to colour frame buffer device 80x30
Jul 25 00:59:13 localhost kernel: [4294669.683000] fb0: VGA16 VGA frame buffer device
Jul 25 00:59:13 localhost kernel: [4294670.833000] Capability LSM initialized
Jul 25 00:59:13 localhost kernel: [4294670.848000] NET: Registered protocol family 1
Jul 25 00:59:13 localhost kernel: [4294670.864000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Jul 25 00:59:13 localhost kernel: [4294670.864000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Jul 25 00:59:13 localhost kernel: [4294670.864000] ACPI: bus type ide registered
Jul 25 00:59:13 localhost kernel: [4294670.876000] SIS5513: IDE controller at PCI slot 0000:00:02.5
Jul 25 00:59:13 localhost kernel: [4294670.876000] ACPI: PCI Interrupt 0000:00:02.5[A] -> GSI 16 (level, low) -> IRQ 16
Jul 25 00:59:13 localhost kernel: [4294670.876000] SIS5513: chipset revision 0
Jul 25 00:59:13 localhost kernel: [4294670.876000] SIS5513: not 100%% native mode: will probe irqs later
Jul 25 00:59:13 localhost kernel: [4294670.876000] SIS5513: SiS 962/963 MuTIOL IDE UDMA133 controller
Jul 25 00:59:13 localhost kernel: [4294670.876000] ide0: BM-DMA at 0xa400-0xa407, BIOS settings: hdaMA, hdbio
Jul 25 00:59:13 localhost kernel: [4294670.877000] ide1: BM-DMA at 0xa408-0xa40f, BIOS settings: hdcMA, hddMA
Jul 25 00:59:13 localhost kernel: [4294671.140000] hda: Maxtor 91080D5, ATA DISK drive
Jul 25 00:59:13 localhost kernel: [4294671.752000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Jul 25 00:59:13 localhost kernel: [4294672.118000] hdc: TSSTcorpCD/DVDW TS-H552B, ATAPI CD/DVD-ROM drive
Jul 25 00:59:13 localhost kernel: [4294672.373000] hdd: WDC WD400BB-71CAA1, ATA DISK drive
Jul 25 00:59:13 localhost kernel: [4294672.424000] ide1 at 0x170-0x177,0x376 on irq 15
Jul 25 00:59:13 localhost kernel: [4294674.479000] hda: max request size: 128KiB
Jul 25 00:59:13 localhost kernel: [4294674.487000] hda: 21095424 sectors (10800 MB) w/512KiB Cache, CHS=20928/16/63, UDMA(33)
Jul 25 00:59:13 localhost kernel: [4294674.487000] hda: cache flushes not supported
Jul 25 00:59:13 localhost kernel: [4294674.487000] /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >
Jul 25 00:59:13 localhost kernel: [4294674.518000] hdd: max request size: 128KiB
Jul 25 00:59:13 localhost kernel: [4294674.545000] hdd: Host Protected Area detected.
Jul 25 00:59:13 localhost kernel: [4294674.545000] ^Icurrent capacity is 78198750 sectors (40037 MB)
Jul 25 00:59:13 localhost kernel: [4294674.545000] ^Inative capacity is 78199632 sectors (40038 MB)
Jul 25 00:59:13 localhost kernel: [4294674.547000] hdd: Host Protected Area disabled.
Jul 25 00:59:13 localhost kernel: [4294674.547000] hdd: 78199632 sectors (40038 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
Jul 25 00:59:13 localhost kernel: [4294674.547000] hdd: cache flushes not supported
Jul 25 00:59:13 localhost kernel: [4294674.547000] /dev/ide/host0/bus1/target1/lun0: p1
Jul 25 00:59:13 localhost kernel: [4294674.557000] hdc: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache
Jul 25 00:59:13 localhost kernel: [4294674.557000] Uniform CD-ROM driver Revision: 3.20
Jul 25 00:59:13 localhost kernel: [4294675.126000] Attempting manual resume
Jul 25 00:59:13 localhost kernel: [4294675.127000] swsusp: Suspend partition has wrong signature?
Jul 25 00:59:13 localhost kernel: [4294675.183000] usbcore: registered new driver usbfs
Jul 25 00:59:13 localhost kernel: [4294675.183000] usbcore: registered new driver hub
Jul 25 00:59:13 localhost kernel: [4294675.184000] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 20 (level, low) -> IRQ 20
Jul 25 00:59:13 localhost kernel: [4294675.184000] ohci_hcd 0000:00:03.0: Silicon Integrated Systems [SiS] USB 1.0 Controller
Jul 25 00:59:13 localhost kernel: [4294675.195000] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
Jul 25 00:59:13 localhost kernel: [4294675.195000] ohci_hcd 0000:00:03.0: irq 20, io mem 0xce800000
Jul 25 00:59:13 localhost kernel: [4294675.248000] hub 1-0:1.0: USB hub found
Jul 25 00:59:13 localhost kernel: [4294675.248000] hub 1-0:1.0: 3 ports detected
Jul 25 00:59:13 localhost kernel: [4294675.251000] ACPI: PCI Interrupt 0000:00:03.1[b] -> GSI 21 (level, low) -> IRQ 21
Jul 25 00:59:13 localhost kernel: [4294675.251000] ohci_hcd 0000:00:03.1: Silicon Integrated Systems [SiS] USB 1.0 Controller (#2)
Jul 25 00:59:13 localhost kernel: [4294675.262000] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 2
Jul 25 00:59:13 localhost kernel: [4294675.262000] ohci_hcd 0000:00:03.1: irq 21, io mem 0xce000000
Jul 25 00:59:13 localhost kernel: [4294675.315000] hub 2-0:1.0: USB hub found
Jul 25 00:59:13 localhost kernel: [4294675.315000] hub 2-0:1.0: 3 ports detected
Jul 25 00:59:13 localhost kernel: [4294675.334000] ACPI: PCI Interrupt 0000:00:03.2[D] -> GSI 23 (level, low) -> IRQ 23
Jul 25 00:59:13 localhost kernel: [4294675.334000] ehci_hcd 0000:00:03.2: Silicon Integrated Systems [SiS] USB 2.0 Controller
Jul 25 00:59:13 localhost kernel: [4294675.334000] ehci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 3
Jul 25 00:59:13 localhost kernel: [4294675.334000] ehci_hcd 0000:00:03.2: irq 23, io mem 0xcd800000
Jul 25 00:59:13 localhost kernel: [4294675.334000] ehci_hcd 0000:00:03.2: USB 2.0 initialized, EHCI 1.00, driver 10 Dec 2004
Jul 25 00:59:13 localhost kernel: [4294675.335000] hub 3-0:1.0: USB hub found
Jul 25 00:59:13 localhost kernel: [4294675.335000] hub 3-0:1.0: 6 ports detected
Jul 25 00:59:13 localhost kernel: [4294675.365000] sis900.c: v1.08.08 Jan. 22 2005
Jul 25 00:59:13 localhost kernel: [4294675.365000] ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 19 (level, low) -> IRQ 19
Jul 25 00:59:13 localhost kernel: [4294675.367000] 0000:00:04.0: Realtek RTL8201 PHY transceiver found at address 1.
Jul 25 00:59:13 localhost kernel: [4294675.378000] 0000:00:04.0: Using transceiver found at address 1 as default
Jul 25 00:59:13 localhost kernel: [4294675.379000] eth0: SiS 900 PCI Fast Ethernet at 0x8800, IRQ 19, 00:0c:6e:b9:f2:a3.
Jul 25 00:59:13 localhost kernel: [4294675.389000] via-rhine.c:v1.10-LK1.2.0-2.6 June-10-2004 Written by Donald Becker
Jul 25 00:59:13 localhost kernel: [4294675.389000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> GSI 18 (level, low) -> IRQ 18
Jul 25 00:59:13 localhost kernel: [4294675.389000] PCI: Via IRQ fixup for 0000:00:0a.0, from 10 to 2
Jul 25 00:59:13 localhost kernel: [4294675.394000] eth1: VIA Rhine II at 0x18400, 00:05:5d:64:11:e0, IRQ 18.
Jul 25 00:59:13 localhost kernel: [4294675.394000] eth1: MII PHY found at address 8, status 0x782d advertising 01e1 Link 41e1.
Jul 25 00:59:13 localhost kernel: [4294675.889000] usb 3-2: new high speed USB device using ehci_hcd and address 3
Jul 25 00:59:13 localhost kernel: [4294675.964000] usb 3-2: configuration #1 chosen from 2 choices
Jul 25 00:59:13 localhost kernel: [4294676.141000] usb 1-1: new low speed USB device using ohci_hcd and address 2
Jul 25 00:59:13 localhost kernel: [4294677.437000] usbcore: registered new driver hiddev
Jul 25 00:59:13 localhost kernel: [4294677.445000] input: USB HID v1.00 Joystick [6666:0667] on usb-0000:00:03.0-1
Jul 25 00:59:13 localhost kernel: [4294677.445000] usbcore: registered new driver usbhid
Jul 25 00:59:13 localhost kernel: [4294677.445000] drivers/usb/input/hid-core.c: v2.01:USB HID core driver
Jul 25 00:59:13 localhost kernel: [4294677.472000] SCSI subsystem initialized
Jul 25 00:59:13 localhost kernel: [4294677.474000] Initializing USB Mass Storage driver...
Jul 25 00:59:13 localhost kernel: [4294677.474000] scsi0 : SCSI emulation for USB Mass Storage devices
Jul 25 00:59:13 localhost kernel: [4294677.474000] usbcore: registered new driver usb-storage
Jul 25 00:59:13 localhost kernel: [4294677.474000] USB Mass Storage support registered.
Jul 25 00:59:13 localhost kernel: [4294678.161000] ACPI: CPU0 (power states: C1[C1])
Jul 25 00:59:13 localhost kernel: [4294678.394000] Attempting manual resume
Jul 25 00:59:13 localhost kernel: [4294678.421000] swsusp: Suspend partition has wrong signature?
Jul 25 00:59:13 localhost kernel: [4294678.430000] EXT3-fs: INFO: recovery required on readonly filesystem.
Jul 25 00:59:13 localhost kernel: [4294678.430000] EXT3-fs: write access will be enabled during recovery.
Jul 25 00:59:13 localhost kernel: [4294681.337000] kjournald starting. Commit interval 5 seconds
Jul 25 00:59:13 localhost kernel: [4294681.337000] EXT3-fs: recovery complete.
Jul 25 00:59:13 localhost kernel: [4294681.344000] EXT3-fs: mounted filesystem with ordered data mode.
Jul 25 00:59:13 localhost kernel: [4294682.474000] Vendor: Apple Model: iPod Rev: 1.62
Jul 25 00:59:13 localhost kernel: [4294682.474000] Type: Direct-Access ANSI SCSI revision: 00
Jul 25 00:59:13 localhost kernel: [4294683.531000] SCSI device sda: 3999744 512-byte hdwr sectors (2048 MB)
Jul 25 00:59:13 localhost kernel: [4294683.532000] sda: Write Protect is off
Jul 25 00:59:13 localhost kernel: [4294683.570000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
Jul 25 00:59:13 localhost kernel: [4294683.624000] SCSI device sda: 3999744 512-byte hdwr sectors (2048 MB)
Jul 25 00:59:13 localhost kernel: [4294683.644000] sda: Write Protect is off
Jul 25 00:59:13 localhost kernel: [4294683.644000] /dev/scsi/host0/bus0/target0/lun0: p1 p2
Jul 25 00:59:13 localhost kernel: [4294683.701000] Attached scsi removable disk sda at scsi0, channel 0, id 0, lun 0
Jul 25 00:59:13 localhost kernel: [4294688.102000] Adding 465844k swap on /dev/hda5. Priority:-1 extents:1
Jul 25 00:59:13 localhost kernel: [4294688.417000] EXT3 FS on hda1, internal journal
Jul 25 00:59:13 localhost kernel: [4294694.977000] parport: PnPBIOS parport detected.
Jul 25 00:59:13 localhost kernel: [4294694.977000] parport0: PC-style at 0x378 (0x77, irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
Jul 25 00:59:13 localhost kernel: [4294695.066000] lp0: using parport0 (interrupt-driven).
Jul 25 00:59:13 localhost kernel: [4294695.102000] mice: PS/2 mouse device common for all mice
Jul 25 00:59:13 localhost kernel: [4294695.700000] input: PS2++ Logitech MX Mouse on isa0060/serio1
Jul 25 00:59:13 localhost kernel: [4294696.358000] ts: Compaq touchscreen protocol output
Jul 25 00:59:13 localhost kernel: [4294697.835000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
Jul 25 00:59:13 localhost kernel: [4294699.236000] cdrom: open failed.
Jul 25 00:59:13 localhost kernel: [4294701.865000] Linux agpgart interface v0.101 (c) Dave Jones
Jul 25 00:59:13 localhost kernel: [4294701.987000] agpgart: Detected SiS 648 chipset
Jul 25 00:59:13 localhost kernel: [4294702.012000] agpgart: AGP aperture is 128M @ 0xd0000000
Jul 25 00:59:13 localhost kernel: [4294702.322000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jul 25 00:59:13 localhost kernel: [4294703.011000] i2c-sis96x version 1.0.0
Jul 25 00:59:13 localhost kernel: [4294703.016000] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0xe600
Jul 25 00:59:13 localhost kernel: [4294705.308000] ACPI: PCI Interrupt 0000:00:02.7[C] -> GSI 18 (level, low) -> IRQ 18
Jul 25 00:59:13 localhost kernel: [4294705.663000] AC'97 0 analog subsections not ready
Jul 25 00:59:13 localhost kernel: [4294705.723000] intel8x0_measure_ac97_clock: measured 49392 usecs
Jul 25 00:59:13 localhost kernel: [4294705.723000] intel8x0: clocking to 48000
Jul 25 00:59:13 localhost kernel: [4294708.445000] Real Time Clock Driver v1.12
Jul 25 00:59:13 localhost kernel: [4294708.561000] input: PC Speaker
Jul 25 00:59:13 localhost kernel: [4294708.718000] Floppy drive(s): fd0 is 1.44M
Jul 25 00:59:13 localhost kernel: [4294708.733000] FDC 0 is a post-1991 82077
Jul 25 00:59:13 localhost kernel: [4294710.811000] eth1: link up, 100Mbps, full-duplex, lpa 0x41E1
Jul 25 00:59:13 localhost kernel: [4294710.846000] NET: Registered protocol family 17
Jul 25 00:59:13 localhost kernel: [4294714.098000] NET: Registered protocol family 10
Jul 25 00:59:13 localhost kernel: [4294714.098000] Disabled Privacy Extensions on device c031eb40(lo)
Jul 25 00:59:13 localhost kernel: [4294714.098000] IPv6 over IPv4 tunneling driver
Jul 25 00:59:13 localhost kernel: [4294715.719000] ACPI: Power Button (FF) [PWRF]
Jul 25 00:59:13 localhost kernel: [4294715.719000] ACPI: Power Button (CM) [PWRB]
Jul 25 00:59:21 localhost hpiod: 0.9.5 accepting connections at 32769...
Jul 25 00:59:21 localhost hp: unable to open /var/run/hplip/hpssd.port: No such file or directory: prnt/hpijs/hplip_api.c 84
Jul 25 00:59:21 localhost hp: unable to connect hpssd socket 50002: Connection refused: prnt/hpijs/hplip_api.c 710
Jul 25 00:59:21 localhost kernel: [4294725.441000] [drm] Initialized drm 1.0.0 20040925
Jul 25 00:59:21 localhost kernel: [4294725.465000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Jul 25 00:59:21 localhost kernel: [4294725.467000] [drm] Initialized radeon 1.16.0 20050311 on minor 0: ATI Technologies Inc RV280 [Radeon 9200 SE]
Jul 25 00:59:21 localhost kernel: [4294725.469000] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
Jul 25 00:59:21 localhost kernel: [4294725.469000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 4x mode
Jul 25 00:59:21 localhost kernel: [4294725.469000] agpgart: SiS delay workaround: giving bridge time to recover.
Jul 25 00:59:21 localhost kernel: [4294725.480000] agpgart: Putting AGP V3 device at 0000:01:00.0 into 4x mode
Jul 25 00:59:21 localhost kernel: [4294725.485000] [drm] Loading R200 Microcode
Jul 25 00:59:26 localhost kernel: [4294729.660000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Jul 25 00:59:26 localhost kernel: [4294729.660000] apm: overridden by ACPI.
Jul 25 00:59:28 localhost kernel: [4294731.988000] Bluetooth: Core ver 2.7
Jul 25 00:59:28 localhost kernel: [4294731.988000] NET: Registered protocol family 31
Jul 25 00:59:28 localhost kernel: [4294731.988000] Bluetooth: HCI device and connection manager initialized
Jul 25 00:59:28 localhost kernel: [4294731.988000] Bluetooth: HCI socket layer initialized
Jul 25 00:59:28 localhost kernel: [4294732.042000] Bluetooth: L2CAP ver 2.7
Jul 25 00:59:28 localhost kernel: [4294732.042000] Bluetooth: L2CAP socket layer initialized
Jul 25 00:59:28 localhost kernel: [4294732.090000] Bluetooth: RFCOMM ver 1.5
Jul 25 00:59:28 localhost kernel: [4294732.090000] Bluetooth: RFCOMM socket layer initialized
Jul 25 00:59:28 localhost kernel: [4294732.090000] Bluetooth: RFCOMM TTY layer initialized
Jul 25 00:59:46 localhost gconfd (daniel-7650): starting (version 2.12.0), pid 7650 user "daniel"
Jul 25 00:59:46 localhost gconfd (daniel-7650): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only config source at position 0
Jul 25 00:59:46 localhost gconfd (daniel-7650): Resolved address "xml:readonly:/usr/share/gconf/local.mandatory" to a read-only config source at position 1
Jul 25 00:59:46 localhost gconfd (daniel-7650): Resolved address "xml:readwrite:/home/daniel/.gconf" till en skrivbar konfigurationskÃ¤lla pÃ¥ position 2
Jul 25 00:59:46 localhost gconfd (daniel-7650): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only config source at position 3
Jul 25 00:59:46 localhost gconfd (daniel-7650): Resolved address "xml:readonly:/usr/share/gconf/local.defaults" to a read-only config source at position 4
Jul 25 00:59:46 localhost gconfd (daniel-7650): Resolved address "xml:readonly:/usr/share/gconf/cdd.defaults" to a read-only config source at position 5
Jul 25 00:59:46 localhost gconfd (daniel-7650): Resolved address "xml:readonly:/usr/share/gconf/debian.defaults" to a read-only config source at position 6
Jul 25 00:59:46 localhost gconfd (daniel-7650): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only config source at position 7
Jul 25 00:59:58 localhost gconfd (daniel-7650): Resolved address "xml:readwrite:/home/daniel/.gconf" to a read-only config source at position 0

---

### Post by Carlsson on 2006-07-24
I couldnt paste the whole file. but if it helps you can find the whole log [here]("http://runshouse.mine.nu/messages.txt").

Please help me.

---

### Post by JoWilly on 2006-07-24
Why not update to dapper (ubuntu 6.0.6) and see if this problem was not fixed there ?

---

### Post by Carlsson on 2006-07-24
[QUOTE=JoWilly]Why not update to dapper (ubuntu 6.0.6) and see if this problem was not fixed there ?[/QUOTE]

I dont believe that will solve my problem. I have tried some other distros before, and i experience the exact same problem with all of them. I think that it is my hardware (or my own linux skills) that fails, and not the software.

BUT: if someone cant help me find any other solution to my problem i will try updating to 6.06 (but i will probably encounter the same problem there :cry: )

Thanks

---

### Post by David Whitfield on 2007-08-31
My first post.
Also new to linux I've spent weeks trying to get my mums old pooter going.  I tried all sorts of distros getting them freezing up randomly, mostly when using firefox but sometimes just opening up or doing something else.  I tried a new ethernet card, noapci, different browsers, different desktops, etc... what ever I found to try in the forums.
Always after a time, sometimes 1 min, sometimes 30mins the mouse would move but not click on anything and the keyboard was DEAD.  
After a while I foud Damn Small Linux and that went fine, what the difference? linux kernel 2.4 not 2.6, I tried an old debian distro 2.4 version and that was fine too but with no support and failed apt-gets with dependancies on 2.6 kernel pkags it was always going to a be a PITA, then I started to to look at bios, processor, motherboard and found I had a AMD K7 processor, I read somewhere about processor specific kernels and thought 'that might be a help'  Re-installed Ubuntu, apt-getted the K7 kernel I think it was just:
```
sudo apt-get install kernel 2.6.xx-k7 
```
and bobs your uncle it all just goes like it should, haven't frozen up or crashed since plus all the playing around with other distros has told me that Ubuntu is the one for me.
This might be old news to some but I never found anything about the kernel choices in the ubuntu install docs or forums so thought I'd share it.
share and share alike and thanks to all the people who post things and helped me out without knowing!

---

