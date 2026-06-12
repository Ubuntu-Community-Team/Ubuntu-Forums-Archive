---
title: "Consistent display freeze after some time"
date: 2017-03-28
forum: General Help
---

### Post by ojima on 2017-03-28
For quite a while now, I've had some issues with Ubuntu, in that the display keeps freezing after some time (usually 5-30 minutes). I feel like I've tried searching for the problem over and over again, trying various solutions (from upgrading to the RC linux kernel to purging and fresh installing graphics drivers), but nothing helps or solves the problem permanently. The greatest problem I deal with is the fact that I don't know where the problem lies or where to look: I've looked in crash logs, system descriptions etc, but in vain. The only thing that appears to help (somewhat) is by running in an older kernel version (the one I have installed is 4.7.0-040700rc3-generic), but even that doesn't always work.

The freeze usually happens after 5 to 30 minutes, and it results in the display freezing (sometimes the mouse still works for a few seconds before it too freezes). I suspect it's a problem with my GPU driver (or a combination of GPU driver with kernel), since sound and mouse/keyboard input *don't* stop working. I then have to reboot my computer either by holding down the power key or by using the magic SysRq key. If I directly reboot into Ubuntu, it tends to freeze again after only one or two minutes, but if I reboot into Windows first (I have a dual boot), use that for a while, and then return to Ubuntu, it once again takes 5 to 30 minutes.

My computer specs:
OS: Ubuntu 16.10
Memory: 15,6 GiB
Processor: Intel® Core™ i7-4770 CPU @ 3.40GHz × 8
Graphics: GeForce GTX 760 (192-bit)/PCIe/SSE2
Graphics driver: NVidia
OS type: 64-bit
Disk: 1,1 TB

If you have any ideas (or any suggestions where to look), please let me know or ask if you want to know more.

---

### Post by dragonfly41 on 2017-03-28
This subject seems to be popping up quite frequently.

Take a look at post #16 here [https://ubuntuforums.org/showthread.php?t=2356585&page=2](https://ubuntuforums.org/showthread.php?t=2356585&page=2)

and see if they help.

When it freezes again see if you can switch to console using Ctrl+Alt+F1 then back to Ctrl+Alt+F7
since this sometimes unfreezes.

Since unticking hardware acceleration in Chromium Settings my recent frequent freezes have stopped.
But I have an old laptop running 14.04 and only 3GB memory.

---

### Post by ojima on 2017-03-28
Thanks for your response!

I've tried unticking hardware acceleration in chromium, I'll see if it works.

I've tried Ctrl+Alt+F1 before, but it doesn't seem to work.

---

### Post by ojima on 2017-03-30
Well, I've tried disabling hardware acceleration in Chromium and to no avail: my computer still freezes after some ~20 minutes of use.

---

### Post by dragonfly41 on 2017-03-30
I must be lucky since I no longer experience freezing with hardware acceleration turned off.

I can only suggest that you try the other possible fixes which are listed in that post #16 I referred you to.

