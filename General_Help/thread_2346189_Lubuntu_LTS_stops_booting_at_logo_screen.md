---
title: "Lubuntu LTS stops booting at logo screen"
date: 2016-12-12
forum: General Help
---

### Post by hiec2 on 2016-12-12
Hi,

I just registered because after days of googling I need help.  I've been running Lubuntu on an 8 year old Laptop for a while now. It worked great until a distribution update broke the boot process into the desktop environment.
[SIZE=3]
**The problem:**
My laptop does not boot into the graphical desktop envionment anymore. It just stays at the boot splash showing the lubuntu logo.[/SIZE]

**Observations:**
[LIST]
[*]I can log into the system using one of the shells accessible via CTRL-ALT-F1 and so on 
[*]Removing the splash and $vt_handoff boot parameters also gets me to a shell I can log into 
[*]My lightdm conf looks like this: 
/etc/lightdm/lightdm.conf.d/20-lubuntu.conf
```
[SeatDefaults]
user-session=Lubuntu
```
There is no greeter-session line. Is that normal for Lubuntu? 
[/LIST]

**History:**
This problem first appeared after a distribution upgrade, probably the one from 15.10 to 16.04. At first I hoped the automatic update to 16.04.1 would fix the problem, but it did not. Then I've tried to launch the Lubuntu desktop manually from the shell, but none of the many ways this might be done worked for me. I also looked for similar problems on the web and tried various solutions. I mostly stayed away from commands that would alter my system permanently though. Finally, I went through the opening post of this thread.

[B]Information about my system:
[/B]Laptop, about 8 years old
Intel CPU
VIA graphics
2GB of memory
Lubuntu 16.04.1

