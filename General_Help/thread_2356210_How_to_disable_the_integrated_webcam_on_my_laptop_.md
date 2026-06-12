---
title: "How to disable the integrated webcam on my laptop in Ubuntu"
date: 2017-03-20
forum: General Help
---

### Post by John_Patrick_Mason on 2017-03-20
In Windows, you go to device manager, right-click, and click disable. Why can't I do the same in Ubuntu?

---

### Post by TheFu on 2017-03-20
Linux isn't Windows.  Expecting it to behave like Windows will only lead to frustration.
I would blacklist the driver for that device .... or just disable it in the BIOS.
[https://askubuntu.com/questions/458515/how-to-disable-internal-webcam](https://askubuntu.com/questions/458515/how-to-disable-internal-webcam) seems to explain.

---

### Post by John_Patrick_Mason on 2017-03-21
> **TheFu said:**
> [https://askubuntu.com/questions/458515/how-to-disable-internal-webcam](https://askubuntu.com/questions/458515/how-to-disable-internal-webcam) seems to explain.

The link you provided requires the use of mkinitcpio to find which modules are loaded automatically. How can I find mkinitcpio? I can't find it when I do:

```
sudo apt-cache search mkinitcpio
```

---

### Post by TheFu on 2017-03-21
That command is in an "extra details" part. It isn't necessary. Plus it is for Arch, so I'm confused why it is part of the AskUbuntu answer.  People running Arch are a little hard-core with their linux and often there is some good internal information in the Arch forums/how-tos, but I don't believe it matters here.

Plus, don't forget to put some electrical tape over the webcam - since someone could just remote into the machine and re-load the blacklisted module manually either for fun or if you are a target.

The main thing is to 
a) determine exactly which driver is being used (there are many different ways)
b) prevent it from being loaded (there are many different ways)

I'd use lsusb, lshw to find the driver and either move/rename the driver filename or block it from loading. If you remove it, the next kernel update might bring a new version back, hence the blacklist.

---

### Post by mastablasta on 2017-03-21
can you be a bit more specific - disable temporary or disable permanently?

---

### Post by vasa1 on 2017-03-21
> **TheFu said:**
> ...
Plus, don't forget to put some electrical tape over the webcam - since someone could just remote into the machine and re-load the blacklisted module manually either for fun or if you are a target.
...
Simple. Effective. Distro-agnostic. And you'll be in good company: [http://www.dailymail.co.uk/sciencetech/article-3790585/FBI-director-covers-webcam-TAPE-says-doing-stop-hackers-spying.html](http://www.dailymail.co.uk/sciencetech/article-3790585/FBI-director-covers-webcam-TAPE-says-doing-stop-hackers-spying.html)

---

### Post by Habitual on 2017-03-21
Scotch tape. works every where.

---

### Post by John_Patrick_Mason on 2017-03-21
[QUOTE=TheFlu]I'd use lsusb, lshw to find the driver and either move/rename the driver  filename or block it from loading. If you remove it, the next kernel  update might bring a new version back, hence the blacklist.[/QUOTE]

I tried typing:

```
sudo lshw -sanitize
```

into the terminal, but it outputed so many drivers that I'm not sure which one to disable, so I posted the results here:

