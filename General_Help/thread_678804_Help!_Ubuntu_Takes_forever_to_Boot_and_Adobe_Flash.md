---
title: "Help! Ubuntu Takes forever to Boot and Adobe Flash wont install"
date: 2008-01-26
forum: General Help
---

### Post by UMD TERPS FAN on 2008-01-26
I'm new to Ubuntu.  I did a full Install on a Gateway laptop MX6446 AMD Turion 64, 2 Ghz, 1 GB ram, Broadcom wireless, and a ATI Mobility 200M. I installed Ubuntu 7.10 64 bit.  Since Ubuntu does not support Broadcom I have a PCI Dlink wireless card that works out of the box (thats how I go the wireless internet to work).  My first problem is Ubuntu TAKES FOREVER to boot up, does anyone know how to speed it up?  My second question is how do I get Adobe Flash player to install?  Mozilla will not install it. I did a search and looked through the forum and found various threads with help, however non of them seem to work.. Does anyone have step by step instructions on how to install it?

Thank You,
Grant

---

### Post by danwood76 on 2008-01-26
can you install bootchart and post the boot image:
```
 sudo apt-get install bootchart
```

then reboot and post the image in /var/log/bootchart/ this will tell us what is taking so long at boot time.

there is a .deb package floating around on the forums if you search, you will need to uninstall gnash for it to work.

regards,
Danny

---

### Post by UMD TERPS FAN on 2008-01-26
> **danwood76 said:**
> can you install bootchart and post the boot image:
```
 sudo apt-get install bootchart
```

then reboot and post the image in /var/log/bootchart/ this will tell us what is taking so long at boot time.

there is a .deb package floating around on the forums if you search, you will need to uninstall gnash for it to work.

regards,
Danny

Its says;

Package bootchart is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package bootchart has no installation candidate
grant@grant-laptop:~$

---

### Post by FuturePilot on 2008-01-26
Go System>Administration>Software Sources. Check all of the boxes in the first tab and uncheck the CD-ROM if it is checked. Then go to the Updates tab and check the first two and optionally the fourth box. Hit Close and Reload the sources when prompted.

