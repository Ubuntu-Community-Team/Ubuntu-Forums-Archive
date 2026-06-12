---
title: "No sound once updated to 20.04"
date: 2021-08-01
forum: General Help
---

### Post by zeframcochrane2 on 2021-08-01
Hello I recently upgraded my ubuntu to 20.04, and I have lost all the sound options in my system, I have tried various methods from the internet and I still can't get it to work, I noticed this is has seemed to happen to a lot of people, is there any solution that fixes this besides a reinstall?

---

### Post by mIk3_08 on 2021-08-01
Their are a lot of this community that may want to extend their help and provide your needs in terms of support.
In order for the community to see the information of your hardware. 
Please run the command in your terminal below and paste the result wrap with code here in this thread.
```
sudo lshw
```
and also run this command in your terminal and paste the result wrap with code here in this thread.
```
hostnamectl status
```

---

### Post by zeframcochrane2 on 2021-08-10
Sorry for not responding I've been busy, I'll post it tomorrow.

---

### Post by zeframcochrane2 on 2021-08-12
lshw
lisa-system-product-name
    description: Desktop Computer
    product: System Product Name (To Be Filled By O.E.M.)
    vendor: System manufacturer
    version: System Version
    serial: System Serial Number
    width: 64 bits
    capabilities: smbios-2.5 dmi-2.5 smp vsyscall32
    configuration: boot=normal chassis=desktop family=To Be Filled By O.E.M. sku=To Be Filled By O.E.M. uuid=2071CC0F-35F7-0412-ABCA-04D4C456D145
  *-core
       description: Motherboard
       product: M5A78L-M PLUS/USB3
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: Rev X.0x
       serial: 190448605200317
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 0502
          date: 11/18/2016
          size: 64KiB
          capacity: 2MiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Phenom(tm) II X4 960T Processor
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: AMD Phenom(tm) II X4 960T Processor
          serial: To Be Filled By O.E.M.
          slot: AM3R2
          size: 3GHz
          capacity: 3GHz
          width: 64 bits
          clock: 200MHz
          capabilities: lm fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp x86-64 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc cpuid extd_apicid aperfmperf pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt nodeid_msr cpb hw_pstate vmmcall npt lbrv svm_lock nrip_save pausefilter
          configuration: cores=4 enabledcores=4 threads=4
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 512KiB
             capacity: 512KiB
             clock: 1GHz (1.0ns)
             capabilities: pipeline-burst internal write-back unified
             configuration: level=1
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 2MiB
             capacity: 2MiB
             clock: 1GHz (1.0ns)
             capabilities: pipeline-burst internal write-back unified
             configuration: level=2
        *-cache:2
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             size: 6MiB
             capacity: 6MiB
             clock: 1GHz (1.0ns)
             capabilities: pipeline-burst internal write-back unified
             configuration: level=3
     *-memory
          description: System Memory
          physical id: 2d
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM [empty]
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
        *-bank:1
             description: DIMM [empty]
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
        *-bank:2
             description: DIMM DDR3 Synchronous 1600 MHz (0.6 ns)
             product: PartNum2
             vendor: Manufacturer2
             physical id: 2
             serial: SerNum2
             slot: DIMM2
             size: 4GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
        *-bank:3
             description: DIMM [empty]
             product: PartNum3
             vendor: Manufacturer3
             physical id: 3
             serial: SerNum3
             slot: DIMM3
     *-pci:0
          description: Host bridge
          product: RS780 Host Bridge
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
        *-pci:0
             description: PCI bridge
             product: RS780 PCI to PCI bridge (ext gfx port 0)
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:d000(size=4096) memory:fe800000-fe8fffff ioport:d0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: Caicos [Radeon HD 6450/7450/8450 / R5 230 OEM]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=0
                resources: irq:39 memory:d0000000-dfffffff memory:fe8e0000-fe8fffff ioport:d000(size=256) memory:c0000-dffff
           *-multimedia
                description: Audio device
                product: Caicos HDMI Audio [Radeon HD 6450 / 7450/8450/8490 OEM / R5 230/235/235X OEM]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:40 memory:fe8bc000-fe8bffff
        *-pci:1
             description: PCI bridge
             product: RS780/RS880 PCI to PCI bridge (PCIE port 3)
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 memory:fe900000-fe9fffff
           *-usb
                description: USB controller
                product: ASM1042A USB 3.0 Host Controller
                vendor: ASMedia Technology Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: msi msix pm pciexpress xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:19 memory:fe9f8000-fe9fffff
              *-usbhost:0
                   product: xHCI Host Controller
                   vendor: Linux 5.4.0-80-generic xhci-hcd
                   physical id: 0
                   bus info: usb@8
                   logical name: usb8
                   version: 5.04
                   capabilities: usb-2.00
                   configuration: driver=hub slots=2 speed=480Mbit/s
                 *-usb
                      description: Keyboard
                      product: 2.4G Composite Devic
                      physical id: 1
                      bus info: usb@8:1
                      version: 2.00
                      capabilities: usb-1.10
                      configuration: driver=usbhid maxpower=100mA speed=12Mbit/s
              *-usbhost:1
                   product: xHCI Host Controller
                   vendor: Linux 5.4.0-80-generic xhci-hcd
                   physical id: 1
                   bus info: usb@9
                   logical name: usb9
                   version: 5.04
                   capabilities: usb-3.00
                   configuration: driver=hub slots=2 speed=5000Mbit/s
        *-pci:2
             description: PCI bridge
             product: RS780/RS880 PCI to PCI bridge (PCIE port 4)
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 9
             bus info: pci@0000:00:09.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 memory:fea00000-feafffff
           *-usb
                description: USB controller
                product: ASM1042A USB 3.0 Host Controller
                vendor: ASMedia Technology Inc.
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: msi msix pm pciexpress xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:17 memory:feaf8000-feafffff
              *-usbhost:0
                   product: xHCI Host Controller
                   vendor: Linux 5.4.0-80-generic xhci-hcd
                   physical id: 0
                   bus info: usb@10
                   logical name: usb10
                   version: 5.04
                   capabilities: usb-2.00
                   configuration: driver=hub slots=2 speed=480Mbit/s
              *-usbhost:1
                   product: xHCI Host Controller
                   vendor: Linux 5.4.0-80-generic xhci-hcd
                   physical id: 1
                   bus info: usb@11
                   logical name: usb11
                   version: 5.04
                   capabilities: usb-3.00
                   configuration: driver=hub slots=2 speed=5000Mbit/s
        *-pci:3
             description: PCI bridge
             product: RS780/RS880 PCI to PCI bridge (PCIE port 5)
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: a
             bus info: pci@0000:00:0a.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:27 ioport:e000(size=4096) memory:feb00000-febfffff
           *-network
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:04:00.0
                logical name: enp4s0
                version: 15
                serial: 04:d4:c4:56:d1:45
                size: 1Gbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 duplex=full firmware=rtl8168h-2_0.0.2 02/26/15 ip=192.168.1.80 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
                resources: irq:18 ioport:e800(size=256) memory:febff000-febfffff memory:febf8000-febfbfff
        *-sata
             description: SATA controller
             product: SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode]
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: sata pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=64
             resources: irq:22 ioport:c000(size=8) ioport:b000(size=4) ioport:a000(size=8) ioport:9000(size=4) ioport:8000(size=16) memory:fe7ffc00-fe7fffff
        *-usb:0
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=64
             resources: irq:16 memory:fe7fe000-fe7fefff
           *-usbhost
                product: OHCI PCI host controller
                vendor: Linux 5.4.0-80-generic ohci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 5.04
                capabilities: usb-1.10
                configuration: driver=hub slots=3 speed=12Mbit/s
        *-usb:1
             description: USB controller
             product: SB7x0 USB OHCI1 Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 12.1
             bus info: pci@0000:00:12.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=64
             resources: irq:16 memory:fe7fd000-fe7fdfff
           *-usbhost
                product: OHCI PCI host controller
                vendor: Linux 5.4.0-80-generic ohci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 5.04
                capabilities: usb-1.10
                configuration: driver=hub slots=3 speed=12Mbit/s
        *-usb:2
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=64
             resources: irq:17 memory:fe7ff800-fe7ff8ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 5.4.0-80-generic ehci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 5.04
                capabilities: usb-2.00
                configuration: driver=hub slots=6 speed=480Mbit/s
        *-usb:3
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=64
             resources: irq:18 memory:fe7fc000-fe7fcfff
           *-usbhost
                product: OHCI PCI host controller
                vendor: Linux 5.4.0-80-generic ohci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 5.04
                capabilities: usb-1.10
                configuration: driver=hub slots=3 speed=12Mbit/s
        *-usb:4
             description: USB controller
             product: SB7x0 USB OHCI1 Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=64
             resources: irq:18 memory:fe7fb000-fe7fbfff
           *-usbhost
                product: OHCI PCI host controller
                vendor: Linux 5.4.0-80-generic ohci_hcd
                physical id: 1
                bus info: usb@6
                logical name: usb6
                version: 5.04
                capabilities: usb-1.10
                configuration: driver=hub slots=3 speed=12Mbit/s
        *-usb:5
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=64
             resources: irq:19 memory:fe7ff400-fe7ff4ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 5.4.0-80-generic ehci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 5.04
                capabilities: usb-2.00
                configuration: driver=hub slots=6 speed=480Mbit/s
        *-serial UNCLAIMED
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 3c
             width: 32 bits
             clock: 66MHz
             capabilities: ht cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: SB7x0/SB8x0/SB9x0 IDE Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide msi isa_compat_mode pci_native_mode bus_master cap_list
             configuration: driver=pata_atiixp latency=64
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ff00(size=16)
        *-multimedia
             description: Audio device
             product: SBx00 Azalia (Intel HDA)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_hda_intel latency=64
             resources: irq:16 memory:fe7f4000-fe7f7fff
        *-isa
             description: ISA bridge
             product: SB7x0/SB8x0/SB9x0 LPC host controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:4
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
        *-usb:6
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=64
             resources: irq:18 memory:fe7fa000-fe7fafff
           *-usbhost
                product: OHCI PCI host controller
                vendor: Linux 5.4.0-80-generic ohci_hcd
                physical id: 1
                bus info: usb@7
                logical name: usb7
                version: 5.04
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
     *-pci:1
          description: Host bridge
          product: Family 10h Processor HyperTransport Configuration
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Family 10h Processor Address Map
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Family 10h Processor DRAM Controller
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Family 10h Processor Miscellaneous Control
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k10temp
          resources: irq:0
     *-pci:5
          description: Host bridge
          product: Family 10h Processor Link Control
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pnp00:00
          product: PnP device PNP0c02
          physical id: 1
          capabilities: pnp
          configuration: driver=system
     *-pnp00:01
          product: PnP device PNP0b00
          physical id: 2
          capabilities: pnp
          configuration: driver=rtc_cmos
     *-pnp00:02
          product: PnP device PNP0400
          physical id: 3
          capabilities: pnp
          configuration: driver=parport_pc
     *-pnp00:03
          product: PnP device PNP0501
          physical id: 5
          capabilities: pnp
          configuration: driver=serial
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
          product: PnP device PNP0c02
          physical id: 9
          capabilities: pnp
          configuration: driver=system
     *-pnp00:08
          product: PnP device PNP0c01
          physical id: a
          capabilities: pnp
          configuration: driver=system
     *-scsi
          physical id: b
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD10EZRZ-00H
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 1A01
             serial: WD-WCC4J1SXJXLJ
             size: 931GiB (1TB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=4096 signature=3cca2b2c
           *-volume
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: 0f03cd02-3a27-4658-b5b9-17029e334cdc
                size: 931GiB
                capacity: 931GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover 64bit extents ext4 ext2 initialized
                configuration: created=2019-12-10 18:27:31 filesystem=ext4 lastmountpoint=/ modified=2021-08-11 20:58:37 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro mounted=2021-08-11 20:58:43 state=mounted

---

### Post by zeframcochrane2 on 2021-08-12
Static hostname: lisa-System-Product-Name
         Icon name: computer-desktop
           Chassis: desktop
        Machine ID: 33d33fef6d4648f1ac3375e9ff5de85a
           Boot ID: 57c8e947427941a0a740f5bb64e4aaee
  Operating System: Ubuntu 20.04.2 LTS
            Kernel: Linux 5.4.0-80-generic
      Architecture: x86-64

---

### Post by zeframcochrane2 on 2021-08-12
im not sure how to do the wrap

---

### Post by mIk3_08 on 2021-08-12
```
Caicos HDMI Audio [Radeon HD 6450 / 7450/8450/8490 OEM / R5 230/235/235X OEM]     sound     snd_hda_intel     detected
PCI     8086:3a6e:1028:0420 / 04-03     Intel Corporation     82801JD/DO (ICH10 Family) HD Audio Controller
```
This device is already known to have some problems in Linux. It has been detected properly but is already known to have some issues in HD Audio Controller.
I think this could be the audio hardware compatibility issue in Linux. Don't worry about this maybe other here in the community knows 
the solution of this audio hardware.

---

### Post by zeframcochrane2 on 2021-08-14
I actually don’t use the hdmi for sound I use the built in sound card.

---

### Post by zeframcochrane2 on 2021-08-14
So I seemed to have fixed it, if I use the command pulseaudio --start it works, but if I reboot then I have to re enter it. Is there a way to have this command run after boot up?

---

### Post by mIk3_08 on 2021-08-15
Have you already installed pulseaudio tools into your system? 
> **zeframcochrane2 said:**
> So I seemed to have fixed it, if I use  the command pulseaudio --start it works, but if I reboot then I have to  re enter it. Is there a way to have this command run after boot  up?
For an easy and handful scripting you can enter the command to the start-up application. But if you are good enough to code it to your system
You can explore to the audio system pulse audio script audio py or you can use configuration editor or dconf editor 
for modification to your system. It might be tricky but maybe it helps you a lot. Good Luck and Enjoy.

---

