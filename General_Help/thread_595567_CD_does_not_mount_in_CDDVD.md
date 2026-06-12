---
title: "CD does not mount in CD/DVD"
date: 2007-10-28
forum: General Help
---

### Post by lduplantie on 2007-10-28
I have installed 7.10. If I insert a CD (data) in my Pioneer DVD-RW DVR-112D it will not read it. It reads DVDs (data). I have also tried to insert a blank CD-R, It does not mount or start the CD-burn application.

Please help with a solution.

The PC is a P3-1GHz-20G-512M

Thanks

---

### Post by seventyeights on 2007-10-28
It sounds like you need another drive.

---

### Post by the_it on 2007-10-28
Some diagnostic aids:

Do the commands eject and eject -t work properly?  They should open and close your cd drive.

Try posting the contents of /etc/fstab

Also, try running sudo tail -f /var/log/messages (control c to quit).
It will print out kernel messages as they happen.  What happens when you insert a cd?  remove one?

lastly, try posting the output of the command 'dmesg'.

---

### Post by lduplantie on 2007-10-29
In terminal, the command eject and eject -t opens the cd-rom not the dvd-rw. However, eject for the dvd does not works in the context sensitive menu.

Content of /etc/fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=f3b1332b-3237-4653-aebd-d55425afc308 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=b46ecd37-553d-4458-8529-645986881b02 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

/var/log/messages:

After inserting a data dvd disk:
Oct 29 09:25:26 Linux kernel: [  645.265819] UDF-fs: No VRS found
No messages are written when I insert a data CD

Output of dmesg:

