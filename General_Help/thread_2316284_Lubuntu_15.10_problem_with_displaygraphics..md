---
title: "Lubuntu 15.10 problem with display/graphics."
date: 2016-03-06
forum: General Help
---

### Post by jbcooper on 2016-03-06
Dear all

I have upgraded from Lubuntu 15.04 to 15.10 and I now seem to have a reccurring problem with the screen on my laptop which goes blank and then the display comes back in a few seconds but it is very corrupt!!

[ATTACH=CONFIG]267681[/ATTACH]

This happens after about an hour and then I reboot and it happens again and keeps happening until I have to give-up and do something else!! 

Help needed very much please.... I should say that I tried the installation several times from USB because it appeared to hang, but whenever I re-booted it seemed to be OK, apart from the above problem!! I looked at the Lubuntu webpage and it said that this installation problem was known about and shouldn't be a problem - you just reboot and the system is OK. Any help and advice much appreciated. Should I try another re-install, etc, etc??

I think it is something to do with the display settings because if I try to change the screen resolution, the screen goes back to normal.

---

### Post by trag on 2016-03-08
The timing of this problem with your upgrade maybe just coincidental, is it possible to swap in a different stick of Ram?, it is a bit of a pain to do this but your screen shot  and symptoms are weirdly similar to an issue I once had.  Out of desperation I swapped in some Ram from another machine and everything went back to normal. In addition overheating comes to mind as a possible cause, everything running nice and cool?
good luck
Tragic

---

### Post by mörgæs on 2016-03-08
In stead if removing the memory sticks one can run memtest from the boot menu.

---

### Post by jbcooper on 2016-03-08
Thanks both for the replies. Some more tests done and it seems to be linked with one of the programs which causes the graphics to go wonky when I do other screen-intensive activities. Looks like a sticky one to solve so I may just slow down and see if it gets better!!

---

### Post by mörgæs on 2016-03-09
Let's see more of the hardware. Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by jbcooper on 2016-03-09
Hello again, thank you for your help with this. 

