---
title: "xenial 64 bit often almost boots but goes to a black screen"
date: 2016-05-08
forum: General Help
---

### Post by a-you on 2016-05-08
Often when booting (maybe 20% or 25% of the time) the process goes almost all the way but before showing the login box it seems to get stuck and shows only a black screen. Unfortunately the only solution in those cases is to hold the power button to shut down, then try again. I'd rather not be doing that kind of shut down. And anyway it's a problem.

I've been searching and found a tip that suggested putting a delay in /etc/init/lightdm.conf. I added a delay of 3 seconds and that seemed to fix it for a few days, but now the problem is back.

Any advice would be most appreciated. Including advice on even where to look. Thanks much in advance!!

Ubuntu Studio 16.4 xenial 64 bit. The computer is a bit old: a sony vaio from 2010. Also I have it set up to dual boot with windows 7 though I never use windows (why would I? ;-) )

---

### Post by mörgæs on 2016-05-09
Let's see the hardware.

Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by a-you on 2016-05-25
Hello @[**[COLOR=#DD4814][B]mörgæs**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=939075") are you still checking this thread?? Sorry for the long delay! If you are still there and still wouldn't mind helping then I can post that. I thought to ask first though, to see if you are still there. Thanks again for the kind offer.

---

### Post by sudodus on 2016-05-25
Many people can help. Please post the hardware specs :-)

---

### Post by a-you on 2016-05-26
Many many thanks.

I should add that there are some other symptoms that may be related.  There seem to be some issues with the OS starting applications, for  example sometimes when I boot the computer network-manager  (the applet, but also network-manager itself because then I have no internet) doesn't start; I can start it with:
```
sudo service network-manager restart
``` but I never had to do that with trusty.

Also it quite  often happens that applications simply don't launch. For example if I  want to use audacity I may have to try to start it (from "Applications"  menu) 3 times before it'll actually start. I've had this  problem with other applications too. At first I thought it was the apps  themselves, then I realized that it must be the OS somehow since it  seems to happen with various programs.

Also I should add that the almost-boot issue seems to have abated somewhat. It still happens occasionally, but it's not as often as before. Per a tip posted on webupd8.org I had added a delay in /etc/init/lightdm.conf just before the line that starts lightdm with "exec lightdm". The delay I added was "sleep 3." I'm now going to try commenting that out to see what happens.

The hardware specs are long, but here goes:
```

sudo lshw -sanitize > lshw.txt

```

```

computer
    description: Computer
    width: 64 bits
    capabilities: smbios-2.6 vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 7965MiB
     *-cpu
          product: Intel(R) Core(TM) i7 CPU       Q 720  @ 1.60GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          size: 1199MHz
          capacity: 1600MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm tpr_shadow vnmi flexpriority ept vpid dtherm ida cpufreq
     *-pci:0
          description: Host bridge
          product: Core Processor DMI
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 11
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Core Processor PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 11
             width: 32 bits
             clock: 33MHz
             capabilities: pci msi pciexpress pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:d000(size=4096) memory:d0000000-e30fffff
           *-display
                description: VGA compatible controller
                product: GT216M [GeForce GT 330M]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a2
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nouveau latency=0
                resources: irq:31 memory:e2000000-e2ffffff memory:d0000000-dfffffff memory:e0000000-e1ffffff ioport:d000(size=128) memory:e3000000-e307ffff
           *-multimedia
                description: Audio device
                product: GT216 HDMI Audio Controller
                vendor: NVIDIA Corporation
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:16 memory:e3080000-e3083fff
        *-generic:0 UNCLAIMED
             description: System peripheral
             product: Core Processor System Management Registers
             vendor: Intel Corporation
             physical id: 8
             bus info: pci@0000:00:08.0
             version: 11
             width: 32 bits
             clock: 33MHz
             capabilities: pciexpress cap_list
             configuration: latency=0
        *-generic:1 UNCLAIMED
             description: System peripheral
             product: Core Processor Semaphore and Scratchpad Registers
             vendor: Intel Corporation
             physical id: 8.1
             bus info: pci@0000:00:08.1
             version: 11
             width: 32 bits
             clock: 33MHz
             capabilities: pciexpress cap_list
             configuration: latency=0
        *-generic:2 UNCLAIMED
             description: System peripheral
             product: Core Processor System Control and Status Registers
             vendor: Intel Corporation
             physical id: 8.2
             bus info: pci@0000:00:08.2
             version: 11
             width: 32 bits
             clock: 33MHz
             capabilities: pciexpress cap_list
             configuration: latency=0
        *-generic:3 UNCLAIMED
             description: System peripheral
             product: Core Processor Miscellaneous Registers
             vendor: Intel Corporation
             physical id: 8.3
             bus info: pci@0000:00:08.3
             version: 11
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-generic:4 UNCLAIMED
             description: System peripheral
             product: Core Processor QPI Link
             vendor: Intel Corporation
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 11
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-generic:5 UNCLAIMED
             description: System peripheral
             product: Core Processor QPI Routing and Protocol Registers
             vendor: Intel Corporation
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: 11
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-usb:0
             description: USB controller
             product: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:16 memory:e8e08000-e8e083ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.4.0-22-lowlatency ehci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 4.04
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
                      product: Sony Visual Communication Camera
                      vendor: SuYin
                      physical id: 2
                      bus info: usb@1:1.2
                      version: 3.00
                      serial: [REMOVED]
                      capabilities: usb-2.00
                      configuration: driver=uvcvideo maxpower=100mA speed=480Mbit/s
        *-multimedia
             description: Audio device
             product: 5 Series/3400 Series Chipset High Definition Audio
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:32 memory:e8e00000-e8e03fff
        *-pci:1
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:c000(size=4096) memory:e7a00000-e8dfffff ioport:e8f00000(size=2097152)
           *-network
                description: Wireless interface
                product: AR9287 Wireless Network Adapter (PCI-Express)
                vendor: Qualcomm Atheros
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlp2s0
                version: 01
                serial: [REMOVED]
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath9k driverversion=4.4.0-22-lowlatency firmware=N/A ip=[REMOVED] latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
                resources: irq:16 memory:e7a00000-e7a0ffff
        *-pci:2
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:b000(size=4096) memory:e6600000-e79fffff ioport:e9100000(size=2097152)
           *-generic:0
                description: SD Host controller
                product: MMC/SD Host Controller
                vendor: Ricoh Co Ltd
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: msi pm pciexpress bus_master cap_list
                configuration: driver=sdhci-pci latency=0
                resources: irq:17 memory:e6603000-e66030ff
           *-generic:1 UNCLAIMED
                description: System peripheral
                product: R5U2xx (R5U230 / R5U231 / R5U241) [Memory Stick Host Controller]
                vendor: Ricoh Co Ltd
                physical id: 0.1
                bus info: pci@0000:03:00.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: msi pm pciexpress bus_master cap_list
                configuration: latency=0
                resources: memory:e6602000-e66020ff
           *-firewire
                description: FireWire (IEEE 1394)
                product: R5C832 PCIe IEEE 1394 Controller
                vendor: Ricoh Co Ltd
                physical id: 0.3
                bus info: pci@0000:03:00.3
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: msi pm pciexpress ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=0
                resources: irq:16 memory:e6601000-e66017ff
           *-generic:2
                description: SD Host controller
                product: MMC/SD Host Controller
                vendor: Ricoh Co Ltd
                physical id: 0.4
                bus info: pci@0000:03:00.4
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: msi pm pciexpress bus_master cap_list
                configuration: driver=sdhci-pci latency=0
                resources: irq:19 memory:e6600000-e66000ff
        *-pci:3
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:18 ioport:a000(size=4096) memory:e5200000-e65fffff ioport:e9300000(size=2097152)
           *-network
                description: Ethernet interface
                product: 88E8057 PCI-E Gigabit Ethernet Controller
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@0000:04:00.0
                logical name: enp4s0
                version: 10
                serial: [REMOVED]
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 latency=0 link=no multicast=yes port=twisted pair
                resources: irq:29 memory:e5220000-e5223fff ioport:a000(size=256) memory:e5200000-e521ffff
        *-pci:4
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:9000(size=4096) memory:e3200000-e51fffff ioport:e9500000(size=2097152)
        *-usb:1
             description: USB controller
             product: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:e8e07000-e8e073ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.4.0-22-lowlatency ehci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 4.04
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
                 *-usb
                      description: Mouse
                      product: USB Optical Mouse
                      vendor: PixArt
                      physical id: 2
                      bus info: usb@2:1.2
                      version: 1.00
                      capabilities: usb-1.10
                      configuration: driver=usbhid maxpower=100mA speed=2Mbit/s
        *-pci:5
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: a5
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: PM55 Chipset LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-storage
             description: SATA controller
             product: 5 Series/3400 Series Chipset 6 port SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:30 ioport:e070(size=8) ioport:e060(size=4) ioport:e050(size=8) ioport:e040(size=4) ioport:e020(size=32) memory:e8e06000-e8e067ff
        *-serial UNCLAIMED
             description: SMBus
             product: 5 Series/3400 Series Chipset SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 05
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:e8e05000-e8e050ff ioport:e000(size=32)
     *-pci:1
          description: Host bridge
          product: Core Processor QuickPath Architecture Generic Non-Core Registers
          vendor: Intel Corporation
          physical id: 101
          bus info: pci@0000:3f:00.0
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Core Processor QuickPath Architecture System Address Decoder
          vendor: Intel Corporation
          physical id: 102
          bus info: pci@0000:3f:00.1
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Core Processor QPI Link 0
          vendor: Intel Corporation
          physical id: 103
          bus info: pci@0000:3f:02.0
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Core Processor QPI Physical 0
          vendor: Intel Corporation
          physical id: 104
          bus info: pci@0000:3f:02.1
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: Core Processor Integrated Memory Controller
          vendor: Intel Corporation
          physical id: 105
          bus info: pci@0000:3f:03.0
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: Core Processor Integrated Memory Controller Target Address Decoder
          vendor: Intel Corporation
          physical id: 106
          bus info: pci@0000:3f:03.1
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: Core Processor Integrated Memory Controller Test Registers
          vendor: Intel Corporation
          physical id: 107
          bus info: pci@0000:3f:03.4
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:8
          description: Host bridge
          product: Core Processor Integrated Memory Controller Channel 0 Control Registers
          vendor: Intel Corporation
          physical id: 108
          bus info: pci@0000:3f:04.0
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:9
          description: Host bridge
          product: Core Processor Integrated Memory Controller Channel 0 Address Registers
          vendor: Intel Corporation
          physical id: 109
          bus info: pci@0000:3f:04.1
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:10
          description: Host bridge
          product: Core Processor Integrated Memory Controller Channel 0 Rank Registers
          vendor: Intel Corporation
          physical id: 10a
          bus info: pci@0000:3f:04.2
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:11
          description: Host bridge
          product: Core Processor Integrated Memory Controller Channel 0 Thermal Control Registers
          vendor: Intel Corporation
          physical id: 10b
          bus info: pci@0000:3f:04.3
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:12
          description: Host bridge
          product: Core Processor Integrated Memory Controller Channel 1 Control Registers
          vendor: Intel Corporation
          physical id: 10c
          bus info: pci@0000:3f:05.0
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:13
          description: Host bridge
          product: Core Processor Integrated Memory Controller Channel 1 Address Registers
          vendor: Intel Corporation
          physical id: 10d
          bus info: pci@0000:3f:05.1
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:14
          description: Host bridge
          product: Core Processor Integrated Memory Controller Channel 1 Rank Registers
          vendor: Intel Corporation
          physical id: 10e
          bus info: pci@0000:3f:05.2
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:15
          description: Host bridge
          product: Core Processor Integrated Memory Controller Channel 1 Thermal Control Registers
          vendor: Intel Corporation
          physical id: 10f
          bus info: pci@0000:3f:05.3
          version: 04
          width: 32 bits
          clock: 33MHz
     *-scsi:0
          physical id: 2
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST9500420AS
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: SDM2
             serial: [REMOVED]
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=18819589
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                version: 3.1
                serial: [REMOVED]
                size: 8881MiB
                capacity: 8883MiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2010-06-02 08:40:15 filesystem=ntfs label=Recovery state=clean
           *-volume:1
                description: Windows NTFS volume
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                version: 3.1
                serial: [REMOVED]
                size: 79MiB
                capacity: 100MiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2010-06-02 08:40:18 filesystem=ntfs label=System Reserved state=clean
           *-volume:2
                description: Windows NTFS volume
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                version: 3.1
                serial: [REMOVED]
                size: 38GiB
                capacity: 38GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2010-06-02 08:40:19 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
           *-volume:3
                description: Extended partition
                physical id: 4
                bus info: scsi@0:0.0.0,4
                logical name: /dev/sda4
                size: 418GiB
                capacity: 418GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   description: Linux filesystem partition
                   physical id: 5
                   logical name: /dev/sda5
                   logical name: /
                   capacity: 23GiB
                   configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered state=mounted
              *-logicalvolume:1
                   description: Linux swap / Solaris partition
                   physical id: 6
                   logical name: /dev/sda6
                   capacity: 4000MiB
                   capabilities: nofs
              *-logicalvolume:2
                   description: Linux filesystem partition
                   physical id: 7
                   logical name: /dev/sda7
                   logical name: /home
                   capacity: 391GiB
                   configuration: mount.fstype=ext4 mount.options=rw,relatime,data=ordered state=mounted
     *-scsi:1
          physical id: 3
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: BD-CMB UJ141AS
             vendor: MATSHITA
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: 1.00
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc

```

---

### Post by sudodus on 2016-05-26
You are using the low-latency kernel.

- Have you tried with the generic kernel version?
- Do you need a low-latency kernel for real-time tasks?

```
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.4.0-22-[COLOR="#FF0000"]lowlatency[/COLOR] ehci_hcd
```

You have nvidia graphics and use the free nouveau driver.

- Have you tried with a proprietary nvidia driver?

```
           *-display
                description: VGA compatible controller
                product: [COLOR="#FF0000"]GT216M [GeForce GT 330M][/COLOR]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a2
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=[COLOR="#FF0000"]nouveau[/COLOR] latency=0
                resources: irq:31 memory:e2000000-e2ffffff memory:d0000000-dfffffff memory:e0000000-e1ffffff ioport:d000(size=128) memory:e3000000-e307ffff
```

---

### Post by a-you on 2016-05-26
Thanks for your comments. I do need the low-latency kernel I would say because I do work in sound/music/audio. As for the nvidia driver: I haven't tried that with xenial. I was using the nvidia driver in trusty and that might be a good thing to try here too. I had decided to try using the nouveau driver because the nvidia driver disabled the use of CTRL-ALT-F1 thru 6 for console access, but I don't really have a need for that anyway so trying the nvidia driver is a good idea.

Btw I tried commenting out the 3 sec sleep delay in /etc/init/lightdm.conf and the result was not good. When I restarted it didn't boot all the way. It got to a black screen and I had to hold the power button to shut down. Fortunately on the second try it booted all the way so I uncommented that delay. It seems that I shouldn't have to add such a delay!! This is rather screwed up!

I'll try the nvidia driver and report back.

I'm not sure if I neglected to mention this but I'm using ubuntu studio 16.04, not generic ubuntu. Sorry if I left that out before. I use ubuntu studio to have the low-latency kernel for audio.

---

### Post by a-you on 2016-05-26
I tried the nvidia driver and enabled the intel microcode driver too (don't know what that does). It's definitely better. Thanks @sudodus for the suggestion!

Audacity still has issues starting up but starting it from a terminal shows that in fact it's not the OS but some audacity settings---various errors are printed, quite a few in fact.

So it looks like this is much better!! :-) It's a bit surprising because I was using the nouveau for quite a while with trusty and only switched to the nvidia driver fairly recently because I wanted to try a program that needed it. The change of graphics driver never made any difference with trusty, so I'm slightly surprised that it does with xenial. But fine. If it fixes it then wonderful.

---

### Post by sudodus on 2016-05-26
Congratulations :KS

When you feel that the the problem of this thread is solved, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

### Post by a-you on 2016-05-28
Too early to tell if it's really solved. I want to try several boots before doing that.

---

### Post by a-you on 2016-05-31
No it's not quite solved. Still occasionally boots to a blank/black screen. Less often than before definitely. But not entirely solved yet. :-(

---

### Post by mörgæs on 2016-06-01
I think the best you can do is keep trying new releases / kernels to see if the problem is completely solved one day.

---

### Post by a-you on 2016-06-01
Thanks @[**[COLOR=#DD4814][B]mörgæs**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=939075"). I was thinking the same. Trusty was working just fine, but I installed it after it had been out for a few months. These various problems with xenial are hopefully being solved. I'll just keep doing the updates. Probably it'll work out fine in the end.

---

