---
title: "Extremely poor performance after fresh install"
date: 2016-02-19
forum: General Help
---

### Post by nordic2 on 2016-02-19
I am trying Lubuntu 14.04 LTS in an old but (what seemed to me) fairly well equipped computer:
-Pentium 4 2.6GHz
-1.5 GB RAM
-Nvidia GeForce4 MX 440 AGP 8x.

However, I'm constantly hitting 100%+ CPU usage, many applications have a lot of lag (even dragging windows around is slow) and browsing the web is a nightmare (there is lag while scrolling the google results of a search, youtube tries to play, but only manages to show a few scattered frames of the videos). This is pretty much a useless state.

Am I missing some crucial step in configuration? Is the hardware just too old to save? I would swear than in most of the examples of recovering old computers (not just the extreme ones) I have seen people claiming to run a smooth system with even worse processor, memory and video card.


Here is the result of 'sudo lshw -sanitize' for further details

```

computer
    description: Desktop Computer
    product: DT300A-AKV T440M
    vendor: HP Pavilion 061
    version: 0qz1211RE101NEON 10
    serial: [REMOVED]
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1 uuid=[REMOVED]
  *-core
       description: Motherboard
       product: Gamila/Giovani/Neon series
       vendor: MICRO-STAR INTERNATIONAL CO., LTD
       physical id: 0
       version: 030
       serial: [REMOVED]
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 3.05
          date: 11/25/2003
          size: 128KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.60GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.2.9
          slot: Socket 478
          size: 2600MHz
          width: 32 bits
          clock: 100MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pebs bts cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: Internal Cache
             size: 8KiB
             capacity: 20KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: External Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous external write-back
     *-memory
          description: System Memory
          physical id: 20
          slot: System board or motherboard
          size: 1536MiB
          capacity: 2GiB
        *-bank:0
             description: DIMM SDRAM Synchronous
             product: None
             vendor: None
             physical id: 0
             serial: [REMOVED]
             slot: A0
             size: 1GiB
             width: 64 bits
        *-bank:1
             description: DIMM SDRAM Synchronous
             product: None
             vendor: None
             physical id: 1
             serial: [REMOVED]
             slot: A1
             size: 512MiB
             width: 64 bits
     *-pci
          description: Host bridge
          product: 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0 memory:d8000000-dbffffff
        *-pci:0
             description: PCI bridge
             product: 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
             resources: memory:dc000000-ddffffff memory:d0000000-d7ffffff
           *-display
                description: VGA compatible controller
                product: NV18 [GeForce4 MX 440 AGP 8x]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a2
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 vga_controller bus_master cap_list rom
                configuration: driver=nouveau latency=32 maxlatency=1 mingnt=5
                resources: irq:16 memory:dc000000-dcffffff memory:d0000000-d7ffffff memory:dd000000-dd01ffff
        *-usb:0
             description: USB controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:d800(size=32)
        *-usb:1
             description: USB controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:d000(size=32)
        *-usb:2
             description: USB controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:d400(size=32)
        *-usb:3
             description: USB controller
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:e0000000-e00003ff
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 82
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:c000(size=4096) memory:de000000-dfffffff memory:60000000-600fffff
           *-communication UNCLAIMED
                description: Communication controller
                product: LT WinModem
                vendor: LSI Corporation
                physical id: b
                bus info: pci@0000:02:0b.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=32 maxlatency=14 mingnt=252
                resources: memory:df001000-df0010ff ioport:c000(size=8) ioport:c400(size=256)
           *-network
                description: Ethernet interface
                product: RTL-8100/8101L/8139 PCI Fast Ethernet Adapter
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: c
                bus info: pci@0000:02:0c.0
                logical name: eth0
                version: 10
                serial: [REMOVED]
                size: 100Mbit/s
                capacity: 100Mbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=[REMOVED] latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
                resources: irq:23 ioport:c800(size=256) memory:df000000-df0000ff memory:60000000-6000ffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller
                vendor: VIA Technologies, Inc.
                physical id: d
                bus info: pci@0000:02:0d.0
                version: 80
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=32 maxlatency=32
                resources: irq:23 memory:df002000-df0027ff ioport:cc00(size=128)
        *-isa
             description: ISA bridge
             product: 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide
             description: IDE interface
             product: 82801DB (ICH4) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:f000(size=16) memory:60100000-601003ff
        *-serial UNCLAIMED
             description: SMBus
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:500(size=32)
        *-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_intel8x0 latency=0
             resources: irq:17 ioport:e000(size=256) ioport:e400(size=64) memory:e0001000-e00011ff memory:e0002000-e00020ff
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: Maxtor 4R120L0
             vendor: Maxtor
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 1TU0
             serial: [REMOVED]
             size: 114GiB (122GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=b9a7fa04
           *-volume:0
                description: Windows FAT volume
                vendor: RECOVERY
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                version: FAT32
                serial: [REMOVED]
                size: 5359MiB
                capacity: 5359MiB
                capabilities: primary bootable fat initialized
                configuration: FATs=2 filesystem=fat
           *-volume:1
                description: Linux swap volume
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                version: 1
                serial: [REMOVED]
                size: 1526MiB
                capacity: 1526MiB
                capabilities: primary nofs swap initialized
                configuration: filesystem=swap pagesize=4096
           *-volume:2
                description: Extended partition
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                size: 107GiB
                capacity: 107GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   description: Linux filesystem partition
                   physical id: 5
                   logical name: /dev/sda5
                   logical name: /
                   capacity: 14GiB
                   configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered state=mounted
              *-logicalvolume:1
                   description: Linux filesystem partition
                   physical id: 6
                   logical name: /dev/sda6
                   logical name: /home
                   capacity: 93GiB
                   configuration: mount.fstype=ext4 mount.options=rw,relatime,data=ordered state=mounted
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-cdrom:0
             description: DVD reader
             product: DVD+RW MP5240A
             vendor: RICOH
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: 1.11
             serial: [REMOVED]
             capabilities: removable audio cd-r cd-rw dvd
             configuration: ansiversion=5 status=nodisc
        *-cdrom:1
             description: DVD reader
             product: DVD-ROM GDR8162B
             vendor: HL-DT-ST
             physical id: 0.1.0
             bus info: scsi@1:0.1.0
             logical name: /dev/sr1
             version: 0019
             capabilities: removable audio dvd
             configuration: ansiversion=5 status=nodisc
     *-scsi:2
          physical id: 3
          bus info: usb@4:1
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdb
             configuration: sectorsize=512
        *-disk:1
             description: SCSI Disk
             physical id: 0.0.1
             bus info: scsi@2:0.0.1
             logical name: /dev/sdc
             configuration: sectorsize=512
        *-disk:2
             description: SCSI Disk
             physical id: 0.0.2
             bus info: scsi@2:0.0.2
             logical name: /dev/sdd
             configuration: sectorsize=512
        *-disk:3
             description: SCSI Disk
             physical id: 0.0.3
             bus info: scsi@2:0.0.3
             logical name: /dev/sde
             configuration: sectorsize=512
```

