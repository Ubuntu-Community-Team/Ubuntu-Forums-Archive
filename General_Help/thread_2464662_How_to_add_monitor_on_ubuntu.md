---
title: "How to add monitor on ubuntu"
date: 2021-07-08
forum: General Help
---

### Post by tyrel05 on 2021-07-08
Good day I just bought an asus portable monitor and I have installed the display link driver but still doesn’t work when I go to settings. And under displays it only shows my laptop no option for join or mirror.

Laptop:
Packard Bell EasyNote TV43HC
with Ubuntu and windows dual boot
Portable Monitor:
Asus MB168B

monitor is connects with one end being USB(plugs into laptop) and other is the cable that is on a HDD external drive that funny looking one. The manual says to install display link driver which I did and the monitor works fine on windows and I installed the driver also on Ubuntu but still nothing when I go to display settings there isn’t an option for mirror or join

---

### Post by zircon_34 on 2021-07-08
You probably have a hybrid graphics intel/nvidia, if that is the case you need to enable the proprietary nvidia driver since the external monitor should run through nvidia.

---

### Post by mIk3_08 on 2021-07-08
In the System Setting then Display. there you can check if you have successfully added an extended monitor by applying the "detect display" and there you can configure it whether you select it as mirror display or extended display. This only works when you plugin via VGA port it will automatically display it. But in your case, you need some script to work on your monitor via USB port. This is not an ordinary plugin play thing. Always remember Linux Ubuntu is not a Microsoft Windows.

---

### Post by tyrel05 on 2021-07-08
It is an I3 with graphics that are in the cpu

---

### Post by tyrel05 on 2021-07-08
It is an I3 third gen with graphics on cpu

---

### Post by mIk3_08 on 2021-07-08
can you run this command to your terminal
```
sudo lshw
```
and
```
hostnamectl status
```
Then paste the result here in thread wrap with code. Thanks a lot.

---

### Post by tyrel05 on 2021-07-09
Code for sudo lshw