```
computer                  
    description: Portable Computer
    product: Dell System Inspiron N7110 (System SKUNumber)
    vendor: Dell Inc.
    version: 0.1
    serial: [REMOVED]
    width: 64 bits
    capabilities: smbios-2.6 dmi-2.6 vsyscall32
    configuration: administrator_password=unknown boot=normal chassis=portable family=HuronRiver System frontpanel_password=unknown keyboard_password=unknown power-on_password=unknown sku=System SKUNumber uuid=[REMOVED]
  *-core
       description: Motherboard
       product: 0YH79Y
       vendor: Dell Inc.
       physical id: 0
       version: A00
       serial: [REMOVED]
       slot: Part Component
     *-firmware
          description: BIOS
          vendor: Dell Inc.
          physical id: 0
          version: A05
          date: 05/19/2011
          size: 128KiB
          capacity: 2496KiB
          capabilities: pci pnp upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i3-2310M CPU @ 2.10GHz
          vendor: Intel Corp.
          physical id: 2e
          bus info: cpu@0
          version: Intel(R) Core(TM) i3-2310M CPU @ 2.10GHz
          serial: [REMOVED]
          slot: CPU
          size: 844MHz
          capacity: 2100MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer xsave avx lahf_lm epb tpr_shadow vnmi flexpriority ept vpid xsaveopt dtherm arat pln pts cpufreq
          configuration: cores=2 enabledcores=2 threads=4
        *-cache:0
             description: L1 cache
             physical id: 2f
             slot: L1-Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: synchronous internal write-through data
             configuration: level=1
        *-cache:1
             description: L2 cache
             physical id: 30
             slot: L2-Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: synchronous internal write-through data
             configuration: level=2
        *-cache:2
             description: L3 cache
             physical id: 31
             slot: L3-Cache
             size: 3MiB
             capacity: 3MiB
             capabilities: synchronous internal write-back unified
             configuration: level=3
     *-memory
          description: System Memory
          physical id: 32
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: SODIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: M471B5273CH0-CH9
             vendor: Samsung
             physical id: 0
             serial: [REMOVED]
             slot: ChannelA-DIMM0
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:1
             description: DIMM [empty]
             physical id: 1
             slot: ChannelB-DIMM0
     *-pci
          description: Host bridge
          product: 2nd Generation Core Processor Family DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
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
             resources: irq:31 memory:d0000000-d03fffff memory:c0000000-cfffffff ioport:4000(size=64) memory:c0000-dffff
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
             configuration: driver=mei_me latency=0
             resources: irq:32 memory:d1705000-d170500f
        *-usb:0
             description: USB controller
             product: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:16 memory:d170a000-d170a3ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.8.0-41-generic ehci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 4.08
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
                 *-usb UNCLAIMED
                      description: Video
                      product: Laptop_Integrated_Webcam_HD
                      vendor: CN0T3NPC7248714EB0C2A00
                      physical id: 4
                      bus info: usb@1:1.4
                      version: 12.09
                      capabilities: usb-2.00
                      configuration: maxpower=500mA speed=480Mbit/s
        *-multimedia
             description: Audio device
             product: 6 Series/C200 Series Chipset Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:34 memory:d1700000-d1703fff
        *-pci:0
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 memory:d1600000-d16fffff
           *-network
                description: Wireless interface
                product: Centrino Wireless-N 1030 [Rainbow Peak]
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: wlp1s0
                version: 34
                serial: [REMOVED]
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlwifi driverversion=4.8.0-41-generic firmware=18.168.6.1 ip=[REMOVED] latency=0 link=yes multicast=yes wireless=IEEE 802.11
                resources: irq:33 memory:d1600000-d1601fff
        *-pci:1
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:18 memory:d1500000-d15fffff
           *-usb
                description: USB controller
                product: uPD720200 USB 3.0 Host Controller
                vendor: NEC Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 04
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi msix pciexpress xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:18 memory:d1500000-d1501fff
              *-usbhost:0
                   product: xHCI Host Controller
                   vendor: Linux 4.8.0-41-generic xhci-hcd
                   physical id: 0
                   bus info: usb@3
                   logical name: usb3
                   version: 4.08
                   capabilities: usb-2.00
                   configuration: driver=hub slots=2 speed=480Mbit/s
              *-usbhost:1
                   product: xHCI Host Controller
                   vendor: Linux 4.8.0-41-generic xhci-hcd
                   physical id: 1
                   bus info: usb@4
                   logical name: usb4
                   version: 4.08
                   capabilities: usb-3.00
                   configuration: driver=hub slots=2 speed=5000Mbit/s
        *-pci:2
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:3000(size=4096) ioport:d0400000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: enp3s0
                version: 05
                serial: [REMOVED]
                size: 10Mbit/s
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8105e-1.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:29 ioport:3000(size=256) memory:d0404000-d0404fff memory:d0400000-d0403fff
        *-pci:3
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:2000(size=4096) memory:d0d00000-d14fffff ioport:d0500000(size=8388608)
        *-usb:1
             description: USB controller
             product: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:d1709000-d17093ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.8.0-41-generic ehci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 4.08
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
                 *-usb:0
                      description: Mouse
                      product: 2.4G Wireless Mouse
                      vendor: MOSART Semi.
                      physical id: 3
                      bus info: usb@2:1.3
                      version: 1.06
                      capabilities: usb-1.10
                      configuration: driver=usbhid maxpower=100mA speed=12Mbit/s
                 *-usb:1
                      description: Bluetooth wireless interface
                      vendor: Intel Corp.
                      physical id: 5
                      bus info: usb@2:1.5
                      version: 69.19
                      capabilities: bluetooth usb-2.00
                      configuration: driver=btusb speed=12Mbit/s
        *-isa
             description: ISA bridge
             product: HM67 Express Chipset Family LPC Controller
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
             product: 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:30 ioport:4088(size=8) ioport:4094(size=4) ioport:4080(size=8) ioport:4090(size=4) ioport:4060(size=32) memory:d1708000-d17087ff
        *-serial UNCLAIMED
             description: SMBus
             product: 6 Series/C200 Series Chipset Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 05
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:d1704000-d17040ff ioport:efa0(size=32)
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST9500325AS
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: DEM1
             serial: [REMOVED]
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=07f2837e
           *-volume:0
                description: Windows FAT volume
                vendor: Dell 8.0
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                version: FAT16
                serial: [REMOVED]
                size: 101MiB
                capacity: 101MiB
                capabilities: primary fat initialized
                configuration: FATs=2 filesystem=fat label=DellUtility
           *-volume:1
                description: Windows NTFS volume
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                version: 3.1
                serial: [REMOVED]
                size: 14GiB
                capacity: 14GiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2011-03-30 02:29:18 filesystem=ntfs label=RECOVERY state=clean
           *-volume:2
                description: Windows NTFS volume
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                version: 3.1
                serial: [REMOVED]
                size: 245GiB
                capacity: 245GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2016-10-14 10:13:29 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
           *-volume:3
                description: Extended partition
                physical id: 4
                bus info: scsi@0:0.0.0,4
                logical name: /dev/sda4
                size: 205GiB
                capacity: 205GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 4008MiB
                   capabilities: nofs
              *-logicalvolume:1
                   description: Linux filesystem partition
                   physical id: 6
                   logical name: /dev/sda6
                   logical name: /
                   capacity: 201GiB
                   configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered state=mounted
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVD+-RW TS-L633J
             vendor: TSSTcorp
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: D400
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
```

