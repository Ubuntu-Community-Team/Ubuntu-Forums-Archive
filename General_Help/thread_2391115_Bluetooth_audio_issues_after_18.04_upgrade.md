---
title: "Bluetooth audio issues after 18.04 upgrade"
date: 2018-05-06
forum: General Help
---

### Post by yendis2 on 2018-05-06
Hi,

After upgrading to 18.04, I'm having some issues with my bluetooth headphones (Bose Silent Comfort 35). When using it for a while, it seems to build up a delay in the audio. I've noticed delays up to around 3s so far.
Turning the headphones on and off does not get rid of the delay, restarting the laptop doesn't fix the delay either. Removing the bluetooth device from the bluetooth settings and connecting them again will (usually) fix the problem. The audio will work fine for a few minutes up to a few hours before the problem appears again.

When I was using 17.10 it worked all the time without a problem.
Does anyone have an idea what I can do to fix this issue or is this a known bug?

Thanks!

---

### Post by mörgæs on 2018-05-08
Hi, welcome to the fora.

As a first step in diagnosing this kind of problems it's always a good idea to try a live boot of 18.04.

---

### Post by yendis2 on 2018-05-20
Sorry for the slow response. I got around to trying the bluetooth audio on the live boot (18.04) and I also got delays in the audio after using it for around 30 minutes. The only thing I did was start the ubuntu live, fire up firefox and watch a couple of youtube video's.

Anything else I can try?

---

### Post by mörgæs on 2018-05-21
Let's see the hardware details. Please copy and paste ```
sudo lshw -sanitize > lshw.txt
``` to the command line, run it and post lshw.txt in CODE tags.

---

### Post by yendis2 on 2018-05-21
This is the output:

```

