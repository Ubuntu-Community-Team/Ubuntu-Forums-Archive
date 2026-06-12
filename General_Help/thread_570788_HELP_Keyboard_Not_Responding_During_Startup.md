---
title: "HELP: Keyboard Not Responding During Startup"
date: 2007-10-08
forum: General Help
---

### Post by joel_r on 2007-10-08
Hello world!

Big problems here in Sweden!

My keyboard is not responding during startup. once reaching login-screen in Ubuntu feisty fawn the keyboard start working again and everything is back to normal.

annoying consequences:

- i cant hit "any button" to start from cd (installing/switching between OS etc.)
- i cant reach bios setup, which basically turns my computer into crap

Please, if anyone knows anything about anything that in someway has something related to this nightmare. I will be very grateful.

I'm using a logitech keyboard (non-wireless) but I've tried other as well., asrock GV775 motherboard,  an additional soundcard, wireless mouse... 3 ghz.. dont know if any of this matters but anyway. 

I remember the keyboard working during startup for about 2 months after I had Linux installed but than suddenly...

// Joel

---

### Post by jnorthr on 2007-10-08
Just to clarify this problem: your keyboard works correctly once ubuntu has started. It does not work during the boot up procedure ? Do you see the grub menu during bootup sequence ? It will offer you a choice of which o/s you can load on your machine. Do the arrow keys move the cursor up and down ? If you press the 'enter' key does it work ?  Has this worked before and now it does not work ? Have up made any hardware changes ? Have you added any new packages or software ?


Just a guess here: is it possible that your keyboard is special for Sweden ? I'm thinking the grub loader may not be smart enough to recognise your keyboard, but as you say, ubuntu works ok, so it must understand your keyboard layout.... ?
Can you post the results of 
lshw
please ?

---

### Post by joel_r on 2007-10-09
Thanks for your reply!

Yes thats right. only when Ubuntu has started it works.. I cannot use up or down key to change os. the menu comes up and all. All I can do during startup is watching my computer give me choices I cant choose and finally I end up in Ubuntu login screen with a drum roll.


HARDWARE / SOFTWARE CHANGES

-No hardware change
-I did install quite a lot of software and packages around that time so it can absolutely has  something to do with that. but I don´t know exactly which or how to undo whats been done. 

Java RE was installed.. some audio editors/music programs. dvd burning tools.. some games from the Ubuntu lib. 

*gonna find out what "post ishw" means and then I will make an additional reply!

I'm really IMPRESSED by this forum, its damn quick and just awesome.

---

### Post by Sef on 2007-10-09
> "post ishw"

That's post lshw.   It means copy and paste the results of listed harhware.

---

### Post by joel_r on 2007-10-09
Okey, here goes the result of lshw.    