As for Flash there's a problem with the Flash package right now. Take a look here
[http://ubuntuforums.org/showthread.php?t=636397]("http://ubuntuforums.org/showthread.php?t=636397")

---

### Post by danwood76 on 2008-01-26
Well go into System > Administration > Software Sources and check all the options (enabling all the software repositories) except the CD.

then do:
```
sudo apt-get update
sudo apt-get install bootchart
```

regards,
Danny

---

### Post by UMD TERPS FAN on 2008-01-26
> **FuturePilot said:**
> Go System>Administration>Software Sources. Check all of the boxes in the first tab and uncheck the CD-ROM if it is checked. Then go to the Updates tab and check the first two and optionally the fourth box. Hit Close and Reload the sources when prompted.

As for Flash there's a problem with the Flash package right now. Take a look here
[http://ubuntuforums.org/showthread.php?t=636397]("http://ubuntuforums.org/showthread.php?t=636397")

AH HA! it worked for the flash player thanks!  However I'm still having problems figuring out why Ubuntu takes forever to Boot, anyone know how to correct the problem.

-Grant

---

### Post by danwood76 on 2008-01-26
well if you post the boot chart we could see whats taking so long at boot and this would help diagnose your problem.

regards,
Danny

---

### Post by UMD TERPS FAN on 2008-01-26
> **danwood76 said:**
> well if you post the boot chart we could see whats taking so long at boot and this would help diagnose your problem.

regards,
Danny

Heres the dmesg > /tmp/dmsg.txt; gedit /tmp/dmsg.txt

[    0.000000] Linux version 2.6.22-14-generic (buildd@crested) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 21:45:15 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] Command line: root=UUID=0ccaddce-6cc5-454b-9bce-c5fe109a2360 ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
[    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000037e80000 (usable)
[    0.000000]  BIOS-e820: 0000000037e80000 - 0000000037e91000 (ACPI data)
[    0.000000]  BIOS-e820: 0000000037e91000 - 0000000037f00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000037f00000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 157) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 228992) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xFFFF8100000F88E0 checksum 0
[    0.000000] ACPI: RSDP 000F88E0, 0014 (r0 PTLTD )
[    0.000000] ACPI: RSDT 37E8B5D3, 0034 (r1 GATEWA M367     20060904  LTP        0)
[    0.000000] ACPI: FACP 37E90DEB, 0074 (r1 GATEWA M367     20060904 ATI     F4240)
[    0.000000] ACPI: DSDT 37E8B607, 57E4 (r1 GATEWA M367     20060904 MSFT  100000E)
[    0.000000] ACPI: FACS 37E91FC0, 0040
[    0.000000] ACPI: SSDT 37E90E5F, 0115 (r1 GATEWA M367     20060904  LTP        1)
[    0.000000] ACPI: APIC 37E90F74, 0050 (r1 GATEWA M367     20060904  LTP        0)
[    0.000000] ACPI: MCFG 37E90FC4, 003C (r1 GATEWA M367     20060904  LTP        0)
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000037e80000
[    0.000000] Entering add_active_range(0, 0, 157) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 228992) 1 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-0000000037e80000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      157
[    0.000000]     0:      256 ->   228992
[    0.000000] On node 0 totalpages: 228893
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1125 pages reserved
[    0.000000]   DMA zone: 2816 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 3074 pages used for memmap
[    0.000000]   DMA32 zone: 221822 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000] ATI board detected. Disabling timer routing over 8254.
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 21 low level)
[    0.000000] Setting APIC routing to flat
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] swsusp: Registered nosave memory region: 000000000009d000 - 000000000009e000
[    0.000000] swsusp: Registered nosave memory region: 000000000009e000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000d2000
[    0.000000] swsusp: Registered nosave memory region: 00000000000d2000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:a0000000)
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 34696 bytes of per cpu data
[    0.000000] Built 1 zonelists.  Total pages: 224638
[    0.000000] Kernel command line: root=UUID=0ccaddce-6cc5-454b-9bce-c5fe109a2360 ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[   13.415974] time.c: Detected 1995.045 MHz processor.
[   13.416883] Console: colour VGA+ 80x25
[   13.416898] Checking aperture...
[   13.416902] CPU 0: aperture @ d056000000 size 32 MB
[   13.416904] Aperture too small (32 MB)
[   13.428581] No AGP bridge found
[   13.436386] Memory: 890676k/915968k available (2274k kernel code, 24896k reserved, 1181k data, 296k init)
[   13.436435] SLUB: Genslabs=23, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   13.513926] Calibrating delay using timer specific routine.. 3994.10 BogoMIPS (lpj=7988200)
[   13.513959] Security Framework v1.0.0 initialized
[   13.513966] SELinux:  Disabled at boot.
[   13.514052] Dentry cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   13.514689] Inode-cache hash table entries: 65536 (order: 7, 524288 bytes)
[   13.514972] Mount-cache hash table entries: 256
[   13.515109] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   13.515112] CPU: L2 Cache: 512K (64 bytes/line)
[   13.515116] CPU 0/0 -> Node 0
[   13.515133] SMP alternatives: switching to UP code
[   13.515288] Freeing SMP alternatives: 24k freed
[   13.515599] Early unpacking initramfs... done
[   13.823802] ACPI: Core revision 20070126
[   13.823860] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   14.273572] Using local APIC timer interrupts.
[   14.323673] result 12469030
[   14.323675] Detected 12.469 MHz APIC timer.
[   14.325569] Brought up 1 CPUs
[   14.325770] NET: Registered protocol family 16
[   14.325856] ACPI: bus type pci registered
[   14.325864] PCI: Using configuration type 1
[   14.326607] ACPI: EC: Look up EC in DSDT
[   14.327519] ACPI: EC: GPE=0x1c, ports=0x66, 0x62
[   14.328603] ACPI: Interpreter enabled
[   14.328606] ACPI: (supports S0 S3 S4 S5)
[   14.328620] ACPI: Using IOAPIC for interrupt routing
[   14.333118] ACPI: EC: GPE=0x1c, ports=0x66, 0x62
[   14.333156] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   14.333167] PCI: Probing PCI hardware (bus 00)
[   14.334487] PCI: Transparent bridge - 0000:00:14.4
[   14.334590] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   14.334738] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB4_._PRT]
[   14.334842] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB5_._PRT]
[   14.334957] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[   14.335048] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[   14.337257] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 11) *0, disabled.
[   14.337387] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 11) *0, disabled.
[   14.337548] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 11) *0, disabled.
[   14.337675] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 11) *0, disabled.
[   14.337801] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11) *0, disabled.
[   14.337928] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11) *0, disabled.
[   14.338055] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11) *0, disabled.
[   14.338181] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11) *0, disabled.
[   14.338308] ACPI: PCI Interrupt Link [LNKU] (IRQs 3 4 5 7 10 11) *0, disabled.
[   14.338384] Linux Plug and Play Support v0.97 (c) Adam Belay
[   14.338394] pnp: PnP ACPI init
[   14.338403] ACPI: bus type pnp registered
[   14.340507] pnp: PnP ACPI: found 10 devices
[   14.340511] ACPI: ACPI bus type pnp unregistered
[   14.340571] PCI: Using ACPI for IRQ routing
[   14.340573] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   14.340674] NET: Registered protocol family 8
[   14.340676] NET: Registered protocol family 20
[   14.340787] pnp: 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
[   14.340791] pnp: 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
[   14.340794] pnp: 00:01: iomem range 0xfee00000-0xfee00fff could not be reserved
[   14.340805] pnp: 00:08: ioport range 0x1080-0x1080 has been reserved
[   14.340808] pnp: 00:08: ioport range 0x220-0x22f has been reserved
[   14.340811] pnp: 00:08: ioport range 0x40b-0x40b has been reserved
[   14.340814] pnp: 00:08: ioport range 0x4d0-0x4d1 has been reserved
[   14.340819] pnp: 00:09: iomem range 0xe0000-0xfffff could not be reserved
[   14.340823] pnp: 00:09: iomem range 0xfff00000-0xffffffff could not be reserved
[   14.340825] pnp: 00:09: iomem range 0x0-0xfff could not be reserved
[   14.341082] PCI: Bridge: 0000:00:01.0
[   14.341084]   IO window: 9000-9fff
[   14.341088]   MEM window: c0100000-c01fffff
[   14.341091]   PREFETCH window: c8000000-cfffffff
[   14.341093] PCI: Bridge: 0000:00:04.0
[   14.341096]   IO window: a000-afff
[   14.341099]   MEM window: c0200000-c02fffff
[   14.341101]   PREFETCH window: disabled.
[   14.341103] PCI: Bridge: 0000:00:05.0
[   14.341104]   IO window: disabled.
[   14.341107]   MEM window: c0300000-c03fffff
[   14.341109]   PREFETCH window: disabled.
[   14.341118] PCI: Bus 9, cardbus bridge: 0000:08:09.0
[   14.341120]   IO window: 00002000-000020ff
[   14.341126]   IO window: 00002400-000024ff
[   14.341132]   PREFETCH window: 50000000-53ffffff
[   14.341138]   MEM window: 54000000-57ffffff
[   14.341143] PCI: Bridge: 0000:00:14.4
[   14.341146]   IO window: 2000-2fff
[   14.341152]   MEM window: c0400000-c04fffff
[   14.341157]   PREFETCH window: 50000000-53ffffff
[   14.341175] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   14.341181] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   14.341209] ACPI: PCI Interrupt 0000:08:09.0[A] -> GSI 20 (level, low) -> IRQ 20
[   14.341262] NET: Registered protocol family 2
[   14.341511] Time: tsc clocksource has been installed.
[   14.377556] IP route cache hash table entries: 32768 (order: 6, 262144 bytes)
[   14.377897] TCP established hash table entries: 131072 (order: 9, 3145728 bytes)
[   14.379517] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   14.380048] TCP: Hash tables configured (established 131072 bind 65536)
[   14.380051] TCP reno registered
[   14.389622] checking if image is initramfs... it is
[   14.991893] Freeing initrd memory: 7745k freed
[   14.996412] audit: initializing netlink socket (disabled)
[   14.996424] audit(1201364432.132:1): initialized
[   14.998192] VFS: Disk quotas dquot_6.5.1
[   14.998241] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   14.998333] io scheduler noop registered
[   14.998335] io scheduler anticipatory registered
[   14.998337] io scheduler deadline registered
[   14.998419] io scheduler cfq registered (default)
[   14.998425] PCI: MSI quirk detected. MSI deactivated.
[   14.998898] Boot video device is 0000:01:05.0
[   14.999043] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   14.999062] assign_interrupt_mode Found MSI capability
[   14.999066] Allocate Port Service[0000:00:04.0:pcie00]
[   14.999121] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   14.999139] assign_interrupt_mode Found MSI capability
[   14.999141] Allocate Port Service[0000:00:05.0:pcie00]
[   15.020405] Real Time Clock Driver v1.12ac
[   15.020485] Linux agpgart interface v0.102 (c) Dave Jones
[   15.020488] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   15.021463] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   15.021631] input: Macintosh mouse button emulation as /class/input/input0
[   15.021694] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[   15.024543] serio: i8042 KBD port at 0x60,0x64 irq 1
[   15.024549] serio: i8042 AUX port at 0x60,0x64 irq 12
[   15.024727] mice: PS/2 mouse device common for all mice
[   15.024841] TCP cubic registered
[   15.024904] NET: Registered protocol family 1
[   15.025093] /build/buildd/linux-source-2.6.22-2.6.22/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   15.025101] Freeing unused kernel memory: 296k freed
[   15.093217] input: AT Translated Set 2 keyboard as /class/input/input1
[   16.191004] AppArmor: AppArmor initialized<5>audit(1201364433.328:2):  type=1505 info="AppArmor initialized" pid=1214
[   16.302808] fuse init (API version 7.8)
[   16.403362] Failure registering capabilities with primary security module.
[   16.506704] ACPI: CPU0 (power states: C1[C1] C2[C2])
[   16.506710] ACPI: Processor [CPU0] (supports 8 throttling states)
[   16.506720] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   16.904296] ACPI: Thermal Zone [THRM] (55 C)
[   26.769133] usbcore: registered new interface driver usbfs
[   26.769156] usbcore: registered new interface driver hub
[   26.769176] usbcore: registered new device driver usb
[   26.769832] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   26.769868] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 19
[   26.769957] ohci_hcd 0000:00:13.0: OHCI Host Controller
[   26.770113] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[   26.770136] ohci_hcd 0000:00:13.0: irq 19, io mem 0xc0004000
[   26.823488] usb usb1: configuration #1 chosen from 1 choice
[   26.823514] hub 1-0:1.0: USB hub found
[   26.823527] hub 1-0:1.0: 4 ports detected
[   26.927434] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 19
[   26.927546] ohci_hcd 0000:00:13.1: OHCI Host Controller
[   26.927598] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[   26.927620] ohci_hcd 0000:00:13.1: irq 19, io mem 0xc0005000
[   26.983412] usb usb2: configuration #1 chosen from 1 choice
[   26.983442] hub 2-0:1.0: USB hub found
[   26.983454] hub 2-0:1.0: 4 ports detected
[   27.100455] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 19
[   27.100542] ehci_hcd 0000:00:13.2: EHCI Host Controller
[   27.100596] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[   27.100656] ehci_hcd 0000:00:13.2: irq 19, io mem 0xc0006000
[   27.100669] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   27.100751] usb usb3: configuration #1 chosen from 1 choice
[   27.100778] hub 3-0:1.0: USB hub found
[   27.100784] hub 3-0:1.0: 8 ports detected
[   27.425384] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   27.425390] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   27.426120] ATIIXP: IDE controller at PCI slot 0000:00:14.1
[   27.426139] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 16
[   27.426150] ATIIXP: chipset revision 128
[   27.426153] ATIIXP: not 100% native mode: will probe irqs later
[   27.426161]     ide0: BM-DMA at 0x8410-0x8417, BIOS settings: hda:DMA, hdb:DMA
[   27.426175] ATIIXP: simplex device: DMA disabled
[   27.426177] ide1: ATIIXP Bus-Master DMA disabled (BIOS)
[   27.426181] Probing IDE interface ide0...
[   27.715347] hda: HTS421210H9AT00, ATA DISK drive
[   28.498933] hdb: HL-DT-ST DVD-RW GWA-4082N, ATAPI CD/DVD-ROM drive
[   28.554501] hda: selected mode 0x45
[   28.554773] hdb: selected mode 0x42
[   28.555691] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   28.943866] Probing IDE interface ide1...
[   29.513271] SCSI subsystem initialized
[   29.518207] ACPI: PCI Interrupt 0000:08:09.1[B] -> GSI 21 (level, low) -> IRQ 21
[   29.568770] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[c0405000-c04057ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   29.569716] libata version 2.21 loaded.
[   29.578308] hda: max request size: 512KiB
[   29.585041] hda: 195371568 sectors (100030 MB) w/7528KiB Cache, CHS=16383/255/63, UDMA(100)
[   29.585334] hda: cache flushes supported
[   29.585383]  hda: hda1 hda2 < hda5 >
[   29.662299] hdb: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[   29.662308] Uniform CD-ROM driver Revision: 3.20
[   30.837459] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00e0b80367007af0]
[   31.150246] Attempting manual resume
[   31.150250] swsusp: Resume From Partition 3:5
[   31.150252] PM: Checking swsusp image.
[   31.249146] PM: Resume from disk failed.
[   32.260697] kjournald starting.  Commit interval 5 seconds
[   32.260708] EXT3-fs: mounted filesystem with ordered data mode.
[  112.130058] ip_tables: (C) 2000-2006 Netfilter Core Team
[  112.155310] Netfilter messages via NETLINK v0.30.
[  112.257155] nf_conntrack version 0.5.0 (3578 buckets, 28624 max)
[  124.715077] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[  124.721105] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[  125.233519] ieee80211_crypt: registered algorithm 'NULL'
[  125.235844] ieee80211: 802.11 data/management/control stack, git-1.1.13
[  125.235848] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[  125.268246] bcm43xx driver
[  125.268343] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[  125.268353] PCI: Setting latency timer of device 0000:05:00.0 to 64
[  125.495789] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[  125.495803] PCI: Setting latency timer of device 0000:02:00.0 to 64
[  125.495911] sky2 0000:02:00.0: v1.18 addr 0xc0200000 irq 16 Yukon-FE (0xb7) rev 1
[  125.496102] sky2 eth1: addr 00:e0:b8:b8:8b:e6
[  125.527441] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[  126.252257] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 16
[  126.575318] input: PC Speaker as /class/input/input2
[  126.746493] Yenta: CardBus bridge found at 0000:08:09.0 [107b:0367]
[  126.746521] Yenta: Using CSCINT to route CSC interrupts to PCI
[  126.746523] Yenta: Routing CardBus interrupts to PCI
[  126.746530] Yenta TI: socket 0000:08:09.0, mfunc 0x01ac1b22, devctl 0x64
[  126.978643] Yenta: ISA IRQ mask 0x0ef8, PCI irq 20
[  126.978649] Socket status: 30000868
[  126.978653] pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
[  126.978657] pcmcia: parent PCI bridge Memory window: 0xc0400000 - 0xc04fffff
[  126.978660] pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x53ffffff
[  126.985999] ACPI: PCI Interrupt 0000:08:09.2[A] -> GSI 20 (level, low) -> IRQ 20
[  127.281233] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x23aeb3, caps: 0xa04713/0x10008
[  127.313888] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[  127.621466] pccard: CardBus card inserted into slot 0
[  127.919681] ath_hal: module license 'Proprietary' taints kernel.
[  127.920882] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[  128.110248] wlan: 0.8.4.2 (0.9.3.2)
[  128.156387] ath_pci: 0.9.4.5 (0.9.3.2)
[  128.156468] PCI: Enabling device 0000:09:00.0 (0000 -> 0002)
[  128.156476] ACPI: PCI Interrupt 0000:09:00.0[A] -> GSI 20 (level, low) -> IRQ 20
[  128.854955] ath_rate_sample: 1.2 (0.9.3.2)
[  128.855878] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[  128.855886] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[  128.855894] wifi0: turboG rates: 6Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[  128.855899] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[  128.855903] wifi0: mac 7.9 phy 4.5 radio 5.6
[  128.855908] wifi0: Use hw queue 1 for WME_AC_BE traffic
[  128.855910] wifi0: Use hw queue 0 for WME_AC_BK traffic
[  128.855912] wifi0: Use hw queue 2 for WME_AC_VI traffic
[  128.855914] wifi0: Use hw queue 3 for WME_AC_VO traffic
[  128.855916] wifi0: Use hw queue 8 for CAB traffic
[  128.855917] wifi0: Use hw queue 9 for beacons
[  128.884848] wifi0: Atheros 5212: mem=0x54000000, irq=20
[  130.943687] lp: driver loaded but no devices found
[  131.053551] Adding 2626588k swap on /dev/hda5.  Priority:-1 extents:1 across:2626588k
[  133.063451] EXT3 FS on hda1, internal journal
[  140.361363] No dock devices found.
[  140.986907] ACPI: AC Adapter [ACAD] (on-line)
[  141.314184] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[  141.622592] ACPI: Battery Slot [BAT1] (battery absent)
[  142.490322] input: Power Button (FF) as /class/input/input4
[  142.494296] ACPI: Power Button (FF) [PWRF]
[  142.518883] input: Lid Switch as /class/input/input5
[  142.522830] ACPI: Lid Switch [LID]
[  142.547459] input: Sleep Button (CM) as /class/input/input6
[  142.551379] ACPI: Sleep Button (CM) [SLPB]
[  142.575883] input: Power Button (CM) as /class/input/input7
[  142.579784] ACPI: Power Button (CM) [PWRB]
[  145.058867] powernow-k8: Found 1 AMD Turion(tm) 64 Mobile Technology MK-36 processors (version 2.00.00)
[  145.058911] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0x10
[  145.058914] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x12
[  145.058916] powernow-k8:    2 : fid 0x8 (1600 MHz), vid 0x14
[  145.058918] powernow-k8:    3 : fid 0x0 (800 MHz), vid 0x18
[  152.815415] sky2 eth0: enabling interface
[  152.948744] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  153.274069] ppdev: user-space parallel port driver
[  154.907854] audit(1201364573.192:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5109 profile="/usr/sbin/cupsd"
[  156.178429] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  157.445467] Failure registering capabilities with primary security module.
[  159.330441] Bluetooth: Core ver 2.11
[  159.330537] NET: Registered protocol family 31
[  159.330539] Bluetooth: HCI device and connection manager initialized
[  159.330543] Bluetooth: HCI socket layer initialized
[  159.423140] Bluetooth: L2CAP ver 2.8
[  159.423144] Bluetooth: L2CAP socket layer initialized
[  159.494603] Bluetooth: RFCOMM socket layer initialized
[  159.494675] Bluetooth: RFCOMM TTY layer initialized
[  159.494677] Bluetooth: RFCOMM ver 1.8
[  170.104428] Marking TSC unstable due to possible TSC halt in C2
[  170.104436] Time: acpi_pm clocksource has been installed.
[  174.574522] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  175.768800] hda-intel: Invalid position buffer, using LPIB read method instead.
[  185.998624] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  186.937580] NET: Registered protocol family 17
[  194.104134] NET: Registered protocol family 10
[  194.104280] lo: Disabled Privacy Extensions
[  194.104421] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  199.631240] ath0: no IPv6 routers present
[  201.578859] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  216.230068] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  231.457847] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  314.390206] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  390.916038] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  456.072584] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  540.463800] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  601.330660] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  664.693732] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  732.161718] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  802.288549] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  867.544416] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  929.466408] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  991.303103] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 1061.218354] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 1134.071680] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 1209.155868] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

---

