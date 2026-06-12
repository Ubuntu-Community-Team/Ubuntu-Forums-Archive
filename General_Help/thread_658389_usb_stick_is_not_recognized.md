---
title: "usb stick is not recognized"
date: 2008-01-04
forum: General Help
---

### Post by closeyourwindows on 2008-01-04
Hello all, I have a Dell PowerEdge 400 with Ubuntu7.10 running the show.  I have USB turned on in the BIOS but when I insert a USB mass storage device I do not get anything.
Here is my fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=1a20a27d-f3bb-4505-a6ef-6b7a82e2b3a0 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=b4e7856e-3caa-49e3-a1f8-c45a92319d9d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/hdd /media/cdrom1 udf,iso9660 user,noauto 0 0
```

when I input dmesg, I get:
```
$ dmesg
[    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Dec 18 08:02:57 UTC 2007 (Ubuntu 2.6.22-14.47-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001ff74000 (usable)
[    0.000000]  BIOS-e820: 000000001ff74000 - 000000001ff76000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001ff76000 - 000000001ff97000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001ff97000 - 0000000020000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fecf0000 - 00000000fecf1000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 511MB LOWMEM available.
[    0.000000] found SMP MP-table at 000fe710
[    0.000000] Entering add_active_range(0, 0, 130932) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   130932
[    0.000000]   HighMem    130932 ->   130932
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   130932
[    0.000000] On node 0 totalpages: 130932
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 990 pages used for memmap
[    0.000000]   Normal zone: 125846 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00FEB90 checksum 0
[    0.000000] ACPI: RSDP 000FEB90, 0014 (r0 DELL  )
[    0.000000] ACPI: RSDT 000FD140, 0038 (r1 DELL    PE400SC        8 ASL        61)
[    0.000000] ACPI: FACP 000FD178, 0074 (r1 DELL    PE400SC        8 ASL        61)
[    0.000000] ACPI: DSDT FFFC66B5, 269E (r1   DELL    dt_ex     1000 MSFT  100000D)
[    0.000000] ACPI: FACS 1FF74000, 0040
[    0.000000] ACPI: SSDT FFFC8DFA, 0096 (r1   DELL    st_ex     1000 MSFT  100000D)
[    0.000000] ACPI: APIC 000FD1EC, 006C (r1 DELL    PE400SC        8 ASL        61)
[    0.000000] ACPI: BOOT 000FD258, 0028 (r1 DELL    PE400SC        8 ASL        61)
[    0.000000] ACPI: ASF! 000FD280, 0067 (r16 DELL    PE400SC        8 ASL        61)
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:2 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:2 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] disabled)
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
[    0.000000] Built 1 zonelists.  Total pages: 129910
[    0.000000] Kernel command line: root=UUID=1a20a27d-f3bb-4505-a6ef-6b7a82e2b3a0 ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 2793.059 MHz processor.
[   23.488234] Console: colour VGA+ 80x25
[   23.488547] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   23.488814] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   23.497794] Memory: 507660k/523728k available (2015k kernel code, 15480k reserved, 916k data, 364k init, 0k highmem)
[   23.497804] virtual kernel memory layout:
[   23.497805]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   23.497806]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   23.497807]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
[   23.497808]     lowmem  : 0xc0000000 - 0xdff74000   ( 511 MB)
[   23.497809]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   23.497810]       .data : 0xc02f7de6 - 0xc03dce84   ( 916 kB)
[   23.497811]       .text : 0xc0100000 - 0xc02f7de6   (2015 kB)
[   23.497814] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   23.497850] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   23.577738] Calibrating delay using timer specific routine.. 5590.49 BogoMIPS (lpj=11180995)
[   23.577763] Security Framework v1.0.0 initialized
[   23.577771] SELinux:  Disabled at boot.
[   23.577783] Mount-cache hash table entries: 512
[   23.577921] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
[   23.577933] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   23.577936] CPU: L2 cache: 512K
[   23.577939] CPU: Physical Processor ID: 0
[   23.577941] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b080 00004400 00000000 00000000
[   23.577951] Compat vDSO mapped to ffffe000.
[   23.577964] Checking 'hlt' instruction... OK.
[   23.593818] SMP alternatives: switching to UP code
[   23.594278] Early unpacking initramfs... done
[   23.878215] ACPI: Core revision 20070126
[   23.890748] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   23.914773] CPU0: Intel(R) Pentium(R) 4 CPU 2.80GHz stepping 09
[   23.914793] SMP alternatives: switching to SMP code
[   23.914994] Booting processor 1/1 eip 3000
[   23.925079] Initializing CPU#1
[   24.005024] Calibrating delay using timer specific routine.. 5586.43 BogoMIPS (lpj=11172876)
[   24.005034] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
[   24.005045] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   24.005048] CPU: L2 cache: 512K
[   24.005050] CPU: Physical Processor ID: 0
[   24.005052] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b080 00004400 00000000 00000000
[   24.005317] CPU1: Intel(R) Pentium(R) 4 CPU 2.80GHz stepping 09
[   24.005357] Total of 2 processors activated (11176.93 BogoMIPS).
[   24.005488] ENABLING IO-APIC IRQs
[   24.005675] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   24.152914] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   24.172899] Brought up 2 CPUs
[   24.242944] migration_cost=197
[   24.243140] Booting paravirtualized kernel on bare hardware
[   24.243211] Time: 14:39:59  Date: 00/04/108
[   24.243237] NET: Registered protocol family 16
[   24.243356] EISA bus registered
[   24.243362] ACPI: bus type pci registered
[   24.243449] PCI: PCI BIOS revision 2.10 entry at 0xfba5e, last bus=2
[   24.243452] PCI: Using configuration type 1
[   24.243454] Setting up standard PCI resources
[   24.244953] ACPI: EC: Look up EC in DSDT
[   24.271864] ACPI: Interpreter enabled
[   24.271869] ACPI: (supports S0 S1 S4 S5)
[   24.271891] ACPI: Using IOAPIC for interrupt routing
[   24.299729] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   24.299746] PCI: Probing PCI hardware (bus 00)
[   24.300229] PCI quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
[   24.300233] PCI quirk: region 0880-08bf claimed by ICH4 GPIO
[   24.300689] PCI: Transparent bridge - 0000:00:1e.0
[   24.300717] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   24.301141] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[   24.412481] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 15)
[   24.412793] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[   24.413097] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 15)
[   24.413402] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[   24.413707] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[   24.414012] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 *5 6 7 9 10 11 12 15)
[   24.414317] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[   24.414623] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 9 10 11 12 15)
[   24.414783] Linux Plug and Play Support v0.97 (c) Adam Belay
[   24.414797] pnp: PnP ACPI init
[   24.414808] ACPI: bus type pnp registered
[   24.435923] pnp: PnP ACPI: found 13 devices
[   24.435926] ACPI: ACPI bus type pnp unregistered
[   24.435931] PnPBIOS: Disabled by ACPI PNP
[   24.436012] PCI: Using ACPI for IRQ routing
[   24.436016] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   24.441872] NET: Registered protocol family 8
[   24.441874] NET: Registered protocol family 20
[   24.441974] pnp: 00:00: iomem range 0x0-0x9ffff could not be reserved
[   24.441977] pnp: 00:00: iomem range 0x100000-0xffffff could not be reserved
[   24.441980] pnp: 00:00: iomem range 0x1000000-0x1ff73fff could not be reserved
[   24.441983] pnp: 00:00: iomem range 0xc0000-0xfffff could not be reserved
[   24.442003] pnp: 00:0c: ioport range 0x800-0x85f has been reserved
[   24.442006] pnp: 00:0c: ioport range 0xc00-0xc7f has been reserved
[   24.442009] pnp: 00:0c: ioport range 0x860-0x8ff could not be reserved
[   24.444315] Time: tsc clocksource has been installed.
[   24.472384] PCI: Bridge: 0000:00:01.0
[   24.472388]   IO window: disabled.
[   24.472393]   MEM window: disabled.
[   24.472397]   PREFETCH window: disabled.
[   24.472403] PCI: Bridge: 0000:00:1e.0
[   24.472406]   IO window: d000-dfff
[   24.472411]   MEM window: fd000000-feafffff
[   24.472416]   PREFETCH window: 30000000-300fffff
[   24.472433] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   24.472446] NET: Registered protocol family 2
[   24.512371] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   24.512421] TCP established hash table entries: 16384 (order: 5, 196608 bytes)
[   24.512548] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   24.512633] TCP: Hash tables configured (established 16384 bind 16384)
[   24.512636] TCP reno registered
[   24.524449] checking if image is initramfs... it is
[   24.975440] Switched to high resolution mode on CPU 0
[   24.975543] Switched to high resolution mode on CPU 1
[   25.096278] Freeing initrd memory: 7062k freed
[   25.096433] Simple Boot Flag value 0x87 read from CMOS RAM was invalid
[   25.096437] Simple Boot Flag at 0x7a set to 0x1
[   25.096742] audit: initializing netlink socket (disabled)
[   25.096760] audit(1199457599.328:1): initialized
[   25.099538] VFS: Disk quotas dquot_6.5.1
[   25.099607] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   25.099730] io scheduler noop registered
[   25.099732] io scheduler anticipatory registered
[   25.099734] io scheduler deadline registered
[   25.099751] io scheduler cfq registered (default)
[   25.099844] Boot video device is 0000:02:00.0
[   25.100042] isapnp: Scanning for PnP cards...
[   25.453560] isapnp: No Plug & Play device found
[   25.483478] Real Time Clock Driver v1.12ac
[   25.483587] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   25.483684] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   25.483868] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   25.484552] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   25.484854] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   25.485736] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   25.486025] input: Macintosh mouse button emulation as /class/input/input0
[   25.486132] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[   25.488993] serio: i8042 KBD port at 0x60,0x64 irq 1
[   25.489001] serio: i8042 AUX port at 0x60,0x64 irq 12
[   25.489212] mice: PS/2 mouse device common for all mice
[   25.489359] EISA: Probing bus 0 at eisa.0
[   25.489402] EISA: Detected 0 cards.
[   25.489512] TCP cubic registered
[   25.489526] NET: Registered protocol family 1
[   25.489552] Using IPI No-Shortcut mode
[   25.489742]   Magic number: 8:883:686
[   25.490320] Freeing unused kernel memory: 364k freed
[   25.509945] input: AT Translated Set 2 keyboard as /class/input/input1
[   26.727794] AppArmor: AppArmor initialized<5>audit(1199457600.828:2):  type=1505 info="AppArmor initialized" pid=1177
[   26.735218] fuse init (API version 7.8)
[   26.741907] Failure registering capabilities with primary security module.
[   27.382976] usbcore: registered new interface driver usbfs
[   27.383033] usbcore: registered new interface driver hub
[   27.383077] usbcore: registered new device driver usb
[   27.384559] USB Universal Host Controller Interface driver v3.0
[   27.384678] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
[   27.384697] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   27.384704] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   27.384910] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   27.384960] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000ff80
[   27.385167] usb usb1: configuration #1 chosen from 1 choice
[   27.385225] hub 1-0:1.0: USB hub found
[   27.385247] hub 1-0:1.0: 2 ports detected
[   27.446774] Intel(R) PRO/1000 Network Driver - version 7.3.20-k2-NAPI
[   27.446780] Copyright (c) 1999-2006 Intel Corporation.
[   27.469838] SCSI subsystem initialized
[   27.487276] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 17
[   27.487293] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   27.487298] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   27.487333] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   27.487363] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000ff60
[   27.487519] usb usb2: configuration #1 chosen from 1 choice
[   27.487562] hub 2-0:1.0: USB hub found
[   27.487573] hub 2-0:1.0: 2 ports detected
[   27.569588] Floppy drive(s): fd0 is 1.44M
[   27.581857] libata version 2.21 loaded.
[   27.591009] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   27.591027] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   27.591033] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   27.591081] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   27.591114] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000ff40
[   27.591278] usb usb3: configuration #1 chosen from 1 choice
[   27.591332] hub 3-0:1.0: USB hub found
[   27.591345] hub 3-0:1.0: 2 ports detected
[   27.606495] FDC 0 is a post-1991 82077
[   27.694762] ACPI: PCI Interrupt 0000:00:1d.3[A] -> GSI 16 (level, low) -> IRQ 16
[   27.694781] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   27.694787] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   27.694827] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   27.694856] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000ff20
[   27.695022] usb usb4: configuration #1 chosen from 1 choice
[   27.695075] hub 4-0:1.0: USB hub found
[   27.695088] hub 4-0:1.0: 2 ports detected
[   27.798776] ACPI: PCI Interrupt 0000:02:0c.0[A] -> GSI 18 (level, low) -> IRQ 18
[   28.072445] e1000: 0000:02:0c.0: e1000_probe: (PCI:33MHz:32-bit) 00:11:11:5b:e4:be
[   28.107425] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[   28.109985] ata_piix 0000:00:1f.1: version 2.11
[   28.110012] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[   28.110066] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   28.110193] scsi0 : ata_piix
[   28.110287] scsi1 : ata_piix
[   28.110359] ata1: PATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001ffa0 irq 14
[   28.110366] ata2: PATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001ffa8 irq 15
[   28.110401] ata1: port disabled. ignoring.
[   28.429517] ata2.00: ATAPI: SAMSUNG CD-ROM  SC-148A, B403, max UDMA/33
[   28.601215] ata2.00: configured for UDMA/33
[   28.601504] scsi 1:0:0:0: CD-ROM            SAMSUNG  CD-ROM SC-148A   B403 PQ: 0 ANSI: 5
[   28.601617] ata_piix 0000:00:1f.2: MAP [ P0 -- P1 -- ]
[   28.601647] ACPI: PCI Interrupt 0000:00:1f.2[A] -> GSI 18 (level, low) -> IRQ 18
[   28.601701] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   28.601776] scsi2 : ata_piix
[   28.601848] scsi3 : ata_piix
[   28.601898] ata3: SATA max UDMA/133 cmd 0x0001fe00 ctl 0x0001fe12 bmdma 0x0001fea0 irq 18
[   28.601903] ata4: SATA max UDMA/133 cmd 0x0001fe20 ctl 0x0001fe32 bmdma 0x0001fea8 irq 18
[   28.821014] ata3.00: ATA-6: ST3160023AS, 8.05, max UDMA/133
[   28.821019] ata3.00: 312581808 sectors, multi 8: LBA48 
[   28.836967] ata3.00: configured for UDMA/133
[   28.992491] scsi 2:0:0:0: Direct-Access     ATA      ST3160023AS      8.05 PQ: 0 ANSI: 5
[   28.992809] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 19
[   28.992832] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   28.992838] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   28.992886] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   28.992930] ehci_hcd 0000:00:1d.7: debug port 1
[   28.992939] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[   28.992956] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xffa80800
[   28.996840] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   28.997044] usb usb5: configuration #1 chosen from 1 choice
[   28.997098] hub 5-0:1.0: USB hub found
[   28.997115] hub 5-0:1.0: 8 ports detected
[   29.003650] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   29.003678] sd 2:0:0:0: [sda] Write Protect is off
[   29.003683] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   29.003721] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   29.003855] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   29.003877] sd 2:0:0:0: [sda] Write Protect is off
[   29.003882] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   29.003914] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   29.003921]  sda:sr0: scsi3-mmc drive: 8x/48x cd/rw xa/form2 cdda tray
[   29.015072] Uniform CD-ROM driver Revision: 3.20
[   29.015146] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   29.024227]  sda1 sda2 sda3 < sda5 >
[   29.043477] sd 2:0:0:0: [sda] Attached SCSI disk
[   29.050724] sr 1:0:0:0: Attached scsi generic sg0 type 5
[   29.050759] sd 2:0:0:0: Attached scsi generic sg1 type 0
[   29.322752] Attempting manual resume
[   29.322756] swsusp: Resume From Partition 8:5
[   29.322758] PM: Checking swsusp image.
[   29.323291] PM: Resume from disk failed.
[   29.360031] kjournald starting.  Commit interval 5 seconds
[   29.360048] EXT3-fs: mounted filesystem with ordered data mode.
[   36.782895] EDAC MC: Ver: 2.0.1 Dec 18 2007
[   36.794986] EDAC i82875p: i82875p init one
[   36.804148] PCI: Unable to reserve mem region #1:1000@fecf0000 for device 0000:00:06.0
[   36.804272] EDAC MC0: Giving out device to i82875p_edac i82875p: DEV 0000:00:00.0
[   36.836265] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   36.949569] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   37.012213] Linux agpgart interface v0.102 (c) Dave Jones
[   37.369680] iTCO_vendor_support: vendor-support=0
[   37.373587] input: PC Speaker as /class/input/input2
[   37.546063] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   38.110615] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 20
[   38.110639] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   38.156227] input: ImPS/2 Logitech Wheel Mouse as /class/input/input3
[   38.159366] iTCO_wdt: Found a ICH5 or ICH5R TCO device (Version=1, TCOBASE=0x0860)
[   38.159455] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   38.160060] parport_pc 00:0b: reported by Plug and Play ACPI
[   38.160115] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[   38.178879] intel_rng: Firmware space is locked read-only. <4>intel_rng: If you can't or
[   38.178883]  don't want to <4>intel_rng: disable this in firmware setup, and <4>intel_rng: if
[   38.178887]  you are certain that your <4>intel_rng: system has a functional
[   38.178890]  RNG, try<4>intel_rng: using the 'no_fwh_detect' option.
[   38.531517] intel8x0_measure_ac97_clock: measured 52319 usecs
[   38.531520] intel8x0: clocking to 48000
[   39.105565] lp0: using parport0 (interrupt-driven).
[   39.162003] Adding 1510068k swap on /dev/sda5.  Priority:-1 extents:1 across:1510068k
[   39.375799] EXT3 FS on sda2, internal journal
[   41.758933] No dock devices found.
[   41.797417] input: Power Button (FF) as /class/input/input4
[   41.797446] ACPI: Power Button (FF) [PWRF]
[   41.797512] input: Power Button (CM) as /class/input/input5
[   41.797541] ACPI: Power Button (CM) [VBTN]
[   43.182542] Failure registering capabilities with primary security module.
[   43.363383] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[   43.375358] ppdev: user-space parallel port driver
[   43.559861] audit(1199475618.416:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4708 profile="/usr/sbin/cupsd"
[   43.698608] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   43.698616] apm: disabled - APM is not SMP safe.
[   43.922514] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[   44.017005] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   44.028346] NFSD: starting 90-second grace period
[   45.054728] Bluetooth: Core ver 2.11
[   45.055202] NET: Registered protocol family 31
[   45.055212] Bluetooth: HCI device and connection manager initialized
[   45.055219] Bluetooth: HCI socket layer initialized
[   45.064868] Bluetooth: L2CAP ver 2.8
[   45.064875] Bluetooth: L2CAP socket layer initialized
[   45.150040] Bluetooth: RFCOMM socket layer initialized
[   45.150481] Bluetooth: RFCOMM TTY layer initialized
[   45.150493] Bluetooth: RFCOMM ver 1.8
[   49.260221] NET: Registered protocol family 17
[   52.707398] NET: Registered protocol family 10
[   52.708093] lo: Disabled Privacy Extensions
[   63.651318] eth0: no IPv6 routers present
[  123.132321] UDF-fs: No VRS found
[  123.177805] ISO 9660 Extensions: Microsoft Joliet Level 3
[  123.646480] ISOFS: changing to secondary root
[  160.610033] UDF-fs: No VRS found
[  160.655591] ISO 9660 Extensions: Microsoft Joliet Level 3
[  161.106451] ISOFS: changing to secondary root
[ 4326.266438] UDF-fs: No VRS found
[ 4326.311979] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 4326.516245] ISOFS: changing to secondary root
[ 4631.613715] end_request: I/O error, dev sr0, sector 240724
[ 4631.613725] Buffer I/O error on device sr0, logical block 60181
[ 4631.613736] Buffer I/O error on device sr0, logical block 60182
[ 4631.613741] Buffer I/O error on device sr0, logical block 60183
[ 4631.613746] Buffer I/O error on device sr0, logical block 60184
[ 4631.613751] Buffer I/O error on device sr0, logical block 60185
[ 4631.613756] Buffer I/O error on device sr0, logical block 60186
[ 4631.613762] Buffer I/O error on device sr0, logical block 60187
[ 4631.613767] Buffer I/O error on device sr0, logical block 60188
[ 4631.613772] Buffer I/O error on device sr0, logical block 60189
[ 4631.613778] Buffer I/O error on device sr0, logical block 60190
[ 4632.575074] end_request: I/O error, dev sr0, sector 240764
[ 4632.575207] UDF-fs: No VRS found
[ 4632.607851] ISO 9660 Extensions: Microsoft Joliet Level 1
[ 4632.624295] ISOFS: changing to secondary root
[ 4655.240885] usb 5-3: new high speed USB device using ehci_hcd and address 2
[ 4655.387603] usb 5-3: configuration #1 chosen from 1 choice
[ 4655.650780] usbcore: registered new interface driver libusual
[ 4655.736916] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[ 4655.737324] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[ 4655.774932] Initializing USB Mass Storage driver...
[ 4655.775447] scsi4 : SCSI emulation for USB Mass Storage devices
[ 4655.776105] usb-storage: device found at 2
[ 4655.776111] usb-storage: waiting for device to settle before scanning
[ 4655.776535] usbcore: registered new interface driver usb-storage
[ 4655.776728] USB Mass Storage support registered.
[ 4660.767335] usb-storage: device scan complete
[ 4660.768194] scsi 4:0:0:0: Direct-Access     Simple   Flash Disk 2.0   2.00 PQ: 0 ANSI: 2
[ 4666.106083] ready
[ 4666.106575] sd 4:0:0:0: [sdb] 4077568 512-byte hardware sectors (2088 MB)
[ 4666.107201] sd 4:0:0:0: [sdb] Write Protect is off
[ 4666.107207] sd 4:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 4666.107211] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 4666.109441] sd 4:0:0:0: [sdb] 4077568 512-byte hardware sectors (2088 MB)
[ 4666.110069] sd 4:0:0:0: [sdb] Write Protect is off
[ 4666.110074] sd 4:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 4666.110079] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 4666.110084]  sdb: sdb1
[ 4666.110924] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[ 4666.110993] sd 4:0:0:0: Attached scsi generic sg2 type 0