computer
    description: Notebook
    product: 20DFCTO1WW (LENOVO_MT_20DF_BU_Think_FM_ThinkPad E550)
    vendor: LENOVO
    version: ThinkPad E550
    serial: [REMOVED]
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 smp vsyscall32
    configuration: administrator_password=disabled chassis=notebook family=ThinkPad E550 power-on_password=disabled sku=LENOVO_MT_20DF_BU_Think_FM_ThinkPad E550 uuid=[REMOVED]
  *-core
       description: Motherboard
       product: 20DFCTO1WW
       vendor: LENOVO
       physical id: 0
       version: SDK0E50510 WIN
       serial: [REMOVED]
       slot: Not Available
     *-cache
          description: L1 cache
          physical id: 3
          slot: L1 Cache
          size: 32KiB
          capacity: 32KiB
          capabilities: synchronous internal write-back data
          configuration: level=1
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i7-5500U CPU @ 2.40GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Core(TM) i7-5500U CPU @ 2.40GHz
          serial: [REMOVED]
          slot: U3E1
          size: 2338MHz
          capacity: 3GHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch cpuid_fault epb invpcid_single pti tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid rdseed adx smap intel_pt xsaveopt ibpb ibrs stibp dtherm ida arat pln pts cpufreq
          configuration: cores=2 enabledcores=2 threads=4
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back instruction
             configuration: level=1
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: synchronous internal write-back unified
             configuration: level=2
        *-cache:2
             description: L3 cache
             physical id: 7
             slot: L3 Cache
             size: 4MiB
             capacity: 4MiB
             capabilities: synchronous internal write-back unified
             configuration: level=3
     *-memory
          description: System Memory
          physical id: 8
          slot: System board or motherboard
          size: 16GiB
        *-bank:0
             description: SODIMM DDR3 Synchronous 1600 MHz (0.6 ns)
             product: KHX1600C9S3L/8G
             vendor: Kingston
             physical id: 0
             serial: [REMOVED]
             slot: ChannelA-DIMM0
             size: 8GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
        *-bank:1
             description: SODIMM DDR3 Synchronous 1600 MHz (0.6 ns)
             product: KHX1600C9S3L/8G
             vendor: Kingston
             physical id: 1
             serial: [REMOVED]
             slot: ChannelB-DIMM0
             size: 8GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
     *-firmware
          description: BIOS
          vendor: LENOVO
          physical id: 30
          version: J5ET60WW (1.31 )
          date: 02/25/2018
          size: 128KiB
          capacity: 15MiB
          capabilities: pci pnp upgrade shadowing cdboot bootselect acpi usb biosbootspecification uefi
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
             resources: irq:47 memory:e0000000-e0ffffff memory:d0000000-dfffffff ioport:4000(size=64) memory:c0000-dffff
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
             resources: irq:51 memory:e1330000-e1333fff
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
             resources: irq:42 memory:e1320000-e132ffff
           *-usbhost:0
                product: xHCI Host Controller
                vendor: Linux 4.15.0-20-generic xhci-hcd
                physical id: 0
                bus info: usb@2
                logical name: usb2
                version: 4.15
                capabilities: usb-2.00
                configuration: driver=hub slots=11 speed=480Mbit/s
              *-usb:0
                   description: Mouse
                   product: Razer DeathAdder
                   vendor: Razer
                   physical id: 3
                   bus info: usb@2:3
                   version: 1.00
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=100mA speed=12Mbit/s
              *-usb:1 UNCLAIMED
                   description: Generic USB device
                   product: VFS5011 Fingerprint Reader
                   vendor: Validity Sensors, Inc.
                   physical id: 6
                   bus info: usb@2:6
                   version: 0.78
                   serial: [REMOVED]
                   capabilities: usb-1.10
                   configuration: maxpower=100mA speed=12Mbit/s
              *-usb:2
                   description: Bluetooth wireless interface
                   vendor: Intel Corp.
                   physical id: 7
                   bus info: usb@2:7
                   version: 0.01
                   capabilities: bluetooth usb-2.00
                   configuration: driver=btusb maxpower=100mA speed=12Mbit/s
              *-usb:3
                   description: Video
                   product: Integrated Camera
                   vendor: J8IF913MA
                   physical id: 8
                   bus info: usb@2:8
                   version: 0.07
                   capabilities: usb-2.00
                   configuration: driver=uvcvideo maxpower=500mA speed=480Mbit/s
           *-usbhost:1
                product: xHCI Host Controller
                vendor: Linux 4.15.0-20-generic xhci-hcd
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
             resources: irq:48 memory:e1339000-e133901f
        *-network
             description: Ethernet interface
             product: Ethernet Connection (3) I218-V
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@0000:00:19.0
             logical name: enp0s25
             version: 03
             serial: [REMOVED]
             capacity: 1Gbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k firmware=0.2-4 latency=0 link=no multicast=yes port=twisted pair
             resources: irq:43 memory:e1300000-e131ffff memory:e133e000-e133efff ioport:4080(size=32)
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
             resources: irq:50 memory:e1334000-e1337fff
        *-pci:0
             description: PCI bridge
             product: Wildcat Point-LP PCI Express Root Port #1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: e3
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode cap_list
             configuration: driver=pcieport
             resources: irq:16
        *-pci:1
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
             resources: irq:18 memory:e1200000-e12fffff
           *-network
                description: Wireless interface
                product: Wireless 3160
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:04:00.0
                logical name: wlp4s0
                version: 93
                serial: [REMOVED]
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlwifi driverversion=4.15.0-20-generic firmware=17.608620.0 ip=[REMOVED] latency=0 link=yes multicast=yes wireless=IEEE 802.11
                resources: irq:49 memory:e1200000-e1201fff
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
             resources: irq:16 ioport:3000(size=4096) memory:e1100000-e11fffff ioport:c0000000(size=268435456)
           *-display
                description: Display controller
                product: Opal XT [Radeon R7 M265]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0
                bus info: pci@0000:05:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list rom
                configuration: driver=radeon latency=0
                resources: irq:45 memory:c0000000-cfffffff memory:e1100000-e113ffff ioport:3000(size=256) memory:e1140000-e115ffff
        *-pci:3
             description: PCI bridge
             product: Wildcat Point-LP PCI Express Root Port #6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: e3
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 memory:e1000000-e10fffff
           *-generic
                description: Unassigned class
                product: RTS5227 PCI Express Card Reader
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:06:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=rtsx_pci latency=0
                resources: irq:44 memory:e1000000-e1000fff
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
             resources: irq:23 memory:e133d000-e133d3ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.15.0-20-generic ehci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 4.15
                capabilities: usb-2.00
                configuration: driver=hub slots=3 speed=480Mbit/s
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
             resources: irq:46 ioport:40a8(size=8) ioport:40b4(size=4) ioport:40a0(size=8) ioport:40b0(size=4) ioport:4060(size=32) memory:e133c000-e133c7ff
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
             resources: memory:e1338000-e13380ff ioport:efa0(size=32)
        *-generic
             description: Signal processing controller
             product: Wildcat Point-LP Thermal Management Controller
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=intel_pch_thermal latency=0
             resources: irq:18 memory:e133b000-e133bfff
     *-scsi:0
          physical id: 0
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: Samsung SSD 840
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: AB0Q
             serial: [REMOVED]
             size: 232GiB (250GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=80bf8a39
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /media/xxxxx/948207B482079A3E
                version: 3.1
                serial: [REMOVED]
                size: 182GiB
                capacity: 182GiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2015-01-18 04:37:05 filesystem=ntfs mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 state=mounted
           *-volume:1
                description: Windows NTFS volume
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                version: 3.1
                serial: [REMOVED]
                size: 843MiB
                capacity: 865MiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2018-03-29 05:37:02 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
           *-volume:2
                description: Extended partition
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                size: 48GiB
                capacity: 48GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 5
                   logical name: /dev/sda5
                   logical name: /
                   version: 1.0
                   serial: [REMOVED]
                   size: 48GiB
                   capacity: 48GiB
                   capabilities: journaled extended_attributes large_files huge_files dir_nlink recover 64bit extents ext4 ext2 initialized
                   configuration: created=2017-09-08 15:07:52 filesystem=ext4 lastmountpoint=/ modified=2018-05-21 07:25:21 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2018-05-21 07:25:22 state=mounted
     *-scsi:1
          physical id: 1
          logical name: scsi1
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST2000LM003 HN-M
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/sdb
             version: 0001
             serial: [REMOVED]
             size: 1863GiB (2TB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=4096 signature=0e7becf6
           *-volume
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@1:0.0.0,1
                logical name: /dev/sdb1
                logical name: /media/xxxxx/Data
                version: 3.1
                serial: [REMOVED]
                size: 1863GiB
                capacity: 1863GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2014-06-05 09:54:29 filesystem=ntfs label=Data mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 state=mounted
  *-battery
       product: LNV-45N1
       vendor: SANYO
       physical id: 1
       slot: Front
       capacity: 47520mWh
       configuration: voltage=10.8V

```

EDIT
A bit more info:
The behaviour of the audio has hanged a little bit. Once I pause a video when there is a delay and then continue, the audio now starts directly but immediately starts popping/cracking until the delay is back like before pausing the video. (befure it didn't "catch up").

The delay also affects video players (default video player & VLC). Volume changes both in the player and the system volume are also delayed.

Switching to wired headphones/speakers, the audio is just fine. (and then switching back to bluetooth, the delay is still there)

---

### Post by mörgæs on 2018-05-23
The hardware is certainly not the bottleneck.

I don't know enough about Bluetooth to guide you further. Maybe you would get better help if you asked a moderator to move the thread to the Networking forum.

---

### Post by yendis2 on 2018-07-19
The issue has changes a bit again, when connecting it will keep connecting, disconnecting, connecting, disconnecting, ...... for around 5 times. Then it will stay disconnected.
The problem seems to appear now after waking up my laptop from sleep mode.

I have recently found a fix that will fix the bluetooth for as long as my laptop doesn't go to sleep mode! The following command will fix the issue:
sudo /etc/init.d/bluetooth restart

Now the sound will not stutter, and the bluetooth will not disconnect at all it seems, so everything is fine again.
I thought this might be helpful if anyone has the same issue in the future or someone might want to look into this.

---

### Post by Pickel on 2018-07-31
I iuse the blueman manager to disconnect and connect the audio sink when this occurs, it helps for a while.

---

### Post by ddleon on 2018-08-08
> **Pickel said:**
> I iuse the blueman manager to disconnect and connect the audio sink when this occurs, it helps for a while.

After I have installed blueman I had no issue with JBL Everest 300. 
I removed the device from Ubuntu's bluetooth manager and reconnected with blueman.

---

### Post by pete0512 on 2018-09-07
I have the same problem, it's only by disconnecting then reconnecting bluetooth I can get it to work and then only until the next time I pause the feed then I have to  go though the same routine again. 18.04 Kubuntu used to work perfectly before the upgrade :(

---

