---
title: "how to check what type of ram your computer has"
date: 2008-06-12
forum: General Help
---

### Post by constantgamer247 on 2008-06-12
hi, I am running ubuntu 7.10 and I added system monitors to my menu bar and noticed that my RAM is all most max-ed out just on desktop, it runs a few apps at a time fine (I have never tried to do any thing more)

but (this is my question) is there a some code or a line or some thing I can put in terminal to check exactly what type of ram it exactly?  I want to order from a new egg or tiger dirrect to save money but don't want to get the wrong one. 

I know there is only one ram chip on the motherboard (3 slots total so room for 2 more) and the colour is a mix of chrom and blue.

thx gabe

---

### Post by ibuclaw on 2008-06-12
There is a GUI app somewhere in the repositories that is very good for this.

But if you paste this one-liner into the terminal, it should give you the information you want.
```
sudo lshw | sed -n '/*-memory/,/*-pci/p' | head -n -1
```

In the meantime, I was look for that app.

Regards
Iain

---

### Post by constantgamer247 on 2008-06-12
thx, im at school now but i'll give it a whirl when I get home

---

### Post by constantgamer247 on 2008-06-12
*-memory             
          description: System Memory
          physical id: 24
          slot: System board or motherboard
          size: 512MB
          capacity: 3GB
        *-bank:0
             description: DIMM DRAM Synchronous [empty]
             physical id: 0
             slot: DDR 1
        *-bank:1
             description: DIMM DRAM Synchronous [empty]
             physical id: 1
             slot: DDR 2
        *-bank:2
             description: DIMM DRAM Synchronous
             physical id: 2
             slot: DDR 3
             size: 512MB
             width: 64 bits


thats what I got, i all ready knew that I have 512MB of ram, can someone plz tell me what kind of ram it is, or (this would be even better) can some one give me a link to a tigger dirrect web page or a new egg page with the ram I need to buy, 

thx gabe

---

### Post by ibuclaw on 2008-06-15
I am guessing by your thank-you that you've figured out what it is...

But, just incase.

It is a **DRAM** type of memory stick (also named **SDRAM**).

As you can see in the output. It tells you that you have 3 ports.
Two, of which are "**[empty]**".




To show you a comparison to my computer:
> 
     *-memory             
          description: System Memory
          physical id: 25
          slot: System board or motherboard
          size: 1GiB
        *-bank:0
             description: DIMM DDR Synchronous 333 MHz (3.0 ns)
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 512MiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:1
             description: DIMM DDR Synchronous 333 MHz (3.0 ns)
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
             size: 512MiB
             width: 64 bits
             clock: 333MHz (3.0ns)

My motherboard takes **DDR** Memory sticks...

Regards
Iain

---

### Post by krzysztofikus on 2012-06-19
When I type in "sudo lshw | sed -n '/*-memory/,/*-pci/p' | head -n -1", I get the following output:

