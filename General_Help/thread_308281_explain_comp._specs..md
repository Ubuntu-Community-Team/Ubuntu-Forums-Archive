---
title: "explain comp. specs."
date: 2006-11-27
forum: General Help
---

### Post by DougieFresh4U on 2006-11-27
sassy@SassiesFunBox:~$ lshw
WARNING: you should run this program as super-user.
sassiesfunbox
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 254MB
     *-cpu
          product: Intel(R) Celeron(TM) CPU                1300MHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.11.4
          size: 1300MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 32KB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 256KB
     *-pci
          description: Host bridge
          product: 82810E DC-133 GMCH [Graphics Memory Controller Hub]
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
        *-display
             description: VGA compatible controller
             product: 82810E DC-133 CGC [Chipset Graphics Controller]
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@00:01.0
             version: 03
             size: 64MB
             width: 32 bits
             clock: 66MHz
             capabilities: vga bus_master cap_list
             configuration: driver=i810_smbus
             resources: iomemory:f8000000-fbffffff iomemory:fea80000-feafffff irq:11
        *-pci
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@00:1e.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-communication
                description: Modem
                product: SmartLink SmartPCI561 56K Modem
                vendor: ALi Corporation
                physical id: 0
                bus info: pci@01:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: generic cap_list
                configuration: driver=serial
                resources: iomemory:febfe000-febfefff ioport:7800-78ff irq:169
           *-network
                description: Ethernet interface
                product: 82801BA/BAM/CA/CAM Ethernet Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@01:08.0
                logical name: eth0
                version: 03
                serial: 00:09:6b:6c:36:5d
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=e100 ip=192.168.254.2 multicast=yes
                resources: iomemory:febff000-febfffff ioport:74c0-74ff irq:193
        *-isa UNCLAIMED
             description: ISA bridge
             product: 82801BA ISA Bridge (LPC)
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@00:1f.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
        *-ide
             description: IDE interface
             product: 82801BA IDE U100
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@00:1f.1
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=PIIX_IDE
             resources: ioport:fff0-ffff
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   product: Maxtor 2F040J0
                   vendor: Maxtor
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   capacity: 38GB
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom
                   product: PLEXTOR CD-R PX-W4012A
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   capabilities: packet
        *-usb:0
             description: USB Controller
             product: 82801BA/BAM USB (Hub #1)
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@00:1f.2
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:fb00-fb1f irq:177
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.15-27-386 uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-serial UNCLAIMED
             description: SMBus
             product: 82801BA/BAM SMBus
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@00:1f.3
             version: 05
             width: 32 bits
             clock: 33MHz
             resources: ioport:fe00-fe0f irq:9
        *-usb:1
             description: USB Controller
             product: 82801BA/BAM USB (Hub #2)
             vendor: Intel Corporation
             physical id: 1f.4
             bus info: pci@00:1f.4
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:fb80-fb9f irq:185
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.15-27-386 uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-multimedia
             description: Multimedia audio controller
             product: 82801BA/BAM AC'97 Audio
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@00:1f.5
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=Intel ICH
             resources: ioport:f000-f0ff ioport:f400-f43f irq:201
sassy@SassiesFunBox:~$ lshw

---

### Post by DougieFresh4U on 2006-11-27
taurus heres the second box, which is better 1rst or 2nd:::::::::::::::dougie@DougiesToyBox:~$ lshw
WARNING: you should run this program as super-user.
dougiestoybox
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 254MB
     *-cpu
          product: Celeron (Coppermine)
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.8.10
          size: 1100MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic  sep mtrr pge mca cmov pat pse36 mmx fxsr sse
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 32KB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 128KB
     *-pci
          description: Host bridge
          product: 82810 GMCH [Graphics Memory Controller Hub]
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
        *-display
             description: VGA compatible controller
             product: 82810 CGC [Chipset Graphics Controller]
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@00:01.0
             version: 03
             size: 64MB
             width: 32 bits
             clock: 66MHz
             capabilities: vga bus_master cap_list
             configuration: driver=i810_smbus
             resources: iomemory:f8000000-fbffffff iomemory:ffa00000-ffa7ffff ir q:9
        *-pci
             description: PCI bridge
             product: 82801AA PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@00:1e.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-communication
                description: Modem
                product: HSP MicroModem 56
                vendor: PCTel Inc
                physical id: 7
                bus info: pci@01:07.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: hayes_16750 cap_list
                configuration: driver=serial
                resources: ioport:ecc0-ecff irq:169
           *-network
                description: Ethernet interface
                product: 82557/8/9 [Ethernet Pro 100]
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@01:08.0
                logical name: eth0
                version: 08
                serial: 00:02:b3:a6:6d:5e
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=e100 ip=192.168.254.3 multic ast=yes
                resources: iomemory:ff8ff000-ff8fffff ioport:ec80-ecbf iomemory: ff700000-ff7fffff irq:185
        *-isa UNCLAIMED
             description: ISA bridge
             product: 82801AA ISA Bridge (LPC)
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
        *-ide
             description: IDE interface
             product: 82801AA IDE
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@00:1f.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=PIIX_IDE
             resources: ioport:ffa0-ffaf
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   product: WDC WD400BB-60DGA0
                   vendor: Western Digital
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   capacity: 37GB
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom
                   product: SAMSUNG CD-ROM SC-148C
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   capabilities: packet
        *-usb
             description: USB Controller
             product: 82801AA USB
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@00:1f.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:ff80-ff9f irq:177
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.15-27-386 uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb:0
                   description: Mouse
                   product: USB-PS/2 Optical Mouse
                   vendor: Logitech
                   physical id: 1
                   bus info: usb@1:1
                   version: 11.10
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=98mA speed=1.5MB/s
              *-usb:1
                   description: USB hub
                   product: General Purpose USB Hub
                   vendor: Dell Computer Corp.
                   physical id: 2
                   bus info: usb@1:2
                   version: 1.01
                   capabilities: usb-1.10
                   configuration: driver=hub maxpower=0mA slots=3 speed=12.0MB/s
        *-serial UNCLAIMED
             description: SMBus
             product: 82801AA SMBus
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             resources: ioport:dcd0-dcdf irq:10
        *-multimedia
             description: Multimedia audio controller
             product: 82801AA AC'97 Audio
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=Intel ICH
             resources: ioport:d800-d8ff ioport:dc80-dcbf irq:185
dougie@DougiesToyBox:~$

---

