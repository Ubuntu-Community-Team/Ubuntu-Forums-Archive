---
title: "Can't mount hard drive: Fdisk showing unknown devices"
date: 2008-07-07
forum: General Help
---

### Post by Yangshuo Joe on 2008-07-07
I'm relatively new at Ubuntu and Linux.

I have been trying to use a Western Digital external hard drive (FAT32), and also a Newman mp3 player (bought in China). Each device has shown up once in Computer, but generally they don't display. When they do show up and I click it, it says Unable to Mount.

I've read some information about this already, but generally, it recommends to run fdisk and then see what displays as the device path (usually /dev/sda1). However, when I run #fdisk -l, I get the following:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa26fa26f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9541    76638051   83  Linux
/dev/sda2            9542        9729     1510110    5  Extended
/dev/sda5            9542        9729     1510078+  82  Linux swap / Solaris

This shows up no matter whether I have one of the external devices in or not. It seems to be the default on my computer, and I don't have any other USB devices plugged in at all.

My main question is to understand what these 3 mean, and why is there no change when I put in another device. 

I'm on Heron and upgraded from Edgy if that helps.

I hope this is enough information to get me started.

Appreciate any help!

---

### Post by Yangshuo Joe on 2008-07-11
Anyone?

Basically, I can't get it to recognize an external USB hard drive at all - though it recognizes flash memory drives just fine.

I read some more about it and ran a dmesg. However, the output from dmesg doesn't change and all when I plug the HD into the USB drive, although a light turn on on the drive itself. The output changes as expected when I plug in a flash drive.

I included the last part of the dmesg output, what I though might be significant. It says something about Driver sd needs updating, so I'm wondering if that is related:

[   39.606446] Driver 'sd' needs updating - please use bus_type methods
[   39.607150] sd 2:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   39.607170] sd 2:0:0:0: [sda] Write Protect is off
[   39.607174] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   39.607199] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   39.607283] sd 2:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   39.607297] sd 2:0:0:0: [sda] Write Protect is off
[   39.607300] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   39.607491] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   39.607498]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   39.621158]  sda1 sda2 < sda5 >
[   39.644115] sd 2:0:0:0: [sda] Attached SCSI disk
[   39.650860] sd 2:0:0:0: Attached scsi generic sg0 type 0
[   39.650889] sr 3:0:0:0: Attached scsi generic sg1 type 5
[   39.659161] sr0: scsi3-mmc drive: 52x/52x cd/rw xa/form2 cdda tray
[   39.659169] Uniform CD-ROM driver Revision: 3.20
[   39.659243] sr 3:0:0:0: Attached scsi CD-ROM sr0
[   40.074745] kjournald starting.  Commit interval 5 seconds
[   40.074768] EXT3-fs: mounted filesystem with ordered data mode.
[   49.782970] Linux agpgart interface v0.102
[   49.838243] agpgart: Detected VIA PT880 chipset
[   49.979026] agpgart: AGP aperture is 64M @ 0xf8000000
[   50.006908] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   50.078245] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   51.305898] input: Power Button (FF) as /devices/virtual/input/input2
[   51.314679] ACPI: Power Button (FF) [PWRF]
[   51.315043] input: Power Button (CM) as /devices/virtual/input/input3
[   51.330610] ACPI: Power Button (CM) [PWRB]
[   52.459556] Real Time Clock Driver v1.12ac
[   52.465087] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   54.596289] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   56.293956] parport_pc 00:06: reported by Plug and Play ACPI
[   56.294196] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   56.587550] ACPI: PCI Interrupt 0000:00:11.5[C] -> GSI 22 (level, low) -> IRQ 19
[   56.587772] PCI: Setting latency timer of device 0000:00:11.5 to 64
[   56.640400] NET: Registered protocol family 17
[   57.136553] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input5
[   60.981595] lp0: using parport0 (interrupt-driven).
[   61.237397] Adding 1510068k swap on /dev/sda5.  Priority:-1 extents:1 across:1510068k
[   61.902419] EXT3 FS on sda1, internal journal
[   62.372153] NET: Registered protocol family 10
[   62.372722] lo: Disabled Privacy Extensions
[   63.729278] ip_tables: (C) 2000-2006 Netfilter Core Team
[   69.573032] No dock devices found.
[   72.796159] eth0: no IPv6 routers present
[   73.504899] apm: BIOS not found.


Thanks for any help!

---

### Post by Yangshuo Joe on 2008-07-11
One more update.

It seems now dmesg is showing that the device was plugged in. It recognizes it as a SAMSUNG, so something must be right. But it still won't display it on file browser.

Here is the dmesg output:

