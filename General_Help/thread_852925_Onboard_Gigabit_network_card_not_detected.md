---
title: "Onboard Gigabit network card not detected"
date: 2008-07-08
forum: General Help
---

### Post by Bout to Snap on 2008-07-08
yeah...i know this is probably wrong section...or atleast feels like it, however I wasnt able to make a new thread in the absolute beginner section.


anywho my problem is this. I've installed ubuntu on a XPS 420 install went perfectly! however my Intel(R) 82566dc-2 Gigabit Network Connection isnt detect only gives me the option to use a dial up connection, I've tried a few things is terminal such as pppoeconf (which basically told me it didnt exist) and it gave me the option to run a utily which i think was called (mod>?) also Im duel booting with Vista. I've searched the forums for a few hours now, found countless topics however none of them seem to be usefull I'm hoping someone can help with this issue. So i guess the starting point would be how can I install the drivers for this adapter?

sorry i didnt post any terminal logs but considering my card doesnt even show up what use could they be? sorry for typos...sleepy

Thanks in advance

---

### Post by p_quarles on 2008-07-08
What's the output of this terminal command?:
```
ifconfig -a
```
You might also post the results of this:
```
sudo lshw
```

---

### Post by Bout to Snap on 2008-07-08
> **p_quarles said:**
> What's the output of this terminal command?:
```
ifconfig -a
```
You might also post the results of this:
```
sudo lshw
```

Tried both of these commands in terminal however they were unsuccesfull sorry didnt post the output but it seems that I cant save either on my swap partition couldnt get permissions to do so, anyone else got anymore suggestions?

---

### Post by Titan8990 on 2008-07-08
Your swap partition is not meant for saving files.

---

### Post by Archmage on 2008-07-08
I think I did understand him.

He can't get into the internet and therefore he wants to save the output on a different partition and than post it in the other system that can go to the internet.

Don't you have a floppy-disk or something else? Without output it is pretty hard to help you.

---

### Post by Titan8990 on 2008-07-08
I understood that as well but it is good know what the swap partition is actually for. Wish I would have posted in the long "Why do I need a swap partition" thread last week so I could easily pull it up for him.

---

### Post by Bout to Snap on 2008-07-08
man...what a headache...anywho..Ubuntu's worth it! I managed to get some outputs from my terminal saved on my OS that can go online so here you go..hope you can make something of it.


