---
title: "[SOLVED] Slow bootup help needed"
date: 2007-12-31
forum: General Help
---

### Post by Dbyte on 2007-12-31
Boot process is currently >6 minutes from start to desktop load completed.  I desperately need to reduce this somehow; 1 minute would be great but definitely need <2 minutes.  I have already tried disabling some startup services based on [http://ubuntuforums.org/showthread.php?t=89491]("http://ubuntuforums.org/showthread.php?t=89491").

Here is a bootchart from today:
[IMG]http://ubuntuforums.org/g/images/466567/large/1_gutsy-20071231-1.png[/IMG]
Link to full-size image is [http://ubuntuforums.org/g/index.php?n=1939](http://ubuntuforums.org/g/index.php?n=1939)
Not sure what to do w/ all this process info.  It also doesn't seem to show the entire boot process (only 200 seconds shown for a 6+ minute bootup).

Here are 2 screenshots of my sysconf:
[IMG]http://ubuntuforums.org/g/images/466567/large/1_Screenshot1.png[/IMG]
[IMG]http://ubuntuforums.org/g/images/466567/large/1_Screenshot2.png[/IMG]

I have a dual-boot environment (XP & Gutsy) running on a Compaq 2.4GHz machine, Intel Pentium 4 processor, & 2GB of RAM.  XP boots (incl. login) in ~45 seconds.

Any help/advice appreciated.  I've spent a few hours searching/reading a # of other threads about this, but nothing jumped out @ me as being a definite cause.  Hoping a guru will notice something obvious & take pity on another "newbuntu".

---

### Post by Sef on 2008-01-01
1) What is your graphics card?

2) Do you get any messages while logging in?

---

### Post by Dbyte on 2008-01-01
Graphics card is an Intel 82865G integrated graphics controller (i810).  I tried updating its driver & got message saying "xserver-xorg-video-i810 is already the newest version".  It's interesting that you mention this, as I'm thinking about getting a new video card due to screen rendering being so slow.    I have no Compiz graphic effects running & it's still really slow.  Side question: what's a good 3rd party card that has Linux drivers, sets up easily, & performs really well?

In terms of messages there is a scrolling list of messages that appear throughout the boot process.  Nothing jumps out @ me as being a critical error though.  Any suggestions on what I can search the logs for that might show a specific problem?

---

### Post by Dbyte on 2008-01-02
Update: I tried the changes indicated [_here_]("http://ubuntuforums.org/showthread.php?t=580903").  No change.  It currently takes 4:30 to get to the login screen & 6:45 to complete boot.  I looked @ my dmesg.0 (which is the latest right?) & saw the following:
```
[   13.579794] input: AT Translated Set 2 keyboard as /class/input/input1
[   33.248437] AppArmor: AppArmor initialized<5>audit(1199302852.073:2):  type=1505 info="AppArmor initialized" pid=1722
[   34.355304] fuse init (API version 7.8)
[   34.620264] Failure registering capabilities with primary security module.
[   60.081206] usbcore: registered new interface driver usbfs
```
and
```
[   73.688469] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   75.610473] Attempting manual resume
[   75.610522] swsusp: Resume From Partition 8:21
[   75.610525] PM: Checking swsusp image.
[   75.610856] PM: Resume from disk failed.
[   76.079176] kjournald starting.  Commit interval 5 seconds
[   76.079200] EXT3-fs: mounted filesystem with ordered data mode.
[  145.789214] Linux agpgart interface v0.102 (c) Dave Jones
```

The top section indicates a security failure, but SELinux is disabled here:
```
[   11.003834] SELinux:  Disabled at boot.
```

Do I need to disable AppArmor?  What about the long delay @ 13.57 due to a possible keyboard issue?  I use a M$ Wireless Comfort Keyboard 1.0A w/ its Wireless Optical Mouse 2.0.  The keyboard model is specified in System>Preferences>Keyboard.  In Device Manager the mouse is a "Microsoft PS/2-style Mouse" with most specifics being "unknown".

Any ideas on what might be causing this ridiculously long boot time, or other things I can check?

---

