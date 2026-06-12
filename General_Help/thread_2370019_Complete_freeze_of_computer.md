---
title: "Complete freeze of computer"
date: 2017-08-29
forum: General Help
---

### Post by jarjarbeans on 2017-08-29
Since installing Ubuntu 16.04, my computer freezes daily, sometimes 2 - 3 - 4... times a day.
It did not do this on Windows.

The screen is on, I can't move my mouse, Ctrl + Alt + F1 does not work. 
I read that I should change a line in etc/default/grub to GRUB_CMDLINE_LINUX_DEFAULT="quiet splash intel_idle.max_cstate=1".

It seems to occur only when I browse the Internet on Chrome, Chromium, Firefox.
The sound is not off because it once froze during a Youtube video : the most recent sound was repeating (duh, duh, duh, duh .....).

Please let me know if I have to add any info.

Here is the output of uname -a
```
 
Linux nik 4.10.0-32-generic #36~16.04.1-Ubuntu SMP Wed Aug 9 09:19:02 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

```

lspci | grep VGA 
```

00:02.0 VGA compatible controller: Intel Corporation Device 22b1 (rev 21)


```


sudo lshw : 
```

nik                       
    description: Notebook
    product: HP x360 310 G2 PC (X7R98EC#ABF)
    vendor: HP
    version: Type1ProductConfigId
    serial: 8CG6321RW3
    width: 64 bits
    capabilities: smbios-2.8 dmi-2.8 vsyscall32
    configuration: boot=normal chassis=notebook family=103C_5336AN G=N L=SMB B=HP S=310 sku=X7R98EC#ABF uuid=E41B5B6A-025F-E611-839F-EC8EB52E8A94
  *-core
       description: Motherboard
       product: 8074
       vendor: HP
       physical id: 0
       version: 66.35
       serial: PFDWL1ANN386AW
       slot: Type2 - Board Chassis Location
     *-firmware
          description: BIOS
          vendor: Insyde
          physical id: 0
          version: F.39
          date: 10/30/2015
          size: 64KiB
          capacity: 6080KiB
          capabilities: pci upgrade shadowing cdboot bootselect edd int9keyboard int14serial int17printer int10video acpi usb zipboot biosbootspecification netboot uefi
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) CPU  N3700  @ 1.60GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Pentium(R) CPU  N3700  @ 1.60GHz
          serial: To Be Filled By O.E.M.
          slot: CHV
          size: 871MHz
          capacity: 2400MHz
          width: 64 bits
          clock: 83MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology tsc_reliable nonstop_tsc aperfmperf tsc_known_freq pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 movbe popcnt tsc_deadline_timer aes rdrand lahf_lm 3dnowprefetch epb tpr_shadow vnmi flexpriority ept vpid tsc_adjust smep erms dtherm ida arat cpufreq
          configuration: cores=4 enabledcores=4 threads=4
        *-cache:0
             description: L1 cache
             physical id: 6
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back instruction
             configuration: level=1
        *-cache:1
             description: L2 cache
             physical id: 7
             slot: L2 Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: synchronous internal write-back unified
             configuration: level=2
     *-cache
          description: L1 cache
          physical id: 5
          slot: L1 Cache
          size: 24KiB
          capacity: 24KiB
          capabilities: synchronous internal write-back data
          configuration: level=1
     *-memory
          description: System Memory
          physical id: 25
          slot: System board or motherboard
          size: 4GiB
        *-bank
             description: SODIMM DDR3 Synchronous 1600 MHz (0.6 ns)
             product: HMT451S6DFR8A-PB
             vendor: Hynix/Hyundai
             physical id: 0
             serial: 23541929
             slot: Bottom
             size: 4GiB
             width: 8 bits
             clock: 1600MHz (0.6ns)
     *-pci
          description: Host bridge
          product: Intel Corporation
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 21
          width: 32 bits
          clock: 33MHz
          configuration: driver=iosf_mbi_pci
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:312 memory:90000000-90ffffff memory:80000000-8fffffff ioport:4000(size=64) memory:c0000-dffff
        *-generic:0
             description: Signal processing controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: b
             bus info: pci@0000:00:0b.0
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list
             configuration: driver=proc_thermal latency=0
             resources: irq:313 memory:91518000-91518fff
        *-storage
             description: SATA controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 21
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:309 ioport:4060(size=32) memory:91521000-915217ff
        *-usb
             description: USB controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:308 memory:91500000-9150ffff
           *-usbhost:0
                product: xHCI Host Controller
                vendor: Linux 4.10.0-32-generic xhci-hcd
                physical id: 0
                bus info: usb@1
                logical name: usb1
                version: 4.10
                capabilities: usb-2.00
                configuration: driver=hub slots=7 speed=480Mbit/s
              *-usb:0
                   description: Human interface device
                   product: ST_SENSOR_HUB
                   vendor: STMicroelectronics
                   physical id: 2
                   bus info: usb@1:2
                   version: 1.10
                   serial: ST_SENSOR_HUB
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=100mA speed=12Mbit/s
              *-usb:1
                   description: Keyboard
                   product: USB Receiver
                   vendor: Logitech
                   physical id: 3
                   bus info: usb@1:3
                   version: 24.00
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=98mA speed=12Mbit/s
              *-usb:2
                   description: USB hub
                   product: USB2.0 Hub
                   vendor: Genesys Logic, Inc.
                   physical id: 5
                   bus info: usb@1:5
                   version: 32.98
                   capabilities: usb-2.00
                   configuration: driver=hub maxpower=100mA slots=4 speed=480Mbit/s
                 *-usb:0
                      description: Bluetooth wireless interface
                      product: Bluetooth Radio
                      vendor: Realtek
                      physical id: 1
                      bus info: usb@1:5.1
                      version: 2.00
                      serial: 00e04c000001
                      capabilities: bluetooth usb-2.10
                      configuration: driver=btusb maxpower=500mA speed=12Mbit/s
                 *-usb:1
                      description: Video
                      product: HP Truevision HD
                      vendor: Generic
                      physical id: 2
                      bus info: usb@1:5.2
                      version: 0.03
                      serial: DETGR019I353S7
                      capabilities: usb-2.00
                      configuration: driver=uvcvideo maxpower=500mA speed=480Mbit/s
           *-usbhost:1
                product: xHCI Host Controller
                vendor: Linux 4.10.0-32-generic xhci-hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 4.10
                capabilities: usb-3.00
                configuration: driver=hub slots=6 speed=5000Mbit/s
        *-generic:1
             description: Encryption controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 21
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_txe latency=0
             resources: irq:314 memory:91400000-914fffff memory:91300000-913fffff
        *-multimedia
             description: Audio device
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:325 memory:91510000-91513fff
        *-pci:0
             description: PCI bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 21
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:0 ioport:1000(size=4096) memory:91600000-917fffff ioport:91800000(size=2097152)
        *-pci:1
             description: PCI bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 21
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:3000(size=4096) memory:91200000-912fffff
           *-network
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: enp2s0
                version: 15
                serial: ec:8e:b5:2e:8a:94
                size: 10Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168h-2_0.0.2 02/26/15 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:311 ioport:3000(size=256) memory:91204000-91204fff memory:91200000-91203fff
        *-pci:2
             description: PCI bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 21
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:18 ioport:2000(size=4096) memory:91100000-911fffff
           *-network
                description: Wireless interface
                product: RTL8723BE PCIe Wireless Network Adapter
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlp3s0
                version: 00
                serial: 94:53:30:17:30:33
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rtl8723be driverversion=4.10.0-32-generic firmware=N/A ip=192.168.1.94 latency=0 link=yes multicast=yes wireless=IEEE 802.11
                resources: irq:18 ioport:2000(size=256) memory:91100000-91103fff
        *-pci:3
             description: PCI bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 21
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:19 memory:91000000-910fffff
           *-generic
                description: Unassigned class
                product: RTS5229 PCI Express Card Reader
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:04:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=rtsx_pci latency=0
                resources: irq:310 memory:91000000-91000fff
        *-isa
             description: ISA bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 21
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-serial UNCLAIMED
             description: SMBus
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 21
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0
             resources: memory:91519000-9151901f ioport:4040(size=32)
     *-scsi
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: LITEON L8H-256V2
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 2803
             serial: 0026311006B3
             size: 238GiB (256GB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=987877ac-10a9-46e0-81c8-e6e9292f3faa logicalsectorsize=512 sectorsize=512
           *-volume:0
                description: Windows NTFS volume
                vendor: Windows
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                version: 3.1
                serial: ec5b-ced1
                size: 448MiB
                capacity: 449MiB
                capabilities: boot precious readonly hidden nomount ntfs initialized
                configuration: clustersize=4096 created=2016-07-04 13:29:42 filesystem=ntfs label=Recovery name=Basic data partition state=clean
           *-volume:1
                description: Windows FAT volume
                vendor: MSDOS5.0
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                logical name: /boot/efi
                version: FAT32
                serial: ee5b-f9be
                size: 93MiB
                capacity: 99MiB
                capabilities: boot fat initialized
                configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,relatime,fmask=0077,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro name=EFI system partition state=mounted
           *-volume:2
                description: reserved partition
                vendor: Windows
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                serial: 3fd2b9fb-0974-4e35-97ca-278adf333625
                capacity: 127MiB
                capabilities: nofs
                configuration: name=Microsoft reserved partition
           *-volume:3
                description: Windows NTFS volume
                vendor: Windows
                physical id: 4
                bus info: scsi@0:0.0.0,4
                logical name: /dev/sda4
                version: 3.1
                serial: 9c91de92-73de-d247-99f3-80521c34b8cf
                size: 78GiB
                capacity: 78GiB
                capabilities: ntfs initialized
                configuration: clustersize=4096 created=2016-07-04 13:29:58 filesystem=ntfs label=OS name=Basic data partition state=clean
           *-volume:4
                description: Windows NTFS volume
                vendor: Windows
                physical id: 5
                bus info: scsi@0:0.0.0,5
                logical name: /dev/sda5
                version: 3.1
                serial: d4d9dfd8-c2e0-034d-9dff-de6435e5bc48
                size: 103GiB
                capacity: 103GiB
                capabilities: ntfs initialized
                configuration: clustersize=4096 created=2016-07-04 13:31:04 filesystem=ntfs label=Donnees name=Basic data partition state=clean
           *-volume:5
                description: Windows NTFS volume
                vendor: Windows
                physical id: 6
                bus info: scsi@0:0.0.0,6
                logical name: /dev/sda6
                version: 3.1
                serial: 628d-affa
                size: 20GiB
                capacity: 20GiB
                capabilities: boot precious readonly hidden nomount ntfs initialized
                configuration: clustersize=4096 created=2016-07-04 13:31:05 filesystem=ntfs label=HP_RECOVERY modified_by_chkdsk=true mounted_on_nt4=true name=Basic data partition resize_log_file=true state=dirty upgrade_on_mount=true
           *-volume:6
                description: EXT4 volume
                vendor: Linux
                physical id: 7
                bus info: scsi@0:0.0.0,7
                logical name: /dev/sda7
                logical name: /
                version: 1.0
                serial: eb59e450-6c03-4f1e-ac0f-f24db9b6c6a4
                size: 30GiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2017-08-02 13:13:55 filesystem=ext4 lastmountpoint=/ modified=2017-08-29 16:45:35 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2017-08-29 16:45:36 state=mounted
           *-volume:7
                description: Linux swap volume
                vendor: Linux
                physical id: 8
                bus info: scsi@0:0.0.0,8
                logical name: /dev/sda8
                version: 1
                serial: 7400e7be-6f4d-4583-92ff-60d33d8b8b1b
                size: 3953MiB
                capacity: 3953MiB
                capabilities: nofs swap initialized
                configuration: filesystem=swap pagesize=4095
  *-battery
       product: HV03048XL
       vendor: 333-42-2A
       physical id: 1
       version: ManufDate
       serial: DummySerialNumber
       slot: Primary
       capacity: 48108mWh
       configuration: voltage=11.4V
  *-power UNCLAIMED
       description: OEM Define 1
       product: OEM Define 5
       vendor: OEM Define 2
       physical id: 2
       version: OEM Define 6
       serial: OEM Define 3
       capacity: 75mWh

```

