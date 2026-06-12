---
title: "Very Very slow"
date: 2007-03-04
forum: General Help
---

### Post by violentblur on 2007-03-04
Refer to cleaner post below. I'm  sorry about forum spam, and thank whom ever moved it for me.

---

### Post by violentblur on 2007-03-04
I've just recently installed ubuntu. It's a dual boot system, windows on a SATA and Linux on IDE. That out of the way, I have installed Ubuntu before noticing speed increase rather then such a large decrease. Any help?

Here is a dump from, lshw

```

violentblur@vblur:~$ sudo lshw
Password:
vblur                     
    description: Desktop Computer
    product: A7N8X
    vendor: ASUSTeK Computer INC.
    version: REV 1.xx
    serial: xxxxxxxxxxx
    width: 32 bits
    capabilities: smbios-2.2 dmi-2.2
    configuration: boot=normal chassis=desktop
  *-core
       description: Motherboard
       product: A7N8X
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: REV 1.xx
       serial: xxxxxxxxxxx
       slot: Serial Port 1
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: ASUS A7N8X Deluxe ACPI BIOS Rev 1008 (03/29/2004)
          size: 64KB
          capacity: 448KB
          capabilities: pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot
     *-cpu
          description: CPU
          product: AMD Athlon(tm) XP 2800+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 6.8.1
          slot: Socket A
          size: 2250MHz
          capacity: 3GHz
          width: 32 bits
          clock: 166MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow up ts
        *-cache:0
             description: L1 cache
             physical id: 9
             slot: L1 Cache
             size: 128KB
             capacity: 128KB
             capabilities: pipeline-burst synchronous internal write-back data
        *-cache:1
             description: L2 cache
             physical id: a
             slot: L2 Cache
             size: 256KB
             capacity: 256KB
             capabilities: pipeline-burst synchronous external write-back data
     *-memory
          description: System Memory
          physical id: 21
          slot: System board or motherboard
          size: 1GB
          capacity: 1536MB
        *-bank:0
             description: DIMM DRAM Synchronous
             physical id: 0
             slot: DDR1
             size: 512MB
             width: 64 bits
        *-bank:1
             description: DIMM DRAM Synchronous [empty]
             physical id: 1
             slot: DDR2
             width: 64 bits
        *-bank:2
             description: DIMM DRAM Synchronous
             physical id: 2
             slot: DDR3
             size: 512MB
             width: 64 bits
     *-pci
          description: Host bridge
          product: nForce2 AGP (different version?)
          vendor: nVidia Corporation
          physical id: a0000000
          bus info: pci@00:00.0
          version: a2
          width: 32 bits
          clock: 66MHz
          resources: iomemory:a0000000-bfffffff
        *-memory:0 UNCLAIMED
             description: RAM memory
             product: nForce2 Memory Controller 1
             vendor: nVidia Corporation
             physical id: 0.1
             bus info: pci@00:00.1
             version: a2
             width: 32 bits
             clock: 66MHz (15.1515ns)
        *-memory:1 UNCLAIMED
             description: RAM memory
             product: nForce2 Memory Controller 4
             vendor: nVidia Corporation
             physical id: 0.2
             bus info: pci@00:00.2
             version: a2
             width: 32 bits
             clock: 66MHz (15.1515ns)
        *-memory:2 UNCLAIMED
             description: RAM memory
             product: nForce2 Memory Controller 3
             vendor: nVidia Corporation
             physical id: 0.3
             bus info: pci@00:00.3
             version: a2
             width: 32 bits
             clock: 66MHz (15.1515ns)
        *-memory:3 UNCLAIMED
             description: RAM memory
             product: nForce2 Memory Controller 2
             vendor: nVidia Corporation
             physical id: 0.4
             bus info: pci@00:00.4
             version: a2
             width: 32 bits
             clock: 66MHz (15.1515ns)
        *-memory:4 UNCLAIMED
             description: RAM memory
             product: nForce2 Memory Controller 5
             vendor: nVidia Corporation
             physical id: 0.5
             bus info: pci@00:00.5
             version: a2
             width: 32 bits
             clock: 66MHz (15.1515ns)
        *-isa UNCLAIMED
             description: ISA bridge
             product: nForce2 ISA Bridge
             vendor: nVidia Corporation
             physical id: 1
             bus info: pci@00:01.0
             version: a3
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master cap_list
        *-serial
             description: SMBus
             product: nForce2 SMBus (MCP)
             vendor: nVidia Corporation
             physical id: 1.1
             bus info: pci@00:01.1
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: cap_list
             configuration: driver=nForce2_smbus
             resources: ioport:e000-e01f irq:5
        *-usb:0
             description: USB Controller
             product: nForce2 USB Controller
             vendor: nVidia Corporation
             physical id: 2
             bus info: pci@00:02.0
             version: a3
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master cap_list
             configuration: driver=ohci_hcd
             resources: iomemory:d7087000-d7087fff irq:185
           *-usbhost
                product: OHCI Host Controller
                vendor: Linux 2.6.17-11-generic ohci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=3 speed=12.0MB/s
        *-usb:1
             description: USB Controller
             product: nForce2 USB Controller
             vendor: nVidia Corporation
             physical id: 2.1
             bus info: pci@00:02.1
             version: a3
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master cap_list
             configuration: driver=ohci_hcd
             resources: iomemory:d7082000-d7082fff irq:193
           *-usbhost
                product: OHCI Host Controller
                vendor: Linux 2.6.17-11-generic ohci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=3 speed=12.0MB/s
              *-usb
                   description: Mouse
                   product: USB-PS/2 Optical Mouse
                   vendor: Logitech
                   physical id: 2
                   bus info: usb@2:2
                   version: 21.00
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=98mA speed=1.5MB/s
        *-usb:2
             description: USB Controller
             product: nForce2 USB Controller
             vendor: nVidia Corporation
             physical id: 2.2
             bus info: pci@00:02.2
             version: a3
             width: 32 bits
             clock: 66MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd
             resources: iomemory:d7083000-d70830ff irq:185
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.17-11-generic ehci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=6 speed=480.0MB/s
        *-network
             description: Ethernet interface
             product: nForce2 Ethernet Controller
             vendor: nVidia Corporation
             physical id: 4
             bus info: pci@00:04.0
             logical name: eth0
             version: a1
             serial: 00:e0:18:dd:3c:60
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
             configuration: autonegociation=on broadcast=yes driver=forcedeth driverversion=0.54 duplex=full ip=192.168.1.101 link=yes multicast=yes port=MII speed=100MB/s
             resources: iomemory:d7086000-d7086fff ioport:e400-e407 irq:193
        *-multimedia:0 UNCLAIMED
             description: Multimedia audio controller
             product: nForce Audio Processing Unit
             vendor: nVidia Corporation
             physical id: 5
             bus info: pci@00:05.0
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master cap_list
             resources: iomemory:d7000000-d707ffff irq:5
        *-multimedia:1
             description: Multimedia audio controller
             product: nForce2 AC97 Audio Controler (MCP)
             vendor: nVidia Corporation
             physical id: 6
             bus info: pci@00:06.0
             version: a1
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master cap_list
             configuration: driver=Intel ICH
             resources: ioport:d000-d0ff ioport:d400-d47f iomemory:d7080000-d7080fff irq:185
        *-pci:0
             description: PCI bridge
             product: nForce2 External PCI Bridge
             vendor: nVidia Corporation
             physical id: 8
             bus info: pci@00:08.0
             version: a3
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-storage
                description: RAID bus controller
                product: SiI 3112 [SATALink/SATARaid] Serial ATA Controller
                vendor: Silicon Image, Inc.
                physical id: b
                bus info: pci@01:0b.0
                logical name: scsi1
                logical name: scsi0
                version: 01
                width: 32 bits
                clock: 66MHz
                capabilities: storage bus_master cap_list emulated scsi-host
                configuration: driver=sata_sil
                resources: ioport:a000-a007 ioport:a400-a403 ioport:a800-a807 ioport:ac00-ac03 ioport:b000-b00f iomemory:d6000000-d60001ff irq:177
              *-disk
                   description: SCSI Disk
                   product: WDC WD3200KS-00P
                   vendor: ATA
                   physical id: 0.0.0
                   bus info: scsi@1:0.0.0
                   logical name: /dev/sda
                   version: 21.0
                   serial: WD-WCAPD2210953
                   size: 298GB
                   capabilities: partitioned partitioned:dos
                   configuration: ansiversion=5
                 *-volume
                      description: HPFS/NTFS partition
                      physical id: 1
                      bus info: scsi@1:0.0.0,1
                      logical name: /dev/sda1
                      capacity: 298GB
                      capabilities: primary bootable
        *-ide
             description: IDE interface
             product: nForce2 IDE
             vendor: nVidia Corporation
             physical id: 9
             bus info: pci@00:09.0
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=AMD_IDE
             resources: ioport:f000-f00f
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 66MHz
              *-disk
                   description: ATA Disk
                   product: Maxtor 51369U3
                   vendor: Maxtor
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: DA620CQ0
                   serial: K3HFYBYC
                   size: 12GB
                   capacity: 12GB
                   capabilities: ata dma lba iordy smart pm apm partitioned partitioned:dos
                   configuration: apm=off mode=udma4 smart=on
                 *-volume:0
                      description: Linux filesystem partition
                      physical id: 1
                      bus info: ide@0.0,1
                      logical name: /dev/hda1
                      capacity: 12GB
                      capabilities: primary bootable
                 *-volume:1
                      description: Extended partition
                      physical id: 2
                      bus info: ide@0.0,2
                      logical name: /dev/hda2
                      capacity: 564MB
                      capabilities: extended partitioned partitioned:extended
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 66MHz
              *-cdrom
                   description: DVD-RAM writer
                   product: HL-DT-ST DVDRAM GSA-4163B
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: AN16
                   serial: K0153GN1827
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy pm audio cd-r cd-rw dvd dvd-r dvd-ram
                   configuration: mode=udma2
                 *-disc
                      physical id: 0
                      logical name: /dev/hdc
        *-pci:1
             description: PCI bridge
             product: nForce2 PCI Bridge
             vendor: nVidia Corporation
             physical id: c
             bus info: pci@00:0c.0
             version: a3
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-network
                description: Ethernet interface
                product: 3C920B-EMB Integrated Fast Ethernet Controller [Tornado]
                vendor: 3Com Corporation
                physical id: 1
                bus info: pci@02:01.0
                logical name: eth1
                version: 40
                serial: 00:26:54:07:fa:9f
                size: 10MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
                configuration: autonegociation=on broadcast=yes driver=3c59x duplex=half link=no multicast=yes port=MII speed=10MB/s
                resources: ioport:c000-c07f iomemory:d1000000-d100007f irq:201
        *-firewire
             description: FireWire (IEEE 1394)
             product: nForce2 FireWire (IEEE 1394) Controller
             vendor: nVidia Corporation
             physical id: d
             bus info: pci@00:0d.0
             version: a3
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master cap_list
             configuration: driver=ohci1394
             resources: iomemory:d7084000-d70847ff iomemory:d7085000-d708503f irq:201
        *-pci:2
             description: PCI bridge
             product: nForce2 AGP
             vendor: nVidia Corporation
             physical id: 1e
             bus info: pci@00:1e.0
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display
                description: VGA compatible controller
                product: NV40 [GeForce 6800 GT]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@03:00.0
                version: a1
                size: 256MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                resources: iomemory:d2000000-d2ffffff iomemory:c0000000-cfffffff iomemory:d3000000-d3ffffff irq:5


```

