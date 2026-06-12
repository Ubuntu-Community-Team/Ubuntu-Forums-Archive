---
title: "Browsing has become slow"
date: 2017-04-23
forum: General Help
---

### Post by dshah on 2017-04-23
From few days my web browsers are taking huge CPU usage like 130%+, webites are very slow while loading. When I close the browser CPU goes normal. It happens both on crhome and fireox, what could be the issue? I am using Ubuntu 14.04.

here my lshw

```

dell                      
    description: Laptop
    product: Latitude E6540 (05BE)
    vendor: Dell Inc.
    version: 00
    serial: G790VZ1
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 vsyscall32
    configuration: administrator_password=disabled boot=normal chassis=laptop frontpanel_password=disabled keyboard_password=disabled power-on_password=disabled sku=05BE uuid=44454C4C-3700-1039-8030-C7C04F565A31
  *-core
       description: Motherboard
       product: 0725FP
       vendor: Dell Inc.
       physical id: 0
       version: A00
       serial: /G790VZ1/CN1296341R00C7/
     *-firmware
          description: BIOS
          vendor: Dell Inc.
          physical id: 0
          version: A19
          date: 12/22/2016
          size: 64KiB
          capacity: 11MiB
          capabilities: pci pnp upgrade shadowing cdboot bootselect edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb smartbattery biosbootspecification netboot uefi
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i7-4800MQ CPU @ 2.70GHz
          vendor: Intel Corp.
          physical id: 43
          bus info: cpu@0
          version: Intel(R) Core(TM) i7-4800MQ CPU @ 2.70GHz
          slot: SOCKET 0
          size: 364MHz
          capacity: 364MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm epb tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid xsaveopt dtherm ida arat pln pts cpufreq
          configuration: cores=4 enabledcores=4 threads=8
        *-cache:0
             description: L1 cache
             physical id: 44
             slot: CPU Internal L1
             size: 256KiB
             capacity: 256KiB
             capabilities: internal write-back
        *-cache:1
             description: L2 cache
             physical id: 45
             slot: CPU Internal L2
             size: 1MiB
             capacity: 1MiB
             capabilities: internal write-back unified
        *-cache:2
             description: L3 cache
             physical id: 46
             slot: CPU Internal L3
             size: 6MiB
             capacity: 6MiB
             capabilities: internal write-back unified
     *-memory
          description: System Memory
          physical id: 47
          slot: System board or motherboard
          size: 8GiB
        *-bank:0
             description: SODIMM DDR3 Synchronous 1600 MHz (0.6 ns)
             product: M471B1G73QH0-YK0
             vendor: Samsung
             physical id: 0
             serial: FFE18996
             slot: DIMM A
             size: 8GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
        *-bank:1
             description: DIMM [empty]
             product: [Empty]
             vendor: [Empty]
             physical id: 1
             serial: [Empty]
             slot: DIMM B
     *-pci
          description: Host bridge
          product: Xeon E3-1200 v3/4th Gen Core Processor DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 06
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 ioport:e000(size=4096) memory:f7c00000-f7cfffff ioport:e0000000(size=268435456)
           *-generic
                description: Unassigned class
                product: Illegal Vendor ID
                vendor: Illegal Vendor ID
                physical id: 0
                bus info: pci@0000:01:00.0
                version: ff
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master vga_palette cap_list rom
                configuration: driver=radeon latency=255 maxlatency=255 mingnt=255
                resources: irq:35 memory:e0000000-efffffff memory:f7c00000-f7c3ffff ioport:e000(size=256) memory:f7c40000-f7c5ffff
        *-display
             description: VGA compatible controller
             product: 4th Gen Core Processor Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 06
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:33 memory:f5800000-f5bfffff memory:d0000000-dfffffff ioport:f000(size=64)
        *-multimedia:0
             description: Audio device
             product: Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller
             vendor: Intel Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 06
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:34 memory:f7d34000-f7d37fff
        *-usb:0
             description: USB controller
             product: 8 Series/C220 Series Chipset Family USB xHCI
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:27 memory:f7d20000-f7d2ffff
        *-communication
             description: Communication controller
             product: 8 Series/C220 Series Chipset Family MEI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:30 memory:f7d40000-f7d4000f
        *-network
             description: Ethernet interface
             product: Ethernet Connection I217-LM
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@0000:00:19.0
             logical name: eth0
             version: 04
             serial: ec:f4:bb:08:81:69
             capacity: 1Gbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k firmware=0.13-3 latency=0 link=no multicast=yes port=twisted pair
             resources: irq:29 memory:f7d00000-f7d1ffff memory:f7d3d000-f7d3dfff ioport:f080(size=32)
        *-usb:1
             description: USB controller
             product: 8 Series/C220 Series Chipset Family USB EHCI #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:16 memory:f7d3c000-f7d3c3ff
        *-multimedia:1
             description: Audio device
             product: 8 Series/C220 Series Chipset High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:31 memory:f7d30000-f7d33fff
        *-pci:1
             description: PCI bridge
             product: 8 Series/C220 Series Chipset Family PCI Express Root Port #1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: d4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:2000(size=4096) memory:cf200000-cf3fffff ioport:cf400000(size=2097152)
        *-pci:2
             description: PCI bridge
             product: 8 Series/C220 Series Chipset Family PCI Express Root Port #3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: d4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:18 memory:f7b00000-f7bfffff
           *-network
                description: Wireless interface
                product: Centrino Advanced-N 6235
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlan0
                version: 24
                serial: c4:d9:87:40:c7:25
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlwifi driverversion=4.4.0-72-generic firmware=18.168.6.1 ip=192.168.1.10 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
                resources: irq:32 memory:f7b00000-f7b01fff
        *-pci:3
             description: PCI bridge
             product: 8 Series/C220 Series Chipset Family PCI Express Root Port #5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: d4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:d000(size=4096) memory:f7000000-f79fffff ioport:f1400000(size=10485760)
        *-pci:4
             description: PCI bridge
             product: 8 Series/C220 Series Chipset Family PCI Express Root Port #6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: d4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:c000(size=4096) memory:f6600000-f6ffffff ioport:f0a00000(size=10485760)
        *-pci:5
             description: PCI bridge
             product: 8 Series/C220 Series Chipset Family PCI Express Root Port #7
             vendor: Intel Corporation
             physical id: 1c.6
             bus info: pci@0000:00:1c.6
             version: d4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:18 ioport:a000(size=8192) memory:f5c00000-f65fffff ioport:f0000000(size=10485760)
        *-pci:6
             description: PCI bridge
             product: 8 Series/C220 Series Chipset Family PCI Express Root Port #8
             vendor: Intel Corporation
             physical id: 1c.7
             bus info: pci@0000:00:1c.7
             version: d4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:19 memory:f7a00000-f7afffff
           *-generic
                description: SD Host controller
                product: SD/MMC Card Reader Controller
                vendor: O2 Micro, Inc.
                physical id: 0
                bus info: pci@0000:0e:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=sdhci-pci latency=0
                resources: irq:19 memory:f7a01000-f7a01fff memory:f7a00000-f7a007ff
        *-usb:2
             description: USB controller
             product: 8 Series/C220 Series Chipset Family USB EHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:21 memory:f7d3b000-f7d3b3ff
        *-isa
             description: ISA bridge
             product: QM87 Express LPC Controller
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
             description: RAID bus controller
             product: 82801 Mobile SATA Controller [RAID mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:28 ioport:f0d0(size=8) ioport:f0c0(size=4) ioport:f0b0(size=8) ioport:f0a0(size=4) ioport:f060(size=32) memory:f7d3a000-f7d3a7ff
        *-serial UNCLAIMED
             description: SMBus
             product: 8 Series/C220 Series Chipset Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 04
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f7d39000-f7d390ff ioport:f040(size=32)
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST500LM000-1EJ16
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: DEM6
             serial: W3720V3W
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=4096 signature=a6c41edf
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                version: 3.1
                serial: 5835-4fa2
                size: 98MiB
                capacity: 100MiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2014-04-25 06:26:55 filesystem=ntfs label=System Reserved state=clean
           *-volume:1
                description: Windows NTFS volume
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                version: 3.1
                serial: b2bb6bb7-9142-7a4d-8566-262aa1cee570
                size: 365GiB
                capacity: 365GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2014-04-25 06:26:58 filesystem=ntfs state=clean
           *-volume:2
                description: Linux swap volume
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                version: 1
                serial: 92ee646d-f5b6-4f2a-b815-aad09db3d713
                size: 7629MiB
                capacity: 7629MiB
                capabilities: primary nofs swap initialized
                configuration: filesystem=swap pagesize=4096
           *-volume:3
                description: EXT4 volume
                vendor: Linux
                physical id: 4
                bus info: scsi@0:0.0.0,4
                logical name: /dev/sda4
                logical name: /
                version: 1.0
                serial: be70a3c7-b982-4b92-b531-cff6668d15a7
                size: 92GiB
                capacity: 92GiB
                capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2015-08-04 14:56:31 filesystem=ext4 lastmountpoint=/ modified=2017-04-23 16:54:15 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2017-04-23 16:54:15 state=mounted
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVD+-RW UJ8DB
             vendor: MATSHITA
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: D.03
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc

```

