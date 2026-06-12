---
title: "Unable to mount CDROM"
date: 2007-09-08
forum: General Help
---

### Post by sit properly on 2007-09-08
Hi folks, 

I'm running 7.04 on a Sony Vaio.laptop. My CDROM drive just stopped working. It worked before. It's not a kernel problem, because it's worked since the last update. Unless I missed something. 

It seemed to be recognized in Nautilus as CD-ROM 1. However, when I click on it, I get: 

"Unable to mount selected drive

mount: special device /dev/cdrom does not exist"

This is my fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3 -- converted during upgrade to edgy
UUID=fbfab767-2d85-4f9b-a223-49b9878f2054 / ext3 defaults,errors=remount-ro 0 1
# /dev/sda6 -- converted during upgrade to edgy
UUID=c2d7cca7-41be-4923-b9f9-4da9b915f5bb none swap sw 0 0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
```


I'm not really sure how to read this or what to do. 

And I'm not sure if this is normal, but I have "fstab" "fstab.edgy" and "fstab.pre-iuud" in my "etc" directory. Tried all of them for fstab. None work - same error (though when it calls for /dev/hda it says that "
mount: special device /dev/hda does not exist"

Any help would be great. 

Thanks!


edit: I dual boot and XP will also not recognize it. Would this mean that the drive is shot? It powers up and spins - seems to be reading the disc.... So in less than a month the motherboard fries and the CDROM drive goes? Viao just isn't what it used to be.

---

### Post by geraldm on 2007-09-08
the command
dmesg
should provide some clues about what the cdrom drive was at discovery in booting.
The file should be available in an editor as /ver/log/dmesg.

If the hardware no longer works DO LOOK AT THE LOG as that is where there should be
error messages.
Were there any clues in there?

Gerald

---

### Post by sit properly on 2007-09-08
Here's the data from dmesg:

```
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:a0000000)
[    0.000000] Detected 1729.124 MHz processor.
[   12.721289] Built 1 zonelists.  Total pages: 257699
[   12.721292] Kernel command line: root=UUID=fbfab767-2d85-4f9b-a223-49b9878f2054 ro quiet splash
[   12.721448] mapped APIC to ffffd000 (fee00000)
[   12.721450] mapped IOAPIC to ffffc000 (fec00000)
[   12.721453] Enabling fast FPU save and restore... done.
[   12.721456] Enabling unmasked SIMD FPU exception support... done.
[   12.721463] Initializing CPU#0
[   12.721525] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   12.723036] Console: colour VGA+ 80x25
[   12.723334] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   12.723727] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   12.748393] Memory: 1017724k/1038912k available (1917k kernel code, 20504k reserved, 867k data, 328k init, 121408k highmem)
[   12.748403] virtual kernel memory layout:
[   12.748404]     fixmap  : 0xfffa9000 - 0xfffff000   ( 344 kB)
[   12.748405]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   12.748406]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   12.748408]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   12.748409]       .init : 0xc03bc000 - 0xc040e000   ( 328 kB)
[   12.748410]       .data : 0xc02df4e3 - 0xc03b8434   ( 867 kB)
[   12.748412]       .text : 0xc0100000 - 0xc02df4e3   (1917 kB)
[   12.748415] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   12.825496] Calibrating delay using timer specific routine.. 3462.00 BogoMIPS (lpj=6924010)
[   12.825529] Security Framework v1.0.0 initialized
[   12.825537] SELinux:  Disabled at boot.
[   12.825547] Mount-cache hash table entries: 512
[   12.825647] CPU: After generic identify, caps: afe9fbff 00100000 00000000 00000000 0000c109 00000000 00000000
[   12.825654] monitor/mwait feature present.
[   12.825656] using mwait in idle threads.
[   12.825660] CPU: L1 I cache: 32K, L1 D cache: 32K
[   12.825662] CPU: L2 cache: 1024K
[   12.825665] CPU: After all inits, caps: afe9fbff 00100000 00000000 00002940 0000c109 00000000 00000000
[   12.825673] Compat vDSO mapped to ffffe000.
[   12.825677] Remapping vsyscall page to ffffe000
[   12.825688] CPU: Intel(R) Celeron(R) M CPU        430  @ 1.73GHz stepping 08
[   12.825694] Checking 'hlt' instruction... OK.
[   12.841882] Early unpacking initramfs... done
[   13.219679] ACPI: Core revision 20060707
[   13.219906] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   13.254674] ENABLING IO-APIC IRQs
[   13.254875] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   13.401468] Booting paravirtualized kernel on bare hardware
[   13.401547] Time: 15:39:44  Date: 08/08/107
[   13.401571] NET: Registered protocol family 16
[   13.401641] EISA bus registered
[   13.401645] ACPI: bus type pci registered
[   13.401785] PCI: PCI BIOS revision 2.10 entry at 0xfd863, last bus=10
[   13.401787] PCI: Using configuration type 1
[   13.401789] Setting up standard PCI resources
[   13.461579] ACPI: Interpreter enabled
[   13.461582] ACPI: Using IOAPIC for interrupt routing
[   13.477709] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   13.477715] PCI: Probing PCI hardware (bus 00)
[   13.486168] Boot video device is 0000:00:02.0
[   13.486818] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[   13.486822] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[   13.488003] PCI: Transparent bridge - 0000:00:1e.0
[   13.488067] PCI: Bus #0b (-#0e) is hidden behind transparent bridge #0a (-#0b) (try 'pci=assign-busses')
[   13.488070] Please report the result to linux-kernel to fix this permanently
[   13.488149] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   13.496114] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[   13.496365] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[   13.496610] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[   13.496856] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[   13.497767] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[   13.498753] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 *7 10 12 14 15)
[   13.498988] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 *3 4 5 6 7 11 12 14 15)
[   13.499224] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[   13.499458] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[   13.499690] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[   13.499924] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[   13.500158] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 *4 5 6 7 10 12 14 15)
[   13.500393] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 11 12 14 15)
[   13.602656] Linux Plug and Play Support v0.97 (c) Adam Belay
[   13.602664] pnp: PnP ACPI init
[   13.614083] pnp: PnP ACPI: found 9 devices
[   13.614088] PnPBIOS: Disabled by ACPI PNP
[   13.614124] PCI: Using ACPI for IRQ routing
[   13.614127] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   13.652824] NET: Registered protocol family 8
[   13.652826] NET: Registered protocol family 20
[   13.653172] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[   13.653179] PCI: Bridge: 0000:00:1c.0
[   13.653182]   IO window: 2000-2fff
[   13.653193]   MEM window: c8000000-c9ffffff
[   13.653200]   PREFETCH window: c0000000-c1ffffff
[   13.653206] PCI: Bridge: 0000:00:1c.1
[   13.653209]   IO window: 3000-3fff
[   13.653215]   MEM window: ca000000-cbffffff
[   13.653220]   PREFETCH window: c2000000-c3ffffff
[   13.653225] PCI: Bridge: 0000:00:1c.2
[   13.653228]   IO window: 4000-4fff
[   13.653234]   MEM window: cc000000-cdffffff
[   13.653239]   PREFETCH window: c4000000-c5ffffff
[   13.653245] PCI: Bridge: 0000:00:1c.3
[   13.653248]   IO window: 5000-5fff
[   13.653254]   MEM window: ce000000-cfffffff
[   13.653258]   PREFETCH window: c6000000-c7ffffff
[   13.653270] PCI: Bus 11, cardbus bridge: 0000:0a:03.0
[   13.653273]   IO window: 00006000-000060ff
[   13.653278]   IO window: 00006400-000064ff
[   13.653283]   PREFETCH window: 50000000-53ffffff
[   13.653289]   MEM window: 54000000-57ffffff
[   13.653294] PCI: Bridge: 0000:00:1e.0
[   13.653297]   IO window: 6000-6fff
[   13.653303]   MEM window: d0000000-d00fffff
[   13.653307]   PREFETCH window: 50000000-53ffffff
[   13.653337] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 16
[   13.653344] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   13.653368] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 17
[   13.653373] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   13.653397] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
[   13.653402] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   13.653426] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 21 (level, low) -> IRQ 19
[   13.653431] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   13.653442] PCI: Enabling device 0000:00:1e.0 (0004 -> 0007)
[   13.653448] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   13.653465] PCI: Enabling device 0000:0a:03.0 (0000 -> 0003)
[   13.653469] ACPI: PCI Interrupt 0000:0a:03.0[A] -> GSI 16 (level, low) -> IRQ 17
[   13.653495] NET: Registered protocol family 2
[   13.689220] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   13.689318] TCP established hash table entries: 131072 (order: 7, 524288 bytes)
[   13.689722] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[   13.689928] TCP: Hash tables configured (established 131072 bind 65536)
[   13.689931] TCP reno registered
[   13.701293] checking if image is initramfs... it is
[   14.441558] Freeing initrd memory: 8056k freed
[   14.441739] Simple Boot Flag at 0x36 set to 0x1
[   14.441998] audit: initializing netlink socket (disabled)
[   14.442010] audit(1189265984.776:1): initialized
[   14.442063] highmem bounce pool size: 64 pages
[   14.442112] VFS: Disk quotas dquot_6.5.1
[   14.442130] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   14.442176] io scheduler noop registered
[   14.442178] io scheduler anticipatory registered
[   14.442180] io scheduler deadline registered
[   14.442187] io scheduler cfq registered (default)
[   14.442430] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   14.442487] assign_interrupt_mode Found MSI capability
[   14.442490] Allocate Port Service[0000:00:1c.0:pcie00]
[   14.442518] Allocate Port Service[0000:00:1c.0:pcie02]
[   14.442632] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   14.442688] assign_interrupt_mode Found MSI capability
[   14.442690] Allocate Port Service[0000:00:1c.1:pcie00]
[   14.442715] Allocate Port Service[0000:00:1c.1:pcie02]
[   14.442826] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   14.442881] assign_interrupt_mode Found MSI capability
[   14.442883] Allocate Port Service[0000:00:1c.2:pcie00]
[   14.442909] Allocate Port Service[0000:00:1c.2:pcie02]
[   14.443022] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   14.443078] assign_interrupt_mode Found MSI capability
[   14.443081] Allocate Port Service[0000:00:1c.3:pcie00]
[   14.443112] Allocate Port Service[0000:00:1c.3:pcie02]
[   14.443263] isapnp: Scanning for PnP cards...
[   14.797490] isapnp: No Plug & Play device found
[   14.820512] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   14.821252] mice: PS/2 mouse device common for all mice
[   14.821672] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   14.821884] input: Macintosh mouse button emulation as /class/input/input0
[   14.821911] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   14.821915] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   14.822143] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   14.825900] i8042.c: Detected active multiplexing controller, rev 1.1.
[   14.831588] serio: i8042 KBD port at 0x60,0x64 irq 1
[   14.831591] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   14.831594] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   14.831596] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   14.831598] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   14.832055] EISA: Probing bus 0 at eisa.0
[   14.832061] Cannot allocate resource for EISA slot 1
[   14.832064] Cannot allocate resource for EISA slot 2
[   14.832066] Cannot allocate resource for EISA slot 3
[   14.832068] Cannot allocate resource for EISA slot 4
[   14.832070] Cannot allocate resource for EISA slot 5
[   14.832073] Cannot allocate resource for EISA slot 6
[   14.832083] EISA: Detected 0 cards.
[   14.862251] TCP cubic registered
[   14.862259] NET: Registered protocol family 1
[   14.862278] Using IPI Shortcut mode
[   14.862345] ACPI: (supports S0 S3 S4 S5)
[   14.862391]   Magic number: 7:342:689
[   14.862688] Freeing unused kernel memory: 328k freed
[   14.864751] Time: tsc clocksource has been installed.
[   15.031583] input: AT Translated Set 2 keyboard as /class/input/input1
[   16.066740] Capability LSM initialized
[   16.081065] device-mapper: ioctl: 4.11.0-ioctl (2006-10-12) initialised: dm-devel@redhat.com
[   16.107596] ACPI: CPU0 (power states: C1[C1] C2[C2])
[   16.107602] ACPI: Processor [CPU0] (supports 8 throttling states)
[   16.109287] ACPI Exception (acpi_thermal-0412): AE_NOT_FOUND, Invalid active threshold [0] [20060707]
[   16.111310] ACPI: Thermal Zone [TZ00] (59 C)
[   16.112469] ACPI Exception (acpi_thermal-0412): AE_NOT_FOUND, Invalid active threshold [0] [20060707]
[   16.113363] ACPI: Thermal Zone [TZ01] (59 C)
[   16.188572] md: linear personality registered for level -1
[   16.191835] md: multipath personality registered for level -4
[   16.194899] md: raid0 personality registered for level 0
[   16.198520] md: raid1 personality registered for level 1
[   16.201536] raid5: automatically using best checksumming function: pIII_sse
[   16.220255]    pIII_sse  :  4397.000 MB/sec
[   16.220257] raid5: using function: pIII_sse (4397.000 MB/sec)
[   16.292292] raid6: int32x1    544 MB/s
[   16.360298] raid6: int32x2    641 MB/s
[   16.428198] raid6: int32x4    535 MB/s
[   16.496194] raid6: int32x8    455 MB/s
[   16.564160] raid6: mmxx1     1578 MB/s
[   16.632122] raid6: mmxx2     1745 MB/s
[   16.700122] raid6: sse1x1    1177 MB/s
[   16.768065] raid6: sse1x2    1633 MB/s
[   16.836055] raid6: sse2x1    1802 MB/s
[   16.904016] raid6: sse2x2    1968 MB/s
[   16.904018] raid6: using algorithm sse2x2 (1968 MB/s)
[   16.904021] md: raid6 personality registered for level 6
[   16.904023] md: raid5 personality registered for level 5
[   16.904025] md: raid4 personality registered for level 4
[   16.934777] md: raid10 personality registered for level 10
[   17.276338] usbcore: registered new interface driver usbfs
[   17.276357] usbcore: registered new interface driver hub
[   17.276374] usbcore: registered new device driver usb
[   17.277151] USB Universal Host Controller Interface driver v3.0
[   17.277199] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 20
[   17.277209] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   17.277213] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   17.277348] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   17.277381] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00001820
[   17.277472] usb usb1: configuration #1 chosen from 1 choice
[   17.277497] hub 1-0:1.0: USB hub found
[   17.277502] hub 1-0:1.0: 2 ports detected
[   17.378775] ieee1394: Initialized config rom entry `ip1394'
[   17.380052] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 16
[   17.380064] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   17.380068] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   17.380089] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   17.380122] uhci_hcd 0000:00:1d.1: irq 16, io base 0x00001840
[   17.380205] usb usb2: configuration #1 chosen from 1 choice
[   17.380226] hub 2-0:1.0: USB hub found
[   17.380231] hub 2-0:1.0: 2 ports detected
[   17.483931] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   17.483945] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   17.483949] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   17.483971] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   17.484005] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[   17.484083] usb usb3: configuration #1 chosen from 1 choice
[   17.484104] hub 3-0:1.0: USB hub found
[   17.484109] hub 3-0:1.0: 2 ports detected
[    4.672000] Time: acpi_pm clocksource has been installed.
[    4.740000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 17
[    4.740000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[    4.740000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    4.740000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    4.740000] uhci_hcd 0000:00:1d.3: irq 17, io base 0x00001880
[    4.740000] usb usb4: configuration #1 chosen from 1 choice
[    4.740000] hub 4-0:1.0: USB hub found
[    4.740000] hub 4-0:1.0: 2 ports detected
[    4.848000] SCSI subsystem initialized
[    4.856000] libata version 2.20 loaded.
[    4.856000] ata_piix 0000:00:1f.1: version 2.10ac1
[    4.856000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[    4.856000] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[    4.856000] ata1: PATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011810 irq 14
[    4.856000] ata2: PATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011818 irq 15
[    4.856000] scsi0 : ata_piix
[    4.980000] usb 3-2: new full speed USB device using uhci_hcd and address 2
[    5.016000] ATA: abnormal status 0x7F on port 0x000101f7
[    5.020000] scsi1 : ata_piix
[    5.020000] ata2: port disabled. ignoring.
[    5.020000] ata_piix 0000:00:1f.2: MAP [ P0 P2 XX XX ]
[    5.020000] ata_piix 0000:00:1f.2: invalid MAP value 0
[    5.176000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 21
[    5.176000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    5.176000] ata3: SATA max UDMA/133 cmd 0x000118d0 ctl 0x000118c6 bmdma 0x000118b0 irq 21
[    5.176000] ata4: SATA max UDMA/133 cmd 0x000118c8 ctl 0x000118c2 bmdma 0x000118b8 irq 21
[    5.176000] scsi2 : ata_piix
[    5.208000] usb 3-2: configuration #1 chosen from 1 choice
[    5.340000] ata3.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[    5.340000] ata3.00: ATA-6: TOSHIBA MK8032GSX, AS111G, max UDMA/100
[    5.340000] ata3.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    5.348000] ata3.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[    5.348000] ata3.00: configured for UDMA/100
[    5.348000] scsi3 : ata_piix
[    5.448000] usb 4-2: new full speed USB device using uhci_hcd and address 2
[    5.504000] scsi 2:0:0:0: Direct-Access     ATA      TOSHIBA MK8032GS AS11 PQ: 0 ANSI: 5
[    5.504000] PCI: Enabling device 0000:0a:03.1 (0000 -> 0002)
[    5.504000] ACPI: PCI Interrupt 0000:0a:03.1[A] -> GSI 16 (level, low) -> IRQ 17
[    5.552000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 20
[    5.552000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    5.552000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    5.552000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    5.552000] ehci_hcd 0000:00:1d.7: debug port 1
[    5.552000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    5.552000] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xd0444000
[    5.556000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    5.556000] usb usb5: configuration #1 chosen from 1 choice
[    5.556000] hub 5-0:1.0: USB hub found
[    5.556000] hub 5-0:1.0: 8 ports detected
[    5.556000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[d0005000-d00057ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    5.564000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[    5.564000] sda: Write Protect is off
[    5.564000] sda: Mode Sense: 00 3a 00 00
[    5.564000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.564000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[    5.564000] sda: Write Protect is off
[    5.564000] sda: Mode Sense: 00 3a 00 00
[    5.568000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.568000]  sda: sda1 sda2 sda3
[    5.596000] sd 2:0:0:0: Attached scsi disk sda
[    5.596000] sd 2:0:0:0: Attached scsi generic sg0 type 0
[    5.936000] kjournald starting.  Commit interval 5 seconds
[    5.936000] EXT3-fs: mounted filesystem with ordered data mode.
[    6.016000] usb 4-2: device not accepting address 2, error -71
[    6.312000] usb 5-6: new high speed USB device using ehci_hcd and address 2
[    6.504000] usb 5-6: configuration #1 chosen from 1 choice
[    6.688000] usb 3-2: USB disconnect, address 2
[    6.688000] usbcore: registered new interface driver libusual
[    7.084000] Initializing USB Mass Storage driver...
[    7.100000] usb 4-2: new full speed USB device using uhci_hcd and address 4
[    7.304000] usb 4-2: configuration #1 chosen from 1 choice
[    7.308000] scsi4 : SCSI emulation for USB Mass Storage devices
[    7.308000] usb-storage: device found at 2
[    7.308000] usb-storage: waiting for device to settle before scanning
[    7.308000] usbcore: registered new interface driver usb-storage
[    7.308000] USB Mass Storage support registered.
[   12.312000] usb-storage: device scan complete
[   12.316000] scsi 4:0:0:0: Direct-Access     Sony     USB   HS-CARD    4.52 PQ: 0 ANSI: 0
[   12.364000] sd 4:0:0:0: Attached scsi removable disk sdb
[   12.364000] sd 4:0:0:0: Attached scsi generic sg1 type 0
[   19.708000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   19.708000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   20.108000] iTCO_vendor_support: vendor-support=0
[   20.112000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   20.112000] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[   20.112000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   20.208000] intel_rng: FWH not detected
[   20.532000] Linux agpgart interface v0.102 (c) Dave Jones
[   20.544000] agpgart: Detected an Intel 945GM Chipset.
[   20.544000] agpgart: Detected 7932K stolen memory.
[   20.560000] agpgart: AGP aperture is 256M @ 0xb0000000
[   20.932000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 17
[   20.932000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   20.932000] sky2 0000:02:00.0: v1.13 addr 0xc8000000 irq 17 Yukon-FE (0xb7) rev 1
[   20.932000] sky2 eth0: addr 00:13:a9:60:ba:a1
[   21.008000] ieee80211_crypt: registered algorithm 'NULL'
[   21.008000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   21.008000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   21.228000] input: PS/2 Mouse as /class/input/input2
[   21.236000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.0mp
[   21.236000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[   21.236000] ACPI: PCI Interrupt 0000:06:00.0[A] -> GSI 18 (level, low) -> IRQ 18
[   21.236000] PCI: Setting latency timer of device 0000:06:00.0 to 64
[   21.236000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   21.244000] input: AlpsPS/2 ALPS GlidePoint as /class/input/input3
[   21.308000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
[   21.308000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   21.388000] Bluetooth: Core ver 2.11
[   21.388000] NET: Registered protocol family 31
[   21.392000] Bluetooth: HCI device and connection manager initialized
[   21.392000] Bluetooth: HCI socket layer initialized
[   21.428000] Bluetooth: HCI USB driver ver 2.9
[   21.456000] Real Time Clock Driver v1.12ac
[   21.508000] hda_codec: Unknown model for ALC262, trying auto-probe from BIOS...
[   21.520000] usbcore: registered new interface driver hci_usb
[   21.948000] PCI: Enabling device 0000:0a:03.2 (0000 -> 0002)
[   21.948000] ACPI: PCI Interrupt 0000:0a:03.2[B] -> GSI 17 (level, low) -> IRQ 16
[   21.948000] Yenta: CardBus bridge found at 0000:0a:03.0 [104d:820f]
[   21.948000] Yenta: Enabling burst memory read transactions
[   21.948000] Yenta: Using CSCINT to route CSC interrupts to PCI
[   21.948000] Yenta: Routing CardBus interrupts to PCI
[   21.948000] Yenta TI: socket 0000:0a:03.0, mfunc 0x01121b22, devctl 0x64
[   22.180000] Yenta: ISA IRQ mask 0x0cf8, PCI irq 17
[   22.180000] Socket status: 30000006
[   22.180000] Yenta: Raising subordinate bus# of parent bus (#0a) from #0b to #0e
[   22.180000] pcmcia: parent PCI bridge I/O window: 0x6000 - 0x6fff
[   22.180000] cs: IO port probe 0x6000-0x6fff: clean.
[   22.180000] pcmcia: parent PCI bridge Memory window: 0xd0000000 - 0xd00fffff
[   22.180000] pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x53ffffff
[   22.532000] cs: IO port probe 0x100-0x3af: clean.
[   22.532000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   22.532000] cs: IO port probe 0x820-0x8ff: clean.
[   22.536000] cs: IO port probe 0xc00-0xcf7: clean.
[   22.536000] cs: IO port probe 0xa00-0xaff: clean.
[   22.688000] lp: driver loaded but no devices found
[   22.892000] EXT3 FS on sda2, internal journal
[   23.760000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
[   25.768000] ACPI: AC Adapter [ADP1] (on-line)
[   25.836000] ACPI: Battery Slot [BAT0] (battery present)
[   25.896000] input: Lid Switch as /class/input/input4
[   25.900000] ACPI: Lid Switch [LID0]
[   25.936000] input: Power Button (CM) as /class/input/input5
[   25.940000] ACPI: Power Button (CM) [PWRB]
[   25.956000] Using specific hotkey driver
[   26.000000] ACPI: ACPI Dock Station Driver 
[   26.072000] ibm_acpi: ec object not found
[   26.168000] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   26.188000] ACPI Sony Notebook Control Driver v0.2 successfully installed
[   26.204000] pcc_acpi: loading...
[   32.844000] sky2 eth0: enabling interface
[   32.848000] sky2 eth0: ram buffer 4K
[   34.512000] [drm] Initialized drm 1.1.0 20060810
[   34.532000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 17
[   34.532000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   35.976000] ppdev: user-space parallel port driver
[   36.176000] apm: BIOS not found.
[   36.768000] sonypi: Sony Programmable I/O Controller Driver v1.26.
[   36.792000] sonypi: detected type3 model, verbose = 0, fnkeyinit = off, camera = off, compat = off, mask = 0xffffffff, useinput = on, acpi = on
[   36.792000] sonypi: enabled at irq=11, port1=0x1080, port2=0x1084
[   36.792000] sonypi: device allocated minor is 61
[   36.848000] input: Sony Vaio Jogdial as /class/input/input6
[   36.992000] input: Sony Vaio Keys as /class/input/input7
[   37.056000] sonypi command failed at drivers/char/sonypi.c : sonypi_call1 (line 646)
[   37.096000] sonypi command failed at drivers/char/sonypi.c : sonypi_call2 (line 657)
[   37.136000] sonypi command failed at drivers/char/sonypi.c : sonypi_call2 (line 659)
[   37.176000] sonypi command failed at drivers/char/sonypi.c : sonypi_call1 (line 646)
[   59.760000] NET: Registered protocol family 17
[ 1659.272000] usb 5-1: new high speed USB device using ehci_hcd and address 4
[ 1659.404000] usb 5-1: configuration #1 chosen from 1 choice
[ 1659.404000] scsi5 : SCSI emulation for USB Mass Storage devices
[ 1659.404000] usb-storage: device found at 4
[ 1659.404000] usb-storage: waiting for device to settle before scanning
[ 1664.404000] usb-storage: device scan complete
[ 1666.724000] scsi 5:0:0:0: CD-ROM            PLEXTOR  DVDR   PX-712A   1.06 PQ: 0 ANSI: 0 CCS
[ 1666.740000] sr0: scsi3-mmc drive: 125x/125x writer cd/rw xa/form2 cdda tray
[ 1666.740000] Uniform CD-ROM driver Revision: 3.20
[ 1666.740000] sr 5:0:0:0: Attached scsi CD-ROM sr0
[ 1666.740000] sr 5:0:0:0: Attached scsi generic sg2 type 5
[ 1733.608000] UDF-fs: Partition marked readonly; forcing readonly mount
[ 1733.608000] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'twin peaks 1', timestamp 2007/02/06 05:27 (1f10)
[ 1789.700000] cdrom: sr0: mrw address space DMA selected
[ 1789.708000] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 1789.708000] ISO 9660 Extensions: RRIP_1991A

```

