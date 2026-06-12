---
title: "System restarts when power adaptor is out"
date: 2016-03-18
forum: General Help
---

### Post by nic11 on 2016-03-18
This is my first post so hopefully I follow the correct procedures. These threads have been a massive assistance to me but I have not been able to find a solution to the following. The closest problem I found was this: 
 [http://ubuntuforums.org/showthread.php?t=2307018](http://ubuntuforums.org/showthread.php?t=2307018) 
 In my case:
 
 OS: ubuntu 15.10
 System:  Dell *Inspiron* 17R SE *7720*
 [more details below] 
 
 When the power adaptor is not plugged in, after a certain period (for example when the power level goes below 66%) when I trigger a certain event (for example opening a 'compose new message' in Thunderbird) the screen goes black and I receive the following message which stays on screen for only a moment:
```
fsck from util-linux 2.26.2
/dev/sda1: clean, 764792/60538880 files, 179373428/242129664 blocks
[    ok    ] Started Light Display Manager.
[    ok    ] Started ACPI event daemon.
``` 
The system then immediately restarts automatically and the log in screen appears even though my system does not require a log in when it boots up.
 
 Any advice gratefully received.
 
 My system details: 
 ```
nic-inspiron-7720          
     description: Computer
     width: 64 bits
     capabilities: smbios-2.7 vsyscall32
   *-core
        description: Motherboard
        physical id: 0
      *-memory
           description: System memory
           physical id: 0
           size: 7840MiB
      *-cpu
           product: Intel(R) Core(TM) i7-3630QM CPU @ 2.40GHz
           vendor: Intel Corp.
           physical id: 1
           bus info: cpu@0
           size: 3204MHz
           capacity: 3400MHz
           width: 64 bits
           capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm ida arat epb pln pts dtherm tpr_shadow vnmi flexpriority ept vpid fsgsbase smep erms xsaveopt cpufreq
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
         *-pci:0
              description: PCI bridge
              product: Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port
              vendor: Intel Corporation
              physical id: 1
              bus info: pci@0000:00:01.0
              version: 09
              width: 32 bits
              clock: 33MHz
              capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
              configuration: driver=pcieport
              resources: irq:24 ioport:3000(size=4096) memory:f0000000-f0ffffff ioport:c0000000(size=301989888)
            *-display
                 description: VGA compatible controller
                 product: GK107M [GeForce GT 650M]
                 vendor: NVIDIA Corporation
                 physical id: 0
                 bus info: pci@0000:01:00.0
                 version: a1
                 width: 64 bits
                 clock: 33MHz
                 capabilities: pm msi pciexpress vga_controller bus_master cap_list
                 configuration: driver=nouveau latency=0
                 resources: irq:28 memory:f0000000-f0ffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:3000(size=128)
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
              resources: irq:29 memory:f1000000-f13fffff memory:e0000000-efffffff ioport:4000(size=64)
         *-usb:0
              description: USB controller
              product: 7 Series/C210 Series Chipset Family USB xHCI Host Controller
              vendor: Intel Corporation
              physical id: 14
              bus info: pci@0000:00:14.0
              version: 04
              width: 64 bits
              clock: 33MHz
              capabilities: pm msi xhci bus_master cap_list
              configuration: driver=xhci_hcd latency=0
              resources: irq:25 memory:f1600000-f160ffff
            *-usbhost:0
                 product: xHCI Host Controller
                 vendor: Linux 4.2.0-34-generic xhci-hcd
                 physical id: 0
                 bus info: usb@2
                 logical name: usb2
                 version: 4.02
                 capabilities: usb-3.00
                 configuration: driver=hub slots=4 speed=5000Mbit/s
            *-usbhost:1
                 product: xHCI Host Controller
                 vendor: Linux 4.2.0-34-generic xhci-hcd
                 physical id: 1
                 bus info: usb@1
                 logical name: usb1
                 version: 4.02
                 capabilities: usb-2.00
                 configuration: driver=hub slots=4 speed=480Mbit/s
               *-usb
                    description: Generic USB device
                    product: 802.11 n WLAN
                    vendor: Ralink
                    physical id: 4
                    bus info: usb@1:4
                    version: 1.01
                    serial: 1.0
                    capabilities: usb-2.00
                    configuration: driver=rt2800usb maxpower=450mA speed=480Mbit/s
         *-communication
              description: Communication controller
              product: 7 Series/C210 Series Chipset Family MEI Controller #1
              vendor: Intel Corporation
              physical id: 16
              bus info: pci@0000:00:16.0
              version: 04
              width: 64 bits
              clock: 33MHz
              capabilities: pm msi bus_master cap_list
              configuration: driver=mei_me latency=0
              resources: irq:30 memory:f1615000-f161500f
         *-usb:1
              description: USB controller
              product: 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2
              vendor: Intel Corporation
              physical id: 1a
              bus info: pci@0000:00:1a.0
              version: 04
              width: 32 bits
              clock: 33MHz
              capabilities: pm debug ehci bus_master cap_list
              configuration: driver=ehci-pci latency=0
              resources: irq:16 memory:f161a000-f161a3ff
            *-usbhost
                 product: EHCI Host Controller
                 vendor: Linux 4.2.0-34-generic ehci_hcd
                 physical id: 1
                 bus info: usb@3
                 logical name: usb3
                 version: 4.02
                 capabilities: usb-2.00
                 configuration: driver=hub slots=2 speed=480Mbit/s
               *-usb
                    description: USB hub
                    product: Integrated Rate Matching Hub
                    vendor: Intel Corp.
                    physical id: 1
                    bus info: usb@3:1
                    version: 0.00
                    capabilities: usb-2.00
                    configuration: driver=hub slots=6 speed=480Mbit/s
                  *-usb:0
                       description: Generic USB device
                       product: USB2.0-CRW
                       vendor: Generic
                       physical id: 3
                       bus info: usb@3:1.3
                       version: 39.60
                       serial: 20100201396000000
                       capabilities: usb-2.00
                       configuration: driver=rtsx_usb maxpower=500mA speed=480Mbit/s
                  *-usb:1
                       description: Video
                       product: Laptop_Integrated_Webcam_HD
                       vendor: CKFB187F301030092840
                       physical id: 5
                       bus info: usb@3:1.5
                       version: 26.19
                       serial: 0x0001
                       capabilities: usb-2.00
                       configuration: driver=uvcvideo maxpower=500mA speed=480Mbit/s
         *-multimedia
              description: Audio device
              product: 7 Series/C210 Series Chipset Family High Definition Audio Controller
              vendor: Intel Corporation
              physical id: 1b
              bus info: pci@0000:00:1b.0
              version: 04
              width: 64 bits
              clock: 33MHz
              capabilities: pm msi pciexpress bus_master cap_list
              configuration: driver=snd_hda_intel latency=0
              resources: irq:32 memory:f1610000-f1613fff
         *-pci:1
              description: PCI bridge
              product: 7 Series/C210 Series Chipset Family PCI Express Root Port 1
              vendor: Intel Corporation
              physical id: 1c
              bus info: pci@0000:00:1c.0
              version: c4
              width: 32 bits
              clock: 33MHz
              capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
              configuration: driver=pcieport
              resources: irq:16 memory:f1500000-f15fffff
            *-network
                 description: Wireless interface
                 product: Centrino Wireless-N 2230
                 vendor: Intel Corporation
                 physical id: 0
                 bus info: pci@0000:02:00.0
                 logical name: wlp2s0
                 version: c4
                 serial: 84:a6:c8:ca:52:83
                 width: 64 bits
                 clock: 33MHz
                 capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                 configuration: broadcast=yes driver=iwlwifi driverversion=4.2.0-34-generic firmware=18.168.6.1 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
                 resources: irq:31 memory:f1500000-f1501fff
         *-pci:2
              description: PCI bridge
              product: 7 Series/C210 Series Chipset Family PCI Express Root Port 5
              vendor: Intel Corporation
              physical id: 1c.4
              bus info: pci@0000:00:1c.4
              version: c4
              width: 32 bits
              clock: 33MHz
              capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
              configuration: driver=pcieport
              resources: irq:16 ioport:2000(size=4096) ioport:f1400000(size=1048576)
            *-network
                 description: Ethernet interface
                 product: RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
                 vendor: Realtek Semiconductor Co., Ltd.
                 physical id: 0
                 bus info: pci@0000:03:00.0
                 logical name: enp3s0
                 version: 05
                 serial: 5c:f9:dd:51:18:60
                 size: 10Mbit/s
                 capacity: 100Mbit/s
                 width: 64 bits
                 clock: 33MHz
                 capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                 configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8105e-1.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                 resources: irq:27 ioport:2000(size=256) memory:f1404000-f1404fff memory:f1400000-f1403fff
         *-usb:2
              description: USB controller
              product: 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1
              vendor: Intel Corporation
              physical id: 1d
              bus info: pci@0000:00:1d.0
              version: 04
              width: 32 bits
              clock: 33MHz
              capabilities: pm debug ehci bus_master cap_list
              configuration: driver=ehci-pci latency=0
              resources: irq:23 memory:f1619000-f16193ff
            *-usbhost
                 product: EHCI Host Controller
                 vendor: Linux 4.2.0-34-generic ehci_hcd
                 physical id: 1
                 bus info: usb@4
                 logical name: usb4
                 version: 4.02
                 capabilities: usb-2.00
                 configuration: driver=hub slots=2 speed=480Mbit/s
               *-usb
                    description: USB hub
                    product: Integrated Rate Matching Hub
                    vendor: Intel Corp.
                    physical id: 1
                    bus info: usb@4:1
                    version: 0.00
                    capabilities: usb-2.00
                    configuration: driver=hub slots=8 speed=480Mbit/s
                  *-usb
                       description: Bluetooth wireless interface
                       vendor: Intel Corp.
                       physical id: 5
                       bus info: usb@4:1.5
                       version: 78.69
                       capabilities: bluetooth usb-2.00
                       configuration: driver=btusb speed=12Mbit/s
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
         *-storage
              description: SATA controller
              product: 7 Series Chipset Family 6-port SATA Controller [AHCI mode]
              vendor: Intel Corporation
              physical id: 1f.2
              bus info: pci@0000:00:1f.2
              version: 04
              width: 32 bits
              clock: 66MHz
              capabilities: storage msi pm ahci_1.0 bus_master cap_list
              configuration: driver=ahci latency=0
              resources: irq:26 ioport:4088(size=8) ioport:409c(size=4) ioport:4080(size=8) ioport:4098(size=4) ioport:4060(size=32) memory:f1618000-f16187ff
         *-serial UNCLAIMED
              description: SMBus
              product: 7 Series/C210 Series Chipset Family SMBus Controller
              vendor: Intel Corporation
              physical id: 1f.3
              bus info: pci@0000:00:1f.3
              version: 04
              width: 64 bits
              clock: 33MHz
              configuration: latency=0
              resources: memory:f1614000-f16140ff ioport:efa0(size=32)
      *-scsi:0
           physical id: 2
           logical name: scsi0
           capabilities: emulated
         *-disk
              description: ATA Disk
              product: Samsung SSD 850
              physical id: 0.0.0
              bus info: scsi@0:0.0.0
              logical name: /dev/sda
              version: 1B6Q
              serial: S21CNWAG207009Z
              size: 931GiB (1TB)
              capabilities: partitioned partitioned:dos
              configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=0008e976
            *-volume:0
                 description: EXT4 volume
                 vendor: Linux
                 physical id: 1
                 bus info: scsi@0:0.0.0,1
                 logical name: /dev/sda1
                 logical name: /
                 version: 1.0
                 serial: 6ba8c4ea-7d82-49a7-82e9-a576cc629499
                 size: 923GiB
                 capacity: 923GiB
                 capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                 configuration: created=2015-11-22 12:23:19 filesystem=ext4 lastmountpoint=/ modified=2016-03-18 12:18:25 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2016-03-17 14:58:57 state=mounted
            *-volume:1
                 description: Extended partition
                 physical id: 2
                 bus info: scsi@0:0.0.0,2
                 logical name: /dev/sda2
                 size: 8048MiB
                 capacity: 8048MiB
                 capabilities: primary extended partitioned partitioned:extended
               *-logicalvolume
                    description: Linux swap / Solaris partition
                    physical id: 5
                    logical name: /dev/sda5
                    capacity: 8048MiB
                    capabilities: nofs
      *-scsi:1
           physical id: 3
           logical name: scsi1
           capabilities: emulated
         *-disk
              description: ATA Disk
              product: ST2000LM003 HN-M
              vendor: Seagate
              physical id: 0.0.0
              bus info: scsi@1:0.0.0
              logical name: /dev/sdb
              version: 0002
              serial: S34FJ90G307547
              size: 1863GiB (2TB)
              capabilities: partitioned partitioned:dos
              configuration: ansiversion=5 logicalsectorsize=512 sectorsize=4096 signature=ec46fcd9
            *-volume
                 description: EXT4 volume
                 vendor: Linux
                 physical id: 1
                 bus info: scsi@1:0.0.0,1
                 logical name: /dev/sdb1
                 version: 1.0
                 serial: adc8b3b7-7674-4e53-8534-bf558eff6837
                 size: 1863GiB
                 capacity: 1863GiB
                 capabilities: primary journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                 configuration: created=2015-12-08 11:39:28 filesystem=ext4 label=2TBINTERNAL lastmountpoint=/media/nic/2TBINTERNAL modified=2016-03-17 16:36:06 mounted=2016-03-17 15:02:29 state=clean
      *-scsi:2
           physical id: 4
           logical name: scsi3
           capabilities: emulated
         *-cdrom
              description: DVD-RAM writer
              product: DVD+-RW DS-8A8SH
              vendor: PLDS
              physical id: 0.0.0
              bus info: scsi@3:0.0.0
              logical name: /dev/cdrom
              logical name: /dev/cdrw
              logical name: /dev/dvd
              logical name: /dev/dvdrw
              logical name: /dev/sr0
              version: KD13
              capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
              configuration: ansiversion=5 status=nodisc
   *-network
        description: Wireless interface
        physical id: 1
        bus info: usb@1:4
        logical name: wlx00c0ca58ddcd
        serial: 00:c0:ca:58:dd:cd
        capabilities: ethernet physical wireless
        configuration: broadcast=yes driver=rt2800usb driverversion=4.2.0-34-generic firmware=0.29 ip=192.168.1.201 link=yes multicast=yes wireless=IEEE 802.11bgn
``` 
 Disk info: 
 ```
sudo fdisk -l
 Disk /dev/ram0: 64 MiB, 67108864 bytes, 131072 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 4096 bytes
 I/O size (minimum/optimal): 4096 bytes / 4096 bytes
 
 Disk /dev/ram1: 64 MiB, 67108864 bytes, 131072 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 4096 bytes
 I/O size (minimum/optimal): 4096 bytes / 4096 bytes
 
 Disk /dev/ram2: 64 MiB, 67108864 bytes, 131072 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 4096 bytes
 I/O size (minimum/optimal): 4096 bytes / 4096 bytes 
 
 Disk /dev/ram3: 64 MiB, 67108864 bytes, 131072 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 4096 bytes
 I/O size (minimum/optimal): 4096 bytes / 4096 bytes 
 
 Disk /dev/ram4: 64 MiB, 67108864 bytes, 131072 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 4096 bytes
 I/O size (minimum/optimal): 4096 bytes / 4096 bytes 
 
 Disk /dev/ram5: 64 MiB, 67108864 bytes, 131072 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 4096 bytes
 I/O size (minimum/optimal): 4096 bytes / 4096 bytes 
 
 Disk /dev/ram6: 64 MiB, 67108864 bytes, 131072 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 4096 bytes
 I/O size (minimum/optimal): 4096 bytes / 4096 bytes 
 
 Disk /dev/ram7: 64 MiB, 67108864 bytes, 131072 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 4096 bytes
 I/O size (minimum/optimal): 4096 bytes / 4096 bytes 
 
 Disk /dev/ram8: 64 MiB, 67108864 bytes, 131072 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 4096 bytes
 I/O size (minimum/optimal): 4096 bytes / 4096 bytes 
 
 Disk /dev/ram9: 64 MiB, 67108864 bytes, 131072 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 4096 bytes
 I/O size (minimum/optimal): 4096 bytes / 4096 bytes 
 
 Disk /dev/ram10: 64 MiB, 67108864 bytes, 131072 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 4096 bytes
 I/O size (minimum/optimal): 4096 bytes / 4096 bytes 
 
 Disk /dev/ram11: 64 MiB, 67108864 bytes, 131072 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 4096 bytes
 I/O size (minimum/optimal): 4096 bytes / 4096 bytes 
 
 Disk /dev/ram12: 64 MiB, 67108864 bytes, 131072 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 4096 bytes
 I/O size (minimum/optimal): 4096 bytes / 4096 bytes 
 
 Disk /dev/ram13: 64 MiB, 67108864 bytes, 131072 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 4096 bytes
 I/O size (minimum/optimal): 4096 bytes / 4096 bytes 
 
 Disk /dev/ram14: 64 MiB, 67108864 bytes, 131072 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 4096 bytes
 I/O size (minimum/optimal): 4096 bytes / 4096 bytes 
 
 Disk /dev/ram15: 64 MiB, 67108864 bytes, 131072 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 4096 bytes
 I/O size (minimum/optimal): 4096 bytes / 4096 bytes 
 
 Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 Disklabel type: dos
 Disk identifier: 0x0008e976
 Device     Boot      Start        End    Sectors   Size Id Type
 /dev/sda1  *          2048 1937039359 1937037312 923.7G 83 Linux
 /dev/sda2       1937041406 1953523711   16482306   7.9G  5 Extended
 /dev/sda5       1937041408 1953523711   16482304   7.9G 82 Linux swap / Solaris 
 
 Disk /dev/sdb: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 4096 bytes
 I/O size (minimum/optimal): 4096 bytes / 4096 bytes
 Disklabel type: dos
 Disk identifier: 0xec46fcd9
 
 Device     Boot Start        End    Sectors  Size Id Type
 /dev/sdb1        2048 3907029167 3907027120  1.8T 83 Linux
```

---

### Post by Nad_Fink on 2016-03-20
I am not sure what is causing your problem, but maybe I can spur some ideas. First off, those messages you are seeing when the screen goes black are boot messages, likely still on that display from boot up.  Secondly, there is probably a log file with some info that is useful.  Look through /var/log/ and see if you can't find what is going on when this problem occurs.  Check Xorg.0.log , there is another one that logs system events, I think it's supposed to be /var/log/syslog or /var/log/messages but I can't find either on my machine.

---

### Post by nic11 on 2016-03-22
> **Nad_Fink said:**
> I am not sure what is causing your problem, but maybe I can spur some ideas. First off, those messages you are seeing when the screen goes black are boot messages, likely still on that display from boot up.  Secondly, there is probably a log file with some info that is useful.  Look through /var/log/ and see if you can't find what is going on when this problem occurs.  Check Xorg.0.log , there is another one that logs system events, I think it's supposed to be /var/log/syslog or /var/log/messages but I can't find either on my machine.

Thanks so much for this valuable advice. I am going to need some time to learn about these log reports. I am also getting some errors on start up so I need to find out how to reproduce them here and if they appear in any specific log file.

---

### Post by grahammechanical on 2016-03-22
> The system then immediately restarts automatically and the log in screen  appears even though my system does not require a log in when it boots  up.

The system might not be restarting. The same password panel is used for unlocking the screen as is used for the initial log in. Something could be triggering a power saving mode which in turn is presenting the unlock screen password panel.

Regards.

---

### Post by nic11 on 2016-04-02
> **grahammechanical said:**
> The system might not be restarting. The same password panel is used for unlocking the screen as is used for the initial log in. Something could be triggering a power saving mode which in turn is presenting the unlock screen password panel.

Regards.

Thanks for this. I am struggling to make sense of Log Reports. If anyone could direct me to useful tutorials or guides so I can identify and hopefully solve this problem, that would be greatly appreciated.

Does it seem a good idea to use APItrace to log the events that lead to this problem?

---

### Post by nic11 on 2016-04-03
I have managed to captured this event by using syslog but the account is 55 pages long.

Should I post it here?

---

