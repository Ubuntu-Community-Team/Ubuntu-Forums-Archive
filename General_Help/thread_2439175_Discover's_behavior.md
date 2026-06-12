---
title: "Discover's behavior"
date: 2020-03-24
forum: General Help
---

### Post by serviteccom on 2020-03-24
Thanks in advance for any helping, I installed Lubuntu 19.10, everything I've used so far works just fine, the only one exception is Discover, its visual interface seems to have problems, it gets stocked for some seconds, refreshing its visual interface is very complicated, the graphical transitions are very slow, what can a}I do to solve this problem? (I'll give you the detailed description of the machine in wich the OS was installed)




```
description: Desktop Computer
    product: CQ1-1405LA (QN673AA#ABM)
    vendor: Hewlett-Packard
    version: Chassis Version
    serial: 3CR1190S0M
    width: 64 bits
    capabilities: smbios-2.6 dmi-2.6 smp vsyscall32
    configuration: boot=normal chassis=desktop family=103C_53316J G=D sku=QN673AA#ABM uuid=808AB69F-467B-E011-A899-E06995A5F669
  *-core
       description: Motherboard
       product: 1598
       vendor: PEGATRON CORPORATION
       physical id: 0
       version: 1.01
       serial: 109791830000926
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 6.08
          date: 03/18/2011
          size: 64KiB
          capacity: 1MiB
          capabilities: isa pci pnp upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Atom(TM) CPU D525   @ 1.80GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Atom(TM) CPU D525   @ 1.80GHz
          slot: CPU 1
          size: 1800MHz
          capacity: 1900MHz
          width: 64 bits
          clock: 200MHz
          capabilities: lm fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl cpuid aperfmperf pni dtes64 monitor ds_cpl tm2 ssse3 cx16 xtpr pdcm movbe lahf_lm dtherm
          configuration: cores=2 enabledcores=2 threads=4
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 48KiB
             capacity: 48KiB
             capabilities: internal write-back data
             configuration: level=1
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: internal write-back unified
             configuration: level=2
     *-memory
          description: System Memory
          physical id: a
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: SODIMM DDR3 Synchronous 800 MHz (1,2 ns)
             product: M471B5773DH0-CK0
             vendor: Samsung
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:1
             description: SODIMM DDR3 Synchronous 800 MHz (1,2 ns)
             product: 8JSF25664HZ-1G4D1
             vendor: Micron Technology
             physical id: 1
             serial: SerNum1
             slot: DIMM1
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
     *-pci
          description: Host bridge
          product: Atom Processor D4xx/D5xx/N4xx/N5xx DMI Bridge
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
        *-display:0
             description: VGA compatible controller
             product: Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:fe980000-fe9fffff ioport:dc00(size=8) memory:e0000000-efffffff memory:fe800000-fe8fffff memory:c0000-dffff
        *-display:1 UNCLAIMED
             description: Display controller
             product: Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:fe780000-fe7fffff
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
             resources: irq:26 memory:fe978000-fe97bfff
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
             resources: irq:24 ioport:e000(size=4096) memory:fea00000-feafffff ioport:f4000000(size=2097152)
           *-network
                description: Ethernet interface
                product: AR8132 Fast Ethernet
                vendor: Qualcomm Atheros
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: enp1s0
                version: c0
                serial: e0:69:95:a5:f6:69
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.1-NAPI latency=0 link=no multicast=yes port=twisted pair
                resources: irq:27 memory:feac0000-feafffff ioport:ec00(size=128)
        *-pci:1
             description: PCI bridge
             product: NM10/ICH7 Family PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:1000(size=4096) memory:feb00000-febfffff ioport:f4200000(size=2097152)
           *-network
                description: Wireless interface
                product: RT5390 Wireless 802.11n 1T/1R PCIe
                vendor: Ralink corp.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlp2s0
                version: 00
                serial: ac:81:12:76:fa:41
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rt2800pci driverversion=5.3.0-42-generic firmware=0.40 ip=192.168.1.13 latency=0 link=yes multicast=yes wireless=IEEE 802.11
                resources: irq:17 memory:febf0000-febfffff
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
             resources: irq:23 ioport:d880(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 5.3.0-42-generic uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 5.03
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
             resources: irq:19 ioport:d800(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 5.3.0-42-generic uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 5.03
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
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
             resources: irq:18 ioport:d480(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 5.3.0-42-generic uhci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 5.03
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
              *-usb:0
                   description: Keyboard
                   product: CASUE USB Keyboard
                   vendor: CASUE
                   physical id: 1
                   bus info: usb@4:1
                   version: 0.01
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=100mA speed=1Mbit/s
              *-usb:1
                   description: Mouse
                   product: Wireless Receiver
                   vendor: Telink
                   physical id: 2
                   bus info: usb@4:2
                   version: 1.00
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=50mA speed=12Mbit/s
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
             resources: irq:16 ioport:d400(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 5.3.0-42-generic uhci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 5.03
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
             resources: irq:23 memory:fe977c00-fe977fff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 5.3.0-42-generic ehci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 5.03
                capabilities: usb-2.00
                configuration: driver=hub slots=8 speed=480Mbit/s
              *-usb
                   description: Mass storage device
                   product: mSATA Wire
                   vendor: Apricorn
                   physical id: 7
                   bus info: usb@1:7
                   logical name: scsi2
                   version: 1.00
                   serial: 1234567891E9
                   capabilities: usb-2.10 scsi emulated scsi-host
                   configuration: driver=usb-storage maxpower=100mA speed=480Mbit/s
                 *-disk
                      description: SCSI Disk
                      product: 2105
                      vendor: ASMT
                      physical id: 0.0.0
                      bus info: scsi@2:0.0.0
                      logical name: /dev/sdb
                      version: 0
                      serial: 9E1987654321
                      size: 238GiB (256GB)
                      capabilities: partitioned partitioned:dos
                      configuration: ansiversion=6 logicalsectorsize=512 sectorsize=512 signature=56760700
                    *-volume:0
                         description: Windows NTFS volume
                         physical id: 1
                         bus info: scsi@2:0.0.0,1
                         logical name: /dev/sdb1
                         logical name: /media/laboratory3/Reservado para el sistema
                         version: 3.1
                         serial: 04cba620-388f-1d49-b9ce-bdd268fce927
                         size: 98MiB
                         capacity: 100MiB
                         capabilities: primary ntfs initialized
                         configuration: clustersize=4096 created=2016-03-23 06:40:09 filesystem=ntfs label=Reservado para el sistema mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 state=mounted
                    *-volume:1
                         description: Windows NTFS volume
                         physical id: 2
                         bus info: scsi@2:0.0.0,2
                         logical name: /dev/sdb2
                         logical name: /media/laboratory3/640E28D50E28A1D2
                         version: 3.1
                         serial: ec938dad-e793-4b4f-b33a-11ed60b5b812
                         size: 238GiB
                         capacity: 238GiB
                         capabilities: primary bootable ntfs initialized
                         configuration: clustersize=4096 created=2016-03-23 06:40:16 filesystem=ntfs mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 state=mounted
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
        *-isa
             description: ISA bridge
             product: NM10 Family LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide
             description: IDE interface
             product: NM10/ICH7 Family SATA Controller [IDE mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm isa_compat_mode pci_native_mode bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ff90(size=16) memory:f4400000-f44003ff
           *-disk
                description: ATA Disk
                product: Hitachi HDS72105
                vendor: Hitachi
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: A3GH
                serial: JP1570HR1MNWAK
                size: 465GiB (500GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=190f8193
              *-volume
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 45c5def0-6d0c-493a-89d1-8052bebcc667
                   size: 465GiB
                   capacity: 465GiB
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover 64bit extents ext4 ext2 initialized
                   configuration: created=2020-03-22 14:01:16 filesystem=ext4 lastmountpoint=/ modified=2020-03-22 17:43:57 mount.fstype=ext4 mount.options=rw,relatime mounted=2020-03-22 17:44:03 state=mounted
           *-cdrom
                description: DVD-RAM writer
                product: DVD A  DS8A5LH
                vendor: hp
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/sr0
                version: 1HD7
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-serial
             description: SMBus
             product: NM10/ICH7 Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: driver=i801_smbus latency=0
             resources: irq:19 ioport:400(size=32)
     *-pnp00:00
          product: PnP device PNP0c01
          physical id: 1
          capabilities: pnp
          configuration: driver=system
     *-pnp00:01
          product: PnP device PNP0b00
          physical id: 2
          capabilities: pnp
          configuration: driver=rtc_cmos
     *-pnp00:02
          product: PnP device PNP0c02
          physical id: 3
          capabilities: pnp
          configuration: driver=system
     *-pnp00:03
          product: PnP device PNP0c02
          physical id: 5
          capabilities: pnp
          configuration: driver=system
     *-pnp00:04
          product: PnP device PNP0c02
          physical id: 6
          capabilities: pnp
          configuration: driver=system
     *-pnp00:05
          product: PnP device PNP0c02
          physical id: 7
          capabilities: pnp
          configuration: driver=system
     *-pnp00:06
          product: PnP device PNP0c02
          physical id: 8
          capabilities: pnp
          configuration: driver=system
     *-pnp00:07
          product: PnP device PNP0c01
          physical id: 9
          capabilities: pnp
          configuration: driver=system
  *-power UNCLAIMED
       product: Standard Efficiency
       physical id: 1
       version: 2.30
       capacity: 32768mWh
```