---

### Post by grahammechanical on 2016-02-19
I will point the finger at the video adapter. AGP is an earlier technology than PCI. The CPU is having to do a lot of the work. I am certain that none of the latest Nvidia drivers support that adapter which Nvidia lists under its legacy section.

When we install Lubuntu and tick the box to install third party software we get not only some third party audio & video codecs but also a proprietary video driver (Nvidia) but if there is any conflict we end up running some kind of fall back video mode.

I do not use Lubuntu so I cannot give you directions. Somewhere in system settings is a utility that might be called Additional Drivers. If we load that utility & are connected to the internet then after a short while it will offer us some proprietary video drivers to install.

But I am not sure if it will find any for that adapter. The Nvidia driver web site recommends Nvidia 100.14 for that adapter and that driver is very old. I am not sure if it is available. You can try to use the software centre to download an older Nvidia driver. It think it has Nvidia 96 & the Nvidia web site does say that driver 96.43.19 does support that adapter.

If after installing the system fails to load to a working desktop, then at the Grub boot menu select Advance options and then select a Linux kernel with recovery mode. At the recovery menu select Resume. That should get you to a working desktop.

Regards

---

### Post by mörgæs on 2016-02-19
Hi, welcome to the fora.

Agree, the graphics card is simply too weak. Drivers can't compensate for that.

> **nordic2 said:**
> ... seen people claiming to run a smooth system with even worse processor, memory and video card.

Links please...

I recommend that you try to find a faster graphics card.

---

### Post by nordic2 on 2016-02-19
> **grahammechanical said:**
> I will point the finger at the video adapter. AGP is an earlier technology than PCI. The CPU is having to do a lot of the work. I am certain that none of the latest Nvidia drivers support that adapter which Nvidia lists under its legacy section.