output from "lshw -sanitize > lshw.txt"
```
computer
    description: Computer
    product: Terra Mobile 2104
    vendor: Wortmann AG
    version: VT6363A
    serial: [REMOVED]
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: administrator_password=disabled boot=oem-specific cpus=2 frontpanel_password=unknown keyboard_password=unknown power-on_password=disabled uuid=[REMOVED]
  *-core
       description: Motherboard
       product: M660SR
       vendor: CLEVO Co.
       physical id: 0
       version: VT6363A
       serial: [REMOVED]
       slot: ï¿½FLOPPY
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies LTD
          physical id: 0
          version: 6.00
          date: 12/25/2007
          size: 98KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect edd int13floppynec int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: Intel(R) Pentium(R) Dual  CPU  T2330  @ 1.60GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.15.13
          serial: [REMOVED]
          slot: mPGA 479m
          size: 800MHz
          capacity: 3600MHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm cpufreq
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 16KiB
             capacity: 16KiB
             capabilities: asynchronous internal write-back
             configuration: level=1
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 1MiB
             capacity: 2MiB
             capabilities: burst external write-through
             configuration: level=2
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
     *-cache
          description: L3 cache
          physical id: 7
          slot: L3 Cache
          size: 1MiB
          capabilities: burst internal write-back
          configuration: level=3
     *-memory
          description: System Memory
          physical id: 23
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM DRAM Synchronous
             physical id: 0
             slot: M1
             size: 1GiB
             width: 64 bits
        *-bank:1
             description: DIMM DRAM Synchronous
             physical id: 1
             slot: M2
             size: 1GiB
             width: 64 bits
        *-bank:2
             description: DIMM DRAM Synchronous [empty]
             physical id: 2
             slot: M3
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.15.13
          serial: [REMOVED]
          size: 1600MHz
          capacity: 1600MHz
          capabilities: ht cpufreq
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             capabilities: logical
     *-pci:0
          description: Host bridge
          product: CN896/VN896/P4M900 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-via latency=32
          resources: irq:0 memory:c0000000-c7ffffff
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
             resources: memory:c9000000-c9ffffff memory:a0000000-bfffffff
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
                resources: memory:a0000000-bfffffff memory:c9000000-c9ffffff
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
             resources: irq:24 ioport:1000(size=4096) memory:80000000-801fffff ioport:80200000(size=2097152)
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
             resources: irq:25 ioport:5000(size=8192) memory:c8800000-c8ffffff ioport:c8000000(size=8388608)
        *-ide:0
             description: IDE interface
             product: VT8237A SATA 2-Port Controller
             vendor: VIA Technologies, Inc.
             physical id: f
             bus info: pci@0000:00:0f.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=sata_via latency=32
             resources: irq:21 ioport:4cb0(size=8) ioport:4ca4(size=4) ioport:4ca8(size=8) ioport:4ca0(size=4) ioport:4c80(size=16) ioport:4400(size=256)
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
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:4c90(size=16)
        *-usb:0
             description: USB controller
             product: VT82xx/62xx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@0000:00:10.0
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:20 ioport:4c00(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 4.4.0-22-generic uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 4.04
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-usb:1
             description: USB controller
             product: VT82xx/62xx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:22 ioport:4c20(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 4.4.0-22-generic uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 4.04
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-usb:2
             description: USB controller
             product: VT82xx/62xx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.2
             bus info: pci@0000:00:10.2
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:21 ioport:4c40(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 4.4.0-22-generic uhci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 4.04
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-usb:3
             description: USB controller
             product: VT82xx/62xx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.3
             bus info: pci@0000:00:10.3
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:23 ioport:4c60(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 4.4.0-22-generic uhci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 4.04
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
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
             resources: irq:21 memory:ca400000-ca4000ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.4.0-22-generic ehci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 4.04
                capabilities: usb-2.00
                configuration: driver=hub slots=8 speed=480Mbit/s
              *-usb:0
                   description: Mass storage device
                   product: DataTraveler 3.0
                   vendor: Kingston
                   physical id: 6
                   bus info: usb@1:6
                   logical name: scsi4
                   version: 1.00
                   serial: [REMOVED]
                   capabilities: usb-2.10 scsi emulated scsi-host
                   configuration: driver=usb-storage maxpower=300mA speed=480Mbit/s
                 *-disk
                      description: SCSI Disk
                      product: DataTraveler 3.0
                      vendor: Kingston
                      physical id: 0.0.0
                      bus info: scsi@4:0.0.0
                      logical name: /dev/sdb
                      version: PMAP
                      serial: [REMOVED]
                      size: 14GiB (16GB)
                      capabilities: removable
                      configuration: ansiversion=6 logicalsectorsize=512 sectorsize=512
                    *-medium
                         physical id: 0
                         logical name: /dev/sdb
                         size: 14GiB (16GB)
                         capabilities: partitioned partitioned:dos
                         configuration: signature=fc28dfdd
                       *-volume
                            description: Windows FAT volume
                            vendor: SYSLINUX
                            physical id: 1
                            logical name: /dev/sdb1
                            logical name: /media/gerald/usb
                            version: FAT32
                            serial: [REMOVED]
                            size: 14GiB
                            capacity: 14GiB
                            capabilities: primary bootable fat initialized
                            configuration: FATs=2 filesystem=fat label=MYLINUXLIVE mount.fstype=vfat mount.options=rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro state=mounted
              *-usb:1
                   description: Generic USB device
                   product: RTL8187B_WLAN_Adapter
                   vendor: Manufacturer_Realtek
                   physical id: 7
                   bus info: usb@1:7
                   version: 2.00
                   serial: [REMOVED]
                   capabilities: usb-2.00
                   configuration: driver=rtl8187 maxpower=500mA speed=480Mbit/s
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
        *-network
             description: Ethernet interface
             product: VT6102/VT6103 [Rhine-II]
             vendor: VIA Technologies, Inc.
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: eth0
             version: 7c
             serial: [REMOVED]
             size: 10Mbit/s
             capacity: 100Mbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.5.1 duplex=half latency=32 link=no maxlatency=8 mingnt=3 multicast=yes port=MII speed=10Mbit/s
             resources: irq:23 ioport:4800(size=256) memory:ca400400-ca4004ff
        *-pci:3
             description: PCI bridge
             product: VT8237A Host Bridge
             vendor: VIA Technologies, Inc.
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci ht normal_decode bus_master cap_list
             resources: memory:ca000000-ca0fffff
           *-multimedia
                description: Audio device
                product: VT8237A/VT8251 HDA Controller
                vendor: VIA Technologies, Inc.
                physical id: 1
                bus info: pci@0000:05:01.0
                version: 10
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:17 memory:ca000000-ca003fff
        *-pci:4
             description: PCI bridge
             product: VT8237A PCI to PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci ht subtractive_decode bus_master cap_list
             resources: memory:ca100000-ca1fffff
           *-memory:0 UNCLAIMED
                description: FLASH memory
                product: ENE PCI Memory Stick Card Reader Controller
                vendor: ENE Technology Inc
                physical id: 4
                bus info: pci@0000:06:04.0
                version: 00
                width: 32 bits
                clock: 33MHz (30.3ns)
                capabilities: pm bus_master cap_list
                configuration: latency=32 maxlatency=4 mingnt=1
                resources: memory:ca100200-ca10027f
           *-generic
                description: SD Host controller
                product: ENE PCI SmartMedia / xD Card Reader Controller
                vendor: ENE Technology Inc
                physical id: 4.1
                bus info: pci@0000:06:04.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci-pci latency=32 maxlatency=72 mingnt=32
                resources: irq:17 memory:ca100000-ca1000ff
           *-memory:1
                description: FLASH memory
                product: ENE PCI Secure Digital / MMC Card Reader Controller
                vendor: ENE Technology Inc
                physical id: 4.3
                bus info: pci@0000:06:04.3
                version: 00
                width: 32 bits
                clock: 33MHz (30.3ns)
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci-pci latency=0 maxlatency=72 mingnt=32
                resources: irq:17 memory:ca100100-ca1001ff
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
     *-scsi:0
          physical id: 2
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: FUJITSU MHY2160B
             vendor: Fujitsu
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 000B
             serial: [REMOVED]
             size: 149GiB (160GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=8d084583
           *-volume:0
                description: EXT3 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: [REMOVED]
                size: 23GiB
                capacity: 23GiB
                capabilities: primary bootable journaled extended_attributes large_files ext3 ext2 initialized
                configuration: created=2015-12-25 11:14:15 filesystem=ext3 lastmountpoint=/ modified=2016-12-12 14:23:10 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2016-12-12 13:20:27 state=mounted
           *-volume:1
                description: Linux swap volume
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                version: 1
                serial: [REMOVED]
                size: 3906MiB
                capacity: 3906MiB
                capabilities: primary nofs swap initialized
                configuration: filesystem=swap pagesize=4096
           *-volume:2
                description: Extended partition
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                size: 121GiB
                capacity: 121GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux filesystem partition
                   physical id: 5
                   logical name: /dev/sda5
                   logical name: /mnt/data
                   capacity: 121GiB
                   configuration: mount.fstype=ext3 mount.options=rw,relatime,data=ordered state=mounted
     *-scsi:1
          physical id: 3
          logical name: scsi2
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVD A  DS8A1P
             vendor: Slimtype
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: CX17
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
  *-remoteaccess UNCLAIMED
       vendor: VIA
       physical id: 1
       capabilities: inbound
  *-network
       description: Wireless interface
       physical id: 2
       bus info: usb@1:7
       logical name: wlan0
       serial: [REMOVED]
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8187 driverversion=4.4.0-22-generic firmware=N/A ip=[REMOVED] link=yes multicast=yes wireless=IEEE 802.11bg

```


Now I'm hoping one of the Ubuntu wizards or Bash Fu masters here in the  forum will help me solve or work around the problem. Thank you!


Oh, and please tell me if I should open a new thread (in General Help?) instead of posting here if you think that would be more appropriate.

---

### Post by howefield on 2016-12-12
Post moved to own thread, much better than tacking on to a somewhat unrelated and old thread.

---

### Post by hiec2 on 2016-12-13
Thank you

---

