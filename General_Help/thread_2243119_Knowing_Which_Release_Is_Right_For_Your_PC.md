---
title: "Knowing Which Release Is Right For Your PC"
date: 2014-09-06
forum: General Help
---

### Post by bigpappajohn1984 on 2014-09-06
A friend gave me a desktop PC with not Hard drive, so I thought i would just pop in a Ubuntu Install and let it roll.  Well i have tried both Ubuntu 14.04 and now Lubuntu 14.04 (this error is generated from Lubuntu) and once the install finishes I get a message that states
Ubuntu 14.04 has experienced an internal Error.  Then many many lines that mean nothing to me :( --- 

Question is, can this PC not support this version and I should revert to an older version?
Or is this just a driver issue that I can get the driver from the Internet?

What info should I provide so that you guys can help me troubleshoot?

EDIT ---
SYSTEM SPECS Are As Follows:
Processor: VIA Esther processor 1500 MH
Memory: 1479MB (257MB used)
Operating System: Ubuntu 14.04.1 LTS

---

### Post by uRock on 2014-09-06
Can you boot into a live session of Ubuntu or Lubuntu? If yes, then please run the following two commands so we can see what you're working with.```
lspci
lsusb
```Or. Open Settings, then Details, then take a screenshot and upload it here. Should look something like this.

Edit: I see you edited your post to include information while I was typing my post.

---

### Post by uRock on 2014-09-06
Can you restart and select the option to "Check disc for defects"

---

### Post by bigpappajohn1984 on 2014-09-06
Below are the requested logs, probably a lot more detailed than what I initially gave.
lspci
```

jo@jo:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. CN896/VN896/P4M900 I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Security Device
00:00.7 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. CN896/VN896/P4M900 PCI to PCI Bridge Controller (rev 80)
00:03.0 PCI bridge: VIA Technologies, Inc. CN896/VN896/P4M900 PCI to PCI Bridge Controller (rev 80)
00:0f.0 IDE interface: VIA Technologies, Inc. Device 5337 (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8237/8251 Ultra VLINK Controller
00:13.0 Host bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
01:00.0 VGA compatible controller: VIA Technologies, Inc. CN896/VN896/P4M900 [Chrome 9 HC] (rev 01)
04:04.0 USB controller: OPTi Inc. 82C861 (rev 10)
04:0e.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 8d)
80:01.0 Audio device: VIA Technologies, Inc. VT8237A/VT8251 HDA Controller (rev 10)

```

lsusb
```

jo@jo:~$ lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 004: ID 0458:0003 KYE Systems Corp. (Mouse Systems) Genius NetScroll+
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

---

### Post by uRock on 2014-09-06
From looking at your processor specs, you will want 32bit Lubuntu. [http://www.cpubenchmark.net/cpu.php?cpu=VIA+Esther+1500MHz](http://www.cpubenchmark.net/cpu.php?cpu=VIA+Esther+1500MHz)

---

### Post by bigpappajohn1984 on 2014-09-06
> **uRock said:**
> [COLOR=#000000]From looking at your processor specs, you will want 32bit Lubuntu. [/COLOR][http://www.cpubenchmark.net/cpu.php?...Esther+1500MHz]("http://www.cpubenchmark.net/cpu.php?cpu=VIA+Esther+1500MHz")

I believe that is what I set-up.  Filename is: lubuntu-14.04.1-desktop-i386.iso

I am checking the disc for errors now.

---

### Post by bigpappajohn1984 on 2014-09-06
> **bigpappajohn1984 said:**
> I am checking the disc for errors now.

And Check finished: no errors found.

---

### Post by grahammechanical on 2014-09-06
> [COLOR=#333333][FONT=Ubuntu]The vast majority of Pentium M and Celeron M CPUs are suitable for fakepae or forcepae and can work with PAE kernels. But some of these processors need a [/FONT][/COLOR][non-pae kernel]("https://help.ubuntu.com/community/9w")[COLOR=#333333][FONT=Ubuntu] also for new versions of Lubuntu. There are also other 'not too old' CPUs that lack PAE capability: Transmeta Crusoe and VIA processors around 1 GHz.[/FONT][/COLOR]

[https://help.ubuntu.com/community/Lubuntu-fake-PAE](https://help.ubuntu.com/community/Lubuntu-fake-PAE)

[https://help.ubuntu.com/community/9w](https://help.ubuntu.com/community/9w)

Those error messages are important in working out what might be wrong. The message that says that Ubuntu has experienced an internal error only comes after we have loaded into a desktop. Are you getting to a desktop? What driver are you thinking you need? We do not normally get drivers from the internet. Drivers are usually installed by the Linux kernel.

What graphic adapter does the machine have? If we install and leave unticked the box marked "Install third party software" then we get an open source video driver. If we tick the box we get a proprietary video driver. If one exists. 

Regards.

---

### Post by bigpappajohn1984 on 2014-09-06
> **grahammechanical said:**
> 
Those error messages are important in working out what might be wrong.

Regards.

Which specific 'more info' data from the list do you need?  It won't let me copy paste the whole lot, and I I attempted to take a screenshot but that didn't work either...

EDIT ---
I also see from the link below how to force PAE from a fresh install, I already have LUBUNTU installed is there a way to do this w/o a fresh install?

[https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Pentium_M_and_Celeron_M](https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Pentium_M_and_Celeron_M)

---

### Post by bigpappajohn1984 on 2014-09-06
How would I find which graphics adapter the machine has?


Yes,  I did check the box to install 3rd party software.

---

### Post by mörgæs on 2014-09-06
The easiest is to get a complete hardware list. Run
```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by bigpappajohn1984 on 2014-09-06
Below are the results of my 

lshw -sanitize command

```

computer
    description: Desktop Computer
    product: Everex IMPACT Series ()
    vendor: Everex Systems,Inc
    version: 1.x
    serial: [REMOVED]
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.1 smp
    configuration: boot=normal chassis=desktop cpus=1 uuid=[REMOVED]
  *-core
       description: Motherboard
       product: PC3500G
       vendor: iDOT Systems,Inc
       physical id: 0
       version: 1.x
       serial: [REMOVED]
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 6.00 PG
          date: 03/16/2007
          size: 128KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification netboot
     *-cpu
          description: CPU
          product: VIA Esther processor 1500MHz
          vendor: CentaurHauls
          physical id: 4
          bus info: cpu@0
          version: 6.10.9
          slot: VIA C7-D
          size: 1500MHz
          capacity: 1500MHz
          width: 32 bits
          clock: 100MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge cmov pat clflush acpi mmx fxsr sse sse2 tm nx pni rng rng_en ace ace_en ace2 ace2_en phe phe_en pmm pmm_en
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: Internal Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: External Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous external write-back
     *-memory
          description: System Memory
          physical id: 17
          slot: System board or motherboard
          size: 1536MiB
        *-bank:0
             description: DIMM DDR2
             physical id: 0
             slot: A0
             size: 512MiB
        *-bank:1
             description: DIMM DDR2
             physical id: 1
             slot: A1
             size: 1GiB
     *-pci:0
          description: Host bridge
          product: CN896/VN896/P4M900 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-via latency=8
          resources: irq:0 memory:d4000000-d7ffffff
        *-generic UNCLAIMED
             description: PIC
             product: CN896/VN896/P4M900 I/O APIC Interrupt Controller
             vendor: VIA Technologies, Inc.
             physical id: 0.5
             bus info: pci@0000:00:00.5
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: io_x_-apic bus_master
             configuration: latency=0
        *-pci:0
             description: PCI bridge
             product: VT8237/VX700 PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci pm normal_decode bus_master cap_list
             resources: ioport:b000(size=4096) memory:dd000000-deffffff memory:d8000000-dbffffff
           *-display UNCLAIMED
                description: VGA compatible controller
                product: CN896/VN896/P4M900 [Chrome 9 HC]
                vendor: VIA Technologies, Inc.
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 01
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 vga_controller bus_master cap_list
                configuration: latency=32 mingnt=2
                resources: memory:d8000000-dbffffff memory:dd000000-ddffffff memory:de000000-de00ffff
        *-pci:1
             description: PCI bridge
             product: CN896/VN896/P4M900 PCI to PCI Bridge Controller
             vendor: VIA Technologies, Inc.
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress pm msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:27 ioport:a000(size=4096) memory:dfb00000-dfbfffff ioport:dfe00000(size=1048576)
        *-pci:2
             description: PCI bridge
             product: CN896/VN896/P4M900 PCI to PCI Bridge Controller
             vendor: VIA Technologies, Inc.
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress pm msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:31 ioport:c000(size=4096) memory:dfd00000-dfdfffff ioport:dfc00000(size=1048576)
        *-ide:0
             description: IDE interface
             product: VIA Technologies, Inc.
             vendor: VIA Technologies, Inc.
             physical id: f
             bus info: pci@0000:00:0f.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=sata_via latency=32
             resources: irq:21 ioport:fc00(size=8) ioport:f800(size=4) ioport:f400(size=8) ioport:f000(size=4) ioport:ec00(size=16) ioport:e800(size=256)
        *-ide:1
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: f.1
             bus info: pci@0000:00:0f.1
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=pata_via latency=32
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:e400(size=16)
        *-usb:0
             description: USB controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@0000:00:10.0
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:20 ioport:e000(size=32)
        *-usb:1
             description: USB controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:22 ioport:dc00(size=32)
        *-usb:2
             description: USB controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.2
             bus info: pci@0000:00:10.2
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:21 ioport:d800(size=32)
        *-usb:3
             description: USB controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.3
             bus info: pci@0000:00:10.3
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:23 ioport:d400(size=32)
        *-usb:4
             description: USB controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 10.4
             bus info: pci@0000:00:10.4
             version: 86
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci-pci latency=32
             resources: irq:21 memory:dffff000-dffff0ff
        *-isa
             description: ISA bridge
             product: VT8237A PCI to ISA Bridge
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa pm cap_list
             configuration: latency=0
        *-pci:3
             description: PCI bridge
             product: VT8237A PCI to PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci ht subtractive_decode bus_master cap_list
             resources: ioport:9000(size=4096) memory:dfa00000-dfafffff ioport:df900000(size=1048576)
           *-usb
                description: USB controller
                product: 82C861
                vendor: OPTi Inc.
                physical id: 4
                bus info: pci@0000:04:04.0
                version: 10
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master
                configuration: driver=ohci-pci latency=32
                resources: irq:17 memory:dfaff000-dfafffff
           *-network
                description: Ethernet interface
                product: VT6102 [Rhine-II]
                vendor: VIA Technologies, Inc.
                physical id: e
                bus info: pci@0000:04:0e.0
                logical name: eth0
                version: 8d
                serial: [REMOVED]
                size: 100Mbit/s
                capacity: 100Mbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.5.1 duplex=full ip=[REMOVED] latency=32 link=yes maxlatency=8 mingnt=3 multicast=yes port=MII speed=100Mbit/s
                resources: irq:18 ioport:9c00(size=256) memory:dfafe000-dfafe0ff
     *-pci:1
          description: Host bridge
          product: CN896/VN896/P4M900 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 101
          bus info: pci@0000:00:00.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: CN896/VN896/P4M900 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 102
          bus info: pci@0000:00:00.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: CN896/VN896/P4M900 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 103
          bus info: pci@0000:00:00.3
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: CN896/VN896/P4M900 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 104
          bus info: pci@0000:00:00.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: CN896/VN896/P4M900 Security Device
          vendor: VIA Technologies, Inc.
          physical id: 105
          bus info: pci@0000:00:00.6
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: CN896/VN896/P4M900 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 106
          bus info: pci@0000:00:00.7
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: VT8237/8251 Ultra VLINK Controller
          vendor: VIA Technologies, Inc.
          physical id: 107
          bus info: pci@0000:00:11.7
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: latency=32
     *-pci:8
          description: Host bridge
          product: VT8237A Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 108
          bus info: pci@0000:00:13.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-multimedia
          description: Audio device
          product: VT8237A/VT8251 HDA Controller
          vendor: VIA Technologies, Inc.
          physical id: 1
          bus info: pci@0000:80:01.0
          version: 10
          width: 64 bits
          clock: 33MHz
          capabilities: pm msi pciexpress bus_master cap_list
          configuration: driver=snd_hda_intel latency=0
          resources: irq:17 memory:d3ffc000-d3ffffff
     *-scsi:0
          physical id: 2
          logical name: scsi2
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD800BD-22MR
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sda
             version: 10.0
             serial: [REMOVED]
             size: 74GiB (80GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=00042df5
           *-volume:0
                description: Linux filesystem partition
                vendor: Linux
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sda1
                logical name: /boot
                version: 1.0
                serial: [REMOVED]
                size: 243MiB
                capacity: 243MiB
                capabilities: primary bootable extended_attributes ext2 initialized
                configuration: filesystem=ext2 lastmountpoint=/boot modified=2014-09-06 14:51:11 mount.fstype=ext2 mount.options=rw,relatime mounted=2014-09-06 14:51:11 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@2:0.0.0,2
                logical name: /dev/sda2
                size: 74GiB
                capacity: 74GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux LVM Physical Volume partition
                   physical id: 5
                   logical name: /dev/sda5
                   serial: [REMOVED]
                   size: 74GiB
                   capacity: 74GiB
                   capabilities: multi lvm2
     *-scsi:1
          physical id: 3
          logical name: scsi3
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD5002AALX-0
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@3:0.0.0
             logical name: /dev/sdb
             version: 15.0
             serial: [REMOVED]
             size: 465GiB (500GB)
             configuration: ansiversion=5 sectorsize=512
     *-scsi:2
          physical id: 5
          bus info: usb@3:1
          logical name: scsi4
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdc
             configuration: sectorsize=512
        *-disk:1
             description: SCSI Disk
             physical id: 0.0.1
             bus info: scsi@4:0.0.1
             logical name: /dev/sdd
             configuration: sectorsize=512
        *-disk:2
             description: SCSI Disk
             physical id: 0.0.2
             bus info: scsi@4:0.0.2
             logical name: /dev/sde
             configuration: sectorsize=512
        *-disk:3
             description: SCSI Disk
             physical id: 0.0.3
             bus info: scsi@4:0.0.3
             logical name: /dev/sdf
             configuration: sectorsize=512



```

---

### Post by mörgæs on 2014-09-06
Please forget what has been said about PAE and additional graphical drivers. It does not apply to your hardware. 

There's not much you need to do. Just install, apply updates and remove old stuff once in a while with **sudo apt-get autoremove**, and you are good to go. If you happen to find a stronger graphics card you could consider swapping it.

---

### Post by bigpappajohn1984 on 2014-09-06
> **mörgæs said:**
> Please forget what has been said about PAE and additional graphical drivers. It does not apply to your hardware. 

There's not much you need to do. Just install, apply updates and remove old stuff once in a while with **sudo apt-get autoremove**, and you are good to go.

What is causing the error message when my desktop loads then?

[COLOR=#000000]Ubuntu 14.04 has experienced an internal Error.[/COLOR]

---

### Post by mörgæs on 2014-09-06
I hope you are running Lubuntu (fully updated) and not Ubuntu on this computer...?

---

### Post by bigpappajohn1984 on 2014-09-06
Correct, this is running Lubuntu.

EDIT ----
What will fix my issue - for example, I am unable to launch Synaptic Package Manger OR Software Updater.
This is the error I get trying to open Synaptic
```

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_trusty-backports_universe_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

```

Are things done in Lubuntu the same as they are Ubuntu? ---- for example, setting up FTP & SFTP?

Also -- if using the terminal I try
```

sudo apt-get install vsftpd

```

I get multiple errors
```

Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_trusty-backports_universe_il8n_Translation-en
E: The package lists or status file could not be parsed or opened

```

---

### Post by mörgæs on 2014-09-07
Old stuff, but some threads are valid regardless of age:
[http://ubuntuforums.org/showthread.php?t=863742](http://ubuntuforums.org/showthread.php?t=863742)

---

### Post by bigpappajohn1984 on 2014-09-07
> **mörgæs said:**
> Old stuff, but some threads are valid regardless of age:
[http://ubuntuforums.org/showthread.php?t=863742](http://ubuntuforums.org/showthread.php?t=863742)

I have attempted this twice and same result at the end both times
Ran this to remove the bad:
```

[COLOR=#000000]sudo rm /var/lib/apt/lists/* -vf
[/COLOR]
```
Then to get all everything up-to-date
```

[COLOR=#000000]sudo apt-get update
[/COLOR]
```[COLOR=#000000]

*Several packages fail when getting the updates and upon reboot error message is back.


EDIT ---
Could this be due to me checking during install the tickbox that stated something similar to 'allow 3rd party apps to be installed'[/COLOR]

---

### Post by mörgæs on 2014-09-08
Please run 
```
sudo apt-get update 
sudo apt-get dist-upgrade
```
and post the complete output.

---

### Post by bigpappajohn1984 on 2014-09-09
Sorry for the delay.  Attached are the terminal output for both of the commands requested to be run.[ATTACH]256296[/ATTACH][ATTACH]256297[/ATTACH]

---

### Post by mörgæs on 2014-09-09
You seem to have nothing but errors from this installation. If you don't have anything of value on the computer have you considered a new install? 

I suggest trying the [minimal ISO]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall") first, if it runs without errors you can add a GUI later.

---

### Post by bigpappajohn1984 on 2014-09-09
> **mörgæs said:**
> You seem to have nothing but errors from this installation. If you don't have anything of value on the computer have you considered a new install? 

I suggest trying the [minimal ISO]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall") first, if it runs without errors you can add a GUI later.

Ugh - nothing of value on it, but this install was a fresh install on a out of the box drive.

I'll try using the minimal ISO and see how that install fares -- if it fails - what options do I have?  Attempt to revert to an older Lubuntu version (prior to 14.04)?

EDIT ---
And it has been "Downloading Release files" for about 30 minutes now and is still holding at 0% -- there is active internet and an internet connection on this PC tho?

EDIT ----
One other edit -- still showing 0% round about an hour into things (maybe more maybe less) the only thing I can think that may (or may not) have caused the hiccup is I left the host name blank when asked as I was unsure what to put there. --- Could I possibly do a 'downgrade' from within Lubuntu via terminal?  If so, what would be the commands in order to do such?

---

### Post by mörgæs on 2014-09-10
Apparently you are getting network problems no matter what you do. Are you able to browse the web in a live boot?

---

### Post by bigpappajohn1984 on 2014-09-10
> **mörgæs said:**
> Apparently you are getting network problems no matter what you do. Are you able to browse the web in a live boot?

When I installed the full version it seemed to download updates/3rd party during install no issue.  I never actually attempted to browse the internet in that install, but I was able to get updates/ping sites/other IP's on my network.

One thing I did notice was that I had to manually turn on the connection each start-up, could this be what is affecting me this time?  Would it make it easier if I used a wireless card?

---

### Post by mörgæs on 2014-09-10
The commands in #19 must run with internet connection. Normally a wired one is easier to work with.

---

### Post by bigpappajohn1984 on 2014-09-10
> **mörgæs said:**
> The commands in #19 must run with internet connection. Normally a wired one is easier to work with.

Yes the commands in post #19 were run with an internet connection. (Wired)

---

### Post by mörgæs on 2014-09-10
Please run again and post the results in CODE tags (not as attached file).

---

### Post by bigpappajohn1984 on 2014-09-10
> **mörgæs said:**
> Please run again and post the results in CODE tags (not as attached file).

So I believe that everything is up and running, I installed first from the 'tiny' install you linked me to, and now I have the desktop environment up and running w/o error (best I can tell).

I am now trying to set a static IP - but if I run the below command
```

nm-tool

```
This is what I see
```

Device: eth0
Driver: via-rhine
State: unmanaged
Default: No
HW Address: 00:1A:4D:0A:65:B7

Capabilities:
Carrier Detect: Yes
Speed: 100 MB/s

Wired Properties:
Carrier: on

```

If I try this

```

nm-connection-editor

```

It shows no connections!?

---

### Post by mörgæs on 2014-09-11
If the installation is working then please mark the thread solved using 'Thread Tools'. 

I don't know why you would prefer a static IP in stead of DHCP, but if you want to change that please open a new thread in Networking.

---

