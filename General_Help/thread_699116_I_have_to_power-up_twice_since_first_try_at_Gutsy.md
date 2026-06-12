---
title: "I have to power-up twice since first try at Gutsy"
date: 2008-02-17
forum: General Help
---

### Post by ricardisimo on 2008-02-17
I kind of doubt that there is any real causal relationship, but my troubles did in fact start the moment I tried upgrading to 7.10. Firstly, Gutsy never installed properly. I tried Ubuntu twice (once by upgrade and once fresh off LiveCD), and Kubuntu once, and all I could get was a frozen quasi-desktop or LiveCD desktop with no "Install" button. Fortunately Feisty could still reinstall every time, and here I am.

Secondly, the much bigger problem: Every single time, without exception, I have to power up, then shut down, and then power up again or else I don't get a display and no system beep. The drive light runs for a while like it's doing something, but nothing comes of it, and the keyboard doesn't seem to work either.

So then, after the second power up, I get this BIOS error message about "overclocking failed. Press F1 to enter setup, F2 to use defaults" or words to that effect. So far as I know, I'm not overclocking now and never have done so. I certainly wouldn't know how to do it even if I knew what it was. I press F2 and everything loads like normal... no issues as far as I can tell.

One odd detail: the American Megatrends website (the BIOS people) suggest unplugging your keyboard before powering up, so that you can read and jot down all of your BIOS specs and so accurately diagnose the problem. Well, I think that's a Windows thing, because it certainly didn't slow down or pause BIOS long enough for me to read anything. Quite the opposite - the "overclocking failed" warning went away. So, I thought that perhaps I had a bad keyboard (and keys were sticking, so it was time anyway) but no, it's still happening on a new set of keys.

Anyhow, here are some of my specs. I'd like to avoid buying a new motherboard, although I think the prospects look a bit dim.

```
:~$ sudo lshw
description: Desktop Computer
    product: To Be Filled By O.E.M.
    vendor: To Be Filled By O.E.M.
    version: To Be Filled By O.E.M.
    serial: To Be Filled By O.E.M.
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=desktop uuid=00020003-0004-0005-0006-000700080009
  *-core
       description: Motherboard
       product: P4P8X
       vendor: ASUSTek Computer Inc.
       physical id: 0
       version: Rev 1.xx
       serial: MB-1234567890
       slot: 
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 1006.007 (05/13/2003)
          size: 64KB
          capacity: 448KB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.40GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.2.9
          slot: CPU 1
          size: 2400MHz
          capacity: 3600MHz
          width: 32 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 8KB
             capacity: 8KB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 512KB
             capacity: 512KB
             capabilities: pipeline-burst internal varies unified
        *-cache:2 DISABLED
             description: L3 cache
             physical id: 7
             slot: L3-Cache
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
          description: System Memory
          physical id: 35
          slot: System board or motherboard
          size: 1GB
        *-bank:0
             description: DIMM SDRAM Synchronous
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 512MB
             width: 64 bits
        *-bank:1
             description: DIMM SDRAM Synchronous
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
             size: 256MB
             width: 64 bits
        *-bank:2
             description: DIMM SDRAM Synchronous
             product: PartNum2
             vendor: Manufacturer2
             physical id: 2
             serial: SerNum2
             slot: DIMM2
             size: 256MB
             width: 64 bits
        *-bank:3
             description: DIMM [empty]
             product: PartNum3
             vendor: Manufacturer3
             physical id: 3
             serial: SerNum3
             slot: DIMM3
     *-pci
          description: Host bridge
          product: 82865G/PE/P DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: f8000000
          bus info: pci@00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          resources: iomemory:f8000000-fbffffff
        *-pci:0
             description: PCI bridge
             product: 82865G/PE/P PCI to AGP Controller
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@00:01.0
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display:0
                description: VGA compatible controller
                product: RV280 [Radeon 9200 SE]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@01:00.0
                version: 01
                size: 128MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                configuration: latency=64 mingnt=8
                resources: iomemory:e8000000-efffffff ioport:c000-c0ff iomemory:fe9f0000-fe9fffff irq:18
           *-display:1 UNCLAIMED
                description: Display controller
                product: RV280 [Radeon 9200 SE] (Secondary)
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@01:00.1
                version: 01
                size: 128MB
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master cap_list
                configuration: latency=64 mingnt=8
                resources: iomemory:e0000000-e7ffffff iomemory:fe9e0000-fe9effff
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
             resources: ioport:ef00-ef1f irq:18
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
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
             resources: ioport:ef20-ef3f irq:19
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb
                   description: Keyboard
                   product: Logitech USB Keyboard
                   vendor: Logitech
                   physical id: 1
                   bus info: usb@2:1
                   version: 28.00
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=100mA speed=1.5MB/s
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
             resources: ioport:ef40-ef5f irq:20
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
             resources: ioport:ef80-ef9f irq:18
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
             resources: iomemory:febffc00-febfffff irq:21
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.20-16-generic ehci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=8 speed=480.0MB/s
              *-usb
                   description: Printer
                   product: Photosmart C5100 series
                   vendor: HP
                   physical id: 2
                   bus info: usb@5:2
                   logical name: scsi2
                   version: 1.00
                   serial: MY74PP604N04MK
                   capabilities: usb-2.00 bidirectional emulated scsi-host
                   configuration: driver=usb-storage maxpower=2mA speed=480.0MB/s
                 *-disk
                      description: SCSI Disk
                      product: Photosmart C5180
                      vendor: HP
                      physical id: 0.0.0
                      bus info: scsi@2:0.0.0
                      logical name: /dev/sdc
                      version: 1.00
                      capabilities: removable
                      configuration: ansiversion=2
                    *-disc
                         physical id: 0
                         logical name: /dev/sdc
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@00:1e.0
             version: c2
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-network:0
                description: Ethernet interface
                product: 3c940 10/100/1000Base-T [Marvell]
                vendor: 3Com Corporation
                physical id: 5
                bus info: pci@02:05.0
                logical name: eth0
                version: 12
                serial: 00:0c:6e:58:94:61
                size: 100MB/s
                capacity: 1GB/s
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=skge driverversion=1.9 duplex=full firmware=N/A ip=192.168.1.64 latency=64 link=yes maxlatency=31 mingnt=23 multicast=yes port=twisted pair speed=100MB/s
                resources: iomemory:feaf8000-feafbfff ioport:d800-d8ff irq:17
           *-communication
                description: Modem
                product: HSP MicroModem 56
                vendor: PCTel Inc
                physical id: 9
                bus info: pci@02:09.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: hayes_16750 cap_list
                configuration: driver=serial latency=0
                resources: ioport:df00-df3f irq:16
           *-network:1
                description: Wireless interface
                product: ACX 100 22Mbps Wireless Interface
                vendor: Texas Instruments
                physical id: b
                bus info: pci@02:0b.0
                logical name: wlan0
                version: 00
                serial: 00:40:05:52:8f:54
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=acx_pci latency=64 multicast=yes wireless=IEEE 802.11b+
                resources: ioport:df80-df9f iomemory:feafe000-feafefff iomemory:fead0000-feadffff irq:21
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
             resources: ioport:1f0-1f7 ioport:3f4-3f3 ioport:170-177 ioport:374-373 ioport:fc00-fc0f iomemory:50000000-500003ff irq:20
           *-disk:0
                description: SCSI Disk
                product: WDC WD800JB-00ET
                vendor: ATA
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 77.0
                serial: WD-WMAHL2892200
                size: 74GB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume:0
                   description: Linux filesystem partition
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   capacity: 71GB
                   capabilities: primary bootable
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 2957MB
                   capacity: 2957MB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 2957MB
                      capabilities: nofs
           *-disk:1
                description: SCSI Disk
                product: Hitachi HDT72503
                vendor: ATA
                physical id: 0.1.0
                bus info: scsi@0:0.1.0
                logical name: /dev/sdb
                version: V54O
                serial: VF1200R2CMK5JA
                size: 298GB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume
                   description: Linux filesystem partition
                   physical id: 1
                   bus info: scsi@0:0.1.0,1
                   logical name: /dev/sdb1
                   capacity: 298GB
                   capabilities: primary
           *-cdrom
                description: DVD reader
                product: COMBO LTC-48161H
                vendor: LITE-ON
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: KH0G
                capabilities: removable audio cd-r cd-rw dvd
                configuration: ansiversion=5
              *-disc
                   physical id: 0
                   logical name: /dev/cdrom
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
             resources: ioport:e800-e8ff ioport:ee80-eebf iomemory:febff800-febff9ff iomemory:febff400-febff4ff irq:22
```
Much and many thanks and praise to be heaped upon the kind soul who can assist me in my tribulations.