**[1]**
Reference ... [https://github.com/l3ib/nitrogen/issues/51](https://github.com/l3ib/nitrogen/issues/51)

Install dconf editor
Launch dconf editor and navigate to /org/gnome/desktop/background/show-desktop-icons true
Check that this is set to true.

**[2]**
Try installing gnome flashback and after reboot use instead of Unity.

[http://www.debugpoint.com/2016/04/install-classic-gnome-flashback-in-ubuntu-16-04-replacing-unity/#](http://www.debugpoint.com/2016/04/install-classic-gnome-flashback-in-ubuntu-16-04-replacing-unity/#)

And ...

**[3]**
Run a memory test on your memory.

---

### Post by ojima on 2017-03-31
I was actually surprised, but **none of those things you suggested actually worked**

*Install dconf editor*: I already had that setting turned to "true"
*installing gnome flashback*: Tried it, didn't work (it actually crashed while I was using the first time-setup, and multiple times after that as if I was using Unity)
*run a memory test*: yielded no results.

For those of you who want to help out, here's the complete output of lshw:
```
ojima-ubuntu                
    description: Desktop Computer
    product: MS-7848
    vendor: MEDION
    version: 1.0
    serial: E316635659
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 smp vsyscall32
    configuration: administrator_password=disabled chassis=desktop frontpanel_password=disabled keyboard_password=disabled power-on_password=disabled uuid=3024969E-4EC5-E311-8EE8-901B6DF32C00
  *-core
       description: Motherboard
       product: MS-7848
       vendor: MEDION
       physical id: 0
       version: 1.0
       serial: E316635659
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: M7848W08.20E
          date: 03/19/2014
          size: 64KiB
          capacity: 4032KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification uefi
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i7-4770 CPU @ 3.40GHz
          vendor: Intel Corp.
          physical id: 25
          bus info: cpu@0
          version: Intel(R) Core(TM) i7-4770 CPU @ 3.40GHz
          slot: SOCKET 0
          size: 3405MHz
          capacity: 3900MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm epb tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid xsaveopt dtherm ida arat pln pts cpufreq
          configuration: cores=4 enabledcores=4 threads=8
        *-cache:0
             description: L2 cache
             physical id: 26
             slot: CPU Internal L2
             size: 1MiB
             capacity: 1MiB
             capabilities: internal write-back unified
             configuration: level=2
        *-cache:1
             description: L1 cache
             physical id: 27
             slot: CPU Internal L1
             size: 256KiB
             capacity: 256KiB
             capabilities: internal write-back
             configuration: level=1
        *-cache:2
             description: L3 cache
             physical id: 28
             slot: CPU Internal L3
             size: 8MiB
             capacity: 8MiB
             capabilities: internal write-back unified
             configuration: level=3
     *-memory
          description: System Memory
          physical id: 29
          slot: System board or motherboard
          size: 16GiB
        *-bank:0
             description: DIMM DDR3 Synchronous 1600 MHz (0,6 ns)
             product: M2F8G64CB8HC5N-DI
             vendor: Conexant (Rockwell)
             physical id: 0
             serial: 2CD6223C
             slot: ChannelA-DIMM0
             size: 8GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
        *-bank:1
             description: DIMM [empty]
             product: [Empty]
             vendor: [Empty]
             physical id: 1
             serial: [Empty]
             slot: ChannelA-DIMM1
        *-bank:2
             description: DIMM DDR3 Synchronous 1600 MHz (0,6 ns)
             product: M2F8G64CB8HC5N-DI
             vendor: Conexant (Rockwell)
             physical id: 2
             serial: DDD5223C
             slot: ChannelB-DIMM0
             size: 8GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
        *-bank:3
             description: DIMM [empty]
             product: [Empty]
             vendor: [Empty]
             physical id: 3
             serial: [Empty]
             slot: ChannelB-DIMM1
     *-pci
          description: Host bridge
          product: 4th Gen Core Processor DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 06
          width: 32 bits
          clock: 33MHz
          configuration: driver=hsw_uncore
          resources: irq:0
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
             resources: irq:25 ioport:e000(size=4096) memory:f6000000-f70fffff ioport:e8000000(size=167772160)
           *-display
                description: VGA compatible controller
                product: GK104 [GeForce GTX 760 OEM]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:33 memory:f6000000-f6ffffff memory:e8000000-efffffff memory:f0000000-f1ffffff ioport:e000(size=128) memory:c0000-dffff
           *-multimedia
                description: Audio device
                product: GK104 HDMI Audio Controller
                vendor: NVIDIA Corporation
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:17 memory:f7080000-f7083fff
        *-usb:0
             description: USB controller
             product: 8 Series/C220 Series Chipset Family USB xHCI
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:29 memory:f7200000-f720ffff
           *-usbhost:0
                product: xHCI Host Controller
                vendor: Linux 4.7.0-040700rc3-generic xhci-hcd
                physical id: 0
                bus info: usb@3
                logical name: usb3
                version: 4.07
                capabilities: usb-2.00
                configuration: driver=hub slots=10 speed=480Mbit/s
              *-usb:0
                   description: Mouse
                   product: Chicony wired mouse
                   vendor: Chicony
                   physical id: 1
                   bus info: usb@3:1
                   version: 0.03
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=100mA speed=1Mbit/s
              *-usb:1
                   description: Keyboard
                   product: USB Keyboard
                   vendor: CHICONY
                   physical id: 2
                   bus info: usb@3:2
                   version: 2.30
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=100mA speed=1Mbit/s
              *-usb:2
                   description: USB hub
                   product: BCM2046B1
                   vendor: Broadcom
                   physical id: 3
                   bus info: usb@3:3
                   version: 1.00
                   capabilities: usb-2.00
                   configuration: driver=hub maxpower=94mA slots=3 speed=12Mbit/s
                 *-usb:0
                      description: Keyboard
                      product: Keyboard (Boot Interface Subclass)
                      vendor: Broadcom Corp.
                      physical id: 1
                      bus info: usb@3:3.1
                      version: 1.00
                      capabilities: usb-2.00
                      configuration: driver=usbhid maxpower=2mA speed=12Mbit/s
                 *-usb:1
                      description: Mouse
                      product: Mouse (Boot Interface Subclass)
                      vendor: Broadcom Corp.
                      physical id: 2
                      bus info: usb@3:3.2
                      version: 1.00
                      capabilities: usb-2.00
                      configuration: driver=usbhid maxpower=2mA speed=12Mbit/s
                 *-usb:2
                      description: Bluetooth wireless interface
                      product: BCM92046DG-CL1ROM
                      vendor: Broadcom Corp
                      physical id: 3
                      bus info: usb@3:3.3
                      version: 8.18
                      serial: 000272AC799A
                      capabilities: bluetooth usb-2.00
                      configuration: driver=btusb maxpower=2mA speed=12Mbit/s
              *-usb:3
                   description: Generic USB device
                   product: 802.11n WLAN Adapter
                   vendor: Realtek
                   physical id: a
                   bus info: usb@3:a
                   version: 2.00
                   serial: 00e04c000001
                   capabilities: usb-2.00
                   configuration: driver=rtl8192cu maxpower=500mA speed=480Mbit/s
           *-usbhost:1
                product: xHCI Host Controller
                vendor: Linux 4.7.0-040700rc3-generic xhci-hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 4.07
                capabilities: usb-3.00
                configuration: driver=hub slots=2 speed=5000Mbit/s
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
             resources: irq:31 memory:f721a000-f721a00f
        *-usb:1
             description: USB controller
             product: 8 Series/C220 Series Chipset Family USB EHCI #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:16 memory:f7218000-f72183ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.7.0-040700rc3-generic ehci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 4.07
                capabilities: usb-2.00
                configuration: driver=hub slots=2 speed=480Mbit/s
              *-usb
                   description: USB hub
                   vendor: Intel Corp.
                   physical id: 1
                   bus info: usb@1:1
                   version: 0.05
                   capabilities: usb-2.00
                   configuration: driver=hub slots=4 speed=480Mbit/s
        *-multimedia
             description: Audio device
             product: 8 Series/C220 Series Chipset High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:32 memory:f7210000-f7213fff
        *-pci:1
             description: PCI bridge
             product: 8 Series/C220 Series Chipset Family PCI Express Root Port #1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: d5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 ioport:2000(size=4096) memory:e0000000-e01fffff ioport:e0200000(size=2097152)
        *-pci:2
             description: PCI bridge
             product: 8 Series/C220 Series Chipset Family PCI Express Root Port #3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: d5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:27 ioport:d000(size=4096) memory:f7100000-f71fffff ioport:f2100000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 0c
                serial: d4:3d:7e:fb:b4:4a
                size: 100Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168g-2_0.0.1 02/06/13 ip=192.168.2.10 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
                resources: irq:28 ioport:d000(size=256) memory:f7100000-f7100fff memory:f2100000-f2103fff
        *-usb:2
             description: USB controller
             product: 8 Series/C220 Series Chipset Family USB EHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:f7217000-f72173ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.7.0-040700rc3-generic ehci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 4.07
                capabilities: usb-2.00
                configuration: driver=hub slots=2 speed=480Mbit/s
              *-usb
                   description: USB hub
                   vendor: Intel Corp.
                   physical id: 1
                   bus info: usb@2:1
                   version: 0.05
                   capabilities: usb-2.00
                   configuration: driver=hub slots=6 speed=480Mbit/s
        *-isa
             description: ISA bridge
             product: C220 Series Chipset Family H81 Express LPC Controller
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
             product: 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:30 ioport:f070(size=8) ioport:f060(size=4) ioport:f050(size=8) ioport:f040(size=4) ioport:f020(size=32) memory:f7216000-f72167ff
        *-serial UNCLAIMED
             description: SMBus
             product: 8 Series/C220 Series Chipset Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 05
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f7215000-f72150ff ioport:f000(size=32)
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: Micron_M510_MTFD
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: MU01
             serial: 14110C09CC78
             size: 238GiB (256GB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=7ffd7fc9-7eef-40b1-a4e2-f62d0ce703c1 logicalsectorsize=512 sectorsize=4096
           *-volume:0
                description: Windows NTFS volume
                vendor: Windows
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                version: 3.1
                serial: f6d8-7897
                size: 497MiB
                capacity: 498MiB
                capabilities: boot ntfs initialized
                configuration: clustersize=4096 created=2014-04-16 22:10:00 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true name=Basic data partition resize_log_file=true state=dirty upgrade_on_mount=true
           *-volume:1
                description: Windows FAT volume
                vendor: MSDOS5.0
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                logical name: /boot/efi
                version: FAT32
                serial: a0d8-ccd7
                size: 76MiB
                capacity: 99MiB
                capabilities: boot fat initialized
                configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,utf8,errors=remount-ro name=EFI system partition state=mounted
           *-volume:2
                description: reserved partition
                vendor: Windows
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                serial: 001b3bad-f362-48d6-ae5f-15ef2bdb23ff
                capacity: 127MiB
                capabilities: nofs
                configuration: name=Microsoft reserved partition
           *-volume:3
                description: Windows FAT volume
                vendor: MSDOS5.0
                physical id: 4
                bus info: scsi@0:0.0.0,4
                logical name: /dev/sda4
                version: FAT32
                serial: 0218-a89c
                size: 997MiB
                capacity: 1023MiB
                capabilities: precious readonly hidden nomount fat initialized
                configuration: FATs=2 filesystem=fat label=PRC_RP name=Basic data partition
           *-volume:4
                description: Windows NTFS volume
                vendor: Windows
                physical id: 5
                bus info: scsi@0:0.0.0,5
                logical name: /dev/sda5
                version: 3.1
                serial: b2bb2176-84cb-174a-8ae9-84b8377d3235
                size: 159GiB
                capacity: 159GiB
                capabilities: ntfs initialized
                configuration: clustersize=4096 created=2014-04-16 22:09:55 filesystem=ntfs label=Boot modified_by_chkdsk=true mounted_on_nt4=true name=Basic data partition resize_log_file=true state=dirty upgrade_on_mount=true
           *-volume:5
                description: Windows NTFS volume
                vendor: Windows
                physical id: 6
                bus info: scsi@0:0.0.0,6
                logical name: /dev/sda6
                version: 3.1
                serial: ba32-266e
                size: 419MiB
                capacity: 449MiB
                capabilities: boot precious readonly hidden nomount ntfs initialized
                configuration: clustersize=4096 created=2015-08-14 19:32:29 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
           *-volume:6
                description: EXT4 volume
                vendor: Linux
                physical id: 7
                bus info: scsi@0:0.0.0,7
                logical name: /dev/sda7
                logical name: /
                version: 1.0
                serial: a2f2ddb9-8387-4b9a-851a-d9ef42f42ab4
                size: 77GiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2015-05-16 23:51:08 filesystem=ext4 lastmountpoint=/ modified=2017-03-31 20:42:55 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2017-03-31 20:42:56 state=mounted
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: TOSHIBA DT01ACA2
             vendor: Toshiba
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/sdb
             version: ABB0
             serial: 24HEXA0TS
             size: 1863GiB (2TB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=8fdef561-d131-4a65-b298-70f244149efa logicalsectorsize=512 sectorsize=4096
           *-volume:0
                description: reserved partition
                vendor: Windows
                physical id: 1
                bus info: scsi@1:0.0.0,1
                logical name: /dev/sdb1
                serial: 7fedf55d-a5dc-41d6-9e48-157d12a1cb52
                capacity: 127MiB
                capabilities: nofs
                configuration: name=Microsoft reserved partition
           *-volume:1
                description: Windows NTFS volume
                vendor: Windows
                physical id: 2
                bus info: scsi@1:0.0.0,2
                logical name: /dev/sdb2
                version: 3.1
                serial: 8040c7de-4ae6-3c45-9c23-1c4bbee29456
                size: 826GiB
                capacity: 826GiB
                capabilities: ntfs initialized
                configuration: clustersize=4096 created=2014-03-17 10:34:36 filesystem=ntfs label=Data modified_by_chkdsk=true mounted_on_nt4=true name=Basic data partition resize_log_file=true state=dirty upgrade_on_mount=true
           *-volume:2
                description: Windows NTFS volume
                vendor: Windows
                physical id: 3
                bus info: scsi@1:0.0.0,3
                logical name: /dev/sdb3
                version: 3.1
                serial: 848b5963-6960-5640-b566-8fb7c5818add
                size: 59GiB
                capacity: 59GiB
                capabilities: ntfs initialized
                configuration: clustersize=4096 created=2014-03-17 10:34:53 filesystem=ntfs label=Recover modified_by_chkdsk=true mounted_on_nt4=true name=Basic data partition resize_log_file=true state=dirty upgrade_on_mount=true
           *-volume:3
                description: Linux swap volume
                vendor: Linux
                physical id: 4
                bus info: scsi@1:0.0.0,4
                logical name: /dev/sdb4
                version: 1
                serial: df296dbe-a8bc-482f-b581-206b52dccae7
                size: 23GiB
                capacity: 23GiB
                capabilities: nofs precious readonly hidden nomount swap initialized
                configuration: filesystem=swap pagesize=4095
           *-volume:4
                description: EXT4 volume
                vendor: Linux
                physical id: 5
                bus info: scsi@1:0.0.0,5
                logical name: /dev/sdb5
                logical name: /home
                version: 1.0
                serial: 17453880-25c1-4477-997e-bf30d8e33620
                size: 953GiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2015-05-16 23:51:10 filesystem=ext4 lastmountpoint=/home modified=2017-03-31 20:43:04 mount.fstype=ext4 mount.options=rw,relatime,data=ordered mounted=2017-03-31 20:43:04 state=mounted
     *-scsi:2
          physical id: 3
          logical name: scsi4
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: CDDVDW SH-216AB
             vendor: TSSTcorp
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: MD00
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@3:10
       logical name: wlan0
       serial: 80:1f:02:f2:19:3e
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192cu driverversion=4.7.0-040700rc3-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11
```

---

### Post by dragonfly41 on 2017-03-31
Installing gnome-flashback on 16.10 is not an unproven idea .. [http://tipsonubuntu.com/2016/10/16/install-classic-gnome-flashback-ubuntu-16-10/](http://tipsonubuntu.com/2016/10/16/install-classic-gnome-flashback-ubuntu-16-10/)

I could throw in some other ideas I've read in my own research on the topic (e.g. try launching in guest account with a fresh profile) but I guess that you are not too keen to experiment.

---

### Post by ojima on 2017-04-01
Well, if you have any suggestions, feel free to toss some around (so long as you warn when I might be entering the danger zone :P). The only "solution" I have so far is setting grub to use the the 4.7.0rc3 kernel as default, since it's more stable than the newer versions.

---

### Post by dragonfly41 on 2017-04-01
If you have searched around you will see that there is no single recommended solution to this freezing problem.
The suggestions below do not need you to wear a hard hat. 

You indicate that the symptoms appear within the first 5 to 30 minutes.   
This suggests to me that the cause might be temperature related or some other cause which builds up quite soon after booting up.

Have you checked your fans, cleaned out any fluff?

Are your disks SMART enabled?
Install smartmontools and gsmartcontrol.

[https://apps.ubuntu.com/cat/applications/natty/gsmartcontrol/](https://apps.ubuntu.com/cat/applications/natty/gsmartcontrol/)

You can monitor disk and cpu temperatures.

Another useful monitor to install is GKrellM System Monitor.

...

Next the fact that memtest checks ok may be a red herring.

Since you have 16 GB of memory I would remove half the memory cards, test if PC freezes with 8 GB , and then try the other half set 8 GB of memory. 
When replacing each set of memory handle carefully and gently clean memory card edges with a clean rubber.

Restore to 16 GB memory after these swapout tests.

...

You did not confirm if you tried a fresh user profile by creating a new user account or using guest account.   Do you have freezes with a different account? 

...


You did not confirm if you managed to install gnome-flashback.   The logic here is to try to eliminate Unity which has been cited in some threads as a possible source of freezing.   
It may be that gnome-flashback crashed because you have password disabled and may not go to the login panel.

...

Here is another line of thought.

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash intel_idle.max_cstate=1" 

[http://askubuntu.com/questions/778045/ubuntu-16-04-freezes-often/778091](http://askubuntu.com/questions/778045/ubuntu-16-04-freezes-often/778091)

...

> Once you eliminate the impossible, whatever remains, no matter how improbable, must be the truth.
*Sir Arthur Conan Doyle stated by Sherlock Holmes*

---

### Post by ojima on 2017-04-04
> [COLOR=#000000]Have you checked your fans, cleaned out any fluff?[/COLOR]

I did that earlier this afternoon (I found that there was a surprising lot of dust buildup in my GPU's fan, but I've managed to blow it all away with compressed air), now testing to see if it makes any clear difference. I've also moved my PC to the other side of my desk, so that it's no longer in a corner of my room next to a wall, but has clear space on all sides and a free path in front of the fan gratings.

> [COLOR=#000000]Are your disks SMART enabled?[/COLOR]

Yes.

> [COLOR=#000000]You did not confirm if you managed to install gnome-flashback.[/COLOR]

I did manage to install and run gnome-flashback, but it made no difference: it crashed at about the same rate as Unity.

> [COLOR=#000000]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash intel_idle.max_cstate=1" [/COLOR]

I tried that one before, but with no difference.

...

I have yet to try out the swapout tests (and the user account change), but I'm not a very experienced technician, so I want to take my time with that and see if this works.

Anyway, so far it *seems* promising (I've had one freeze, but to my surprise my computer managed to recover from it after a split second), but I don't want to walk ahead of the facts and first test to see if this actually helped.

---

### Post by dragonfly41 on 2017-04-04
Well the impossible is slowly being eliminated ...

(a) If you are not comfortable with pulling out memory cards then leave that experiment for now and try simply a different user profile.

(b) If you stlll have a live Ubuntu USB which you used to install Ubuntu you could try running that to see if this live Ubuntu USB can run for say an hour or so without a freeze.

(c) Remember that if an apparent freeze occurs again you can sometimes get out of it by Ctrl+Alt+F1 followed by Ctrl+Alt+F7. This saves the pain of rebooting
.
(d) If these don't work then the next idea will be to use using GkrellMD (server option) to capture parameters to try to pin down the root cause.

[http://www.techrepublic.com/blog/linux-and-open-source/how-to-use-gkrellmd-to-monitor-linux-boxes-automatically/](http://www.techrepublic.com/blog/linux-and-open-source/how-to-use-gkrellmd-to-monitor-linux-boxes-automatically/)

---

### Post by samuelfcampbell on 2017-04-15
*  make sure you have the correct & updated drivers for the audio, video, and motherboard/chipset.


* the screen resolution? Do you have it set at the correct native resolution?

* I read someone discovered their machine freezes because the radiator on the chipset had been detached and the machine overheated when doing intense computations like decoding video for example. Once it was reattached to the bloody thing everything went back to normal. 

Mr. Samuel F. Campbell 


Administrative Executive Assistant 2014 Certificate

Your Emerging Contemporary Artist 
Harmonicas & Acoustic Guitar Soloist & Grand Piano Soloist
&#8226; Dramatic Musical Instrumental Interpretations 
&#8226; Hand Drawings 
&#8226; Acrylic Paintings 
&#8226; Oil Paintings 
&#8226; Computer Operator Windows XP, Windows 7, Linux Mint 17 Rebecca Video editing and graphics

---