I'm not sure what to make of it. 

The CD-ROM  PLEXTOR is *not* the one in question. That was an external I used earlier today. It worked fine (to watch twin peaks - as it says.. ).

---

### Post by Damanther on 2007-09-08
So there are 2 CD drives on this system? There is only one listed in the fstab.

---

### Post by rainwalker on 2007-09-08
My cdrom is mounted at /media rather than /dev

---

### Post by geraldm on 2007-09-08
If the device had been in fstab before, there should be an entry, with no hardware mounted
for it, usually at /dev/hdX.  I have not seen an fstab entry at /dev/cdrom before. 

I looked, but could not find any hints.  hda_codec was there, but no hdX entry.
Next check would be in the BIOS, to see if it also does not see the cdrom, which would
then suggest possibly a data cable was loose, or some other hardware problem.
You said the drive looks like it is spinning, so it is not the power cable.

Gerald

---

### Post by atlfalcons866 on 2007-09-09
i had this problem i fixed by leaving a cd in the drive during boot or compile 2.6.22. i compiled 2.6.22 and everything is faster.

---

### Post by sit properly on 2007-09-09
Hi again, 

Thanks a bunch for the help - here are my follow ups and more questions:

There have been a total of two cdrom drives on the system. There is one that's in the laptop and the other one (plextor external) that I hooked up yesterday. 