[  534.515818] usb 5-8: new high speed USB device using ehci_hcd and address 2
[  534.649896] usb 5-8: configuration #1 chosen from 1 choice
[  534.731821] usbcore: registered new interface driver libusual
[  534.782791] Initializing USB Mass Storage driver...
[  534.794638] scsi4 : SCSI emulation for USB Mass Storage devices
[  534.799529] usbcore: registered new interface driver usb-storage
[  534.799540] USB Mass Storage support registered.
[  534.802921] usb-storage: device found at 2
[  534.802928] usb-storage: waiting for device to settle before scanning
[  539.799444] usb-storage: device scan complete
[  539.800365] scsi 4:0:0:0: Direct-Access     SAMSUNG  HM160HC          LQ10 PQ: 0 ANSI: 0
[  539.802667] sd 4:0:0:0: [sdb] 312581808 512-byte hardware sectors (160042 MB)
[  539.807841] sd 4:0:0:0: [sdb] Write Protect is off
[  539.807847] sd 4:0:0:0: [sdb] Mode Sense: 03 00 00 00
[  539.807850] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  539.809038] sd 4:0:0:0: [sdb] 312581808 512-byte hardware sectors (160042 MB)
[  539.809922] sd 4:0:0:0: [sdb] Write Protect is off
[  539.809927] sd 4:0:0:0: [sdb] Mode Sense: 03 00 00 00
[  539.809930] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  539.809938]  sdb:<6>usb 5-8: reset high speed USB device using ehci_hcd and address 2
[  600.156376] usb 5-8: reset high speed USB device using ehci_hcd and address 2
[  630.396968] usb 5-8: reset high speed USB device using ehci_hcd and address 2
[  660.637548] usb 5-8: reset high speed USB device using ehci_hcd and address 2
[  690.878088] usb 5-8: reset high speed USB device using ehci_hcd and address 2
[  721.118660] usb 5-8: reset high speed USB device using ehci_hcd and address 2
[  721.251812] sd 4:0:0:0: [sdb] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK,SUGGEST_OK
[  721.251822] end_request: I/O error, dev sdb, sector 0
[  721.251827] Buffer I/O error on device sdb, logical block 0
[  751.359230] usb 5-8: reset high speed USB device using ehci_hcd and address 2
[  781.599796] usb 5-8: reset high speed USB device using ehci_hcd and address 2
[  811.840388] usb 5-8: reset high speed USB device using ehci_hcd and address 2
[  842.080941] usb 5-8: reset high speed USB device using ehci_hcd and address 2
[  872.321514] usb 5-8: reset high speed USB device using ehci_hcd and address 2
[  902.562108] usb 5-8: reset high speed USB device using ehci_hcd and address 2
[  902.695220] sd 4:0:0:0: [sdb] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK,SUGGEST_OK
[  902.695231] end_request: I/O error, dev sdb, sector 0
[  902.695236] Buffer I/O error on device sdb, logical block 0
[  932.802643] usb 5-8: reset high speed USB device using ehci_hcd and address 2
[  963.043242] usb 5-8: reset high speed USB device using ehci_hcd and address 2
[  993.283796] usb 5-8: reset high speed USB device using ehci_hcd and address 2

----------------------

fdisk is still showing the same output as the first post:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa26fa26f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9541    76638051   83  Linux
/dev/sda2            9542        9729     1510110    5  Extended
/dev/sda5            9542        9729     1510078+  82  Linux swap / Solaris

---

### Post by hal8000 on 2008-07-11
fdisk -l will list all partitions on all hard drives. Your system is only showing sda1,2, and 5, which will be your fixed internal drive.

In your case you have created a single / partition, no /home partition and a /swap partition as a logical drive. Thers nothing wrong with this except that if your / became corrupted you would lose all your file in home this is why its advisable to create a /home partition.

To your problem, its possible that hal (hardware abstraction layer) is not running, you have a lose or flaky usb socket or some file system that Ubuntu
doesnt recognise.

Boot your system normally, then plug in your external usb drive.
Post the output of dmesg

At the very least the kernel messages should reveal some useful output.

---

### Post by Yangshuo Joe on 2008-07-15
When I do that, I just get an error loop as above:

...

[ 539.809938] sdb:<6>usb 5-8: reset high speed USB device using ehci_hcd and address 2
[ 600.156376] usb 5-8: reset high speed USB device using ehci_hcd and address 2
[ 630.396968] usb 5-8: reset high speed USB device using ehci_hcd and address 2
[ 660.637548] usb 5-8: reset high speed USB device using ehci_hcd and address 2
[ 690.878088] usb 5-8: reset high speed USB device using ehci_hcd and address 2
[ 721.118660] usb 5-8: reset high speed USB device using ehci_hcd and address 2
[ 721.251812] sd 4:0:0:0: [sdb] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK,SUGGEST_OK
[ 721.251822] end_request: I/O error, dev sdb, sector 0
[ 721.251827] Buffer I/O error on device sdb, logical block 0
[ 751.359230] usb 5-8: reset high speed USB device using ehci_hcd and address 2
[ 781.599796] usb 5-8: reset high speed USB device using ehci_hcd and address 2
[ 811.840388] usb 5-8: reset high speed USB device using ehci_hcd and address 2
[ 842.080941] usb 5-8: reset high speed USB device using ehci_hcd and address 2
[ 872.321514] usb 5-8: reset high speed USB device using ehci_hcd and address 2
[ 902.562108] usb 5-8: reset high speed USB device using ehci_hcd and address 2
[ 902.695220] sd 4:0:0:0: [sdb] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK,SUGGEST_OK
[ 902.695231] end_request: I/O error, dev sdb, sector 0
[ 902.695236] Buffer I/O error on device sdb, logical block 0
[ 932.802643] usb 5-8: reset high speed USB device using ehci_hcd and address 2

