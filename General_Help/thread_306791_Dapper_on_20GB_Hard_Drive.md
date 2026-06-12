---
title: "Dapper on 20GB Hard Drive?"
date: 2006-11-25
forum: General Help
---

### Post by DougieFresh4U on 2006-11-25
I was given an old computer today and I am wondering if it's hard drive (20GB) can handle Dapper and it also has 256RAM. Also the guy said some thing about 900 mherzt or some thing like that. Maybe some one can give me code to find out system info (I'm installing Dapper and almost finished) Thanks.

---

### Post by iamhugeinjapan on 2006-11-25
20 GB is more than enough space. You could fit multiple installs on it :)

---

### Post by taurus on 2006-11-25
You can run either Gnome (Ubuntu) or KDE (Kubuntu) with 256MB of RAM but if you want a little speed, try installing Xubuntu (XFce4).  20GB of harddrive is more than enough...

---

### Post by xmastree on 2006-11-25
My laptop was happily running Dapper on a 4GB hard disk.

---

### Post by DougieFresh4U on 2006-11-25
taurus,how about a **code** please to find out hardware,graphics, modem ect. I am putting this together for my **other** sister, so I can have 2 sisters that bother me about Linux-:evil:   oh joy! This machine is gonna have to have dial-up. I am using it now via ethernet card that dapper found no problem.

---

### Post by aysiu on 2006-11-25
I'm using about 3.1 GB right now for Ubuntu with IceWM on top of it. 20 GB is plenty.

For 256 MB, you can run anything you want, but if you want a decent working speed, use Xubuntu or IceWM.

---

### Post by DougieFresh4U on 2006-11-25
In order to get Xubuntu I need to download the ISO, am I correct on that? Can I do some tweaking w/terminal to get Xubuntu as I just installed dapper and sat through 199 updates (in 55 minutes)

---