Thanks

---

### Post by RobGoss on 2017-04-23
Hello and welcome to the forum, Have you tried disabling your browser extensions to see if it would help speed up things

Somethings the add-ons can interfere with the browser performance. I'm aware you mentioned you're having this issue with both Goggle chrome and Firefox, but I still think this would be a good start

---

### Post by dshah on 2017-04-24
Thanks for answer, I have done that but I suspect that is the issue. I see whole system lagging, when I open explorer, or other apps...it takes CPU over 300% some times, Not just with browsers, also I noticed with top command a process compiz takes like 50% of CPU. Whole system is lagging...

---

### Post by RobGoss on 2017-04-24
Compiz will use more of your system resources and slow things down

---

### Post by dshah on 2017-04-24
what should I do? I am thinking to reinstall _Ubuntu _but I have a lot of data and settings to backup which is currently not possible.  
Thanks again....

---

### Post by deadflowr on 2017-04-24
I'd investigate more on this section here:
```
*-generic
                description: Unassigned class
                product: Illegal Vendor ID
                vendor: Illegal Vendor ID
                physical id: 0
                bus info: pci@0000:01:00.0
                version: ff
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master vga_palette cap_list rom
                configuration: driver=radeon latency=255 maxlatency=255 mingnt=255
                resources: irq:35 memory:e0000000-efffffff memory:f7c00000-f7c3ffff ioport:e000(size=256) memory:f7c40000-f7c5ffff
```

looks like somehow the gpu isn't properly being recognized...
I mean it's showing a driver for something it doesn't even know what it is?
What does 
```
lspci | grep VGA
```
show?

---

### Post by dshah on 2017-04-25
thanks, output
```
$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Mars XTX [Radeon HD 8790M] (rev ff)
```

---

### Post by mörgæs on 2017-04-27
> **dshah said:**
> I am thinking to reinstall Ubuntu ...

Yes, that might be the solution. I suggest that you first try a live boot of 16.04.2 and/or 17.04 and run lshw in both. Look for how the graphics processor is identified in these as pointed out by Deadflowr.

---

