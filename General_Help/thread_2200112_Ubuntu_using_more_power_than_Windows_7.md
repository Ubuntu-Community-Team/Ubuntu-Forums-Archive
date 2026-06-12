---
title: "Ubuntu using more power than Windows 7?"
date: 2014-01-17
forum: General Help
---

### Post by marc13 on 2014-01-17
It seems that using Ubuntu 12.04 is sucking the power off my laptop faster than when I was using Windows. Are there any reasons for this or am I just plain wrong? 

If it is using more power, then are there ways to make the power usage less (apart from the obvious screen brightness/overall sound volume and usage)? Maybe an application is using more power than it should, and its specifically doing that on Ubuntu?

---

### Post by QIII on 2014-01-17
Hello!

This often occurs when proprietary graphics drivers are not used (Intel is an exception) or when the machine has hybrid Intel/ATI or Intel/Nvidia graphics.

Can you give us your machine specs?

---

### Post by marc13 on 2014-01-17
Where do I best see all the machine specs so that I can paste it out here?

---

### Post by electrohandyman501 on 2014-01-17
A can't say as I have an answer to fix your power issues, I have noticed the same issues with my laptop as well when using Ubuntu. 
It comes down to the laptop maker designed the power managment sofware to work with windows only. Otherwise the hardware will run, you just don't have the "fine tuning" abilities more truely managing you power usage.

---

### Post by QIII on 2014-01-17
Please run 

```
sudo lshw
```

This will produce a lot of stuff -- more than I need -- but I can look through it more quickly than I can tell you how to pick out what we need to see.

When you post back, please use code tags.

If you are using New Reply button - highlight text and use the # button in the text box header.

