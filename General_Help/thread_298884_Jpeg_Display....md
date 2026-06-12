---
title: "Jpeg Display..."
date: 2006-11-13
forum: General Help
---

### Post by jscanzoni on 2006-11-13
All of my jpgs (including old ones that were on windows and worked great) are showing up like this (or distorted variations). Any ideas? I have tried different programs (even Firefox). I check my email constantly, so please let me know what information you need from my computer.

[IMG]http://jsay.net/wordpress/wp-content/uploads/2006/11/screenshot.png[/IMG]

---

### Post by jscanzoni on 2006-11-13
ok... it is my card reader (or PCIMIA drivers)... my old pictures DO work.

Are there drivers for each? never needed drivers in windows...

---

### Post by taurus on 2006-11-13
Have you tried using gqview?  Are those pictures on your XP on the same machine?  Can you describe exactly how and where are those pictures located?

---

### Post by jscanzoni on 2006-11-13
After playing around a little more, I found out it was two things:

-F-Spot was displaying ALL pictures strangely (including my old ones)
-I plugged my Nikon D50 directly up to my computer and viewed files (everything works)

I think I am going to use picasa (I loved it on windows and did not realize there is now a linux version). I suppose the problem is with my card reader (PCIMCIA). It is an off-brand and I cannot find any info on it to get drivers... Can I find info somewhere on the device manager?

---

### Post by taurus on 2006-11-13
(Applications -> Accessories -> Terminal)

```
dmesg | tail
lspci
lshw
```
Could be on one of those!!!

---

