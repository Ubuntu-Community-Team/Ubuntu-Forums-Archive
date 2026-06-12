---
title: "When I log out, it stays on a black screen for hours..."
date: 2007-09-17
forum: General Help
---

### Post by acelin on 2007-09-17
It always goes to black- it even pays my custom logout sound...

Ever since i installed it it has always done this... anyway I can figure out why it goes to a black screen when switching users and logging out?

---

### Post by dcstar on 2007-09-18
> **acelin said:**
> It always goes to black- it even pays my custom logout sound...

Ever since i installed it it has always done this... anyway I can figure out why it goes to a black screen when switching users and logging out?

Possibly a video driver issue - do a forum search for your particular hardware and see if there are any solutions.

Find what you have with the following commands:
```
lshw
lspci
```

---

### Post by acelin on 2007-09-18
description: Notebook
    vendor: Acer
    version: V2.84
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4
    configuration: boot=normal chassis=notebook uuid=FFFFFFFF-FFFF-FFFF-FFFF-0016D4D4871F
  *-core
       description: Motherboard
       product: Navarro
       vendor: Acer
       physical id: 0
       version: N/A
     *-firmware
          description: BIOS
          vendor: Acer
          physical id: 0
          version: V2.84 (04/30/2007)
          size: 109KB
          capacity: 960KB
          capabilities: pci pcmcia pnp upgrade shadowing escd cdboot bootselect int5printscreen int9keyboard int17printer int10video acpi usb agp smartbattery biosbootspecification
     *-cpu
          description: CPU
          product: AMD Turion(tm) 64 X2 Mobile Technology TL-50
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 15.8.2
          slot: Socket M2/S1G1
          size: 1600MHz
          capacity: 1600MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm cr8legacy ts fid vid ttp tm stc cpufreq
        *-cache:0
             description: L2 cache
             physical id: 5
             slot: L2 Cache
             size: 512KB
             capacity: 1MB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L1 cache
             physical id: 0
             size: 128KB
        *-cache:2
             description: L2 cache
             physical id: 1
             size: 256KB
     *-memory
          description: System Memory
          physical id: a
          slot: System board or motherboard
          size: 1GB
        *-bank:0
             description: DIMM Synchronous
             physical id: 0
             slot: S1
             size: 512MB
             width: 64 bits
        *-bank:1
             description: DIMM Synchronous
             physical id: 1
             slot: S2
             size: 512MB
             width: 64 bits
     *-pci:0
          description: Host bridge
          product: RS480 Host Bridge
          vendor: ATI Technologies Inc
          physical id: 100
          bus info: pci@00:00.0
          version: 10
          width: 32 bits
          clock: 66MHz
          configuration: latency=64
        *-pci:0
             description: PCI bridge
             product: RS480 PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 1
             bus info: pci@00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master cap_list
           *-display
                description: VGA compatible controller
                product: RS482 [Radeon Xpress 200M]
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@01:05.0
                version: 00
                size: 256MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                configuration: driver=fglrx_pci latency=255 mingnt=8
                resources: iomemory:c0000000-cfffffff ioport:9000-90ff iomemory:b0100000-b010ffff irq:22
        *-pci:1
             description: PCI bridge
             product: RS480 PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 4
             bus info: pci@00:04.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:2
             description: PCI bridge
             product: ATI Technologies Inc
             vendor: ATI Technologies Inc
             physical id: 5
             bus info: pci@00:05.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-usb:0
             description: USB Controller
             product: IXP SB400 USB Host Controller
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@00:13.0
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: iomemory:b0005000-b0005fff irq:19
           *-usbhost
                product: OHCI Host Controller
                vendor: Linux 2.6.20-16-generic ohci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=4 speed=12.0MB/s
        *-usb:1
             description: USB Controller
             product: IXP SB400 USB Host Controller
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@00:13.1
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: iomemory:b0006000-b0006fff irq:19
           *-usbhost
                product: OHCI Host Controller
                vendor: Linux 2.6.20-16-generic ohci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=4 speed=12.0MB/s
        *-usb:2
             description: USB Controller
             product: IXP SB400 USB2 Host Controller
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@00:13.2
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: iomemory:b0007000-b0007fff irq:19
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.20-16-generic ehci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=8 speed=480.0MB/s
              *-usb:0
                   description: Mass storage device
                   product: External HDD
                   vendor: Western Digital
                   physical id: 1
                   bus info: usb@1:1
                   logical name: scsi0
                   version: 1.08
                   serial: 57442D5743414D5234353839313836
                   capabilities: usb-2.00 scsi emulated scsi-host
                   configuration: driver=usb-storage maxpower=100mA speed=480.0MB/s
                 *-disk
                      description: SCSI Disk
                      product: 3200SB External
                      vendor: WD
                      physical id: 0.0.0
                      bus info: scsi@0:0.0.0
                      logical name: /dev/sda
                      version: 0108
                      size: 298GB
                      capabilities: partitioned partitioned:dos
                    *-volume:0
                         description: HPFS/NTFS partition
                         physical id: 1
                         bus info: scsi@0:0.0.0,1
                         logical name: /dev/sda1
                         capacity: 240GB
                         capabilities: primary
                    *-volume:1
                         description: Linux filesystem partition
                         physical id: 2
                         bus info: scsi@0:0.0.0,2
                         logical name: /dev/sda2
                         capacity: 57GB
                         capabilities: primary
                    *-volume:2
                         description: Linux swap / Solaris partition
                         physical id: 3
                         bus info: scsi@0:0.0.0,3
                         logical name: /dev/sda3
                         capacity: 1027MB
                         capabilities: primary nofs
              *-usb:1 UNCLAIMED
                   description: Generic USB device
                   product: USB2.0 Camera
                   physical id: 4
                   bus info: usb@1:4
                   version: 1.00
                   capabilities: usb-2.00
                   configuration: maxpower=500mA speed=480.0MB/s
        *-serial
             description: SMBus
             product: IXP SB400 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@00:14.0
             version: 83
             width: 32 bits
             clock: 66MHz
             capabilities: cap_list
             configuration: driver=piix4_smbus latency=0
             resources: ioport:8410-841f iomemory:54000000-540003ff
        *-ide
             description: IDE interface
             product: Standard Dual Channel PCI IDE Controller ATI
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@00:14.1
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ATIIXP_IDE latency=0
             resources: ioport:1f0-1f7 ioport:3f4-3f3 ioport:170-177 ioport:374-373 ioport:8420-842f irq:17
           *-ide
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 66MHz
              *-disk
                   description: ATA Disk
                   product: HTS541010G9AT00
                   vendor: Hitachi
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: MBZOA60A
                   serial: MP20XAX0K61W1S
                   size: 93GB
                   capacity: 93GB
                   capabilities: ata dma lba iordy smart security pm apm partitioned partitioned:dos
                   configuration: apm=off mode=udma5 smart=on
                 *-volume:0
                      description: Compaq diagnostics partition
                      physical id: 1
                      bus info: ide@0.0,1
                      logical name: /dev/hda1
                      capacity: 4996MB
                      capabilities: primary boot
                 *-volume:1
                      description: HPFS/NTFS partition
                      physical id: 2
                      bus info: ide@0.0,2
                      logical name: /dev/hda2
                      capacity: 47GB
                      capabilities: primary bootable
                 *-volume:2
                      description: HPFS/NTFS partition
                      physical id: 3
                      bus info: ide@0.0,3
                      logical name: /dev/hda3
                      capacity: 41GB
                      capabilities: primary
              *-cdrom
                   description: DVD-RAM writer
                   product: HL-DT-ST DVDRAM GSA-T20N
                   physical id: 1
                   bus info: ide@0.1
                   logical name: /dev/hdb
                   version: WP03
                   serial: KY174341258
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy pm audio cd-r cd-rw dvd dvd-r dvd-ram
                   configuration: mode=udma2
                 *-disc
                      physical id: 0
                      logical name: /dev/hdb
        *-multimedia
             description: Audio device
             product: SB450 HDA Audio
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@00:14.2
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=64
             resources: iomemory:b0000000-b0003fff irq:17
        *-isa
             description: ISA bridge
             product: IXP SB400 PCI-ISA Bridge
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@00:14.3
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:3
             description: PCI bridge
             product: IXP SB400 PCI-PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@00:14.4
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
           *-network:0
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 1
                bus info: pci@06:01.0
                logical name: eth0
                version: 10
                serial: 00:16:d4:d4:87:1f
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=129.237.95.122 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
                resources: ioport:a000-a0ff iomemory:b0210000-b02100ff irq:18
           *-network:1
                description: Wireless interface
                product: AR5005G 802.11abg NIC
                vendor: Atheros Communications, Inc.
                physical id: 2
                bus info: pci@06:02.0
                logical name: wifi0
                version: 01
                serial: 00:16:cf:49:e1:09
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=ath_pci driverversion=0.9.4.5 (0.9.3.1) latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11g
                resources: iomemory:b0200000-b020ffff irq:20
           *-pcmcia
                description: CardBus bridge
                product: CB-712/4 Cardbus Controller
                vendor: ENE Technology Inc
                physical id: 4
                bus info: pci@06:04.0
                version: 10
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: iomemory:b0211000-b0211fff irq:16
           *-memory:0 UNCLAIMED
                description: FLASH memory
                product: ENE PCI Memory Stick Card Reader Controller
                vendor: ENE Technology Inc
                physical id: 4.1
                bus info: pci@06:04.1
                version: 01
                width: 32 bits
                clock: 33MHz (30.3ns)
                capabilities: bus_master cap_list
                configuration: latency=64 maxlatency=4 mingnt=1
                resources: iomemory:b0210400-b021047f irq:10
           *-system
                description: Generic system peripheral
                product: ENE PCI Secure Digital Card Reader Controller
                vendor: ENE Technology Inc
                physical id: 4.2
                bus info: pci@06:04.2
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=sdhci latency=64 maxlatency=72 mingnt=32
                resources: iomemory:b0210800-b02108ff irq:21
           *-memory:1 UNCLAIMED
                description: FLASH memory
                product: FLASH memory: ENE Technology Inc:
                vendor: ENE Technology Inc
                physical id: 4.3
                bus info: pci@06:04.3
                version: 01
                width: 32 bits
                clock: 33MHz (30.3ns)
                capabilities: bus_master cap_list
                configuration: latency=64 maxlatency=4 mingnt=1
                resources: iomemory:b0210c00-b0210c7f irq:10
           *-memory:2 UNCLAIMED
                description: FLASH memory
                product: ENE Technology Inc
                vendor: ENE Technology Inc
                physical id: 4.4
                bus info: pci@06:04.4
                version: 01
                width: 32 bits
                clock: 33MHz (30.3ns)
                capabilities: cap_list
                configuration: latency=0 maxlatency=72 mingnt=32
                resources: iomemory:b0210100-b02101ff irq:255
     *-pci:1
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
  *-battery
       description: Lithium Ion Battery
       product: PANASONIC
       vendor: PANASONIC
       physical id: 1
       slot: 1st Battery
       capacity: 3900mWh
       configuration: voltage=14.8V
root@salane-laptop:/home/salane# lspci

---