Thank you.

---

### Post by VMC on 2017-08-29
Did you install additional hardware for you intel graphics card?

---

### Post by jarjarbeans on 2017-08-29
I don't think so, is there any way to check that?

---

### Post by VMC on 2017-08-29
What's the output of:
```
lspci | grep VGA
```

---

### Post by Autodave on 2017-08-30
I do not agree with emanuel2222 on this. Does it happen? Yes. But in Linux, it RARELY happens. I run 13 machines and have been for about 10 years now. I have NEVER had to reinstall it on any of the machines! Windows has problems with the registry. Linux does not have those problems.

It also sounds like a graphics card problem to me. Do what VMC suggested and report back.

---

### Post by jarjarbeans on 2017-09-01
Thank you, all of you.

The output of lspci | grep VGA was
```

00:02.0 VGA compatible controller: Intel Corporation Device 22b1 (rev 21)


```

---

### Post by VMC on 2017-09-01
Maybe this article will help:
[http://www.techzim.co.zw/2017/01/heres-guide-installing-intel-graphics-driver-ubuntu-16-04/](http://www.techzim.co.zw/2017/01/heres-guide-installing-intel-graphics-driver-ubuntu-16-04/)

---

### Post by jarjarbeans on 2017-09-02
This is a noob problem.
It says on the website [https://01.org/linuxgraphics/downloads/intel-graphics-update-tool-linux-os-v2.0.3](https://01.org/linuxgraphics/downloads/intel-graphics-update-tool-linux-os-v2.0.3) that the update is for Ubuntu 16.10. Isn't that an older version?
I am on 16.04 LTS and according to [https://01.org/linuxgraphics/downloads/intel-graphics-update-tool-linux-os-v2.0.3](https://01.org/linuxgraphics/downloads/intel-graphics-update-tool-linux-os-v2.0.3) 16.04  LTS is much newer.

Should I install it anyway?

---

### Post by gordintoronto on 2017-09-02
There are several different things which might cause your problem. On my computer, it was ACPI. This stopped the problem:

[https://askubuntu.com/questions/139157/booting-ubuntu-with-acpi-off-grub-parameter](https://askubuntu.com/questions/139157/booting-ubuntu-with-acpi-off-grub-parameter)

---

