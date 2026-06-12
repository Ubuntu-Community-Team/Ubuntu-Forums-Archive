---
title: "What happens to lubuntu if left without power for some time?"
date: 2017-07-29
forum: General Help
---

### Post by abovethecloud on 2017-07-29
I recently installed Lubutu 16.04 (32 bit) on a relatively old laptop.
The battery doesn't work anymore, so when I have to move the computer, it stays completely out of power for hours, maybe more.
I didn't think this could be much of a problem, but the first time I did it (yesterday), the clock resetted itself (but I guess this can't be helped and I understand why) and, more importantly, the **drivers** I had installed to fix the Wi-Fi **had** completely **disappeared** (and with them also the standard versions that were pre-installed the first time I booted the OS). I had to reinstall them again (and had some troubles doing so without the Wi-Fi working!).

My questions are:
[LIST]
[*]Is this behaviour normal?
[*]What is the cause of the drivers disappearing? Is it really dependent of the absence of power?
[*]Is it possible to prevent this from happening?
[/LIST]

Thanks in advance!

---

### Post by Futant on 2017-07-29
Whatever the problem is, it's not caused by the computer being switched off for a few hours. That behaviour isn't normal if it happened by itself, did you cut power or run any commands before it started? How old is the laptop? Could the hdd be failing? This can cause all kinds of random problems.

---

### Post by oldos2er on 2017-07-29
Did you properly shut down Lubuntu before turning it off?

Losing clock settings could be the CMOS battery failing. And losing drivers after a power down isn't normal at all. I agree with Futant it could be failing hardware.

What make/model laptop? BIOS version? Hardware specs?

---

### Post by efflandt on 2017-07-30
The clock is easily explainable by dead CMOS battery, unless it also loses timezone settings. In some cases the CMOS battery is a rechargeable battery that gets recharged when the laptop is on. Otherwise it might be some sort of long life lithium battery.

The only reason I think a system could lose drivers (and forget timezone) is if the system is not really "installed" at all, it is just a live/install system to use to test that version or do an install, and you had installed the drivers to RAM disk, which went away when the system was shut down.

Post the output of the **mount** command when the system is running.

---

### Post by abovethecloud on 2017-07-30
First, thank you all for your answers.

