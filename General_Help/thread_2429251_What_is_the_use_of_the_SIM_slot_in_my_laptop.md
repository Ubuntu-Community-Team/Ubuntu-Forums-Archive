---
title: "What is the use of the SIM slot in my laptop?"
date: 2019-10-15
forum: General Help
---

### Post by ardouronerous on 2019-10-15
My laptop has a SIM card slot in it. I've read the manual for my laptop and it doesn't really say much on the function of it, it only identifies it as a SIM card slot.
[https://s16-us2.startpage.com/cgi-bin/serveimage?url=https:%2F%2Fqph.fs.quoracdn.net%2Fmain-qimg-ff76cc8b80aa504c81de6d52e7131790&sp=91de253cdf6c7ea88c0a2d2023ed31ea](https://s16-us2.startpage.com/cgi-bin/serveimage?url=https:%2F%2Fqph.fs.quoracdn.net%2Fmain-qimg-ff76cc8b80aa504c81de6d52e7131790&sp=91de253cdf6c7ea88c0a2d2023ed31ea)
What is the function of the SIM card slot exactly? Reason why I'm asking this is because I'm interested in making my laptop function like a cellphone also, making and receiving calls and SMS from my laptop, is that possible on Lubuntu?

Thanks.

---

### Post by Irihapeti on 2019-10-16
I have a single-board computer (setup as a router) which has a SIM slot. It's intended to work with a 3G card which can be installed in one of the internal card sockets.

Maybe your laptop is designed to do the same. Does it have a socket for an additional card?

---

### Post by ardouronerous on 2019-10-16
> Does it have a socket for an additional card? 				

Not that I see, no, it's similar to the picture.

---

### Post by Irihapeti on 2019-10-16
You could try
```

sudo lshw

```
and see if there's anything interesting in the output. There might already be a 3G or 4G card installed, or an indication of an empty slot where one might go.

---

### Post by ardouronerous on 2019-10-16
Going through the output, I can't really make heads or tails of the output. What would the output for a SIM card slot look like?

---

### Post by Irihapeti on 2019-10-16
You could post the output of that command here, between code tags. Someone should be able to decipher the output.

---

### Post by mc4man on 2019-10-16
It's for WWAN on your laptop , easy to search out..
Basically it  gives you mobile internet access that you can purchase from a provider.
Pretty much like getting a tablet that can use cellular, nothing to do with your mobile phone service

---

### Post by ardouronerous on 2019-10-16
```
hp-probook-450-g2
    description: Notebook
    product: HP ProBook 450 G2 (L8E03UT#ABA)
    vendor: Hewlett-Packard
    version: A3009DD10303
    serial: CND5192ST1
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 smp vsyscall32
    configuration: boot=normal chassis=notebook family=103C_5336AN G=N L=BUS B=HP S=PRO sku=L8E03UT#ABA uuid=7F6BA180-8EF1-E411-A707-5029500000FF
  *-core
       description: Motherboard
       product: 2248
       vendor: Hewlett-Packard
       physical id: 0
       version: KBC Version 59.22
       serial: PEUZUG5WV8N9QA
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: c
          version: M73 Ver. 01.11
          date: 03/17/2015
          size: 64KiB
          capacity: 6080KiB
          capabilities: pci pcmcia upgrade shadowing cdboot bootselect edd int5printscreen int9keyboard int14serial int17printer acpi usb smartbattery biosbootspecification netboot uefi
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i5-5200U CPU @ 2.20GHz
          vendor: Intel Corp.
          physical id: 7
          bus info: cpu@0
          version: Intel(R) Core(TM) i5-5200U CPU @ 2.20GHz
          serial: To Be Filled By O.E.M.
          slot: U3E1
          size: 2016MHz
          capacity: 2700MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch cpuid_fault epb invpcid_single pti ssbd ibrs ibpb stibp tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid rdseed adx smap intel_pt xsaveopt dtherm ida arat pln pts md_clear flush_l1d cpufreq
          configuration: cores=2 enabledcores=2 threads=4
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: asynchronous internal write-back instruction
             configuration: level=1
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: L2 Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: asynchronous internal write-back unified
             configuration: level=2
        *-cache:2
             description: L3 cache
             physical id: a
             slot: L3 Cache
             size: 3MiB
             capacity: 3MiB
             capabilities: asynchronous internal write-back unified
             configuration: level=3
     *-cache
          description: L1 cache
          physical id: 6
          slot: L1 Cache
          size: 32KiB
          capacity: 32KiB
          capabilities: asynchronous internal write-back data
          configuration: level=1
     *-memory
          description: System Memory
          physical id: 0
          slot: System board or motherboard
          size: 8GiB
        *-bank:0
             description: SODIMM DDR3 Synchronous 1600 MHz (0.6 ns)
             product: HMT451S6BFR8A-PB
             vendor: Hynix/Hyundai
             physical id: 0
             serial: 37892146
             slot: Bottom-Slot 1(left)
             size: 4GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
        *-bank:1
             description: SODIMM DDR3 Synchronous 1600 MHz (0.6 ns)
             product: HMT451S6BFR8A-PB
             vendor: Hynix/Hyundai
             physical id: 1
             serial: 23482466
             slot: Bottom-Slot 2(right)
             size: 4GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
     *-pci
          description: Host bridge
          product: Broadwell-U Host Bridge -OPI
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
          configuration: driver=bdw_uncore
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: HD Graphics 5500
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:51 memory:c0000000-c0ffffff memory:b0000000-bfffffff ioport:6000(size=64) memory:c0000-dffff
        *-multimedia:0
             description: Audio device
             product: Broadwell-U Audio Controller
             vendor: Intel Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:52 memory:c1410000-c1413fff
        *-usb:0
             description: USB controller
             product: Wildcat Point-LP USB xHCI Controller
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:44 memory:c1400000-c140ffff
           *-usbhost:0
                product: xHCI Host Controller
                vendor: Linux 4.15.0-65-generic xhci-hcd
                physical id: 0
                bus info: usb@2
                logical name: usb2
                version: 4.15
                capabilities: usb-2.00
                configuration: driver=hub slots=11 speed=480Mbit/s
              *-usb:0
                   description: Mouse
                   product: USB OPTICAL MOUSE
                   physical id: 2
                   bus info: usb@2:2
                   version: 1.00
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=100mA speed=2Mbit/s
              *-usb:1
                   description: Video
                   product: HP HD Webcam
                   vendor: SunplusIT INC.
                   physical id: 7
                   bus info: usb@2:7
                   version: 1.01
                   capabilities: usb-2.00
                   configuration: driver=uvcvideo maxpower=500mA speed=480Mbit/s
              *-usb:2
                   description: USB hub
                   product: USB2.0 Hub
                   vendor: VIA Labs, Inc.
                   physical id: 8
                   bus info: usb@2:8
                   version: 90.01
                   capabilities: usb-2.10
                   configuration: driver=hub slots=4 speed=480Mbit/s
                 *-usb
                      description: Keyboard
                      product: Generic USB K/B
                      vendor: PCPlay
                      physical id: 4
                      bus info: usb@2:8.4
                      version: 0.01
                      capabilities: usb-1.10
                      configuration: driver=usbhid maxpower=100mA speed=2Mbit/s
           *-usbhost:1
                product: xHCI Host Controller
                vendor: Linux 4.15.0-65-generic xhci-hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 4.15
                capabilities: usb-3.00
                configuration: driver=hub slots=4 speed=5000Mbit/s
        *-communication
             description: Communication controller
             product: Wildcat Point-LP MEI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:48 memory:c141b000-c141b01f
        *-multimedia:1
             description: Audio device
             product: Wildcat Point-LP High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=64
             resources: irq:49 memory:c1414000-c1417fff
        *-pci:0
             description: PCI bridge
             product: Wildcat Point-LP PCI Express Root Port #1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: e3
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 memory:c1300000-c13fffff
        *-pci:1
             description: PCI bridge
             product: Wildcat Point-LP PCI Express Root Port #2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: e3
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:4000(size=8192) memory:c1200000-c12fffff ioport:ae900000(size=2097152)
           *-generic
                description: Unassigned class
                product: RTS5227 PCI Express Card Reader
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:07:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=rtsx_pci latency=0
                resources: irq:45 memory:c1200000-c1200fff
        *-pci:2
             description: PCI bridge
             product: Wildcat Point-LP PCI Express Root Port #3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: e3
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:3000(size=4096) memory:c1100000-c11fffff
           *-network
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:08:00.0
                logical name: enp8s0
                version: 10
                serial: 48:0f:cf:6f:c0:c7
                size: 10Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168g-3_0.0.1 04/23/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:18 ioport:3000(size=256) memory:c1104000-c1104fff memory:c1100000-c1103fff
        *-pci:3
             description: PCI bridge
             product: Wildcat Point-LP PCI Express Root Port #4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: e3
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:43 memory:c1000000-c10fffff
           *-network
                description: Wireless interface
                product: Wireless 3160
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:09:00.0
                logical name: wlo1
                version: 83
                serial: 34:e6:ad:59:14:7e
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlwifi driverversion=4.15.0-65-generic firmware=17.948900127.0 ip=192.168.1.13 latency=0 link=yes multicast=yes wireless=IEEE 802.11
                resources: irq:50 memory:c1000000-c1001fff
        *-usb:1
             description: USB controller
             product: Wildcat Point-LP USB EHCI Controller
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:17 memory:c1419000-c14193ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.15.0-65-generic ehci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 4.15
                capabilities: usb-2.00
                configuration: driver=hub slots=2 speed=480Mbit/s
              *-usb
                   description: USB hub
                   vendor: Intel Corp.
                   physical id: 1
                   bus info: usb@1:1
                   version: 0.03
                   capabilities: usb-2.00
                   configuration: driver=hub slots=8 speed=480Mbit/s
        *-isa
             description: ISA bridge
             product: Wildcat Point-LP LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-storage
             description: SATA controller
             product: Wildcat Point-LP SATA Controller [AHCI Mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:46 ioport:6088(size=8) ioport:6094(size=4) ioport:6080(size=8) ioport:6090(size=4) ioport:6060(size=32) memory:c1418000-c14187ff
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: SAMSUNG MZ7TE128
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 9H0Q
             serial: S1BDNSAG826747
             size: 119GiB (128GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=e25836c5
           *-volume
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: 55c0f7f6-9a52-479d-8ad2-9d3915c278ab
                size: 119GiB
                capacity: 119GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover 64bit extents ext4 ext2 initialized
                configuration: created=2019-06-03 14:45:48 filesystem=ext4 lastmountpoint=/ modified=2019-10-16 07:55:13 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2019-10-16 07:55:13 state=mounted
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVDRW  DU8A6SH
             vendor: hp
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: DH61
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
  *-battery
       product: VI04044
       vendor: 13-22
       physical id: 1
       slot: Primary
       capacity: 44400mWh
       configuration: voltage=14.8V
```

> It's for WWAN on your laptop , easy to search out..
Basically it  gives you mobile internet access that you can purchase from a provider.
Pretty much like getting a tablet that can use cellular, nothing to do with your mobile phone service 		

So I cannot recieve or send phone calls or SMS messages from my laptop?

---

### Post by Irihapeti on 2019-10-16
I'll leave you with mc4man; they know *far* more about these things than I do.

---

### Post by mc4man on 2019-10-16
> So I cannot recieve or send phone calls or SMS messages from my laptop?
Not sure what you mean. 
Can a sim card turn your laptop into a phone? No
Can you make calls or messaging on your laptop?
 Sure, there are apps for that.

---