If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by marc13 on 2014-01-25
```
 description: Notebook
    product: Aspire 5750G ()
    vendor: Acer
    version: V1.14
    serial: LXRMU02158141009333400
    width: 64 bits
    capabilities: vsyscall32
    configuration: boot=normal chassis=notebook uuid=D1C7E898-D081-11E0-A0E8-B870F4EA8241
  *-core
       description: Motherboard
       product: JE50_HR
       vendor: Acer
       physical id: 0
       version: Base Board Version
       serial: Base Board Serial Number
       slot: Base Board Chassis Location
     *-firmware
          description: BIOS
          vendor: Acer
          physical id: 0
          version: V1.14
          date: 09/07/2011
          size: 1MiB
          capacity: 2496KiB
          capabilities: pci upgrade shadowing cdboot bootselect edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video acpi usb biosbootspecification
     *-memory
          description: System Memory
          physical id: 1b
          slot: System board or motherboard
          size: 6GiB
        *-bank:0
             description: SODIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: ACR256X64D3S13C9G
             vendor: Kinston
             physical id: 0
             serial: 8C14DCC0
             slot: ChannelA-DIMM0
             size: 2GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:1
             description: DIMMProject-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>POT-Creation-Date: 2009-10-08 14:02+0200PO-Revision-Date: 2012-02-05 00:26+0000Last-Translator: Andi Chandler <Unknown>Language-Team: English (United Kingdom) <en_GB@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2014-01-06 21:08+0000X-Generator: Launchpad (build 16877) [empty]
             physical id: 1
             slot: ChannelA-DIMM1
        *-bank:2
             description: SODIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: ACR512X64D3S13C9G
             vendor: Kinston
             physical id: 2
             serial: 0E36F924
             slot: ChannelB-DIMM0
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:3
             description: DIMMProject-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>POT-Creation-Date: 2009-10-08 14:02+0200PO-Revision-Date: 2012-02-05 00:26+0000Last-Translator: Andi Chandler <Unknown>Language-Team: English (United Kingdom) <en_GB@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2014-01-06 21:08+0000X-Generator: Launchpad (build 16877) [empty]
             physical id: 3
             slot: ChannelB-DIMM1
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i3-2330M CPU @ 2.20GHz
          vendor: Intel Corp.
          physical id: 2e
          bus info: cpu@0
          version: Intel(R) Core(TM) i3-2330M CPU @ 2.20GHz
          slot: CPU1
          size: 800MHz
          capacity: 4GHz
          width: 64 bits
          clock: 1333MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer xsave avx lahf_lm arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid cpufreq
          configuration: cores=2 enabledcores=2 threads=4
        *-cache:0
             description: L1 cache
             physical id: 30
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-through instruction
        *-cache:1
             description: L2 cache
             physical id: 31
             slot: L2 Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: synchronous internal write-through unified
        *-cache:2
             description: L3 cache
             physical id: 32
             slot: L3 Cache
             size: 3MiB
             capacity: 3MiB
             capabilities: synchronous internal write-through unified
     *-cache
          description: L1 cache
          physical id: 2f
          slot: L1 Cache
          size: 32KiB
          capacity: 32KiB
          capabilities: synchronous internal write-through data
     *-pci
          description: Host bridge
          product: 2nd Generation Core Processor Family DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 09
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:2000(size=4096) memory:d0000000-d10fffff ioport:a0000000(size=301989888)
           *-display
                description: VGA compatible controller
                product: GF108M [GeForce GT 520M]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nouveau latency=0
                resources: irq:16 memory:d0000000-d0ffffff memory:a0000000-afffffff memory:b0000000-b1ffffff ioport:2000(size=128) memory:d1000000-d107ffff
        *-display
             description: VGA compatible controller
             product: 2nd Generation Core Processor Family Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:43 memory:d1400000-d17fffff memory:c0000000-cfffffff ioport:3000(size=64)
        *-communication
             description: Communication controller
             product: 6 Series/C200 Series Chipset Family MEI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei latency=0
             resources: irq:42 memory:d1a04000-d1a0400f
        *-usb:0
             description: USB controller
             product: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:16 memory:d1a0a000-d1a0a3ff
        *-multimedia
             description: Audio device
             product: 6 Series/C200 Series Chipset Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:44 memory:d1a00000-d1a03fff
        *-pci:1
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: b4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 memory:9fb00000-9fbfffff ioport:d1800000(size=1048576)
           *-network
                description: Ethernet interface
                product: NetLink BCM57785 Gigabit Ethernet PCIe
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 10
                serial: b8:70:f4:ea:82:41
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi msix pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.128 firmware=sb latency=0 link=no multicast=yes port=twisted pair
                resources: irq:16 memory:d1830000-d183ffff memory:d1840000-d184ffff memory:d1850000-d18507ff
           *-generic:0
                description: SD Host controller
                product: BCM57765/57785 SDXC/MMC Card Reader
                vendor: Broadcom Corporation
                physical id: 0.1
                bus info: pci@0000:02:00.1
                version: 10
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=sdhci-pci latency=0
                resources: irq:17 memory:d1800000-d180ffff
           *-generic:1 UNCLAIMED
                description: System peripheral
                product: BCM57765/57785 MS Card Reader
                vendor: Broadcom Corporation
                physical id: 0.2
                bus info: pci@0000:02:00.2
                version: 10
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: latency=0
                resources: memory:d1810000-d181ffff
           *-generic:2 UNCLAIMED
                description: System peripheral
                product: BCM57765/57785 xD-Picture Card Reader
                vendor: Broadcom Corporation
                physical id: 0.3
                bus info: pci@0000:02:00.3
                version: 10
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: latency=0
                resources: memory:d1820000-d182ffff
        *-pci:2
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: b4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 memory:d1900000-d19fffff
           *-network
                description: Wireless interface
                product: AR9287 Wireless Network Adapter (PCI-Express)
                vendor: Qualcomm Atheros
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlan0
                version: 01
                serial: 94:39:e5:18:db:85
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath9k driverversion=3.8.0-35-generic firmware=N/A ip=192.168.1.131 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
                resources: irq:17 memory:d1900000-d190ffff
        *-usb:1
             description: USB controller
             product: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:d1a09000-d1a093ff
        *-isa
             description: ISA bridge
             product: HM65 Express Chipset Family LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-storage
             description: SATA controller
             product: 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:41 ioport:3088(size=8) ioport:309c(size=4) ioport:3080(size=8) ioport:3098(size=4) ioport:3060(size=32) memory:d1a08000-d1a087ff
        *-serial UNCLAIMED
             description: SMBus
             product: 6 Series/C200 Series Chipset Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 04
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:d1a06000-d1a060ff ioport:3040(size=32)
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD5000BPVT-0
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 01.0
             serial: WD-WX11E23VC970
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=00026f4e
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: ff9d6753-46a7-4cad-92c3-c0d27599f39a
                size: 459GiB
                capacity: 459GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2014-01-12 14:43:37 filesystem=ext4 lastmountpoint=/ modified=2014-01-12 14:54:08 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2014-01-25 13:02:23 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 5995MiB
                capacity: 5995MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 5995MiB
                   capabilities: nofs
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVD-RW DVRTD11RS
             vendor: PIONEER
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: 1.01
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
  *-power UNCLAIMED
       description: OEM_Define1
       product: OEM_Define5
       vendor: OEM_Define2
       physical id: 1
       version: OEM_Define6
       serial: OEM_Define3
       capacity: 75mWh
  *-battery
       description: Lithium-Ion Battery
       product: CRB Battery 0
       vendor: -Virtual Battery 0-
       physical id: 2
       version: 10/12/2007
       serial: Battery 0
       slot: Fake


```

Hope this helps. Its sucking power like a beast.

---

### Post by philinux on 2014-01-25
Have a look at this and post back a screenshot of your Power Stats.

[http://www.omgubuntu.co.uk/2013/12/check-battery-life-health-ubuntu-linux?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG!+Ubuntu!%29](http://www.omgubuntu.co.uk/2013/12/check-battery-life-health-ubuntu-linux?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG!+Ubuntu!%29)

---

### Post by marc13 on 2014-01-25
Looks like I got my answer. The battery discrepancy is off my 10 between the two. Have to bite the dust and get a new one. Thanks for all the support.

---

### Post by philinux on 2014-01-25
> **marc13 said:**
> Looks like I got my answer. The battery discrepancy is off my 10 between the two. Have to bite the dust and get a new one. Thanks for all the support.

10 don't sound a lot at all. Still got life in it yet.

How is it windows. What battery life do you get compared to ubuntu?

---

### Post by marc13 on 2014-01-25
I guess thats the main thing yes. When I was on Windows, it seemed to perform 20% better. Held onto life better for sure. Ubuntu seems to be sucking in dry, despite the fact that I am hardly using as many processes as I was in Windows. Or maybe the battery really degraded after the reinstall, or maybe I am imagining things. I am not sure, but it just seems to be worse in Ubuntu. 

On the other hand it doesnt matter, Ubuntu beats Windows, any Windows, by lightyears. I finally found an OS that is damn near PERFECT for my needs.

---