---

### Post by wildmanne39 on 2020-03-24
Hello and welcome to the forum.

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end, if you are editing a post to add code tags click the edit button then click the go advanced button, highlight the code then select the # symbol from the tool bar.

---

### Post by guiverc on 2020-03-24
I can't help much with `discover`, as I don't use it.  I think it's speed is mostly related to what is is, how it works, and how it was written. It's a nice program to have at times, but I rarely use it.

All I'm suggesting here is it's not your only choice.  Looking at the Lubuntu manual, another option is provided, eg. [https://manual.lubuntu.me/stable/4/Installing_Updating_and_Removing_Software.html](https://manual.lubuntu.me/stable/4/Installing_Updating_and_Removing_Software.html)


[LIST]
[*][Chapter 4.1 Discover Software Center]("https://manual.lubuntu.me/stable/4/4.1/discover.html")
[*][Chapter 4.2 Muon Package Manager]("https://manual.lubuntu.me/stable/4/4.2/muon.html")
[/LIST]

Muon isn't as pretty, and because it deals with packages, has many times the number of choices as it lists everything, so it can be somewhat confusing for newcomers (it lists packages available which may not be programs, but are libraries & other resources that `discover` hides from users). So in the early days for new users `discover` probably makes more sense, but I'd suggest trying `muon`.


Those aren't your only choices either, I prefer command, or if I need/want to search using an interactive program usually opt for `aptitude` (which is terminal based, and likely not most users tastes).

---