And ...

```

violentblur@vblur:~$ sudo lshw -C disk
  *-disk                  
       description: SCSI Disk
       product: WDC WD3200KS-00P
       vendor: ATA
       physical id: 0.0.0
       bus info: scsi@1:0.0.0
       logical name: /dev/sda
       version: 21.0
       serial: WD-WCAPD2210953
       size: 298GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5
     *-volume
          description: HPFS/NTFS partition
          physical id: 1
          bus info: scsi@1:0.0.0,1
          logical name: /dev/sda1
          capacity: 298GB
          capabilities: primary bootable
  *-disk
       description: ATA Disk
       product: Maxtor 51369U3
       vendor: Maxtor
       physical id: 0
       bus info: ide@0.0
       logical name: /dev/hda
       version: DA620CQ0
       serial: K3HFYBYC
       size: 12GB
       capacity: 12GB
       capabilities: ata dma lba iordy smart pm apm partitioned partitioned:dos
       configuration: apm=off mode=udma4 smart=on
     *-volume:0
          description: Linux filesystem partition
          physical id: 1
          bus info: ide@0.0,1
          logical name: /dev/hda1
          capacity: 12GB
          capabilities: primary bootable
     *-volume:1
          description: Extended partition
          physical id: 2
          bus info: ide@0.0,2
          logical name: /dev/hda2
          capacity: 564MB
          capabilities: extended partitioned partitioned:extended
  *-cdrom
       description: DVD-RAM writer
       product: HL-DT-ST DVDRAM GSA-4163B
       physical id: 0
       bus info: ide@1.0
       logical name: /dev/hdc
       version: AN16
       serial: K0153GN1827
       capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy pm audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: mode=udma2
     *-disc
          physical id: 0
          logical name: /dev/hdc

```

HELP! I want my ubuntu back to the way it was :o(

---

### Post by violentblur on 2007-03-04
Shameless bump.

---