### Post by Dbyte on 2008-01-03
Just ran another boot - 6:05 to login & 8:10 total.  Yay for progress.:confused:
Here is my entire dmesg:
```
[    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Dec 18 08:02:57 UTC 2007 (Ubuntu 2.6.22-14.47-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007f7d0000 (usable)
[    0.000000]  BIOS-e820: 000000007f7d0000 - 000000007f7df000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007f7df000 - 000000007f800000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000ffb80000 - 0000000100000000 (reserved)
[    0.000000] 1143MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000ff780
[    0.000000] Entering add_active_range(0, 0, 522192) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   522192
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   522192
[    0.000000] On node 0 totalpages: 522192
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2287 pages used for memmap
[    0.000000]   HighMem zone: 290529 pages, LIFO batch:31
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F5460 checksum 0
[    0.000000] ACPI: RSDP 000F5460, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT 7F7D0000, 0030 (r1 A M I  OEMRSDT   7000318 MSFT       97)
[    0.000000] ACPI: FACP 7F7D0200, 0081 (r2 A M I  OEMFACP   7000318 MSFT       97)
[    0.000000] ACPI: DSDT 7F7D03F0, 350F (r1  PSLA1 PSLA1062       62 INTL  2002026)
[    0.000000] ACPI: FACS 7F7DF000, 0040
[    0.000000] ACPI: APIC 7F7D0390, 005C (r1 A M I  OEMAPIC   7000318 MSFT       97)
[    0.000000] ACPI: OEMB 7F7DF040, 003F (r1 A M I  OEMBIOS   7000318 MSFT       97)
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:2 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:2 APIC version 20
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 7f800000:80380000)
[    0.000000] Built 1 zonelists.  Total pages: 518113
[    0.000000] Kernel command line: root=UUID=6aa1d149-5887-4e02-96f4-64ed5be5bc53
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2400.231 MHz processor.
[   13.041520] Console: colour VGA+ 80x25
[   13.044084] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   13.044658] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   13.177158] Memory: 2059276k/2088768k available (2015k kernel code, 28176k reserved, 916k data, 364k init, 1171264k highmem)
[   13.177237] virtual kernel memory layout:
[   13.177238]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   13.177240]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   13.177242]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   13.177244]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   13.177245]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   13.177246]       .data : 0xc02f7de6 - 0xc03dce84   ( 916 kB)
[   13.177247]       .text : 0xc0100000 - 0xc02f7de6   (2015 kB)
[   13.177616] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   13.177754] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   13.257721] Calibrating delay using timer specific routine.. 4804.31 BogoMIPS (lpj=9608633)
[   13.257844] Security Framework v1.0.0 initialized
[   13.257899] SELinux:  Disabled at boot.
[   13.257959] Mount-cache hash table entries: 512
[   13.258183] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
[   13.258197] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   13.258276] CPU: L2 cache: 512K
[   13.258321] CPU: Physical Processor ID: 0
[   13.258367] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b080 00004400 00000000 00000000
[   13.258379] Compat vDSO mapped to ffffe000.
[   13.258440] Checking 'hlt' instruction... OK.
[   13.273872] SMP alternatives: switching to UP code
[   13.274463] Early unpacking initramfs... done
[   13.822426] ACPI: Core revision 20070126
[   13.824701] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   13.830768] CPU0: Intel(R) Pentium(R) 4 CPU 2.40GHz stepping 09
[   13.830896] SMP alternatives: switching to SMP code
[   13.831116] Booting processor 1/1 eip 3000
[   13.841246] Initializing CPU#1
[   13.920743] Calibrating delay using timer specific routine.. 4800.53 BogoMIPS (lpj=9601079)
[   13.920753] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
[   13.920765] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   13.920768] CPU: L2 cache: 512K
[   13.920771] CPU: Physical Processor ID: 0
[   13.920774] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b080 00004400 00000000 00000000
[   13.921046] CPU1: Intel(R) Pentium(R) 4 CPU 2.40GHz stepping 09
[   13.921436] Total of 2 processors activated (9604.85 BogoMIPS).
[   13.921615] ENABLING IO-APIC IRQs
[   13.921851] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   14.068673] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   14.088740] Brought up 2 CPUs
[   14.667239] migration_cost=23
[   14.667578] Booting paravirtualized kernel on bare hardware
[   14.667706] Time: 21:54:57  Date: 00/02/108
[   14.667781] NET: Registered protocol family 16
[   14.667953] EISA bus registered
[   14.668003] ACPI: bus type pci registered
[   14.668123] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=1
[   14.668172] PCI: Using configuration type 1
[   14.668218] Setting up standard PCI resources
[   14.679399] ACPI: EC: Look up EC in DSDT
[   14.684979] ACPI: Interpreter enabled
[   14.685031] ACPI: (supports S0 S1 S3 S4 S5)
[   14.685283] ACPI: Using IOAPIC for interrupt routing
[   14.695698] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   14.695763] PCI: Probing PCI hardware (bus 00)
[   14.696314] PCI quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
[   14.696366] PCI quirk: region 0480-04bf claimed by ICH4 GPIO
[   14.696816] PCI: Transparent bridge - 0000:00:1e.0
[   14.696886] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   14.697025] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[   14.704871] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   14.705417] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   14.705958] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   14.706496] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 6 7 10 11 12 14 15)
[   14.707035] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   14.707670] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   14.708220] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   14.708834] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   14.709378] Linux Plug and Play Support v0.97 (c) Adam Belay
[   14.709444] pnp: PnP ACPI init
[   14.709501] ACPI: bus type pnp registered
[   14.715044] pnp: PnP ACPI: found 14 devices
[   14.715093] ACPI: ACPI bus type pnp unregistered
[   14.715143] PnPBIOS: Disabled by ACPI PNP
[   14.715281] PCI: Using ACPI for IRQ routing
[   14.715331] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   14.718478] NET: Registered protocol family 8
[   14.718526] NET: Registered protocol family 20
[   14.718678] pnp: 00:0a: ioport range 0x680-0x6ff has been reserved
[   14.718734] pnp: 00:0b: iomem range 0xfed20000-0xfed8ffff has been reserved
[   14.718785] pnp: 00:0b: iomem range 0xffb00000-0xffbfffff could not be reserved
[   14.718846] pnp: 00:0b: iomem range 0xfff80000-0xffffffff could not be reserved
[   14.718911] pnp: 00:0c: iomem range 0xfec00000-0xfec00fff has been reserved
[   14.718962] pnp: 00:0c: iomem range 0xfee00000-0xfee00fff has been reserved
[   14.719016] pnp: 00:0d: iomem range 0x0-0x9ffff could not be reserved
[   14.719066] pnp: 00:0d: iomem range 0xc0000-0xdffff could not be reserved
[   14.719117] pnp: 00:0d: iomem range 0xe0000-0xfffff could not be reserved
[   14.719168] pnp: 00:0d: iomem range 0x100000-0x7f7fffff could not be reserved
[   14.719581] Time: tsc clocksource has been installed.
[   14.749719] PCI: Bridge: 0000:00:1e.0
[   14.749767]   IO window: b000-bfff
[   14.749816]   MEM window: fe500000-fe5fffff
[   14.749864]   PREFETCH window: disabled.
[   14.749923] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   14.749939] NET: Registered protocol family 2
[   14.787525] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   14.787728] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   14.788989] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   14.789491] TCP: Hash tables configured (established 131072 bind 65536)
[   14.789546] TCP reno registered
[   14.799669] checking if image is initramfs... it is
[   15.247046] Switched to high resolution mode on CPU 1
[   15.250795] Switched to high resolution mode on CPU 0
[   15.681797] Freeing initrd memory: 7119k freed
[   15.682354] audit: initializing netlink socket (disabled)
[   15.682420] audit(1199310897.924:1): initialized
[   15.682630] highmem bounce pool size: 64 pages
[   15.685705] VFS: Disk quotas dquot_6.5.1
[   15.685836] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   15.686017] io scheduler noop registered
[   15.686075] io scheduler anticipatory registered
[   15.686123] io scheduler deadline registered
[   15.686187] io scheduler cfq registered (default)
[   15.686251] Boot video device is 0000:00:02.0
[   15.686544] isapnp: Scanning for PnP cards...
[   16.039858] isapnp: No Plug & Play device found
[   16.073128] Real Time Clock Driver v1.12ac
[   16.073309] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   16.073532] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   16.074513] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   16.075609] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   16.075992] input: Macintosh mouse button emulation as /class/input/input0
[   16.076164] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   16.079116] serio: i8042 KBD port at 0x60,0x64 irq 1
[   16.079175] serio: i8042 AUX port at 0x60,0x64 irq 12
[   16.079459] mice: PS/2 mouse device common for all mice
[   16.079679] EISA: Probing bus 0 at eisa.0
[   16.079767] EISA: Detected 0 cards.
[   16.079925] TCP cubic registered
[   16.079983] NET: Registered protocol family 1
[   16.080055] Using IPI No-Shortcut mode
[   16.080309]   Magic number: 8:237:954
[   16.080382]   hash matches device ttya9
[   16.080506]   hash matches device ptyzb
[   16.080989] Freeing unused kernel memory: 364k freed
[   16.171521] input: AT Translated Set 2 keyboard as /class/input/input1
[   35.823388] AppArmor: AppArmor initialized<5>audit(1199310918.425:2):  type=1505 info="AppArmor initialized" pid=1718
[   36.927521] fuse init (API version 7.8)
[   37.164399] Failure registering capabilities with primary security module.
[   61.740129] usbcore: registered new interface driver usbfs
[   61.740238] usbcore: registered new interface driver hub
[   61.740358] usbcore: registered new device driver usb
[   61.744878] USB Universal Host Controller Interface driver v3.0
[   61.745023] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
[   61.745129] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   61.745135] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   61.745395] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   61.745489] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000dc00
[   61.745728] usb usb1: configuration #1 chosen from 1 choice
[   61.745828] hub 1-0:1.0: USB hub found
[   61.745885] hub 1-0:1.0: 2 ports detected
[   61.847848] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 17
[   61.847959] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   61.847965] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   61.848049] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   61.848139] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000e000
[   61.848351] usb usb2: configuration #1 chosen from 1 choice
[   61.848452] hub 2-0:1.0: USB hub found
[   61.848508] hub 2-0:1.0: 2 ports detected
[   61.951644] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   61.951754] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   61.951760] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   61.951849] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   61.951941] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000e400
[   61.952150] usb usb3: configuration #1 chosen from 1 choice
[   61.952249] hub 3-0:1.0: USB hub found
[   61.952305] hub 3-0:1.0: 2 ports detected
[   62.055521] ACPI: PCI Interrupt 0000:00:1d.3[A] -> GSI 16 (level, low) -> IRQ 16
[   62.055632] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   62.055638] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   62.055727] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   62.055814] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000e800
[   62.056042] usb usb4: configuration #1 chosen from 1 choice
[   62.056137] hub 4-0:1.0: USB hub found
[   62.056193] hub 4-0:1.0: 2 ports detected
[   62.087297] usb 1-2: new low speed USB device using uhci_hcd and address 2
[   62.284781] usb 1-2: configuration #1 chosen from 1 choice
[   62.909355] SCSI subsystem initialized
[   65.418453] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 19
[   65.418569] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   65.418587] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   65.418688] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   65.419487] ehci_hcd 0000:00:1d.7: debug port 1
[   65.419544] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[   65.419568] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xfe77bc00
[   65.423514] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   65.423734] usb usb5: configuration #1 chosen from 1 choice
[   65.423834] hub 5-0:1.0: USB hub found
[   65.423895] hub 5-0:1.0: 8 ports detected
[   65.455121] Floppy drive(s): fd0 is 1.44M
[   65.474008] FDC 0 is a post-1991 82077
[   65.709857] usb 1-2: USB disconnect, address 2
[   65.949393] usb 1-2: new low speed USB device using uhci_hcd and address 3
[   66.149232] usb 1-2: configuration #1 chosen from 1 choice
[   66.800110] libata version 2.21 loaded.
[   67.066840] ata_piix 0000:00:1f.1: version 2.11
[   67.066863] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[   67.066925] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[   67.067094] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   67.170530] scsi0 : ata_piix
[   67.170706] scsi1 : ata_piix
[   67.170965] ata1: PATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001fc00 irq 14
[   67.171039] ata2: PATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001fc08 irq 15
[   67.339694] ata1.00: ATA-7: SAMSUNG SV1203N, TQ100-23, max UDMA/133
[   67.339760] ata1.00: 234493056 sectors, multi 16: LBA48 
[   67.340148] ata1.01: ATA-5: MAXTOR 6L060J3, A93.0300, max UDMA/133
[   67.340205] ata1.01: 117266688 sectors, multi 16: LBA 
[   67.347811] ata1.00: configured for UDMA/133
[   67.363859] ata1.01: configured for UDMA/133
[   67.838910] ata2.00: ATAPI: ATAPI DVDROM 16X, V14HJ, max UDMA/33
[   67.839065] ata2.01: ATAPI: CW088D ATAPI CD-R/RW, V15HF, max UDMA/33
[   68.002791] ata2.00: configured for UDMA/33
[   68.174443] ata2.01: configured for UDMA/33
[   68.182010] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG SV1203N  TQ10 PQ: 0 ANSI: 5
[   68.189994] scsi 0:0:1:0: Direct-Access     ATA      MAXTOR 6L060J3   A93. PQ: 0 ANSI: 5
[   68.190445] scsi 1:0:0:0: CD-ROM                     ATAPI DVDROM 16X 14HJ PQ: 0 ANSI: 5
[   68.191194] scsi 1:0:1:0: CD-ROM            CyberDrv CW088D CD-R/RW   15HF PQ: 0 ANSI: 5
[   69.381433] usbcore: registered new interface driver hiddev
[   69.880860] hiddev96: USB HID v1.10 Device [APC Back-UPS ES 725 FW:802.n2.D USB FW:n2] on usb-0000:00:1d.0-2
[   69.881043] usbcore: registered new interface driver usbhid
[   69.881130] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   72.086669] sd 0:0:0:0: [sda] 234493056 512-byte hardware sectors (120060 MB)
[   72.086757] sd 0:0:0:0: [sda] Write Protect is off
[   72.086809] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   72.086858] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   72.087032] sd 0:0:0:0: [sda] 234493056 512-byte hardware sectors (120060 MB)
[   72.087111] sd 0:0:0:0: [sda] Write Protect is off
[   72.087163] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   72.087210] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   72.087278]  sda: sda1
[   72.156677] sd 0:0:0:0: [sda] Attached SCSI disk
[   72.159872] sr0: scsi3-mmc drive: 6x/40x cd/rw xa/form2 cdda tray
[   72.159938] Uniform CD-ROM driver Revision: 3.20
[   72.160061] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   72.164066] sr1: scsi3-mmc drive: 4x/48x writer cd/rw xa/form2 cdda tray
[   72.164220] sr 1:0:1:0: Attached scsi CD-ROM sr1
[   72.271789] sd 0:0:1:0: [sdb] 117266688 512-byte hardware sectors (60041 MB)
[   72.271900] sd 0:0:1:0: [sdb] Write Protect is off
[   72.271952] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   72.272001] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   72.272179] sd 0:0:1:0: [sdb] 117266688 512-byte hardware sectors (60041 MB)
[   72.272258] sd 0:0:1:0: [sdb] Write Protect is off
[   72.272310] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   72.272358] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   72.272428]  sdb:<5>sd 0:0:0:0: Attached scsi generic sg0 type 0
[   72.933052] sd 0:0:1:0: Attached scsi generic sg1 type 0
[   72.933140] sr 1:0:0:0: Attached scsi generic sg2 type 5
[   72.933222] sr 1:0:1:0: Attached scsi generic sg3 type 5
[   72.944454]  sdb1 sdb2 < sdb5 >
[   73.849626] sd 0:0:1:0: [sdb] Attached SCSI disk
[   76.973607] 8139too Fast Ethernet driver 0.9.28
[   76.973838] ACPI: PCI Interrupt 0000:01:0f.0[A] -> GSI 19 (level, low) -> IRQ 17
[   76.974477] eth0: RealTek RTL8139 at 0xf883a800, 00:0c:6e:7d:49:7c, IRQ 17
[   76.974541] eth0:  Identified 8139 chip type 'RTL-8101'
[   77.157008] ACPI: PCI Interrupt 0000:01:0e.0[A] -> GSI 21 (level, low) -> IRQ 20
[   77.209144] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[20]  MMIO=[fe5ff000-fe5ff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   77.351975] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   78.479133] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00e01800002943df]
[   79.420802] Attempting manual resume
[   79.420860] swsusp: Resume From Partition 8:21
[   79.420862] PM: Checking swsusp image.
[   79.421164] PM: Resume from disk failed.
[   79.976192] kjournald starting.  Commit interval 5 seconds
[   79.976221] EXT3-fs: mounted filesystem with ordered data mode.
[  185.414889] input: ImExPS/2 Generic Explorer Mouse as /class/input/input2
[  186.596807] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[  186.606974] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[  192.342894] input: PC Speaker as /class/input/input3
[  192.361361] Linux agpgart interface v0.102 (c) Dave Jones
[  192.372191] agpgart: Detected an Intel 865 Chipset.
[  192.372466] agpgart: Detected 8060K stolen memory.
[  192.386831] agpgart: AGP aperture is 128M @ 0xf0000000
[  198.656408] iTCO_vendor_support: vendor-support=0
[  198.687462] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[  198.687610] iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hardware
[  198.687679] iTCO_wdt: No card detected
[  203.783897] parport_pc 00:09: reported by Plug and Play ACPI
[  203.784008] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[  205.285763] usbcore: registered new interface driver xpad
[  205.286676] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/joystick/xpad.c: driver for Xbox controllers v0.1.6
[  207.567472] intel_rng: FWH not detected
[  218.570746] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 21
[  218.570870] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[  218.892100] intel8x0_measure_ac97_clock: measured 52711 usecs
[  218.892155] intel8x0: clocking to 48000
[  221.030866] lp0: using parport0 (interrupt-driven).
[  222.699263] Adding 2433808k swap on /dev/sdb5.  Priority:-1 extents:1 across:2433808k
[  223.808016] EXT3 FS on sdb1, internal journal
```