[    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001fee06c0 (usable)
[    0.000000]  BIOS-e820: 000000001fee06c0 - 000000001fee66c0 (ACPI data)
[    0.000000]  BIOS-e820: 000000001fee66c0 - 000000001feee700 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001feee700 - 0000000020000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 510MB LOWMEM available.
[    0.000000] found SMP MP-table at 0009fe00
[    0.000000] Entering add_active_range(0, 0, 130784) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   130784
[    0.000000]   HighMem    130784 ->   130784
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   130784
[    0.000000] On node 0 totalpages: 130784
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 989 pages used for memmap
[    0.000000]   Normal zone: 125699 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00FDFE0 checksum 0
[    0.000000] ACPI: RSDP 000FDFE0, 0014 (r0 IBM   )
[    0.000000] ACPI: RSDT 1FEE6640, 002C (r1 IBM    CDTPWSPI     1010 IBM         0)
[    0.000000] ACPI: FACP 1FEE65C0, 0074 (r1 IBM    CDTPWSPI     1010 IBM         0)
[    0.000000] ACPI: DSDT 1FEE1D00, 43EB (r1 IBM    CDTPWSPI     1000 MSFT  1000007)
[    0.000000] ACPI: FACS 1FEEE680, 0040
[    0.000000] ACPI: APIC 1FEE6540, 005A (r1 IBM    CDTPWSPI     1010 IBM         0)
[    0.000000] ACPI: PM-Timer IO Port: 0xf808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:8 APIC version 17
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
[    0.000000] Built 1 zonelists.  Total pages: 129763
[    0.000000] Kernel command line: root=UUID=f3b1332b-3237-4653-aebd-d55425afc308 ro quiet splash locale=fr_FR
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 996.739 MHz processor.
[   19.021462] Console: colour VGA+ 80x25
[   19.022391] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   19.023618] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   19.070926] Memory: 506892k/523136k available (2015k kernel code, 15728k reserved, 916k data, 364k init, 0k highmem)
[   19.070949] virtual kernel memory layout:
[   19.070951]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   19.070954]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   19.070957]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
[   19.070960]     lowmem  : 0xc0000000 - 0xdfee0000   ( 510 MB)
[   19.070963]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   19.070966]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
[   19.070969]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
[   19.070976] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   19.071054] SLUB: Genslabs=22, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   19.151058] Calibrating delay using timer specific routine.. 1994.98 BogoMIPS (lpj=3989966)
[   19.151116] Security Framework v1.0.0 initialized
[   19.151134] SELinux:  Disabled at boot.
[   19.151166] Mount-cache hash table entries: 512
[   19.151421] CPU: After generic identify, caps: 0383fbff 00000000 00000000 00000000 00000000 00000000 00000000
[   19.151443] CPU: L1 I cache: 16K, L1 D cache: 16K
[   19.151449] CPU: L2 cache: 256K
[   19.151457] CPU: After all inits, caps: 0383fbff 00000000 00000000 00000040 00000000 00000000 00000000
[   19.151477] Compat vDSO mapped to ffffe000.
[   19.151506] Checking 'hlt' instruction... OK.
[   19.167240] SMP alternatives: switching to UP code
[   19.167555] Freeing SMP alternatives: 11k freed
[   19.168150] Early unpacking initramfs... done
[   19.882303] ACPI: Core revision 20070126
[   19.882588] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   19.886194] CPU0: Intel Pentium III (Coppermine) stepping 0a
[   19.886249] Total of 1 processors activated (1994.98 BogoMIPS).
[   19.886398] ENABLING IO-APIC IRQs
[   19.886632] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   20.030874] Brought up 1 CPUs
[   20.031159] Booting paravirtualized kernel on bare hardware
[   20.031279] Time: 13:15:00  Date: 09/29/107
[   20.031351] NET: Registered protocol family 16
[   20.031611] EISA bus registered
[   20.031636] ACPI: bus type pci registered
[   20.032825] PCI: PCI BIOS revision 2.10 entry at 0xfd55c, last bus=1
[   20.032831] PCI: Using configuration type 1
[   20.032835] Setting up standard PCI resources
[   20.035833] ACPI: EC: Look up EC in DSDT
[   20.044430] ACPI: Interpreter enabled
[   20.044438] ACPI: (supports S0 S1 S4 S5)
[   20.044472] ACPI: Using IOAPIC for interrupt routing
[   20.053263] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   20.053282] PCI: Probing PCI hardware (bus 00)
[   20.053581] PCI quirk: region f800-f87f claimed by ICH4 ACPI/GPIO/TCO
[   20.053589] PCI quirk: region fc00-fc3f claimed by ICH4 GPIO
[   20.053909] PCI: Firmware left 0000:01:08.0 e100 interrupts enabled, disabling
[   20.053984] PCI: Transparent bridge - 0000:00:1e.0
[   20.054021] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   20.054346] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI2._PRT]
[   20.064016] ACPI: PCI Interrupt Link [PIN1] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   20.064272] ACPI: PCI Interrupt Link [PIN2] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   20.064520] ACPI: PCI Interrupt Link [PIN3] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   20.064769] ACPI: PCI Interrupt Link [PIN4] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   20.065017] ACPI: PCI Interrupt Link [PIN5] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   20.065265] ACPI: PCI Interrupt Link [PIN6] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   20.065513] ACPI: PCI Interrupt Link [PIN7] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   20.065762] ACPI: PCI Interrupt Link [PIN8] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   20.065985] Linux Plug and Play Support v0.97 (c) Adam Belay
[   20.066011] pnp: PnP ACPI init
[   20.066047] ACPI: bus type pnp registered
[   20.071719] pnp: PnP ACPI: found 16 devices
[   20.071729] ACPI: ACPI bus type pnp unregistered
[   20.071736] PnPBIOS: Disabled by ACPI PNP
[   20.071870] PCI: Using ACPI for IRQ routing
[   20.071878] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   20.077391] NET: Registered protocol family 8
[   20.077396] NET: Registered protocol family 20
[   20.077584] pnp: 00:0c: ioport range 0x4d0-0x4d1 has been reserved
[   20.077592] pnp: 00:0c: ioport range 0x800-0x87f has been reserved
[   20.077598] pnp: 00:0c: ioport range 0xf800-0xf87f has been reserved
[   20.077605] pnp: 00:0c: ioport range 0xfc00-0xfc3f has been reserved
[   20.077613] pnp: 00:0c: iomem range 0xfff80000-0xffffffff could not be reserved
[   20.077626] pnp: 00:0e: iomem range 0x0-0x9ffff could not be reserved
[   20.077633] pnp: 00:0e: iomem range 0x100000-0xffffff could not be reserved
[   20.077640] pnp: 00:0e: iomem range 0x1000000-0x1fffffff could not be reserved
[   20.077651] pnp: 00:0f: iomem range 0xca000-0xcbfff has been reserved
[   20.077658] pnp: 00:0f: iomem range 0xcd800-0xcffff has been reserved
[   20.077664] pnp: 00:0f: iomem range 0xe0000-0xe0fff has been reserved
[   20.077671] pnp: 00:0f: iomem range 0xe1000-0xe1fff has been reserved
[   20.078767] Time: tsc clocksource has been installed.
[   20.108325] PCI: Bridge: 0000:00:1e.0
[   20.108331]   IO window: 7000-7fff
[   20.108340]   MEM window: feb00000-febfffff
[   20.108346]   PREFETCH window: disabled.
[   20.108365] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   20.108393] NET: Registered protocol family 2
[   20.146876] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   20.147016] TCP established hash table entries: 16384 (order: 5, 196608 bytes)
[   20.147681] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   20.148299] TCP: Hash tables configured (established 16384 bind 16384)
[   20.148307] TCP reno registered
[   20.159119] checking if image is initramfs...<6>Switched to high resolution mode on CPU 0
[   20.744257]  it is
[   21.493313] Freeing initrd memory: 7354k freed
[   21.494352] audit: initializing netlink socket (disabled)
[   21.494388] audit(1193663700.904:1): initialized
[   21.499418] VFS: Disk quotas dquot_6.5.1
[   21.499593] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   21.499889] io scheduler noop registered
[   21.499896] io scheduler anticipatory registered
[   21.499901] io scheduler deadline registered
[   21.499955] io scheduler cfq registered (default)
[   21.499990] Boot video device is 0000:00:02.0
[   21.500351] isapnp: Scanning for PnP cards...
[   21.854169] isapnp: No Plug & Play device found
[   21.922649] Real Time Clock Driver v1.12ac
[   21.922846] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   21.922974] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   21.923359] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   21.924655] 00:05: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   21.925205] 00:06: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   21.927026] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   21.927569] input: Macintosh mouse button emulation as /class/input/input0
[   21.927757] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   21.929994] serio: i8042 KBD port at 0x60,0x64 irq 1
[   21.930039] serio: i8042 AUX port at 0x60,0x64 irq 12
[   21.930462] mice: PS/2 mouse device common for all mice
[   21.930694] EISA: Probing bus 0 at eisa.0
[   21.930738] Cannot allocate resource for EISA slot 7
[   21.930747] EISA: Detected 0 cards.
[   21.930973] TCP cubic registered
[   21.931011] NET: Registered protocol family 1
[   21.931073] Using IPI No-Shortcut mode
[   21.931402]   Magic number: 11:302:282
[   21.931458]   hash matches device ttyvd
[   21.931585]   hash matches device tty19
[   21.932668] Freeing unused kernel memory: 364k freed
[   21.966154] input: AT Translated Set 2 keyboard as /class/input/input1
[   23.463225] AppArmor: AppArmor initialized<5>audit(1193663702.904:2):  type=1505 info="AppArmor initialized" pid=1176
[   23.484422] fuse init (API version 7.8)
[   23.496734] Failure registering capabilities with primary security module.
[   23.529587] ACPI: Processor [CPU0] (supports 8 throttling states)
[   24.955857] usbcore: registered new interface driver usbfs
[   24.955914] usbcore: registered new interface driver hub
[   24.955965] usbcore: registered new device driver usb
[   24.959244] USB Universal Host Controller Interface driver v3.0
[   24.959416] ACPI: PCI Interrupt 0000:00:1f.2[D] -> GSI 19 (level, low) -> IRQ 16
[   24.959440] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   24.959448] uhci_hcd 0000:00:1f.2: UHCI Host Controller
[   24.959717] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
[   24.959763] uhci_hcd 0000:00:1f.2: irq 16, io base 0x0000fb00
[   24.960061] usb usb1: configuration #1 chosen from 1 choice
[   24.960134] hub 1-0:1.0: USB hub found
[   24.960152] hub 1-0:1.0: 2 ports detected
[   25.011695] SCSI subsystem initialized
[   25.031579] libata version 2.21 loaded.
[   25.078395] e100: Intel(R) PRO/100 Network Driver, 3.5.17-k4-NAPI
[   25.078404] e100: Copyright(c) 1999-2006 Intel Corporation
[   25.078513] ACPI: PCI Interrupt 0000:01:08.0[A] -> GSI 20 (level, low) -> IRQ 17
[   25.101227] e100: eth0: e100_probe: addr 0xfebff000, irq 17, MAC addr 00:02:55:0D:ED:D0
[   25.142874] ata_piix 0000:00:1f.1: version 2.11
[   25.143005] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   25.143264] scsi0 : ata_piix
[   25.143379] scsi1 : ata_piix
[   25.143625] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001fff0 irq 14
[   25.143634] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001fff8 irq 15
[   25.261002] Floppy drive(s): fd0 is 1.44M
[   25.313168] ata1.00: ATA-5: IC35L020AVER07-0, ER2OA45A, max UDMA/100
[   25.313180] ata1.00: 39876480 sectors, multi 16: LBA 
[   25.337144] ata1.00: configured for UDMA/100
[   25.372856] FDC 0 is a post-1991 82077
[   25.812809] ata2.00: ATAPI: SAMSUNG CD-ROM  SC-148C, B100, max UDMA/33
[   25.812834] ata2.01: ATAPI: PIONEER DVD-RW  DVR-112D, 1.09, max UDMA/66
[   25.976607] ata2.00: configured for UDMA/33
[   26.148608] ata2.01: configured for UDMA/66
[   26.148904] scsi 0:0:0:0: Direct-Access     ATA      IC35L020AVER07-0 ER2O PQ: 0 ANSI: 5
[   26.150119] scsi 1:0:0:0: CD-ROM            SAMSUNG  CD-ROM SC-148C   B100 PQ: 0 ANSI: 5
[   26.156813] scsi 1:0:1:0: CD-ROM            PIONEER  DVD-RW  DVR-112D 1.09 PQ: 0 ANSI: 5
[   26.205729] sd 0:0:0:0: [sda] 39876480 512-byte hardware sectors (20417 MB)
[   26.205831] sd 0:0:0:0: [sda] Write Protect is off
[   26.205837] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   26.205873] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   26.206007] sd 0:0:0:0: [sda] 39876480 512-byte hardware sectors (20417 MB)
[   26.206029] sd 0:0:0:0: [sda] Write Protect is off
[   26.206035] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   26.206067] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   26.206079]  sda: sda1 sda2 < sda5 >
[   26.233558] sd 0:0:0:0: [sda] Attached SCSI disk
[   26.245754] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   26.246131] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[   26.246431] scsi 1:0:1:0: Attached scsi generic sg2 type 5
[   26.294205] sr0: scsi3-mmc drive: 1x/48x cd/rw xa/form2 cdda tray
[   26.294221] Uniform CD-ROM driver Revision: 3.20
[   26.294905] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   26.329497] sr1: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[   26.330166] sr 1:0:1:0: Attached scsi CD-ROM sr1
[   26.579516] Attempting manual resume
[   26.579525] swsusp: Resume From Partition 8:5
[   26.579529] PM: Checking swsusp image.
[   26.579839] PM: Resume from disk failed.
[   26.642943] kjournald starting.  Commit interval 5 seconds
[   26.642975] EXT3-fs: mounted filesystem with ordered data mode.
[   34.461187] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[   35.947929] NET: Registered protocol family 17
[   37.316596] intel_rng: Firmware space is locked read-only. <4>intel_rng: If you can't or
[   37.316602]  don't want to <4>intel_rng: disable this in firmware setup, and <4>intel_rng: if
[   37.316606]  you are certain that your <4>intel_rng: system has a functional
[   37.316610]  RNG, try<4>intel_rng: using the 'no_fwh_detect' option.
[   37.361708] iTCO_vendor_support: vendor-support=0
[   37.364602] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   37.364752] iTCO_wdt: Found a ICH2 TCO device (Version=1, TCOBASE=0xf860)
[   37.364823] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   37.542637] Linux agpgart interface v0.102 (c) Dave Jones
[   37.575005] agpgart: Detected an Intel i815 Chipset.
[   37.585259] agpgart: AGP aperture is 64M @ 0xf8000000
[   37.594939] i810_smbus 0000:00:02.0: i810/i815 i2c device found.
[   37.763327] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   37.776475] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   39.832037] input: ImPS/2 Generic Wheel Mouse as /class/input/input2
[   39.905150] parport_pc 00:02: reported by Plug and Play ACPI
[   39.905212] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   40.137585] input: PC Speaker as /class/input/input3
[   40.428206] PCI: Enabling device 0000:00:1f.5 (0000 -> 0001)
[   40.428236] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 18
[   40.428269] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   41.042422] intel8x0_measure_ac97_clock: measured 52037 usecs
[   41.042433] intel8x0: clocking to 41144
[   41.832805] lp0: using parport0 (interrupt-driven).
[   41.916925] Adding 875500k swap on /dev/sda5.  Priority:-1 extents:1 across:875500k
[   42.211477] EXT3 FS on sda1, internal journal
[   42.839559] NET: Registered protocol family 10
[   42.839865] lo: Disabled Privacy Extensions
[   44.474455] No dock devices found.
[   44.848938] input: Power Button (FF) as /class/input/input4
[   44.849471] ACPI: Power Button (FF) [PWRF]
[   44.884927] input: Power Button (CM) as /class/input/input5
[   44.885474] ACPI: Power Button (CM) [PWRB]
[   47.263222] ppdev: user-space parallel port driver
[   47.672463] audit(1193663729.046:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4571 profile="/usr/sbin/cupsd"
[   47.762623] IBM machine detected. Enabling interrupts during APM calls.
[   47.762638] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   47.762644] apm: overridden by ACPI.
[   48.149496] Failure registering capabilities with primary security module.
[   48.392186] Bluetooth: Core ver 2.11
[   48.392432] NET: Registered protocol family 31
[   48.392438] Bluetooth: HCI device and connection manager initialized
[   48.392446] Bluetooth: HCI socket layer initialized
[   48.426825] Bluetooth: L2CAP ver 2.8
[   48.426838] Bluetooth: L2CAP socket layer initialized
[   48.438688] Bluetooth: RFCOMM socket layer initialized
[   48.438881] Bluetooth: RFCOMM TTY layer initialized
[   48.438887] Bluetooth: RFCOMM ver 1.8
[   53.189574] eth0: no IPv6 routers present
[  645.265819] UDF-fs: No VRS found
[  645.290363] ISO 9660 Extensions: Microsoft Joliet Level 3
[  645.418166] ISO 9660 Extensions: RRIP_1991A