> **Futant said:**
> did you cut power or run any commands before it started? How old is the laptop? Could the hdd be failing? This can cause all kinds of random problems.
I didn't run any particular commands before, no. The laptop is old and has been left unused for the longest time, so the HDD might as well be failing, but I don't know how to know for sure. I'm posting the output of sanitized lshw for more info on the hardware:
```
computer                  
    description: Hand Held Computer
    product: MS-1012
    vendor: MICRO-STAR INT'L CO.,LTD
    version: 0121
    serial: [REMOVED]
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.1 smp
    configuration: chassis=handheld cpus=1 uuid=[REMOVED]
  *-core
       description: Motherboard
       physical id: 0
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: A1012IMS V2.50
          date: 02/22/2005
          size: 64KiB
          capacity: 448KiB
          capabilities: isa pci pcmcia pnp upgrade shadowing escd cdboot bootselect edd int5printscreen int9keyboard int17printer acpi usb agp smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) M processor 1.60GHz
          vendor: Intel Corp.
          physical id: 3
          bus info: cpu@0
          version: 6.13.8
          slot: CPU 1
          size: 1596MHz
          capacity: 1596MHz
          width: 32 bits
          clock: 400MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx bts est tm2 cpufreq
        *-cache:0
             description: L1 cache
             physical id: 4
             slot: L1-Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: pipeline-burst internal varies data
             configuration: level=1
        *-cache:1
             description: L2 cache
             physical id: 5
             slot: L2-Cache
             size: 2MiB
             capacity: 2MiB
             capabilities: pipeline-burst internal varies unified
             configuration: level=2
     *-memory
          description: System Memory
          physical id: 8
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM SDRAM Synchronous
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: [REMOVED]
             slot: DIMM0
             size: 1GiB
             width: 64 bits
        *-bank:1
             description: DIMM SDRAM Synchronous
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: [REMOVED]
             slot: DIMM1
             size: 1GiB
             width: 64 bits
     *-pci
          description: Host bridge
          product: Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
        *-display:0
             description: VGA compatible controller
             product: Mobile 915GM/GMS/910GML Express Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:fbe80000-fbefffff ioport:dc00(size=8) memory:d0000000-dfffffff memory:fbe40000-fbe7ffff memory:c0000-dffff
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 915GM/GMS/910GML Express Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:fbd80000-fbdfffff
        *-usb:0
             description: USB controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:d880(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 4.10.0-28-generic uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 4.10
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
              *-usb
                   description: Generic USB device
                   product: 802.11n NIC
                   vendor: Realtek
                   physical id: 1
                   bus info: usb@1:1
                   version: 0.00
                   serial: [REMOVED]
                   capabilities: usb-2.00
                   configuration: driver=r8188eu maxpower=500mA speed=12Mbit/s
        *-usb:1
             description: USB controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:d800(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 4.10.0-28-generic uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 4.10
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-usb:2
             description: USB controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:d480(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 4.10.0-28-generic uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 4.10
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-usb:3
             description: USB controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:d400(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 4.10.0-28-generic uhci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 4.10
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-pci
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: d4
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: ioport:e000(size=4096) memory:fbf00000-fbffffff
           *-network:0
                description: Ethernet interface
                product: RTL-8100/8101L/8139 PCI Fast Ethernet Adapter
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 3
                bus info: pci@0000:01:03.0
                logical name: enp1s3
                version: 10
                serial: [REMOVED]
                size: 10Mbit/s
                capacity: 100Mbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
                resources: irq:22 ioport:e800(size=256) memory:fbfffc00-fbfffcff memory:fbfe0000-fbfeffff
           *-pcmcia:0
                description: CardBus bridge
                product: RL5c476 II
                vendor: Ricoh Co Ltd
                physical id: 4
                bus info: pci@0000:01:04.0
                version: ac
                width: 64 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=131
                resources: iomemory:b00202010-b0020200f irq:19 memory:80000000-80000fff ioport:e000(size=256) ioport:e400(size=256) memory:84000000-87ffffff memory:88000000-8bffffff
           *-pcmcia:1
                description: CardBus bridge
                product: RL5c476 II
                vendor: Ricoh Co Ltd
                physical id: 4.1
                bus info: pci@0000:01:04.1
                version: ac
                width: 64 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=128
                resources: iomemory:b00603010-b0060300f irq:20 memory:8c000000-8c000fff ioport:ec00(size=256) ioport:1000(size=256) memory:90000000-93ffffff memory:94000000-97ffffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: R5C552 IEEE 1394 Controller
                vendor: Ricoh Co Ltd
                physical id: 4.2
                bus info: pci@0000:01:04.2
                version: 04
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=64 maxlatency=4 mingnt=2
                resources: irq:21 memory:fbfff000-fbfff7ff
           *-network:1 UNCLAIMED
                description: Network controller
                product: PRO/Wireless 2200BG [Calexico2] Network Connection
                vendor: Intel Corporation
                physical id: 9
                bus info: pci@0000:01:09.0
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=64 maxlatency=24 mingnt=3
                resources: memory:fbffe000-fbffefff
        *-multimedia
             description: Multimedia audio controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1e.2
             bus info: pci@0000:00:1e.2
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_intel8x0 latency=0
             resources: irq:17 ioport:d000(size=256) ioport:cc00(size=64) memory:fbe3bc00-fbe3bdff memory:fbe3b800-fbe3b8ff
        *-communication UNCLAIMED
             description: Modem
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1e.3
             bus info: pci@0000:00:1e.3
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm generic cap_list
             configuration: latency=0
             resources: ioport:c800(size=256) ioport:c480(size=128)
        *-isa
             description: ISA bridge
             product: 82801FBM (ICH6M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide
             description: IDE interface
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16)
        *-serial UNCLAIMED
             description: SMBus
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 04
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:400(size=32)
     *-scsi
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: SAMSUNG MP0402H
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 0-14
             serial: [REMOVED]
             size: 37GiB (40GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=10deb571
           *-volume:0
                description: Linux filesystem partition
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /boot
                version: 1.0
                serial: [REMOVED]
                size: 487MiB
                capacity: 487MiB
                capabilities: primary bootable extended_attributes large_files ext2 initialized
                configuration: filesystem=ext2 lastmountpoint=/boot modified=2017-07-29 15:48:00 mount.fstype=ext2 mount.options=rw,relatime,block_validity,barrier,user_xattr,acl mounted=2017-07-29 14:29:39 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 36GiB
                capacity: 36GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux LVM Physical Volume partition
                   physical id: 5
                   logical name: /dev/sda5
                   serial: [REMOVED]
                   size: 36GiB
                   capacity: 36GiB
                   capabilities: multi lvm2
        *-cdrom
             description: DVD writer
             product: DVDRW SOSW-852S
             vendor: Slimtype
             physical id: 0.1.0
             bus info: scsi@0:0.1.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: PES2
             capabilities: removable audio cd-r cd-rw dvd dvd-r
             configuration: ansiversion=5 status=nodisc
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:1
       logical name: wlx60e3270f5426
       serial: [REMOVED]
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=r8188eu ip=[REMOVED] multicast=yes wireless=IEEE 802.11bgn
```