```

any help would be help.

---

### Post by RelativelyQuantum on 2008-01-04
Wondering: does the drive contain any programs (U3, etc)? Although I haven't heard of this happening before, might it be that Linux doesn't recognize it because of program which requires it to be used with a specific OS?

How large is it, in GB? And what type of stick, specifically?

---

### Post by closeyourwindows on 2008-01-04
It is not a U3 drive, it is a 2 GB and it is made by SimpleTech.  I tried an Ativa and that did not work either.  Both work in PC and MAC

---

### Post by RelativelyQuantum on 2008-01-04
Has the computer recognized it before?

---

### Post by niethslim on 2008-01-04
You should try typing "lsusb" in terminal with and without the stick.
 Does it recognize the stick?

---

### Post by closeyourwindows on 2008-01-04
this is a fresh install, it has yet to recognize it.

this is with the USB in the slot. 
```
$ lsusb
Bus 005 Device 003: ID 0ea0:2168 Ours Technology, Inc. Transcend JetFlash 2.0 / Astone USB Drive
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000 
```

without it does nothing

---

### Post by closeyourwindows on 2008-01-04
If I restart the computer with the disk in it will show up, but if I remove the disk and then reinsert the USB disk, it will not show up.  Also the fstab is the same with the drive mounted and unmounted.   ??

---

### Post by fjgaude on 2008-01-04
What happens if you add this line to your fstab and reboot:

usbfs /proc/bus/usb usbfs auto 0 0

---

### Post by freddyp on 2008-01-04
Not to insult, but have you checked:

System>Preferences>Storage Tab and made sure the following is checked:

Mount removable drives when hot-plugged
Mount removable media when inserted
Browse removable media when inserted

Don't ask me how I know how easy it is to accidentally uncheck one :oops:

---

### Post by dcstar on 2008-01-05
> **freddyp said:**
> Not to insult, but have you checked:

System>Preferences>Storage Tab and made sure the following is checked:

Mount removable drives when hot-plugged
Mount removable media when inserted
Browse removable media when inserted

Don't ask me how I know how easy it is to accidentally uncheck one :oops:

Exactly, the USB drive is being recognised by Ubuntu on insert but if you don't ask the O/S to automount it, then it won't be automounted.

---

### Post by bks on 2008-01-06
> **RelativelyQuantum said:**
> Wondering: does the drive contain any programs (U3, etc)? Although I haven't heard of this happening before, might it be that Linux doesn't recognize it because of program which requires it to be used with a specific OS?

Thanks! I had the same problem and that is what it was!

---

### Post by closeyourwindows on 2008-01-07
I inserted the line in the fstab and still nothing even after reboots.
the boxes are checked as well in the system preferences.  The usb is blinking but will not mount.
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=1a20a27d-f3bb-4505-a6ef-6b7a82e2b3a0 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=b4e7856e-3caa-49e3-a1f8-c45a92319d9d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/hdd /media/cdrom1 udf,iso9660 user,noauto 0 0
usbfs /proc/bus/usb usbfs auto 0 0
```

---