```
computer
    description: Computer
    width: 64 bits
    capabilities: smbios-2.4 vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 1992MiB
     *-cpu
          product: Intel(R) Core(TM)2 CPU         U7600  @ 1.20GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          size: 1200MHz
          capacity: 1200MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm tpr_shadow cpufreq
     *-pci
          description: Host bridge
          product: Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:ffc80000-ffcfffff ioport:cff8(size=8) memory:e0000000-efffffff memory:ffc40000-ffc7ffff
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0
             resources: memory:8c000000-8c07ffff
        *-multimedia
             description: Audio device
             product: NM10/ICH7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:29 memory:8c080000-8c083fff
        *-pci:0
             description: PCI bridge
             product: NM10/ICH7 Family PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:b000(size=4096) memory:ff900000-ff9fffff
           *-network
                description: Ethernet interface
                product: 82573L Gigabit Ethernet Controller
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: enp1s0
                version: 00
                serial: [REMOVED]
                capacity: 1Gbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.5-k firmware=0.5-1 latency=0 link=no multicast=yes port=twisted pair
                resources: irq:27 memory:ff9e0000-ff9fffff ioport:bfe0(size=32)
        *-pci:1
             description: PCI bridge
             product: NM10/ICH7 Family PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 memory:ff800000-ff8fffff
           *-network
                description: Wireless interface
                product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlp2s0
                version: 61
                serial: [REMOVED]
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwl4965 driverversion=4.2.0-16-generic firmware=228.61.2.24 ip=[REMOVED] latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
                resources: irq:28 memory:ff8fe000-ff8fffff
        *-usb:0
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:afe0(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 4.2.0-16-generic uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 4.02
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-usb:1
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:af80(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 4.2.0-16-generic uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 4.02
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
              *-usb UNCLAIMED
                   description: Generic USB device
                   product: Fingerprint Sensor
                   vendor: AuthenTec, Inc.
                   physical id: 1
                   bus info: usb@3:1
                   version: c.10
                   capabilities: usb-1.10
                   configuration: maxpower=100mA speed=12Mbit/s
        *-usb:2
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:af60(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 4.2.0-16-generic uhci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 4.02
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
              *-usb
                   description: Mouse
                   product: PS/2+USB Mouse
                   vendor: Elan Microelectronics Corp.
                   physical id: 1
                   bus info: usb@4:1
                   version: 22.90
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=100mA speed=2Mbit/s
        *-usb:3
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:af40(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 4.2.0-16-generic uhci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 4.02
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-usb:4
             description: USB controller
             product: NM10/ICH7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:ffc3fc00-ffc3ffff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.2.0-16-generic ehci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 4.02
                capabilities: usb-2.00
                configuration: driver=hub slots=8 speed=480Mbit/s
              *-usb
                   description: Mass storage device
                   product: Optical Drive Controller
                   vendor: TOSHIBA
                   physical id: 4
                   bus info: usb@1:4
                   logical name: scsi4
                   version: 0.00
                   capabilities: usb-2.00 emulated scsi-host
                   configuration: driver=usb-storage maxpower=2mA speed=480Mbit/s
                 *-cdrom
                      description: DVD-RAM writer
                      product: DVD-RAM UJ-844S
                      vendor: MATSHITA
                      physical id: 0.0.0
                      bus info: scsi@4:0.0.0
                      logical name: /dev/cdrom
                      logical name: /dev/cdrw
                      logical name: /dev/dvd
                      logical name: /dev/dvdrw
                      logical name: /dev/sr0
                      version: 1.10
                      capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                      configuration: status=nodisc
        *-pci:2
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e2
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: ioport:1000(size=4096) memory:80000000-8bffffff
           *-pcmcia
                description: CardBus bridge
                product: PCIxx12 Cardbus Controller
                vendor: Texas Instruments
                physical id: b
                bus info: pci@0000:03:0b.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: irq:21 memory:80000000-80000fff ioport:1000(size=256) ioport:1400(size=256) memory:84000000-87ffffff memory:88000000-8bffffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: PCIxx12 OHCI Compliant IEEE 1394 Host Controller
                vendor: Texas Instruments
                physical id: b.1
                bus info: pci@0000:03:0b.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=64 maxlatency=4 mingnt=2
                resources: irq:20 memory:80001000-800017ff memory:80004000-80007fff
           *-generic
                description: SD Host controller
                product: PCIxx12 SDA Standard Compliant SD Host Controller
                vendor: Texas Instruments
                physical id: b.3
                bus info: pci@0000:03:0b.3
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci-pci latency=64 maxlatency=4 mingnt=7
                resources: irq:23 memory:80001800-800018ff
        *-isa
             description: ISA bridge
             product: 82801GBM (ICH7-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-storage
             description: SATA controller
             product: 82801GBM/GHM (ICH7-M Family) SATA Controller [AHCI mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:26 ioport:af38(size=8) ioport:af34(size=4) ioport:af28(size=8) ioport:af24(size=4) ioport:af10(size=16) memory:ffc3f800-ffc3fbff
     *-scsi
          physical id: 2
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD1600BEVT-7
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 1A11
             serial: [REMOVED]
             size: 149GiB (160GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=0002a51f
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                version: 1.0
                serial: [REMOVED]
                size: 74GiB
                capacity: 74GiB
                capabilities: primary journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuration: created=2015-12-08 02:25:58 filesystem=ext4 lastmountpoint=/ modified=2016-02-26 22:03:16 mounted=2016-02-26 22:03:16 state=clean
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 74GiB
                capacity: 74GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 2037MiB
                   capabilities: nofs
              *-logicalvolume:1
                   description: Linux filesystem partition
                   physical id: 6
                   logical name: /dev/sda6
                   logical name: /
                   capacity: 72GiB
                   capabilities: bootable
                   configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered state=mounted
```

---

### Post by mörgæs on 2016-03-09
If you click the link in my signature and search on the page for 'UXA' you will see instructions about changing graphics mode. Try this and reboot.

---

### Post by jbcooper on 2016-03-09
Great!! That seems to have cracked it. I will let you know if I have any more problems, but the UXA thing seems to have solved it. I am sure I would have been able to break it by now, but it seems to be working perfectly. Pretty sure its fully sorted now - many thanks.

---