[QUOTE=mastablasta]can you be a bit more specific - disable temporary or disable permanently?[/QUOTE]

Disable permanently, but I also want it to be easily reversible in case I decide to video chat with someone in the future.

[QUOTE=TheFlu]Plus, don't forget to put some electrical tape over the webcam - since  someone could just remote into the machine and re-load the blacklisted  module manually either for fun or if you are a target.[/QUOTE]

Yes, I know, I know. I can put tape over my webcam, but right now I'm out of tape, and I want to learn how to disable it manually, so that if a hacker ever gains access, they'll have to jump through hoops to get it to work.

---

### Post by TheFu on 2017-03-21
For "Disable permanently, but I also want it to be easily reversible" - then do it in the BIOS.

BTW, the lshw output has the webcam in it.  Look through the output. It is **VERY explicit** and shows the exact driver used (you want to black list that driver).  Hint: Scan the 'product:' lines.

Just trying to teach you to fish, not hand you a fish.

Regardless, even with the driver blacklisted, please put the electrical tape over the camera.

---

### Post by John_Patrick_Mason on 2017-03-21
[QUOTE=TheFlu]BTW, the lshw output has the webcam in it.  Look through the output. It is **VERY explicit** and shows the exact driver used (you want to black list that driver).  Hint: Scan the 'product:' lines.

Just trying to teach you to fish, not hand you a fish.[/QUOTE]

Found it! I must have read it too fast before. So, how do I go about blacklisting the driver? Should I use the driver name, as in:

```
blacklist uvcvideo
```?

Also, how do I go about disabling it in the BIOS?

---

### Post by John_Patrick_Mason on 2017-03-21
OK. So I created a new file in /etc/modprobe.d called blacklist.uvcdriver.conf with the following lines:

```

# Disables webcam driver
blacklist uvcvideo

```

My question is, do I have to add:

```
install uvcvideo /bin/false
```

at the end of the same file, or am I supposed to create an entirely new file in /etc/modprobe.d with the above line of code?

---