### Post by jscanzoni on 2006-11-13
```
jason@jason-laptop:~$ dmesg | tail
[17210517.500000] sda: Mode Sense: 27 00 00 00
[17210517.500000] sda: assuming drive cache: write through
[17210517.500000]  sda: sda1 sda2
[17210517.516000] sd 2:0:0:0: Attached scsi disk sda
[17210517.516000] sd 2:0:0:0: Attached scsi generic sg0 type 0
[17210518.536000] usb-storage: device scan complete
[17210518.544000]   Vendor: HP        Model: photosmart 7900   Rev: 1.00
[17210518.544000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[17210518.612000] sd 3:0:0:0: Attached scsi removable disk sdb
[17210518.612000] sd 3:0:0:0: Attached scsi generic sg1 type 0
```
```
jason@jason-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
02:02.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
02:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
02:06.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
02:06.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
02:06.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
``````

jason@jason-laptop:~$ lshw
WARNING: you should run this program as super-user.
jason-laptop              
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 1994MB
     *-cpu
          product: Intel(R) Pentium(R) M processor 1.50GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.13.8
          size: 600MHz
          capacity: 600MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx up est tm2 cpufreq
     *-pci
          description: Host bridge
          product: 82852/82855 GM/GME/PM/GMV Processor to I/O Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
        *-system:0 UNCLAIMED
             description: System peripheral
             product: 82852/82855 GM/GME/PM/GMV Processor to I/O Controller
             vendor: Intel Corporation
             physical id: 0.1
             bus info: pci@00:00.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
        *-system:1 UNCLAIMED
             description: System peripheral
             product: 82852/82855 GM/GME/PM/GMV Processor to I/O Controller
             vendor: Intel Corporation
             physical id: 0.3
             bus info: pci@00:00.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
        *-display:0
             description: VGA compatible controller
             product: 82852/855GM Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@00:02.0
             version: 02
             size: 128MB
             width: 32 bits
             clock: 33MHz
             capabilities: vga bus_master cap_list
             resources: iomemory:e8000000-efffffff iomemory:e0000000-e007ffff ioport:1800-1807 irq:6
        *-display:1 UNCLAIMED
             description: Display controller
             product: 82852/855GM Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@00:02.1
             version: 02
             size: 128MB
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             resources: iomemory:f0000000-f7ffffff iomemory:e0080000-e00fffff
        *-usb:0
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:1820-183f irq:6
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-10-generic uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:1
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:1840-185f irq:6
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-10-generic uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:2
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:1860-187f irq:6
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-10-generic uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:3
             description: USB Controller
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd
             resources: iomemory:e0100000-e01003ff irq:10
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.17-10-generic ehci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=6 speed=480.0MB/s
              *-usb
                   description: USB hub
                   product: HighSpeed Hub
                   vendor: NEC Corp.
                   physical id: 3
                   bus info: usb@4:3
                   version: 1.00
                   capabilities: usb-2.00
                   configuration: driver=hub maxpower=100mA slots=4 speed=480.0MB/s
                 *-usb:0
                      description: USB hub
                      product: HighSpeed Hub
                      vendor: NEC Corp.
                      physical id: 1
                      bus info: usb@4:3.1
                      version: 1.00
                      capabilities: usb-2.00
                      configuration: driver=hub maxpower=100mA slots=4 speed=480.0MB/s
                    *-usb:0
                         description: Mass storage device
                         product: USB2.0 Storage Device
                         vendor: Cypress Semiconductor
                         physical id: 1
                         bus info: usb@4:3.1.1
                         version: 0.01
                         serial: DEF10A7418AF
                         capabilities: usb-2.00 scsi
                         configuration: driver=usb-storage maxpower=0mA speed=480.0MB/s
                    *-usb:1
                         description: USB hub
                         vendor: Belkin Components
                         physical id: 2
                         bus info: usb@4:3.1.2
                         version: 0.00
                         capabilities: usb-2.00
                         configuration: driver=hub maxpower=2mA slots=7 speed=480.0MB/s
                    *-usb:2 UNCLAIMED
                         description: Generic USB device
                         product: USB Scanner
                         vendor: Visioneer
                         physical id: 3
                         bus info: usb@4:3.1.3
                         version: 3.00
                         capabilities: usb-2.00
                         configuration: maxpower=0mA speed=480.0MB/s
                    *-usb:3
                         description: Printer
                         product: photosmart 7900 series
                         vendor: hp
                         physical id: 4
                         bus info: usb@4:3.1.4
                         version: 1.00
                         serial: CN3BS311VDN8
                         capabilities: usb-2.00 bidirectional
                         configuration: driver=usb-storage maxpower=2mA speed=12.0MB/s
                 *-usb:1
                      description: USB hub
                      product: HighSpeed Hub
                      vendor: NEC Corp.
                      physical id: 2
                      bus info: usb@4:3.2
                      version: 1.00
                      capabilities: usb-2.00
                      configuration: driver=hub maxpower=100mA slots=4 speed=480.0MB/s
                    *-usb:0
                         description: Keyboard
                         product: USB Receiver
                         vendor: Logitech
                         physical id: 3
                         bus info: usb@4:3.2.3
                         version: 17.21
                         capabilities: usb-1.10
                         configuration: driver=usbhid maxpower=98mA speed=1.5MB/s
                    *-usb:1
                         description: Bluetooth wireless interface
                         product: Wireless Transceiver for Bluetooth
                         vendor: Microsoft
                         physical id: 4
                         bus info: usb@4:3.2.4
                         version: 5.05
                         serial: 00E474CF00F20050
                         capabilities: bluetooth usb-2.00
                         configuration: driver=hci_usb maxpower=150mA speed=12.0MB/s
                 *-usb:2
                      description: Audio device
                      product: Sound Blaster Extigy
                      vendor: Creative Technology Ltd.
                      physical id: 3
                      bus info: usb@4:3.3
                      version: 1.00
                      capabilities: usb-1.10 audio-control
                      configuration: driver=snd-usb-audio maxpower=0mA speed=12.0MB/s
        *-pci
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@00:1e.0
             version: 83
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-network:0
                description: Ethernet interface
                product: BCM4401 100Base-T
                vendor: Broadcom Corporation
                physical id: 2
                bus info: pci@02:02.0
                logical name: eth0
                version: 01
                serial: 00:c0:9f:75:63:91
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=b44 multicast=yes
                resources: iomemory:e0204000-e0205fff irq:6
           *-network:1
                description: Wireless interface
                product: PRO/Wireless 2200BG Network Connection
                vendor: Intel Corporation
                physical id: 4
                bus info: pci@02:04.0
                logical name: eth1
                version: 05
                serial: 00:0e:35:67:78:a9
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw2200 ip=192.168.1.50 multicast=yes wireless=IEEE 802.11g
                resources: iomemory:e0208000-e0208fff irq:10
           *-pcmcia
                description: CardBus bridge
                product: PCIxx21/x515 Cardbus Controller
                vendor: Texas Instruments
                physical id: 6
                bus info: pci@02:06.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus
                resources: iomemory:e0209000-e0209fff irq:10
           *-firewire
                description: FireWire (IEEE 1394)
                product: OHCI Compliant IEEE 1394 Host Controller
                vendor: Texas Instruments
                physical id: 6.2
                bus info: pci@02:06.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci1394
                resources: iomemory:e020a000-e020a7ff iomemory:e0200000-e0203fff irq:10
           *-storage
                description: Mass storage controller
                product: PCIxx21 Integrated FlashMedia Controller
                vendor: Texas Instruments
                physical id: 6.3
                bus info: pci@02:06.3
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: storage bus_master cap_list
                configuration: driver=tifm_7xx1
                resources: iomemory:e0206000-e0207fff irq:10
        *-isa UNCLAIMED
             description: ISA bridge
             product: 82801DBM (ICH4-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
        *-ide
             description: IDE interface
             product: 82801DBM (ICH4-M) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@00:1f.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=PIIX_IDE
             resources: ioport:1810-181f iomemory:8b000000-8b0003ff irq:6
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   product: ST9120821A
                   vendor: Seagate
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   capacity: 111GB
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom
                   product: QSI CD-RW/DVD-ROM SBW242C
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   capacity: 4342MB
                   capabilities: packet
        *-serial UNCLAIMED
             description: SMBus
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@00:1f.3
             version: 03
             width: 32 bits
             clock: 33MHz
             resources: ioport:1880-189f irq:10
        *-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@00:1f.5
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Intel ICH
             resources: ioport:1c00-1cff ioport:18c0-18ff iomemory:e0100c00-e0100dff iomemory:e0100800-e01008ff irq:10
        *-communication UNCLAIMED
             description: Modem
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@00:1f.6
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: generic cap_list
             resources: ioport:2400-24ff ioport:2000-207f irq:10
  *-scsi:0
       physical id: 1
       bus info: scsi@2
       logical name: scsi2
       capabilities: scsi-host
       configuration: driver=usb-storage
  *-scsi:1
       physical id: 2
       bus info: scsi@3
       logical name: scsi3
       capabilities: scsi-host
       configuration: driver=usb-storage
```

---

### Post by taurus on 2006-11-13
Is that your smart card?

```
Vendor: HP        Model: photosmart 7900
```

---

### Post by jscanzoni on 2006-11-13
no, that is on my printer... 

I believe that this one does not work:

02:06.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller

---