It will continue doing this the entire time the device is plugged in

---

### Post by VMC on 2008-07-15
What does the output of 'lshw' reveal? Does your usb devices look normal? Does any usb device work on this machine?

---

### Post by Yangshuo Joe on 2008-07-18
USB flash drives work with no problem. The drives seem to look normal. Output of lshw:

    description: Computer
    product: P4V88+
    version: 1.00
    serial: 00000000
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: uuid=00020003-0004-0005-0006-000700080009
  *-core
       description: Motherboard
       product: P4V88+
       physical id: 0
       version: 1.00
       serial: 00000000
       slot: TBD
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: P1.60 (12/01/2005)
          size: 64KiB
          capacity: 192KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Celeron(R) CPU 2.66GHz
          vendor: Intel Corp.
          physical id: 3
          bus info: cpu@0
          version: 15.4.1
          serial: 0000-0F41-0000-0000-0000-0000
          slot: CPUSocket
          size: 2660MHz
          capacity: 2660MHz
          width: 32 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc pebs bts sync_rdtsc pni monitor ds_cpl cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 4
             slot: L1-Cache
             size: 16KiB
             capacity: 16KiB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 5
             slot: L2-Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: pipeline-burst internal varies unified
     *-memory
          description: System memory
          physical id: 1
          size: 511MiB
     *-pci:0
          description: Host bridge
          product: PT880 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: driver=agpgart-via latency=8 module=via_agp
        *-pci
             description: PCI bridge
             product: VT8237 PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci pm normal_decode bus_master cap_list
           *-display UNCLAIMED
                description: VGA compatible controller
                product: NV34 [GeForce FX 5200]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 vga_controller bus_master cap_list
                configuration: latency=32 maxlatency=1 mingnt=5
        *-storage
             description: RAID bus controller
             product: VIA VT6420 SATA RAID Controller
             vendor: VIA Technologies, Inc.
             physical id: f
             bus info: pci@0000:00:0f.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: storage pm bus_master cap_list
             configuration: driver=sata_via latency=32 module=sata_via
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: f.1
             bus info: pci@0000:00:0f.1
             logical name: scsi0
             logical name: scsi1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_via latency=32 module=pata_via
           *-disk
                description: ATA Disk
                product: WDC WD800BB-00JH
                vendor: Western Digital
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 05.0
                serial: WD-WCAM9E939501
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=a26fa26f
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: 0e755c2c-6533-4fc4-b967-dbb9a1522abf
                   size: 73GiB
                   capacity: 73GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: filesystem=ext3 modified=2008-07-18 20:11:37 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2008-07-18 16:59:14 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 1474MiB
                   capacity: 1474MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1474MiB
                      capabilities: nofs
           *-cdrom
                description: SCSI CD-ROM
                product: CD-ROM GCR-8523B
                vendor: HL-DT-ST
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.03
                capabilities: removable audio
                configuration: ansiversion=5 status=open
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.2
             bus info: pci@0000:00:10.2
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.3
             bus info: pci@0000:00:10.3
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 10.4
             bus info: pci@0000:00:10.4
             version: 86
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=32 module=ehci_hcd
        *-isa
             description: ISA bridge
             product: VT8237 ISA bridge [KT600/K8T800/K8T890 South]
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa pm bus_master cap_list
             configuration: latency=0
        *-multimedia
             description: Multimedia audio controller
             product: VT8233/A/8235/8237 AC97 Audio Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.5
             bus info: pci@0000:00:11.5
             version: 60
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: driver=VIA 82xx Audio latency=0 module=snd_via82xx
        *-network
             description: Ethernet interface
             product: VT6102 [Rhine-II]
             vendor: VIA Technologies, Inc.
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: eth0
             version: 78
             serial: 00:13:8f:7a:4a:53
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full ip=192.168.1.100 latency=32 link=yes maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=100MB/s
     *-pci:1
          description: Host bridge
          product: PT880 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 101
          bus info: pci@0000:00:00.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: PT880 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 102
          bus info: pci@0000:00:00.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: PT880 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 103
          bus info: pci@0000:00:00.3
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: PT880 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 104
          bus info: pci@0000:00:00.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: PT880 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 105
          bus info: pci@0000:00:00.7
          version: 00
          width: 32 bits
          clock: 33MHz

---