> *-memory:0           
          description: System Memory
          physical id: 18
          slot: System board or motherboard
          size: 497MiB
        *-bank:0
             description: DIMM 200 MHz (5.0 ns) [empty]
             physical id: 0
             slot: A0
             width: 64 bits
             clock: 200MHz (5.0ns)
        *-bank:1
             description: DIMM 200 MHz (5.0 ns) [empty]
             physical id: 1
             slot: A1
             width: 64 bits
             clock: 200MHz (5.0ns)
        *-bank:2
             description: DIMM 200 MHz (5.0 ns) [empty]
             physical id: 2
             slot: A2
             width: 64 bits
             clock: 200MHz (5.0ns)
     *-memory:1 UNCLAIMED
          description: Memory controller
          product: CK804 Memory Controller
          vendor: NVIDIA Corporation
          physical id: 4
          bus info: pci@0000:00:00.0
          version: a3
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: CK804 ISA Bridge
          vendor: NVIDIA Corporation
          physical id: 1
          bus info: pci@0000:00:01.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
     *-serial
          description: SMBus
          product: CK804 SMBus
          vendor: NVIDIA Corporation
          physical id: 1.1
          bus info: pci@0000:00:01.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm cap_list
          configuration: driver=nForce2_smbus latency=0 maxlatency=1 mingnt=3
          resources: irq:10 ioport:ec00(size=32) ioport:1c00(size=64) ioport:1c40(size=64)
     *-usb:0
          description: USB controller
          product: CK804 USB Controller
          vendor: NVIDIA Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:23 memory:ea004000-ea004fff
     *-usb:1
          description: USB controller
          product: CK804 USB Controller
          vendor: NVIDIA Corporation
          physical id: 2.1
          bus info: pci@0000:00:02.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:22 memory:ea005000-ea0050ff
     *-multimedia
          description: Multimedia audio controller
          product: CK804 AC'97 Audio Controller
          vendor: NVIDIA Corporation
          physical id: 5
          bus info: pci@0000:00:04.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm bus_master cap_list
          configuration: driver=Intel ICH latency=0 maxlatency=5 mingnt=2
          resources: irq:22 ioport:b800(size=256) ioport:bc00(size=256) memory:ea000000-ea000fff
     *-ide:0
          description: IDE interface
          product: CK804 IDE
          vendor: NVIDIA Corporation
          physical id: 6
          bus info: pci@0000:00:06.0
          logical name: scsi0
          version: f2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list emulated
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
          resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:f000(size=16)
        *-cdrom:0
             description: CD-R/CD-RW writer
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/scd0
             logical name: /dev/sr0
             capabilities: audio cd-r cd-rw
             configuration: status=nodisc
        *-cdrom:1
             description: DVD reader
             product: DVD-ROM SD-M1212
             vendor: TOSHIBA
             physical id: 0.1.0
             bus info: scsi@0:0.1.0
             logical name: /dev/cdrom1
             logical name: /dev/dvd1
             logical name: /dev/scd1
             logical name: /dev/sr1
             version: 1R22
             capabilities: removable audio dvd
             configuration: ansiversion=5 status=nodisc
     *-ide:1
          description: IDE interface
          product: CK804 Serial ATA Controller
          vendor: NVIDIA Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          logical name: scsi3
          version: f3
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list emulated
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:21 ioport:9f0(size=8) ioport:bf0(size=4) ioport:970(size=8) ioport:b70(size=4) ioport:d000(size=16) memory:ea001000-ea001fff
        *-disk
             description: ATA Disk
             product: WDC WD1600JS-22M
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@3:0.0.0
             logical name: /dev/sda
             version: 02.0
             serial: WD-WMANM1633423
             size: 149GiB (160GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=b4cab4ca
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@3:0.0.0,1
                logical name: /dev/sda1
                logical name: /windows
                version: 3.1
                serial: c289d1d7-e57e-d147-b1fc-1f31c6a8a478
                size: 19GiB
                capacity: 19GiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2008-09-20 17:38:06 filesystem=ntfs mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@3:0.0.0,2
                logical name: /dev/sda2
                size: 129GiB
                capacity: 129GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   description: HPFS/NTFS partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 23GiB
              *-logicalvolume:1
                   description: Linux filesystem partition
                   physical id: 6
                   logical name: /dev/sda6
                   logical name: /
                   capacity: 41GiB
                   configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered state=mounted
              *-logicalvolume:2
                   description: HPFS/NTFS partition
                   physical id: 7
                   logical name: /dev/sda7
                   capacity: 65GiB
     *-ide:2
          description: IDE interface
          product: CK804 Serial ATA Controller
          vendor: NVIDIA Corporation
          physical id: 8
          bus info: pci@0000:00:08.0
          version: f3
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:20 ioport:9e0(size=8) ioport:be0(size=4) ioport:960(size=8) ioport:b60(size=4) ioport:e400(size=16) memory:ea002000-ea002fff

It seems as if my computer was not using any RAM, three slots are empty. Do I understand that correctly?

---