description: Computer
    product: 775i65GV
    version: 1.00
    serial: 00000000
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: uuid=00020003-0004-0005-0006-000700080009
  *-core
       description: Motherboard
       product: 775i65GV
       physical id: 0
       version: 1.0
       serial: 00000000
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: P1.40 (09/17/2004)
          size: 64KB
          capacity: 192KB
          capabilities: isa pci upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 3.00GHz
          vendor: Intel Corp.
          physical id: 3
          bus info: cpu@0
          version: 15.3.4
          serial: 0000-0F34-0000-0000-0000-0000
          slot: P4 Socket
          size: 3GHz
          capacity: 3GHz
          width: 32 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc pni monitor ds_cpl cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 4
             slot: L1-Cache
             size: 16KB
             capacity: 16KB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 5
             slot: L2-cache
             size: 1MB
             capacity: 1MB
             capabilities: pipeline-burst internal varies unified
        *-cache:2 DISABLED
             description: L3 cache
             physical id: 6
             slot: L3-cache
             capabilities: internal
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 32 bits
             capabilities: logical
     *-memory
          description: System memory
          physical id: 1
          size: 503MB
     *-pci
          description: Host bridge
          product: 82865G/PE/P DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: fe800000
          bus info: pci@00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          resources: iomemory:fe800000-febfffff
        *-display
             description: VGA compatible controller
             product: 82865G Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@00:02.0
             version: 02
             size: 128MB
             width: 32 bits
             clock: 33MHz
             capabilities: vga bus_master cap_list
             configuration: latency=0
             resources: iomemory:f0000000-f7ffffff iomemory:fe780000-fe7fffff ioport:ec00-ec07 irq:16
        *-usb:0
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:dc00-dc1f irq:16
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb:0
                   description: Human interface device
                   product: USB Game Controllers
                   vendor: Mega World
                   physical id: 1
                   bus info: usb@1:1
                   version: 1.01
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=350mA speed=1.5MB/s
              *-usb:1
                   description: Mouse
                   product: RF USB Mouse
                   vendor: A4Tech
                   physical id: 2
                   bus info: usb@1:2
                   version: 0.01
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=100mA speed=1.5MB/s
        *-usb:1
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:e000-e01f irq:17
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:2
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:e400-e41f irq:18
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:3
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:e800-e81f irq:16
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:4
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: iomemory:fe77bc00-fe77bfff irq:19
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.20-16-generic ehci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=8 speed=480.0MB/s
        *-pci
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@00:1e.0
             version: c2
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-multimedia
                description: Multimedia audio controller
                product: SB Audigy
                vendor: Creative Labs
                physical id: 1
                bus info: pci@01:01.0
                version: 04
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=EMU10K1_Audigy latency=32 maxlatency=20 mingnt=2
                resources: ioport:b800-b83f irq:20
           *-input
                description: Input device controller
                product: SB Audigy Game Port
                vendor: Creative Labs
                physical id: 1.1
                bus info: pci@01:01.1
                version: 04
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=Emu10k1_gameport latency=32
                resources: ioport:bc00-bc07
           *-firewire
                description: FireWire (IEEE 1394)
                product: SB Audigy FireWire Port
                vendor: Creative Labs
                physical id: 1.2
                bus info: pci@01:01.2
                version: 04
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci1394 latency=32 maxlatency=4 mingnt=2
                resources: iomemory:fe5ff800-fe5fffff iomemory:fe5f8000-fe5fbfff irq:19
           *-network
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 5
                bus info: pci@01:05.0
                logical name: eth0
                version: 10
                serial: 00:0b:6a:8b:58:db
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=83.255.5.71 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
                resources: ioport:b400-b4ff iomemory:fe5ff400-fe5ff4ff irq:20
        *-isa
             description: ISA bridge
             product: 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801EB/ER (ICH5/ICH5R) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@00:1f.1
             logical name: scsi0
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated scsi-host
             configuration: driver=ata_piix latency=0
             resources: ioport:1f0-1f7 ioport:3f4-3f3 ioport:170-177 ioport:374-373 ioport:fc00-fc0f iomemory:20000000-200003ff irq:18
           *-disk
                description: SCSI Disk
                product: Maxtor 6Y080P0
                vendor: ATA
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: YAR4
                serial: Y23YSMDE
                size: 76GB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume:0
                   description: HPFS/NTFS partition
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   capacity: 19GB
                   capabilities: primary bootable
              *-volume:1
                   description: Linux filesystem partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   capacity: 55GB
                   capabilities: primary
              *-volume:2
                   description: Extended partition
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   size: 1451MB
                   capacity: 1451MB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1451MB
                      capabilities: nofs
           *-cdrom:0
                description: CD-R/CD-RW writer
                product: CD-R/RW SW-252S
                vendor: SAMSUNG
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: R952
                capabilities: removable audio cd-r cd-rw
                configuration: ansiversion=5
              *-disc
                   physical id: 0
                   logical name: /dev/cdrom
           *-cdrom:1
                description: DVD writer
                product: DVDRW SOHW-1693S
                vendor: LITE-ON
                physical id: 0.1.0
                bus info: scsi@1:0.1.0
                logical name: /dev/dvd
                logical name: /dev/scd1
                logical name: /dev/sr1
                version: KS04
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5
              *-disc
                   physical id: 0
                   logical name: /dev/dvd
        *-serial UNCLAIMED
             description: SMBus
             product: 82801EB/ER (ICH5/ICH5R) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:400-41f irq:11
        *-multimedia
             description: Multimedia audio controller
             product: 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Intel ICH latency=0
             resources: ioport:d800-d8ff ioport:d400-d43f iomemory:fe77b800-fe77b9ff iomemory:fe77b400-fe77b4ff irq:21

---

### Post by petay on 2007-10-09
Do you have a USB keyboard??

sometimes BIOS does not see them unless legacy support is enabled.

maybe your BIOS has changed for one reason or another and it has stopped seeing the keyboard. as ubuntu can access USB devices it can see your keyboard.

Just a thought

Pete

---

### Post by joel_r on 2007-10-09
its not an usb-keyboard.. damn..

---

### Post by petay on 2007-10-09
thats my theory out of the window then!!

sorry i could not help

Pete

---

### Post by SpyroViper on 2007-10-09
Hello, Joel

I had this problem at my old workplace when I was trying to fix a computer the keyboard sometimes did not work..  At all!  I had to continuously unplug it and plug it back it over and over again during startup/shutdown/rebooting etc.  Try that or if you have one laying around, a PS2 keyboard (NOT the console, the connector style) lol.


Good Luck.  Hope this helps.



-Adam:guitar:

---

### Post by joel_r on 2007-10-10
Okey, im gonna try that to, thanks.

/Joe

---

### Post by joel_r on 2007-10-11
nope.. nothing works..

damn.

Will it help to change harddrive or will my only option be to get another motherboard?

If anyone knows, I would be gratefull

Joel

---