chris@chris-desktop:~$ lshw
WARNING: you should run this program as super-user.
chris-desktop             
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 3041MB
     *-cpu
          product: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.15.11
          serial: 0000-06FB-0000-0000-0000-0000
          size: 18EHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 64 bits
             capabilities: logical
        *-logicalcpu:2
             description: Logical CPU
             physical id: 0.3
             width: 64 bits
             capabilities: logical
        *-logicalcpu:3
             description: Logical CPU
             physical id: 0.4
             width: 64 bits
             capabilities: logical
     *-pci
          description: Host bridge
          product: Intel Corporation
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@00:00.0
          version: 00
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@00:01.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-display
                description: VGA compatible controller
                product: ATI Technologies Inc
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@01:00.0
                version: 00
                size: 256MB
                width: 64 bits
                clock: 33MHz
                capabilities: vga bus_master cap_list
                configuration: latency=0
                resources: iomemory:d0000000-dfffffff iomemory:fe9f0000-fe9fffff ioport:dc00-dcff irq:11
        *-pci:1
             description: PCI bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 6
             bus info: pci@00:06.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-network UNCLAIMED
             description: Ethernet controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@00:19.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
             resources: iomemory:febe0000-febfffff iomemory:febdb000-febdbfff ioport:eca0-ecbf irq:10
        *-usb:0
             description: USB Controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@00:1a.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: ioport:ff20-ff3f irq:16
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-15-generic uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:1
             description: USB Controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@00:1a.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: ioport:ff00-ff1f irq:17
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-15-generic uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb
                   description: Audio device
                   product: Logitech USB Headset
                   vendor: Logitech
                   physical id: 2
                   bus info: usb@2:2
                   version: 10.12
                   capabilities: usb-1.10 audio-control
                   configuration: driver=snd-usb-audio maxpower=100mA speed=12.0MB/s
        *-usb:2
             description: USB Controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1a.2
             bus info: pci@00:1a.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: ioport:ecc0-ecdf irq:18
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-15-generic uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:3
             description: USB Controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@00:1a.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: iomemory:febdac00-febdafff irq:18
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.20-15-generic ehci_hcd
                physical id: 1
                bus info: usb@7
                logical name: usb7
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=6 speed=480.0MB/s
              *-usb UNCLAIMED
                   description: Generic USB device
                   product: XPS MiniView
                   vendor: Microsoft Co
                   physical id: 6
                   bus info: usb@7:6
                   version: 7.20
                   serial: AAAAAAAAAAAAAAAAAAAA
                   capabilities: usb-2.00
                   configuration: maxpower=0mA speed=480.0MB/s
        *-multimedia
             description: Audio device
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: iomemory:febdc000-febdffff irq:16
        *-pci:2
             description: PCI bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-usb:4
             description: USB Controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: ioport:ff80-ff9f irq:19
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-15-generic uhci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb
                   description: USB hub
                   product: BT Mini-Receiver
                   vendor: Logitech
                   physical id: 1
                   bus info: usb@4:1
                   version: 58.00
                   capabilities: usb-2.00
                   configuration: driver=hub maxpower=0mA slots=3 speed=12.0MB/s
                 *-usb:0
                      description: Bluetooth wireless interface
                      product: BT Mini-Receiver
                      vendor: Logitech
                      physical id: 1
                      bus info: usb@4:1.1
                      version: 58.00
                      serial: 001C26DC3FEB
                      capabilities: bluetooth usb-2.00
                      configuration: driver=hci_usb maxpower=0mA speed=12.0MB/s
                 *-usb:1
                      description: Keyboard
                      product: BT Mini-Receiver
                      vendor: Logitech
                      physical id: 2
                      bus info: usb@4:1.2
                      version: 58.00
                      serial: 001C26DC3FEB
                      capabilities: usb-2.00
                      configuration: driver=usbhid maxpower=98mA speed=12.0MB/s
                 *-usb:2
                      description: Mouse
                      product: BT Mini-Receiver
                      vendor: Logitech
                      physical id: 3
                      bus info: usb@4:1.3
                      version: 58.00
                      serial: 001C26DC3FEB
                      capabilities: usb-2.00
                      configuration: driver=usbhid maxpower=98mA speed=12.0MB/s
        *-usb:5
             description: USB Controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: ioport:ff60-ff7f irq:17
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-15-generic uhci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:6
             description: USB Controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: ioport:ff40-ff5f irq:20
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-15-generic uhci_hcd
                physical id: 1
                bus info: usb@6
                logical name: usb6
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb:0
                   description: Mouse
                   product: Dell USB Optical Mouse
                   vendor: Dell
                   physical id: 1
                   bus info: usb@6:1
                   version: 43.01
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=100mA speed=1.5MB/s
              *-usb:1
                   description: Keyboard
                   product: Dell USB Keyboard
                   vendor: Dell
                   physical id: 2
                   bus info: usb@6:2
                   version: 3.06
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=70mA speed=1.5MB/s
        *-usb:7
             description: USB Controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: iomemory:ff980800-ff980bff irq:19
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.20-15-generic ehci_hcd
                physical id: 1
                bus info: usb@8
                logical name: usb8
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=6 speed=480.0MB/s
              *-usb
                   description: Mass storage device
                   product: CAB-200
                   vendor: DELL
                   physical id: 2
                   bus info: usb@8:2
                   version: 7.08
                   serial: 00000201484D
                   capabilities: usb-2.00 scsi
                   configuration: driver=usb-storage maxpower=500mA speed=480.0MB/s
        *-pci:3
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@00:1e.0
             version: 92
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-communication UNCLAIMED
                description: Communication controller
                product: HSF 56k Data/Fax Modem
                vendor: Conexant
                physical id: 5
                bus info: pci@04:05.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=64
                resources: iomemory:fe7f0000-fe7fffff ioport:ccf8-ccff irq:9
           *-firewire
                description: FireWire (IEEE 1394)
                product: TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
                vendor: Texas Instruments
                physical id: a
                bus info: pci@04:0a.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=2
                resources: iomemory:fe7eb800-fe7ebfff iomemory:fe7ec000-fe7effff irq:20
        *-isa
             description: ISA bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list scsi-host
             configuration: driver=ata_piix latency=0
             resources: ioport:fe00-fe07 ioport:fe10-fe13 ioport:fe20-fe27 ioport:fe30-fe33 ioport:fec0-fecf ioport:ec80-ec8f irq:21
        *-serial UNCLAIMED
             description: SMBus
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@00:1f.3
             version: 02
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: iomemory:febdab00-febdabff ioport:ece0-ecff irq:10
        *-ide:1
             description: IDE interface
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@00:1f.5
             logical name: scsi2
             logical name: scsi3
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list scsi-host
             configuration: driver=ata_piix latency=0
             resources: ioport:fe40-fe47 ioport:fe50-fe53 ioport:fe60-fe67 ioport:fe70-fe73 ioport:fed0-fedf ioport:ec90-ec9f irq:21
  *-scsi
       physical id: 1
       bus info: scsi@4
       logical name: scsi4
       capabilities: scsi-host
       configuration: driver=usb-storage
chris@chris-desktop:~$ 

-----------------------------------------------------------------------
-----------------------------------------------------------------------

This is the Results I got after Using the (ifconfig -a)

chris@chris-desktop:~$ ifconfig -a
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)


Hope this helps someone.

---

### Post by Bout to Snap on 2008-07-08
Problem solved! Downgraded my Ethernet Card to an older one, so now Im good to go..however it's crappy look card ...meh

---