---

### Post by hyperair on 2008-02-17
I think the problem lies with your CMOS battery. It's getting weak. I've also got that same problem, but I think something's damaged in my motherboard such that the battery, when inserted, doesn't get into contact. So, when I remove the power cord from the socket, the clock and everything resets. This is not a problem of Ubuntu, but of your hardware. =\ Also, BIOS does not depend on your operating system in any way. Windows's behaviour cannot influence the BIOS.

---

### Post by ricardisimo on 2008-02-17
I had assumed that if it were something like a battery issue that the results would be a little more uneven. Instead it's extremely regular, being exactly twice that I have to power up each time, never once, never three times.

It also occurred to me since I posted that the bigger problem might not be the power-up detail after all, but rather the fact that, for some reason, nothing past Feisty will install on this computer. How can I determine what that's about, and if the two problems are related? Thanks again.

---

### Post by hyperair on 2008-02-18
It's not related. Try installing and running Windows and you'll see the problem persistent. The BIOS keeps having some improper CPU setting stored in for some reason or other, so every time you boot, it hangs your CPU. The second time round detects that it hung in the previous boot and so it reverts to the "emergency" or "default" BIOS settings, and alerts you that your CPU wasn't clocked properly or something of that sort. I think the problem is mainly to do with the PSU. Back in the last few months before my PSU blew (smoke came out), I had this problem. Now, I don't.

---

### Post by ricardisimo on 2008-02-18
So you think I might get away with just changing the battery? I would be in heaven. A million thanks.

---

### Post by hyperair on 2008-02-19
No guarantees. It might go as far as corruption in your BIOS chip.

---

### Post by Robbyx on 2008-02-19
I am also having the same problem and it unlikely that both of our batteries are flat. My board is relatively new. It is a MSI  P6N SLI.  It so happens I recently had trouble loading the bios and had to reset it with the battery cut off button on the board. I then had to redo the grub.

---

### Post by ricardisimo on 2008-02-20
> **Robbyx said:**
> I am also having the same problem and it unlikely that both of our batteries are flat. My board is relatively new. It is a MSI  P6N SLI.  It so happens I recently had trouble loading the bios and had to reset it with the battery cut off button on the board. I then had to redo the grub.

The null power-up is the new issue? Or was it what led to your resetting the battery, etc.?

Also, what are you running right now? Feisty, Gutsy, or some other?

---