When we install Lubuntu and tick the box to install third party software we get not only some third party audio & video codecs but also a proprietary video driver (Nvidia) but if there is any conflict we end up running some kind of fall back video mode.

I do not use Lubuntu so I cannot give you directions. Somewhere in system settings is a utility that might be called Additional Drivers. If we load that utility & are connected to the internet then after a short while it will offer us some proprietary video drivers to install.

But I am not sure if it will find any for that adapter. The Nvidia driver web site recommends Nvidia 100.14 for that adapter and that driver is very old. I am not sure if it is available. You can try to use the software centre to download an older Nvidia driver. It think it has Nvidia 96 & the Nvidia web site does say that driver 96.43.19 does support that adapter.

If after installing the system fails to load to a working desktop, then at the Grub boot menu select Advance options and then select a Linux kernel with recovery mode. At the recovery menu select Resume. That should get you to a working desktop.

Regards

Thanks for the directions; I did some research on this and  apparently there is a driver available that supports this video card  ([http://www.nvidia.com/download/driverResults.aspx/48996/en-us](http://www.nvidia.com/download/driverResults.aspx/48996/en-us)) but  sadly it seems like it is not compatible with my version of xorg (I am  getting this error after installing the headers:  [https://devtalk.nvidia.com/default/topic/707443/unable-to-install-nvidia-driver-96-43-23-in-xubuntu-13-10-the-kernel-header-file-does-not-exist-/](https://devtalk.nvidia.com/default/topic/707443/unable-to-install-nvidia-driver-96-43-23-in-xubuntu-13-10-the-kernel-header-file-does-not-exist-/)).  I am thinking of changing to LXLE since apparently it runs an older  version of xorg and seems better than manually downgrading lubuntu's  xorg ([http://ubuntuforums.org/showthread.php?t=2258812](http://ubuntuforums.org/showthread.php?t=2258812)). Any other  options available are welcome.



> **mörgæs said:**
> Hi, welcome to the fora.

Agree, the graphics card is simply too weak. Drivers can't compensate for that.



Links please...

I recommend that you try to find a faster graphics card.


Thank you for the welcome; that was my general impression, it might well be the case that I was just generalizing from nothing solid (though I do think 1.5 gigs of ram is more than the norm and the Pentium 4 is cited in "Old hardware brought back to life" as the base from which you should not be worrying). You think that even if I get the right drivers this card is just not usable anymore?

---

### Post by mörgæs on 2016-02-20
The initial post in the Old Hardware thread links to advice especially for the MX 400 / 440 cards. I have not tried myself but maybe you can get some inspiration.

Please also notice the performance list to which I'm linking.

---

### Post by gordintoronto on 2016-02-20
More than eight years ago, I hauled an old computer (previously used by my son) out of the basement for my first try to use Linux. It ran Ubuntu just fine, and had very similar specs to your computer -- including the identical video card. I have run operating systems of the Ubuntu family ever since, although the computer failed after a few years.

However, there are limits to what you can expect from a 12-year-old computer. The memory is fine, but the performance is going to be slow, slow, slow.

---

### Post by nordic2 on 2016-02-21
> **mörgæs said:**
> The initial post in the Old Hardware thread links to advice especially for the MX 400 / 440 cards. I have not tried myself but maybe you can get some inspiration.

Please also notice the performance list to which I'm linking.

Do you mean this reply?: [http://ubuntuforums.org/showthread.php?t=2130640&page=11&p=13219687&viewfull=1#post13219687](http://ubuntuforums.org/showthread.php?t=2130640&page=11&p=13219687&viewfull=1#post13219687)

I don't know much about what is nouveau and how it interacts with the video card driver, so all I can do really is try that fix. I did and didn't really make any difference though. Thanks for the advice anyways.

I have just changed to LXLE and performance has improved significantly. Processor is still getting 100% pikes frequently when running anything (like update manager), but lagging has been reduced dramatically: it is slow, but usable. If I'm not running other things, I can actually watch a youtube video. Unless you think that this puts a lot of stress on a processor that is still good and with a little better graphics card could have a life of at least 2 years of **good** performance, I think I will settle with this. I don't want to spend money to update a computer if the CPU is going to be unusable in less than 2 years from now.

---

### Post by mörgæs on 2016-02-21
Good that you liked it. If it fulfills your needs then please mark the thread solved.

I don't think the CPU is going to be unusable. The problem is mainly the GPU.

I suggest that you begin using the Links2 browser. It takes some time to get familiar with (PgUp, PgDown and Ctrl+mouse are important) but it is worth the while.

---