The BIOS seems really unhelpful. It's set to first boot off the internal optical drive, but don't tell me what that is or if it exists. Am I missing something here?

Install a CD and then rebooting didn't work.

Doesn't Bios usually tell you a lot about the machine? I'm getting not much info at all. No descriptions of what anything is. Just CPU, RAM & Time... Boot order... something about the speaker and Exit. That's about it.


So is dmesg saying that I have never had a CDROM installed anywhere (aside from the plextor external)?

---

### Post by Amazona aestiva on 2007-09-09
Post Your current /etc/fstab please.

---

### Post by sit properly on 2007-09-09
Here is the current fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3 -- converted during upgrade to edgy
UUID=fbfab767-2d85-4f9b-a223-49b9878f2054 / ext3 defaults,errors=remount-ro 0 1
# /dev/sda6 -- converted during upgrade to edgy
UUID=c2d7cca7-41be-4923-b9f9-4da9b915f5bb none swap sw 0 0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

---

### Post by prodigal on 2007-09-09
If your CD Rom isn't working in XP either then I would ring Sony support and get it replaced under warranty. If neither OS can find it that would suggest a hardware fault. Believe it or not it isn't that rare for CD/DVD-ROMs not to work on laptops out of the box these days. I deal with ALOT of them at work and the amount we get where the DVD ROM drive just doesn't work is ridiculous. If you ring Sony I wouldn't tell them you installed Linux, they'll use anything they can to get out of a warranty claim.

---

### Post by Amazona aestiva on 2007-09-09
Change the last line to
```
/dev/hda	/media/cdrom0	auto	users,noauto	0	0
```
Use this command to do it:
```
sudo gedit /etc/fstab
```

---

### Post by sit properly on 2007-09-09
changed the last line in fstab to above. nada. 

I think that prodigal is probably right. I *did* just have them replace the motherboard on it. Who knows what else they took out while doing it.

Last time they were *this* close to offering to have a technician visit me "on site." I'll be pretty adamant about that now. 

Thanks all for the help narrowing it down. I really appreciate it.

---

### Post by southernman on 2007-09-09
> **Amazona aestiva said:**
> Change the last line to
```
/dev/hda	/media/cdrom0	auto	users,noauto	0	0
```
Use this command to do it:
```
sudo gedit /etc/fstab
```
Ummmm, that would be

```
**_gk_**sudo gedit /etc/fstab
```

And sit's cdrom drive wouldn't be /dev/hda either. At best it would be hdc (first optical drive on the secondary IDE).

---

