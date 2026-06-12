---
title: "Green dots on screen 12.04 (not hardware)"
date: 2013-04-07
forum: General Help
---

### Post by Dilleyboy on 2013-04-07
I tried searching for a similar issue, but couldn't find anything for my exact problem.  I am running Ubuntu 12.04 32-bit, and I have a series of green vertical dots across my screen.  I see the dots even when I VNC into the system, and in screenshots, so I know it's not hardware.  Does anyone have any ideas?

Graphics: 
Driver VESA: MACH64GM
Experience Standard

---

### Post by mörgæs on 2013-04-08
I only see a black screen shot. 

Please run ```
sudo lshw > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by Dilleyboy on 2013-04-08
I have also attached a screen shot from the VNC connection on my phone.  
```

dbc-computers
    description: Desktop Computer
    product: System Product Name (To Be Filled By O.E.M.)
    vendor: System manufacturer
    version: System Version
    serial: System Serial Number
    width: 32 bits
    capabilities: smbios-2.5 dmi-2.5 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=4 family=To Be Filled By O.E.M. sku=To Be Filled By O.E.M. uuid=00FD001E-8C00-0045-BF30-F46D049936F7
  *-core
       description: Motherboard
       product: M4A79XTD EVO
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: Rev X.0X
       serial: MT7013K54900964
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 2102
          date: 06/17/2010
          size: 64KiB
          capacity: 960KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: AMD Phenom(tm) II X4 965 Processor
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 4
          bus info: cpu@0
          version: 15.4.3
          serial: To Be Filled By O.E.M.
          slot: AM3
          size: 800MHz
          capacity: 3400MHz
          width: 64 bits
          clock: 200MHz
          capabilities: x86-64 boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp 3dnowext 3dnow constant_tsc nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt npt lbrv svm_lock nrip_save cpufreq
          configuration: cores=4 enabledcores=4
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 128KiB
             capacity: 512KiB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 512KiB
             capacity: 2MiB
             capabilities: pipeline-burst internal varies unified
        *-cache:2
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             size: 6MiB
             capacity: 6MiB
             capabilities: pipeline-burst internal varies unified
     *-memory
          description: System Memory
          physical id: 36
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM Synchronous 1333 MHz (0.8 ns)
             product: ModulePartNumber00
             vendor: Manufacturer00
             physical id: 0
             serial: SerNum00
             slot: DIMM0
             size: 1GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:1
             description: DIMM Synchronous 1333 MHz (0.8 ns)
             product: ModulePartNumber01
             vendor: Manufacturer01
             physical id: 1
             serial: SerNum01
             slot: DIMM1
             size: 1GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:2
             description: DIMM Synchronous 1333 MHz (0.8 ns)
             product: ModulePartNumber02
             vendor: Manufacturer02
             physical id: 2
             serial: SerNum02
             slot: DIMM2
             size: 1GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:3
             description: DIMM Synchronous 1333 MHz (0.8 ns)
             product: ModulePartNumber03
             vendor: Manufacturer03
             physical id: 3
             serial: SerNum03
             slot: DIMM3
             size: 1GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 15.4.3
          size: 800MHz
          capacity: 800MHz
          capabilities: cpufreq
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-cpu:2
          physical id: 2
          bus info: cpu@2
          version: 15.4.3
          size: 800MHz
          capacity: 800MHz
          capabilities: cpufreq
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-cpu:3
          physical id: 3
          bus info: cpu@3
          version: 15.4.3
          size: 3400MHz
          capacity: 3400MHz
          capabilities: cpufreq
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-pci:0
          description: Host bridge
          product: RD780 Northbridge only dual slot PCI-e_GFX and HT1 K8 part
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
        *-pci:0
             description: PCI bridge
             product: RD790 PCI to PCI bridge (PCI express gpp port C)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:b000(size=4096) memory:fac00000-facfffff ioport:f9f00000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: eth0
                version: 03
                serial: f4:6d:04:99:36:f7
                size: 1Gbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168d-2.fw ip=192.168.111.20 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
                resources: irq:44 ioport:b800(size=256) memory:f9fff000-f9ffffff memory:f9ff8000-f9ffbfff memory:facf0000-facfffff
        *-pci:1
             description: PCI bridge
             product: RD790 PCI to PCI bridge (PCI express gpp port D)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:c000(size=4096) memory:fad00000-fadfffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: VT6315 Series Firewire Controller
                vendor: VIA Technologies, Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=0
                resources: irq:19 memory:fadff800-fadfffff ioport:c800(size=256)
        *-pci:2
             description: PCI bridge
             product: RD790 PCI to PCI bridge (PCI express gpp port E)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 9
             bus info: pci@0000:00:09.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:d000(size=4096) memory:fae00000-faefffff
           *-ide
                description: IDE interface
                product: 88SE6121 SATA II Controller
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                version: b2
                width: 32 bits
                clock: 33MHz
                capabilities: ide pm msi pciexpress bus_master cap_list
                configuration: driver=pata_marvell latency=0
                resources: irq:17 ioport:dc00(size=8) ioport:d880(size=4) ioport:d800(size=8) ioport:d480(size=4) ioport:d400(size=16) memory:faeffc00-faefffff
        *-storage
             description: RAID bus controller
             product: SB7x0/SB8x0/SB9x0 SATA Controller [RAID5 mode]
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 11
             bus info: pci@0000:00:11.0
             logical name: scsi0
             logical name: scsi2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi bus_master cap_list emulated
             configuration: driver=ahci latency=64
             resources: irq:43 ioport:a000(size=8) ioport:9000(size=4) ioport:8000(size=8) ioport:7000(size=4) ioport:6000(size=16) memory:fabffc00-fabfffff
           *-disk:0
                description: ATA Disk
                product: WDC WD5003ABYX-0
                vendor: Western Digital
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 01.0
                serial: WD-WMAYP0899693
                size: 465GiB (500GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000b771a
              *-volume:0 UNCLAIMED
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   version: 1.0
                   serial: 69d1357c-3a6a-48b7-a2a0-807ef58c501f
                   size: 461GiB
                   capacity: 461GiB
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2012-05-28 12:27:36 filesystem=ext4 lastmountpoint=/ modified=2012-05-28 12:54:03 mounted=2013-04-07 15:53:17 state=clean
              *-volume:1 UNCLAIMED
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   size: 4087MiB
                   capacity: 4087MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume UNCLAIMED
                      description: Linux swap / Solaris partition
                      physical id: 5
                      capacity: 4087MiB
                      capabilities: nofs
           *-disk:1
                description: ATA Disk
                product: WDC WD5003ABYX-0
                vendor: Western Digital
                physical id: 1
                bus info: scsi@2:0.0.0
                logical name: /dev/sdb
                version: 01.0
                serial: WD-WMAYP0890723
                size: 465GiB (500GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000b771a
              *-volume:0 UNCLAIMED
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   version: 1.0
                   serial: 69d1357c-3a6a-48b7-a2a0-807ef58c501f
                   size: 461GiB
                   capacity: 461GiB
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2012-05-28 12:27:36 filesystem=ext4 lastmountpoint=/ modified=2012-05-28 12:54:03 mounted=2013-04-07 15:53:17 state=clean
              *-volume:1 UNCLAIMED
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   size: 4087MiB
                   capacity: 4087MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume UNCLAIMED
                      description: Linux swap / Solaris partition
                      physical id: 5
                      capacity: 4087MiB
                      capabilities: nofs
        *-usb:0
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:16 memory:fabfd000-fabfdfff
        *-usb:1
             description: USB controller
             product: SB7x0 USB OHCI1 Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 12.1
             bus info: pci@0000:00:12.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:16 memory:fabfe000-fabfefff
        *-usb:2
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:17 memory:fabff800-fabff8ff
        *-usb:3
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:fabf7000-fabf7fff
        *-usb:4
             description: USB controller
             product: SB7x0 USB OHCI1 Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:fabfc000-fabfcfff
        *-usb:5
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:19 memory:fabff400-fabff4ff
        *-serial UNCLAIMED
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 3c
             width: 32 bits
             clock: 66MHz
             capabilities: ht cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: SB7x0/SB8x0/SB9x0 IDE Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14.1
             bus info: pci@0000:00:14.1
             logical name: scsi7
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide msi bus_master cap_list emulated
             configuration: driver=pata_atiixp latency=64
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ff00(size=16)
           *-cdrom
                description: SCSI CD-ROM
                physical id: 0.0.0
                bus info: scsi@7:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/sr0
                logical name: /media/V101FBXEDGEUSERG
                capabilities: audio
                configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime,uid=1001,gid=1001,iocharset=utf8,mode=0400,dmode=0500 state=mounted status=ready
        *-multimedia
             description: Audio device
             product: SBx00 Azalia (Intel HDA)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_hda_intel latency=64
             resources: irq:16 memory:fabf0000-fabf3fff
        *-isa
             description: ISA bridge
             product: SB7x0/SB8x0/SB9x0 LPC host controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:3
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
             resources: ioport:e000(size=4096) memory:faf00000-fbffffff
           *-display UNCLAIMED
                description: VGA compatible controller
                product: Rage XL AGP 2X
                vendor: Hynix Semiconductor (Hyundai Electronics)
                physical id: 5
                bus info: pci@0000:04:05.0
                version: 65
                width: 32 bits
                clock: 33MHz
                capabilities: pm vga_controller bus_master cap_list
                configuration: latency=64 mingnt=8
                resources: memory:fb000000-fbffffff ioport:e000(size=256) memory:fafff000-faffffff memory:fafc0000-fafdffff
        *-usb:6
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:fabf6000-fabf6fff
     *-pci:1
          description: Host bridge
          product: Family 10h Processor HyperTransport Configuration
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Family 10h Processor Address Map
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Family 10h Processor DRAM Controller
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Family 10h Processor Miscellaneous Control
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k10temp
          resources: irq:0
     *-pci:5
          description: Host bridge
          product: Family 10h Processor Link Control
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz

```

---

### Post by Dilleyboy on 2013-04-08
I just viewed both attachments on my Windows system, and you're right the dots do not appear.  If you actually zoom in on the image, you can see grey dots though.  I don't know if they are being lost over the web or what, but I know they're there in both VNC and hardware.

---

### Post by Dilleyboy on 2013-04-08
The forum is converting my png to a jpg which is where the loss occurs.  Here is the original image
[http://i.imgur.com/S4Agove.png](http://i.imgur.com/S4Agove.png)

---

### Post by mörgæs on 2013-04-08
Moving to General Help. Let's see if anyone there has a suggestion.

---

### Post by ppjdee on 2013-04-09
That is a very old gfx card. I don't know if there is anything you can do besides upgrade your gfx card, or down grade to a older Ubuntu release.
Please someone correct me if I'm mistaken.

---

### Post by mörgæs on 2013-04-09
No, you're correct. The card is too weak (how could I miss that?) 

Don't install old releases, but Lubuntu 12.10 is a good option.

---

### Post by Dilleyboy on 2013-04-09
Does the graphics card explain the green dots over VNC as well?

---

### Post by mörgæs on 2013-04-10
I don't know, but it's easy to find out :-) Try Lubuntu 12.10 with only open-source drivers.

Googling seems to indicate that these dots have been around for some time and that there might be more than one reason. I guess some more experimenting is needed.

---

