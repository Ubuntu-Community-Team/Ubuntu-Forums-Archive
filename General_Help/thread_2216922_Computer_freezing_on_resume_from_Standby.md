---
title: "Computer freezing on resume from Standby"
date: 2014-04-14
forum: General Help
---

### Post by alphabetaparkinglot on 2014-04-14
I have an odd problem, Not sure if it is the result of hardware of software problems.

Several times recently, when I put the computer in standby... well that part works just fine.

But when I try to resume from standby... nothing happens. The screen stays blank. I can't do anything. I have to just shut down by holding the external power button and restart. I have dual screens, and both of them stay blank, not responding to when I press the power button to resume. The fans come on and all that jazz... but the screens stay off and as far as I can tell the only option is to restart.

Similarly, occasionally when I leave my computer running and step away for a while, the computer freezes up. I will just sit back down at my computer to find the mouse won't move (trackpad or external mouse) and none of the keyboard buttons do anything. Once again the only option here seems to be for me to hold down the power button and restart.

For obvious reasons I suspect the those two issues are symptoms of the same problem. No idea what that might be though. I am under warranty, and have a line of dead pixels on my screen (so I suppose getting it sent for repairs is in order), but I have not done this yet (and don't wish to do it) because I need the computer for work.

I am using a SONY VIAO [COLOR=#333333][FONT=arial]15.5" E [/FONT][/COLOR][COLOR=#333333][FONT=arial]Series, with Ubuntu 12.04 LTS, 64 bit.

[/FONT][/COLOR][FONT=arial]rd gen Intel® Core™ i5-3210M processor (2.50GHz / 3.10GHz with Turbo Boost)[/FONT]
[FONT=arial]8GB (4GB x2) DDR3-1333MHz[/FONT]
[FONT=arial]AMD Radeon™ HD 7550M (1GB) dedicated graphics[/FONT]
[FONT=arial]15.5" LED backlit display (1366 x 768)[/FONT]
[FONT=arial]750GB (5400rpm) hard drive[/FONT][FONT=arial]

lshw output is below, incase anyone wants that much detail
[/FONT]```
kaylee                        description: Notebook
    product: SVE151190X (N/A)
    vendor: Sony Corporation
    version: C10F6B0X
    serial: 54295740-0001519
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 vsyscall32
    configuration: boot=normal chassis=notebook family=VAIO sku=N/A uuid=20FBAF5E-C933-E111-8B5E-30F9EDB8C5E6
  *-core
       description: Motherboard
       product: VAIO
       vendor: Sony Corporation
       physical id: 0
       version: N/A
       serial: N/A
     *-firmware
          description: BIOS
          vendor: Insyde Corp.
          physical id: 0
          version: R0180E5
          date: 04/24/2012
          size: 128KiB
          capacity: 3008KiB
          capabilities: pci pnp upgrade shadowing cdboot bootselect edd int9keyboard int10video acpi usb smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i5-3210M CPU @ 2.50GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Core(TM) i5-3210M CPU @ 2.50GHz
          serial: N/A
          slot: N/A
          size: 1200MHz
          capacity: 1200MHz
          width: 64 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm ida arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid fsgsbase smep erms cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: internal write-through data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: internal write-through unified
        *-cache:2
             description: L3 cache
             physical id: 7
             slot: L3 Cache
             size: 3MiB
             capacity: 3MiB
             capabilities: internal write-back unified
     *-memory
          description: System Memory
          physical id: 9
          slot: System board or motherboard
          size: 8GiB
        *-bank:0
             description: SODIMM DDR3
             physical id: 0
             slot: SODIMM1
             size: 4GiB
             width: 64 bits
        *-bank:1
             description: SODIMM DDR3
             physical id: 1
             slot: SODIMM2
             size: 4GiB
             width: 64 bits
     *-pci
          description: Host bridge
          product: 3rd Gen Core processor DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
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
             resources: irq:40 ioport:3000(size=4096) memory:c0000000-c0ffffff ioport:b0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: Thames [Radeon HD 7550M/7570M/7650M]
                vendor: Hynix Semiconductor (Hyundai Electronics)
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
                configuration: driver=fglrx_pci latency=0
                resources: irq:47 memory:b0000000-bfffffff memory:c0000000-c001ffff ioport:3000(size=256) memory:c0040000-c005ffff
           *-multimedia
                description: Audio device
                product: Turks/Whistler HDMI Audio [Radeon HD 6000 Series]
                vendor: Hynix Semiconductor (Hyundai Electronics)
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:46 memory:c0020000-c0023fff
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
             resources: irq:42 memory:c1300000-c130ffff
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
             configuration: driver=mei latency=0
             resources: irq:44 memory:c1314000-c131400f
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
             configuration: driver=ehci_hcd latency=0
             resources: irq:16 memory:c1319000-c13193ff
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
             resources: irq:45 memory:c1310000-c1313fff
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
             resources: irq:17 memory:c1200000-c12fffff ioport:c1500000(size=1048576)
           *-network
                description: Wireless interface
                product: AR9485 Wireless Network Adapter
                vendor: Qualcomm Atheros
                physical id: 0
                bus info: pci@0000:07:00.0
                logical name: wlan0
                version: 01
                serial: 08:ed:b9:d5:61:f7
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
                configuration: broadcast=yes driver=ath9k driverversion=3.2.0-60-generic firmware=N/A ip=192.168.1.3 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
                resources: irq:16 memory:c1200000-c127ffff memory:c1500000-c150ffff
        *-pci:2
             description: PCI bridge
             product: 7 Series/C210 Series Chipset Family PCI Express Root Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 memory:c1100000-c11fffff
           *-generic
                description: Unassigned class
                product: RTS5209 PCI Express Card Reader
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:08:00.0
                logical name: scsi6
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list emulated scsi-host
                configuration: driver=rts_pstor latency=0
                resources: irq:17 memory:c1100000-c1100fff
              *-disk:0
                   description: SCSI Disk
                   physical id: 0.0.0
                   bus info: scsi@6:0.0.0
                   logical name: /dev/sdb
              *-disk:1
                   description: SCSI Disk
                   product: MemoryStick
                   vendor: Generic-
                   physical id: 0.0.1
                   bus info: scsi@6:0.0.1
                   logical name: /dev/sdc
                   version: 1.00
                   serial: 3
                   capabilities: removable
                 *-medium
                      physical id: 0
                      logical name: /dev/sdc
        *-pci:3
             description: PCI bridge
             product: 7 Series/C210 Series Chipset Family PCI Express Root Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:18 ioport:2000(size=4096) ioport:c1000000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:09:00.0
                logical name: eth0
                version: 07
                serial: 30:f9:ed:b8:c5:e6
                size: 10Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:43 ioport:2000(size=256) memory:c1004000-c1004fff memory:c1000000-c1003fff
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
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:c1318000-c13183ff
        *-isa
             description: ISA bridge
             product: HM76 Express Chipset LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: SATA controller
             product: 7 Series Chipset Family 6-port SATA Controller [AHCI mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi4
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:41 ioport:4048(size=8) ioport:4054(size=4) ioport:4040(size=8) ioport:4050(size=4) ioport:4020(size=32) memory:c1317000-c13177ff
           *-disk
                description: ATA Disk
                product: TOSHIBA MQ01ABD0
                vendor: Toshiba
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: AX0A
                serial: 52OAF5J7S
                size: 698GiB (750GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=f9eef613
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 0a73-9419
                   size: 18GiB
                   capacity: 18GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2012-07-14 08:23:17 filesystem=ntfs label=Recovery state=clean
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   version: 3.1
                   serial: 4afc-b5fe
                   size: 331MiB
                   capacity: 350MiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2012-07-14 08:41:27 filesystem=ntfs label=System Reserved state=clean
              *-volume:2
                   description: Windows NTFS volume
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   version: 3.1
                   serial: 50757ccc-9c4b-0e4e-8c86-7b5b4f06826f
                   size: 92GiB
                   capacity: 92GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2012-07-14 08:41:28 filesystem=ntfs state=clean
              *-volume:3
                   description: Extended partition
                   physical id: 4
                   bus info: scsi@0:0.0.0,4
                   logical name: /dev/sda4
                   size: 587GiB
                   capacity: 587GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 8160MiB
                      capabilities: nofs
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      logical name: /
                      capacity: 579GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,barrier=1,data=ordered state=mounted
           *-cdrom
                description: DVD-RAM writer
                product: CDDVDW SN-208BB
                vendor: TSSTcorp
                physical id: 1
                bus info: scsi@4:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/sr0
                version: SN02
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
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
             resources: memory:c1315000-c13150ff ioport:4000(size=32)



```[FONT=arial]
[/FONT]

---

### Post by jbaerboc on 2014-04-17
I don't know if this will help, but I use the suspend feature in Ubuntu a lot and it never used to work until I messed around with my swap partition size. It's something like 4GB or somesuch right now and suspend works fine. Do you know what your swap partition's size it? If it's in your previous info I completely missed it.

---

### Post by alphabetaparkinglot on 2014-04-18
I have an 8GB swap partition. 

Also it worked fine for about 1.5 years until just a few weeks ago. I have not changed anything significant that I can think of.

Oddly enough, today it successfully arose from standby as it normally should... but it had only been in standby for a few minutes.

---

### Post by jbaerboc on 2014-04-18
Wow that is really strange...well hopefuly someone here can help you further. I'd assume finding a way to make the computer log what it's doing when going into suspend and then have it attempt to log waking back up might help more advanced Ubuntu Forum individuals peg where the problem lays. No clue how you'd set it up to log those instances though :(

---

### Post by su:bhatta on 2014-04-18
What version Ubuntu are you using?
Made any changes in Kernel version, after which this started to happen?

Asking because, with kernel 3.13.my laptop never would 'wake' from 'Sleep' .
After generating a bug report, Canonical asked me to try mainline kernel 3.14 & using kernel 3.14 it was fixed.

[**[COLOR=#000000]jbaerboc[/COLOR]**]("http://ubuntuforums.org/member.php?u=1260320"), since your distro says, Dev release, you can give Kernel 3.14.1 a try from here : [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.14.1-trusty/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.14.1-trusty/)

---

### Post by alphabetaparkinglot on 2014-04-18
Im on Ubuntu 12.04, I gave that and plenty more detail in the original post.

I don't think I changed the kernel version (because Im not sure how to do that). I have updated, installed, and removed a few packages... but that was all done automatically through the update manager.

How would I go about generating a bug report? Even if I were to get the computer to log what is going on, would I be able to retrieve the info? In order to use my computer I need to force-restart it... so I imagine any logged data would be lost.

---

### Post by su:bhatta on 2014-04-18
You can generate a bug report following this [wiki.]("https://help.ubuntu.com/community/ReportingBugs")

The log files should be present , just check once.

---

### Post by jbaerboc on 2014-04-18
> **su:bhatta said:**
> What version Ubuntu are you using?
Made any changes in Kernel version, after which this started to happen?

Asking because, with kernel 3.13.my laptop never would 'wake' from 'Sleep' .
After generating a bug report, Canonical asked me to try mainline kernel 3.14 & using kernel 3.14 it was fixed.

[**[COLOR=#000000]jbaerboc[/COLOR]**]("http://ubuntuforums.org/member.php?u=1260320"), since your distro says, Dev release, you can give Kernel 3.14.1 a try from here : [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.14.1-trusty/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.14.1-trusty/)


Now that Trusty is out I really need to update that :D

---

### Post by arm-c on 2014-04-19
Resume from Suspend:  In case anyone is reading and using Noveau drivers for their NVIDA card.... I don't know when it will be fixed, but the Noveau drives under 14.04 kept crashing after suspend....  

Once I changed to the proprietary drivers for NVIDIA... suspend/resume works perfect.  No issues.

---

### Post by alphabetaparkinglot on 2014-04-19
Thanks su:bhatta,

That link says the first thing to do is update your BIOS. I did a little google-ing, but I'm afraid I still have no idea how to do that... and it seems to be a really complicated procedure. Do you think that might solve this?

Also can you clarify what you meant by "[COLOR=#000000]The log files should be present , just check once."
[/COLOR]

---