---

### Post by the_it on 2007-10-29
```
[ 26.148904] scsi 0:0:0:0: Direct-Access ATA IC35L020AVER07-0 ER2O PQ: 0 ANSI: 5
[ 26.150119] scsi 1:0:**0**:0: CD-ROM SAMSUNG CD-ROM SC-148C B100 PQ: 0 ANSI: 5
[ 26.156813] scsi 1:0:**1**:0: CD-ROM PIONEER DVD-RW DVR-112D 1.09 PQ: 0 ANSI: 5
```

correct me if I'm wrong, but doesn't this mean you have 2 cd drives?  You have a cdrom and a dvd-rw... does your dvd-rw really read cds?  Maybe it's just for dvds...

---

### Post by lduplantie on 2007-10-29
Yes I have two drives. One is configured a master and the other as slave

Pioneer spec states:

DVR-112D
	Writes and reads DVD-R/RW, +R/RW and CD-R/RW formats. Read-only feature for DVD-RAM

---

### Post by boast on 2008-04-17
bump

---

### Post by crazyfuturamanoob on 2008-04-17
I like apple pie!
:lol::lol::lol::lol::lol::lol::lol::lol:

---

### Post by boast on 2008-04-18
no one has any clues???

is there some sort of hardware reconfigure setup???

---

### Post by russo.mic on 2008-04-18
I'm hard pressed to believe this is a hardware failure, usually, it would be the other way around, DVD's not working, but CD's still working.

Have you tried manully mounting /dev/cdrom or whatever to a directory in ubuntu?

Russo

---