### Post by aysiu on 2006-11-25
You don't need to downlaod the ISO. You can just paste this command into the terminal and install Xubuntu straight off the internet: ```
sudo aptitude update && sudo aptitude install xubuntu-desktop -y
``` If that's too big a download, you can also just install vanilla XFCE: ```
[code]sudo aptitude update && sudo aptitude install xfce4 -y
``` You'll need to [**enable extra repositories**](http://www.psychocats.net/ubuntu/sources) first for that second method, though, for some strange reason.

---

### Post by DougieFresh4U on 2006-11-25
Thanks aysiu, downloading that first code now (18 minutes it says) I was looking for Automatix 2 and I still need a sudo code to find out what kind of crap is in this machine (graphics card etc.) thank you

---

### Post by taurus on 2006-11-25
```
lspci
```

---

### Post by MJN on 2006-11-25
**sudo lshw** should suffice.

Mathew

---

### Post by iamhugeinjapan on 2006-11-25
or look in System - Device Manager

Good luck getting the dialup working, modems designed for Windows are notoriously troublesome. You may need to resort to an external serial modem.

---

### Post by MJN on 2006-11-25
I've had 100% success with a variety of WinModems following [https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto) so there is hope!

Mathew

---

### Post by DougieFresh4U on 2006-11-25
~$ lspci
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 81)
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
0000:00:03.0 Ethernet controller: Accton Technology Corporation SMC2-1211TX (rev  10)
0000:00:04.0 Modem: PCTel Inc HSP MicroModem 56 (rev 02)
0000:00:14.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (r ev 22)
0000:00:14.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT82 3x/A/C PIPC Bus Master IDE (rev 10)
0000:00:14.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr oller (rev 10)
0000:00:14.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr oller (rev 10)
0000:00:14.4 Bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 30 )
0000:00:14.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 A udio Controller (rev 20)
0000:01:00.0 VGA compatible controller: S3 Inc. ProSavage KM1!!!!! Ok what am I working with here? Is the graphics card ok? Modem? Thanks every one, please let me know if my hardware is  gonna give me 'drama'

---

### Post by taurus on 2006-11-25
Your graphic card is a "S3 Inc. ProSavage KM1".  And since you have a DSL which I assume connects to a router, why not get a cheap ethernet card and install it into that old machine.  Then, you can connect it to your router and you would have a fast network connection instead of the dialup thing!!!

---

### Post by DougieFresh4U on 2006-11-25
sudo lshw
sassysfunbox
    description: Mini Tower Computer
    product: Presario 4090US 470016-303
    vendor: Compaq
    version: W21CDBCB
    serial: 2H17JLD123AC
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=mini-tower uuid=30323031-3030-3031-3030-313231304345
  *-core
       description: Motherboard
       product: 0708h
       vendor: Compaq
       physical id: 0
       version: None
       serial: None
     *-firmware
          description: BIOS
          vendor: Compaq
          physical id: 0
          version: 786K3 (05/03/2001)
          size: 64KB
          capacity: 192KB
          capabilities: pci pnp upgrade shadowing escd cdboot bootselect edd int13floppynec int13floppytosh iba int13floppy360 int13floppy1200 int13floppy720 int5printscreen int9keyboard int14serial int17printer acp i usb agp ls120boot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Duron(tm) Processor
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 6.3.1
          slot: U12A
          size: 900MHz
          capacity: 1100MHz
          width: 32 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36  mmx fxsr syscall mmxext 3dnowext 3dnow
        *-cache:0
             description: L1 cache
             physical id: 5
             size: 128KB
             capacity: 128KB
             capabilities: synchronous internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 6
             size: 64KB
             capacity: 64KB
             capabilities: synchronous internal write-back data
     *-memory
          description: System Memory
          physical id: 7
          slot: System board or motherboard
          size: 256MB
          capacity: 1536MB
        *-bank:0
             description: DIMM DRAM Synchronous 100 MHz (10.0 ns)
             physical id: 0
             slot: DIMM1
             size: 128MB
             width: 64 bits
             clock: 100MHz (10ns)
        *-bank:1
             description: DIMM DRAM Synchronous 100 MHz (10.0 ns)
             physical id: 1
             slot: DIMM2
             size: 128MB
             width: 64 bits
             clock: 100MHz (10ns)
        *-bank:2
             description: DIMM DRAM Synchronous [empty]
             physical id: 2
             slot: DIMM3
     *-pci
          description: Host bridge
          product: VT8363/8365 [KT133/KM133]
          vendor: VIA Technologies, Inc.
          physical id: 90000000
          bus info: pci@00:00.0
          version: 81
          width: 32 bits
          clock: 33MHz
          resources: iomemory:90000000-93ffffff
        *-pci
             description: PCI bridge
             product: VT8363/8365 [KT133/KM133 AGP]
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master cap_list
           *-display
                description: VGA compatible controller
                product: ProSavage KM133
                vendor: S3 Inc.
                physical id: 0
                bus info: pci@01:00.0
                version: 00
                size: 128MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                resources: iomemory:80000000-8007ffff iomemory:88000000-8fffffff irq:3
        *-network
             description: Ethernet interface
             product: SMC2-1211TX
             vendor: Accton Technology Corporation
             physical id: 3
             bus info: pci@00:03.0
             logical name: eth0
             version: 10
             serial: 00:30:f1:08:e5:30
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autoneg ociation
             configuration: autonegociation=on broadcast=yes driver=8139too driverversion=0.9.27 duplex=ful l ip=192.168.254.3 link=yes multicast=yes port=MII speed=100MB/s
             resources: ioport:1800-18ff iomemory:a0000000-a00000ff irq:3
        *-communication
             description: Modem
             product: HSP MicroModem 56
             vendor: PCTel Inc
             physical id: 4
             bus info: pci@00:04.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: hayes_16750 cap_list
             configuration: driver=serial
             resources: ioport:1400-143f irq:10
        *-isa
             description: ISA bridge
             product: VT82C686 [Apollo Super South]
             vendor: VIA Technologies, Inc.
             physical id: 14
             bus info: pci@00:14.0
             version: 22
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=parport_pc
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: 14.1
             bus info: pci@00:14.1
             version: 10
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master cap_list
             configuration: driver=VIA_IDE
             resources: ioport:1480-148f
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   description: ATA Disk
                   product: Maxtor 5T020H2
                   vendor: Maxtor
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: TAH71DP0
                   serial: T2KMDTZC
                   size: 19GB
                   capacity: 19GB
                   capabilities: ata dma lba iordy smart pm apm partitioned partitioned:dos
                   configuration: apm=off mode=udma4 smart=on
                 *-volume:0
                      description: Linux filesystem partition
                      physical id: 1
                      bus info: ide@0.0,1
                      logical name: /dev/hda1
                      capacity: 18GB
                      capabilities: primary bootable
                 *-volume:1
                      description: Extended partition
                      physical id: 2
                      bus info: ide@0.0,2
                      logical name: /dev/hda2
                      capacity: 705MB
                      capabilities: extended partitioned partitioned:extended
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom
                   description: CD-R/CD-RW writer
                   product: CDD4801 CD-R/RW
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: C2,1
                   serial: 7378605HWM0BJW
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw
                 *-disc
                      physical id: 0
                      logical name: /dev/hdc
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 14.2
             bus info: pci@00:14.2
             version: 10
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd
             resources: ioport:1440-145f irq:11
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.15-27-386 uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 14.3
             bus info: pci@00:14.3
             version: 10
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd
             resources: ioport:1460-147f irq:11
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.15-27-386 uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-bridge UNCLAIMED
             description: Bridge
             product: VT82C686 [Apollo Super ACPI]
             vendor: VIA Technologies, Inc.
             physical id: 14.4
             bus info: pci@00:14.4
             version: 30
             width: 32 bits
             clock: 33MHz
             capabilities: bridge cap_list
             resources: irq:9
        *-multimedia
             description: Multimedia audio controller
             product: VT82C686 AC97 Audio Controller
             vendor: VIA Technologies, Inc.
             physical id: 14.5
             bus info: pci@00:14.5
             version: 20
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: driver=VIA 82xx Audio
             resources: ioport:1000-10ff ioport:1490-1493 ioport:1494-1497 irq:10

---

### Post by MJN on 2006-11-25
Just get on with the installation - best (and often **only**) way to find out! :)

The modem is definitely a so-called Winmodem, however it's a very popular one (indeed there are even proprietory Linux drivers for it) however take a look at the link I posted earlier and follow the instructions. For further info, check out [http://www.faqs.org/docs/Linux-mini/PCTel-MicroModem-Config.html](http://www.faqs.org/docs/Linux-mini/PCTel-MicroModem-Config.html)

Mathew

---

### Post by DougieFresh4U on 2006-11-25
taurus, it does have a ether card as I am using it now but where my one sister lives is only dial-up-no hook up for ethernet card. will the graphics card be dood and what driver do I need for it. thanks. so far machine is doing good but firefox is dog slow and I'll change that in a minute,thanks

---

### Post by MJN on 2006-11-25
It'll be the 'savage' but I expect that's what you're using. Check the **Section "Device"** portion of /etc/X11/xorg.conf.

Mathew

---

