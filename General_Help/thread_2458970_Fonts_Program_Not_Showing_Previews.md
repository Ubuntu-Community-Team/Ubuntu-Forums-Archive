---
title: "Fonts Program Not Showing Previews"
date: 2021-03-08
forum: General Help
---

### Post by rebeltaz on 2021-03-08
I took the ssd drive out of my old laptop and dropped it in my new-to-me laptop. I'm running 18.04 LTS and the last time I ran Fonts, it worked fine. I don't know why putting the drive in another system, without changing anything else would break that, but...

The Fonts program is lists all of the fonts and I can preview them if I click on each one, but there is no preview on the main page. Every single font is shown as a page with an A in the middle. 

Is there some way I can fix this?

EDIT: OK... so apparently there is also a graphics issue because at least one program isn't showing up right. Not sure if this is related or not, but...


[ATTACH=CONFIG]288081[/ATTACH]

[ATTACH=CONFIG]288082[/ATTACH]

Just spitballing here, but if I were to run a distro upgrade to 20 LTS, would that correct driver issues?

---

### Post by CelticWarrior on 2021-03-08
> [COLOR=#000000]if I were to run a distro upgrade to 20 LTS, would that correct driver issues?[/COLOR]
No.
IF you need additional proprietary drivers that aren't installed already the release upgrade won't install them.

Please post the new hardware specifications with special attention to the graphics.

---

### Post by rebeltaz on 2021-03-08
I wasn't sure what would or wouldn't be helpful, so:

```

sudo lshw

laptop                      
    description: Laptop
    product: Latitude E7450 (062E)
    vendor: Dell Inc.
    serial: 5HDJT32
    width: 64 bits
    capabilities: smbios-2.8 dmi-2.8 smp vsyscall32
    configuration: administrator_password=disabled boot=normal chassis=laptop frontpanel_password=disabled keyboard_password=disabled power-on_password=disabled sku=062E uuid=44454C4C-4800-1044-804A-B5C04F543332
  *-core
       description: Motherboard
       product: 06HN6G
       vendor: Dell Inc.
       physical id: 0
       version: A00
       serial: /5HDJT32/CN129635720264/
     *-firmware
          description: BIOS
          vendor: Dell Inc.
          physical id: 0
          version: A21
          date: 05/16/2019
          size: 64KiB
          capacity: 11MiB
          capabilities: pci pnp upgrade shadowing cdboot bootselect edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb smartbattery biosbootspecification netboot uefi
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i7-5600U CPU @ 2.60GHz
          vendor: Intel Corp.
          physical id: 4d
          bus info: cpu@0
          version: Intel(R) Core(TM) i7-5600U CPU @ 2.60GHz
          serial: NULL
          slot: SOCKET 0
          size: 3163MHz
          capacity: 3200MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch cpuid_fault epb invpcid_single pti ssbd ibrs ibpb stibp tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 hle avx2 smep bmi2 erms invpcid rtm rdseed adx smap intel_pt xsaveopt dtherm ida arat pln pts md_clear flush_l1d cpufreq
          configuration: cores=2 enabledcores=2 threads=4
        *-cache:0
             description: L1 cache
             physical id: 3e
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back instruction
             configuration: level=1
        *-cache:1
             description: L2 cache
             physical id: 43
             slot: L2 Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: synchronous internal write-back unified
             configuration: level=2
        *-cache:2
             description: L3 cache
             physical id: 48
             slot: L3 Cache
             size: 4MiB
             capacity: 4MiB
             capabilities: synchronous internal write-back unified
             configuration: level=3
     *-cache
          description: L1 cache
          physical id: 39
          slot: L1 Cache
          size: 32KiB
          capacity: 32KiB
          capabilities: synchronous internal write-back data
          configuration: level=1
     *-memory
          description: System Memory
          physical id: 52
          slot: System board or motherboard
          size: 8GiB
        *-bank:0
             description: SODIMM DDR3 Synchronous 1600 MHz (0.6 ns)
             product: HMT451S6BFR8A-PB
             vendor: Hynix/Hyundai
             physical id: 0
             serial: D48B83BB
             slot: DIMM A
             size: 4GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
        *-bank:1
             description: SODIMM DDR3 Synchronous 1600 MHz (0.6 ns)
             product: HMT451S6BFR8A-PB
             vendor: Hynix/Hyundai
             physical id: 1
             serial: 918BF3BB
             slot: DIMM B
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
             resources: irq:49 memory:f6000000-f6ffffff memory:e0000000-efffffff ioport:f000(size=64) memory:c0000-dffff
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
             resources: irq:51 memory:f723c000-f723ffff
        *-generic
             description: Signal processing controller
             product: Broadwell-U Processor Thermal Subsystem
             vendor: Intel Corporation
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list
             configuration: driver=proc_thermal latency=0
             resources: irq:16 memory:f7230000-f7237fff
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
             resources: irq:45 memory:f7220000-f722ffff
           *-usbhost:0
                product: xHCI Host Controller
                vendor: Linux 4.15.0-136-generic xhci-hcd
                physical id: 0
                bus info: usb@2
                logical name: usb2
                version: 4.15
                capabilities: usb-2.00
                configuration: driver=hub slots=11 speed=480Mbit/s
              *-usb
                   description: Mouse
                   product: Kensington USB/PS2 Orbit
                   vendor: Kensington
                   physical id: 2
                   bus info: usb@2:2
                   version: 4.00
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=100mA speed=2Mbit/s
           *-usbhost:1
                product: xHCI Host Controller
                vendor: Linux 4.15.0-136-generic xhci-hcd
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
             resources: irq:48 memory:f7246000-f724601f
        *-network
             description: Ethernet interface
             product: Ethernet Connection (3) I218-LM
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@0000:00:19.0
             logical name: eno1
             version: 03
             serial: 20:47:47:a8:7a:07
             capacity: 1Gbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k firmware=0.2-3 latency=0 link=no multicast=yes port=twisted pair
             resources: irq:47 memory:f7200000-f721ffff memory:f7243000-f7243fff ioport:f080(size=32)
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
             configuration: driver=snd_hda_intel latency=32
             resources: irq:50 memory:f7238000-f723bfff
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
             resources: irq:42 memory:f7100000-f71fffff
           *-generic
                description: SD Host controller
                product: SD/MMC Card Reader Controller
                vendor: O2 Micro, Inc.
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=sdhci-pci latency=0
                resources: irq:16 memory:f7101000-f7101fff memory:f7100000-f71007ff
        *-pci:1
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
             resources: irq:43 memory:f7000000-f70fffff
           *-network
                description: Wireless interface
                product: Wireless 7265
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlp2s0
                version: 59
                serial: 5c:e0:c5:65:ef:d7
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlwifi driverversion=4.15.0-136-generic firmware=29.1044073957.0 ip=192.168.1.5 latency=0 link=yes multicast=yes wireless=IEEE 802.11
                resources: irq:52 memory:f7000000-f7001fff
        *-pci:2
             description: PCI bridge
             product: Wildcat Point-LP PCI Express Root Port #5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: e3
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:44
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
             resources: irq:21 memory:f7242000-f72423ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.15.0-136-generic ehci_hcd
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
                 *-usb
                      description: Bluetooth wireless interface
                      vendor: Intel Corp.
                      physical id: 3
                      bus info: usb@1:1.3
                      version: 0.01
                      capabilities: bluetooth usb-2.01
                      configuration: driver=btusb maxpower=100mA speed=12Mbit/s
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
             description: RAID bus controller
             product: 82801 Mobile SATA Controller [RAID mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:46 ioport:f0d0(size=8) ioport:f0c0(size=4) ioport:f0b0(size=8) ioport:f0a0(size=4) ioport:f060(size=32) memory:f7241000-f72417ff
        *-serial UNCLAIMED
             description: SMBus
             product: Wildcat Point-LP SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f7240000-f72400ff ioport:f040(size=32)
     *-scsi
          physical id: 1
          logical name: scsi1
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: Samsung SSD 850
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/sda
             version: 2B6Q
             serial: S2RANX0HA45855E
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=c1e7da95
           *-volume
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@1:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: bef42d94-85c2-4fe1-9147-1ee90251b849
                size: 465GiB
                capacity: 465GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover 64bit extents ext4 ext2 initialized
                configuration: created=2018-08-27 01:23:39 filesystem=ext4 lastmountpoint=/ modified=2021-03-08 00:37:22 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2021-03-08 00:37:23 state=mounted
  *-battery
       product: DELL 0D47W
       vendor: LG
       physical id: 1
       version: 11/06/2017
       serial: 0038
       slot: Sys. Battery Bay
       capacity: 47120mWh
       configuration: voltage=7.6V

```

---

### Post by rebeltaz on 2021-03-12
Oddly enough, after I've rebooted a few times, it seems to have fixed itself, so... yeah.

---