> **oldos2er said:**
> Did you properly shut down Lubuntu before turning it off?

Losing clock settings could be the CMOS battery failing. And losing drivers after a power down isn't normal at all. I agree with Futant it could be failing hardware.

What make/model laptop? BIOS version? Hardware specs?
Yes, I did properly shut down and THEN removed the power cord. Indeed the CMOS battery could be failing, good hypothesis. Is it that much of a problem in your opinion? I don't know if it would be worth to replace conidering the age of the computer. As for the hardware questions, I posted the result of lshw above*.* 

> **efflandt said:**
> The clock is easily explainable by dead CMOS battery
Yeah, that's probably it.. Again, do you think it would cause much troubles and would have to be replaced (if feasible)?

> **efflandt said:**
> The only reason I think a system could lose drivers (and forget timezone) is if the system is not really "installed" at all, it is just a live/install system to use to test that version or do an install, and you had installed the drivers to RAM disk, which went away when the system was shut down.
Post the output of the **mount** command when the system is running.
As far as I know this is an absolutely installed version of Lubuntu! But I will post the output of **mount** as requested:
```
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=993168k,nr_inodes=208887,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=202796k,mode=755)
/dev/mapper/lubuntu--vg-root on / type ext4 (rw,relatime,errors=remount-ro,data=ordered)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/lib/systemd/systemd-cgroups-agent,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=32,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=13181)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime)
mqueue on /dev/mqueue type mqueue (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
/dev/sda1 on /boot type ext2 (rw,relatime,block_validity,barrier,user_xattr,acl)
tmpfs on /run/user/1000 type tmpfs (rw,nosuid,nodev,relatime,size=202796k,mode=700,uid=1000,gid=1000)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000)
```

Anyway, I will probably need to unplug it for some hours again in about 12 h, so I will check to see if the drivers like to disappear again (and at this point I will expect to lose the clock if the CMOS batter is dead).

---

### Post by abovethecloud on 2017-07-31
Ok, I had to move the laptop again and I powered it down correctly, waited, and then remove the power cord. After 2-3 hours I could plug it in again and in fact the starting screen showed "CMOS settings wrong. F2 to load defaults" or something like that. Then the first attempt to load Lubuntu was a fail (black screen for many minutes). I forced shutdown and the next attempt was successful, even though with some errors I had no time to write down.

And** the Wireless driver is gone again**. I am really puzzled, since everything else seems to be more or less okay.
To install the driver I followed that guide: [https://askubuntu.com/questions/678134/how-to-install-tp-link-wn725n-wifi-usb-adapter-on-ubuntu-ubuntu-14-04-3-lts](https://askubuntu.com/questions/678134/how-to-install-tp-link-wn725n-wifi-usb-adapter-on-ubuntu-ubuntu-14-04-3-lts).

Any ideas? It feels really wrong to have to reinstall this driver each time, who knows what else I may be losing in the future or even now without noticing.

Thanks in advance.

---

### Post by oldos2er on 2017-07-31
> Indeed the CMOS battery could be failing, good hypothesis. Is it that much of a problem in your opinion? For me? Having to re-enter all my settings every time I boot would really test my patience to the breaking point. However I've only changed out CMOS on desktops, not laptops, so I don't know how difficult it would be to change it on your hardware. Check the manufacturer's website. Usually the batteries themselves are cheap.

Have you run smartctl on the hard disk? [https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)

---

### Post by abovethecloud on 2017-08-02
> **oldos2er said:**
> For me? Having to re-enter all my settings every time I boot would really test my patience to the breaking point.
Yeah, good point. Though, I plan to use the computer as a pi-hole, leaving it on 24/7.


> **oldos2er said:**
> Have you run smartctl on the hard disk? [https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)
Not yet, but thanks for the tip, I will next week!

---