Thanks in advance for any help.

---

### Post by theheadlessrabbit on 2008-01-03
does compiz work if you turn it on?

I'm not sure why, but when I updated to Gutsy, my boot time was well over 10 minutes (1 ghz, 1 gig ram ATI radeon xpress i believe)  and compiz didn't work, but didn't use it in feisty, so it was no big loss.

following some advice found here:
[http://ubuntuforums.org/showthread.php?t=569654](http://ubuntuforums.org/showthread.php?t=569654)
(about half way down the page, following the steps given after this headline:
"If you are upgrading from Feisty 7.04 or earlier versions and you have run Xgl before."

I got my compiz working.  the wobbly windoes were nice, but my real treat came when i restarted, i was overjoyed!  my boot time was now 2 minutes!

i dont know why fixing compiz improved my boot time by 500%, but it did, and I hope it works for you.

---

### Post by Dbyte on 2008-01-03
Compiz worked somewhat (i.e. **very **slowly).  I tried some of the process you linked to, but my PC doesn't have an ATI card so I skipped those steps.  Net result was an increase in boot time.

Bummer - I'd read so much good stuff about Ubuntu & was psyched to get off Windows.  To install it & immediately have a boot time of 6+ minutes, with no clear sign of hardware incompatibility or driver issues in any of the code/bootchart/pics I have posted, is just not gonna work for me.

Can the "Ubuntu experiment" be over for me already?

---

### Post by clarinet on 2008-01-04
What motherboard and how much memory do you have? Extremely slow boot might be related to a BIOS bug that seems to appear more frequently last months. See e.g. [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/129172](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/129172)

Try to boot with 'mem=..." parameter to force kernel to use a little bit less memory than you really have (the actual amount needs some testing). Please let me know if it changed anything.

---

### Post by Dbyte on 2008-01-04
The PC is a Compaq Presario S4300nx.  Processor is Intel Pentium 4 2.4GHz w/ 800MHz bus on an Intel i865G-based motherboard.  Currently have 2GB of installed RAM.

Stuck @ work now but will go thru the steps indicated in Clarinet's link tonight.  It's been awhile since I updated the BIOS so that may be a good start.  And the observations in the link are consistent w/ what I am seeing, so hopefully this will help.

Am also ordering a new NVidia 256MB graphics card today.  Even if it doesn't help the boot problem I still like eye candy.

Thanks for your reply Clarinet!

---

### Post by Dbyte on 2008-01-05
**Problem SOLVED!!!**

No BIOS updates were available.  I was able to get a package of driver updates for my chipset from Intel's website which updated the NIC, sound card, & USB ports; all of which are integrated on the motherboard.  I also went into the BIOS; the video card's memory was set to 8MB in spite of the integrated card being 64MB.  I was only able to bump it up to 32MB.

After the above changes my total boot time is currently ~1:15 & all apps are launching **much** faster.  Seeing how the driver updates all occurred via Windows I am not sure they were the root cause - the BIOS change seems much more likely.

BIG thanks to all who posted here in an effort to help me out. As a noob  I really appreciate the support & insight.

---