```
tyrelubuntu                 
    description: Notebook
    product: EasyNote TV43HC (EasyNote TV43HC_064B_V2.15)
    vendor: Packard Bell
    version: V2.15
    serial: NXC0PMF0043120E7991601
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 smp vsyscall32
    configuration: chassis=notebook family=Type1Family sku=EasyNote TV43HC_064B_V2.15 uuid=810F909C-89F8-11E2-9E12-20898483D87E
  *-core
       description: Motherboard
       product: VG50_HC_CR
       vendor: Packard Bell
       physical id: 0
       version: Type2 - Board Version
       serial: NBC0A11001312016301601
       slot: Type2 - Board Chassis Location
     *-firmware
          description: BIOS
          vendor: Insyde Corp.
          physical id: 0
          version: V2.15
          date: 03/11/2013
          size: 128KiB
          capacity: 3584KiB
          capabilities: pci upgrade shadowing cdboot bootselect edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video acpi usb biosbootspecification uefi
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i3-3120M CPU @ 2.50GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Core(TM) i3-3120M CPU @ 2.50GHz
          serial: To Be Filled By O.E.M.
          slot: U3E1
          size: 2207MHz
          capacity: 4GHz
          width: 64 bits
          clock: 100MHz
          capabilities: lm fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer xsave avx f16c lahf_lm cpuid_fault epb pti ssbd ibrs ibpb stibp tpr_shadow vnmi flexpriority ept vpid fsgsbase smep erms xsaveopt dtherm arat pln pts md_clear flush_l1d cpufreq
          configuration: cores=2 enabledcores=2 threads=4
        *-cache:0
             description: L1 cache
             physical id: b
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: internal write-through instruction
             configuration: level=1
        *-cache:1
             description: L2 cache
             physical id: c
             slot: L2 Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: internal write-through unified
             configuration: level=2
        *-cache:2
             description: L3 cache
             physical id: d
             slot: L3 Cache
             size: 3MiB
             capacity: 3MiB
             capabilities: internal write-back unified
             configuration: level=3
     *-cache
          description: L1 cache
          physical id: a
          slot: L1 Cache
          size: 32KiB
          capacity: 32KiB
          capabilities: internal write-through data
          configuration: level=1
     *-memory
          description: System Memory
          physical id: 1a
          slot: System board or motherboard
          size: 10GiB
        *-bank:0
             description: SODIMM DDR3 Synchronous 1600 MHz (0.6 ns)
             product: Maxm 8G-DDR3-204
             vendor: Unknown
             physical id: 0
             serial: 0000007C
             slot: DIMM0
             size: 8GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
        *-bank:1
             description: DIMM [empty]
             product: Empty
             vendor: Empty
             physical id: 1
             serial: Empty
             slot: DIMM1
        *-bank:2
             description: SODIMM DDR3 Synchronous 1600 MHz (0.6 ns)
             product: EBJ20UF8BDU0-GN-F
             vendor: ELPIDA
             physical id: 2
             serial: 05123CF9
             slot: DIMM1
             size: 2GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
        *-bank:3
             description: DIMM [empty]
             product: Empty
             vendor: Empty
             physical id: 3
             serial: Empty
             slot: DIMM3
     *-pci
          description: Host bridge
          product: 3rd Gen Core processor DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
          configuration: driver=ivb_uncore
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: 3rd Gen Core processor Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:28 memory:c0000000-c03fffff memory:b0000000-bfffffff ioport:2000(size=64) memory:c0000-dffff
        *-communication
             description: Communication controller
             product: 7 Series/C216 Chipset Family MEI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:27 memory:c0604000-c060400f
        *-usb:0
             description: USB controller
             product: 7 Series/C216 Chipset Family USB Enhanced Host Controller #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:16 memory:c0609000-c06093ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 5.8.0-59-generic ehci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 5.08
                capabilities: usb-2.00
                configuration: driver=hub slots=2 speed=480Mbit/s
              *-usb
                   description: USB hub
                   product: Integrated Rate Matching Hub
                   vendor: Intel Corp.
                   physical id: 1
                   bus info: usb@1:1
                   version: 0.00
                   capabilities: usb-2.00
                   configuration: driver=hub slots=6 speed=480Mbit/s
                 *-usb
                      description: Video
                      product: HD WebCam
                      vendor: HD WebCam
                      physical id: 3
                      bus info: usb@1:1.3
                      version: 13.07
                      capabilities: usb-2.00
                      configuration: driver=uvcvideo maxpower=500mA speed=480Mbit/s
        *-multimedia
             description: Audio device
             product: 7 Series/C216 Chipset Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:29 memory:c0600000-c0603fff
        *-pci:0
             description: PCI bridge
             product: 7 Series/C216 Chipset Family PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 memory:afb00000-afbfffff ioport:c0400000(size=1048576)
           *-network
                description: Ethernet interface
                product: NetLink BCM57785 Gigabit Ethernet PCIe
                vendor: Broadcom Inc. and subsidiaries
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: enp2s0f0
                version: 10
                serial: 20:89:84:83:d8:7e
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi msix pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=5.8.0-59-generic firmware=sb latency=0 link=no multicast=yes port=twisted pair
                resources: irq:16 memory:c0430000-c043ffff memory:c0440000-c044ffff memory:afb00000-afb007ff
           *-generic:0
                description: SD Host controller
                product: BCM57765/57785 SDXC/MMC Card Reader
                vendor: Broadcom Inc. and subsidiaries
                physical id: 0.1
                bus info: pci@0000:02:00.1
                version: 10
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=sdhci-pci latency=0
                resources: irq:17 memory:c0400000-c040ffff
           *-generic:1 UNCLAIMED
                description: System peripheral
                product: BCM57765/57785 MS Card Reader
                vendor: Broadcom Inc. and subsidiaries
                physical id: 0.2
                bus info: pci@0000:02:00.2
                version: 10
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: latency=0
                resources: memory:c0410000-c041ffff
           *-generic:2 UNCLAIMED
                description: System peripheral
                product: BCM57765/57785 xD-Picture Card Reader
                vendor: Broadcom Inc. and subsidiaries
                physical id: 0.3
                bus info: pci@0000:02:00.3
                version: 10
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: latency=0
                resources: memory:c0420000-c042ffff
        *-pci:1
             description: PCI bridge
             product: 7 Series/C210 Series Chipset Family PCI Express Root Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 memory:c0500000-c05fffff
           *-network
                description: Wireless interface
                product: BCM4313 802.11bgn Wireless Network Adapter
                vendor: Broadcom Inc. and subsidiaries
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlp3s0b1
                version: 01
                serial: f4:b7:e2:74:cc:e8
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=brcmsmac driverversion=5.8.0-59-generic firmware=610.812 ip=192.168.3.62 latency=0 link=yes multicast=yes wireless=IEEE 802.11
                resources: irq:17 memory:c0500000-c0503fff
        *-usb:1
             description: USB controller
             product: 7 Series/C216 Chipset Family USB Enhanced Host Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:c0608000-c06083ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 5.8.0-59-generic ehci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 5.08
                capabilities: usb-2.00
                configuration: driver=hub slots=2 speed=480Mbit/s
              *-usb
                   description: USB hub
                   product: Integrated Rate Matching Hub
                   vendor: Intel Corp.
                   physical id: 1
                   bus info: usb@2:1
                   version: 0.00
                   capabilities: usb-2.00
                   configuration: driver=hub slots=8 speed=480Mbit/s
                 *-usb UNCLAIMED
                      description: Generic USB device
                      product: MB168B
                      vendor: DisplayLink
                      physical id: 3
                      bus info: usb@2:1.3
                      version: 32.11
                      serial: L9LMTF010567
                      capabilities: usb-2.10
                      configuration: maxpower=500mA speed=480Mbit/s
        *-isa
             description: ISA bridge
             product: HM77 Express Chipset LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-sata
             description: SATA controller
             product: 7 Series Chipset Family 6-port SATA Controller [AHCI mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: sata msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:26 ioport:2088(size=8) ioport:2094(size=4) ioport:2080(size=8) ioport:2090(size=4) ioport:2060(size=32) memory:c0607000-c06077ff
        *-serial
             description: SMBus
             product: 7 Series/C216 Chipset Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 04
             width: 64 bits
             clock: 33MHz
             configuration: driver=i801_smbus latency=0
             resources: irq:19 memory:c0605000-c06050ff ioport:2040(size=32)
     *-pnp00:00
          product: PnP device MSF0001
          physical id: 1
          capabilities: pnp
          configuration: driver=i8042 kbd
     *-pnp00:01
          product: PnP device ETD0500
          physical id: 2
          capabilities: pnp
          configuration: driver=i8042 aux
     *-pnp00:02
          product: PnP device PNP0c02
          physical id: 3
          capabilities: pnp
          configuration: driver=system
     *-pnp00:03
          product: PnP device PNP0b00
          physical id: 5
          capabilities: pnp
          configuration: driver=rtc_cmos
     *-pnp00:04
          product: PnP device INT3f0d
          physical id: 6
          capabilities: pnp
          configuration: driver=system
     *-pnp00:05
          product: PnP device PNP0c02
          physical id: 7
          capabilities: pnp
          configuration: driver=system
     *-pnp00:06
          product: PnP device PNP0c01
          physical id: 8
          capabilities: pnp
          configuration: driver=system
     *-scsi:0
          physical id: 9
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: CT240BX500SSD1
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 041
             serial: 2105E4F258FC
             size: 223GiB (240GB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=aabf6250-0e7a-45d7-843c-ec25211a7ee6 logicalsectorsize=512 sectorsize=512
           *-volume:0 UNCLAIMED
                description: Windows FAT volume
                vendor: MSDOS5.0
                physical id: 1
                bus info: scsi@0:0.0.0,1
                version: FAT32
                serial: 90ec-bdb1
                size: 95MiB
                capacity: 99MiB
                capabilities: boot fat initialized
                configuration: FATs=2 filesystem=fat name=EFI system partition
           *-volume:1
                description: reserved partition
                vendor: Windows
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                serial: 35f1ecee-c87f-4bd8-aedb-600ed6e4fddf
                capacity: 15MiB
                capabilities: nofs
                configuration: name=Microsoft reserved partition
           *-volume:2
                description: Windows NTFS volume
                vendor: Windows
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                version: 3.1
                serial: e457c062-7ca6-144d-a816-9e092b2227f8
                size: 185GiB
                capacity: 185GiB
                capabilities: ntfs initialized
                configuration: clustersize=4096 created=2021-06-02 02:55:07 filesystem=ntfs name=Basic data partition state=clean
           *-volume:3
                description: Windows NTFS volume
                vendor: Windows
                physical id: 4
                bus info: scsi@0:0.0.0,4
                logical name: /dev/sda4
                version: 3.1
                serial: 3051-1669
                size: 496MiB
                capacity: 507MiB
                capabilities: boot precious ntfs initialized
                configuration: clustersize=4096 created=2021-06-02 02:00:37 filesystem=ntfs state=clean
           *-volume:4
                description: EXT4 volume
                vendor: Linux
                physical id: 5
                bus info: scsi@0:0.0.0,5
                logical name: /dev/sda5
                logical name: /
                version: 1.0
                serial: 44960d0f-e84b-4526-910a-f9d300eb1474
                size: 37GiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink recover 64bit extents ext4 ext2 initialized
                configuration: created=2021-06-06 15:13:34 filesystem=ext4 lastmountpoint=/ modified=2021-07-09 20:26:57 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro mounted=2021-07-09 20:26:57 state=mounted
     *-scsi:1
          physical id: b
          logical name: scsi2
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVD-RAM UJ8E1
             vendor: MATSHITA
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: 1.00
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc


```


code for hostnamectl status
```
   Static hostname: TyrelUbuntu
         Icon name: computer-laptop
           Chassis: laptop
        Machine ID: 2ff1af1d179f452dbf150e2caf5503bb
           Boot ID: e30af9aa4cec40d3bf7e507dcb6e673f
  Operating System: Ubuntu 20.04.2 LTS
            Kernel: Linux 5.8.0-59-generic
      Architecture: x86-64


```

---

### Post by mIk3_08 on 2021-07-15
In this case with you, Linux Ubuntu with some extended monitor in it via USB. You have to install an application with some displaylink driver on it that can run your USB monitor via Linux Ubuntu Operating System. 
This is very complicated here in Linux Ubuntu Operating System. Always remember Linux Ubuntu Operating System is not the same as MS Windows. If you want to push this through this case you have to follow what I said lately that you have
to install some application displaylink driver and the process is a little bit complicated, so Good Luck. Welcome to Linux Ubuntu World.

---

