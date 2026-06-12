---
title: "Can't Install 'buntu 13.04 on External HDD via eSATA"
date: 2013-08-05
forum: General Help
---

### Post by DeadlyOats on 2013-08-05
I have a Vantec HX4R external enclosure. It seems to be using a hardware SATA/RAID adapter by JMicron. I can only find it listed as "JMicron H/W RAID5 ATA Device", in Win7 Device Manager, and during the POST, during boot up, it has the same name (I think - it flashes by quicker'n I can read it, but I think that's what it is). I set it for a RAID 5 set up, so that's probably why "RAID5" is in its name.

The issue is that 'buntu can't see it. I installed Win7 on it, both in EFI and in legacy ROM modes, but 'buntu just can't see the drive. I double-triple checked the "BIOS" to ensure the drive is set to boot (boot flag), and that it is set to boot after the DVD drive (boot order). I tried both EFI and Legacy Rom, and no joy on both attempts. 'buntu just can't see the RAID array/drive connected via eSATA.

The eSATA is actaully a JMicron SATA controller on the motherboard, too. Like I eluded to, both the BIOS and Win7 properly recognize it, and Win7 installs and boots from it with no issues.

What can I do to fix 'buntu 13.04 not being able to see it?

---

### Post by TheFu on 2013-08-05
Is there a driver for the RAID in Windows?  If so, then it is a FakeRaid and probably not supported by any Linux.
I have 4 disks connected via eSATA and use Linux software RAID - have for 6+ yrs. Works perfectly.

So, all is not completely lost. You just need to get the exact hardware and see how well supported it is under Linux.
[http://blog.jdpfu.com/2013/04/27/linux-troubleshooting-101-knowing-your-hardware](http://blog.jdpfu.com/2013/04/27/linux-troubleshooting-101-knowing-your-hardware) should help.

---

### Post by DeadlyOats on 2013-08-05
No drivers.  Win7 saw it during installation without any need to install additional drivers.

---

### Post by TheFu on 2013-08-05
> **DeadlyOats said:**
> No drivers.  Win7 saw it during installation without any need to install additional drivers.

What do your mean by "during installation"?  
It really isn't surprising that relatively new hardware supports Windows, is it?
Where you able to review that link and run those commands to gather information about your hardware?

---

### Post by DeadlyOats on 2013-08-05
> **TheFu said:**
> Is there a driver for the RAID in Windows?  If so, then it is a FakeRaid and probably not supported by any Linux.

Based on the question you posed, I surmised that would mean that my hardware is supported - since I din't have to install any drivers in Win7 to get it to work.  Since you asked *that*, I answered *that*.  Below is the step-by-step of what I did, to explain why I said, "During installation."

I stuck the Win7 install disk in the DVD.  I booted from that DVD.  I clicked the Start Intall button.  I checked the I agree box and clicked next.  A list of hard drives was presented, and there it was.  I did not need to do anything more than that to create a partition on it and begin the installation.

I'm in Win7.  I need to reboot the machine and get into the Kubuntu live CD to run those commands.  Wait a while for the results, please.

EDIT:  Results of lshw command.

EDIT: Additional info.  The Marvell SE9120 SATA (eSATA connector) controller is set to AHCI, and set to "Bootable."  EFI is turned on.  To get Kubuntu install DVD to start, I had to use the "nomodeset" option (otherwise the video turns off).

```
kubuntu@kubuntu:~$ lshw
WARNING: you should run this program as super-user.
kubuntu                   
    description: Computer
    width: 64 bits
    capabilities: vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 7969MiB
     *-cpu
          product: Intel(R) Core(TM) i5-2500K CPU @ 3.30GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          size: 1600MHz
          capacity: 1600MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 popcnt tsc_deadline_timer aes xsave avx lahf_lm ida arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid cpufreq
     *-pci
          description: Host bridge
          product: 2nd Generation Core Processor Family DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 09
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:e000(size=4096) memory:f8000000-fa0fffff ioport:d0000000(size=201326592)
           *-display UNCLAIMED
                description: VGA compatible controller
                product: GF114 [GeForce GTX 560 Ti]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: vga_controller bus_master cap_list
                configuration: latency=0
                resources: memory:f8000000-f9ffffff memory:d0000000-d7ffffff memory:d8000000-dbffffff ioport:e000(size=128) memory:fa000000-fa07ffff
           *-multimedia
                description: Audio device
                product: GF114 HDMI Audio Controller
                vendor: NVIDIA Corporation
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:17 memory:fa080000-fa083fff
        *-pci:1
             description: PCI bridge
             product: Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1.1
             bus info: pci@0000:00:01.1
             version: 09
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:d000(size=4096) memory:f4000000-f60fffff ioport:c0000000(size=201326592)
           *-display UNCLAIMED
                description: VGA compatible controller
                product: GF114 [GeForce GTX 560 Ti]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: vga_controller cap_list
                configuration: latency=0
                resources: memory:f4000000-f5ffffff memory:c0000000-c7ffffff memory:c8000000-cbffffff ioport:d000(size=128) memory:f6000000-f607ffff
           *-multimedia
                description: Audio device
                product: GF114 HDMI Audio Controller
                vendor: NVIDIA Corporation
                physical id: 0.1
                bus info: pci@0000:02:00.1
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:18 memory:f6080000-f6083fff
        *-communication
             description: Communication controller
             product: 6 Series/C200 Series Chipset Family MEI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=mei latency=0
             resources: irq:60 memory:f6108000-f610800f
        *-usb:0
             description: USB controller
             product: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:16 memory:f6107000-f61073ff
        *-multimedia
             description: Audio device
             product: 6 Series/C200 Series Chipset Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:61 memory:f6100000-f6103fff
        *-pci:2
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42
        *-pci:3
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:43 ioport:c000(size=4096) memory:fa600000-fa6fffff
           *-storage
                description: SATA controller
                product: 88SE9120 SATA 6Gb/s Controller
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@0000:04:00.0
                version: 12
                width: 32 bits
                clock: 33MHz
                capabilities: storage ahci_1.0 bus_master cap_list rom
                configuration: driver=ahci latency=0
                resources: irq:59 ioport:c040(size=8) ioport:c030(size=4) ioport:c020(size=8) ioport:c010(size=4) ioport:c000(size=16) memory:fa610000-fa6107ff memory:fa600000-fa60ffff
        *-pci:4
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:44 memory:fa500000-fa5fffff
           *-usb
                description: USB controller
                product: EJ168 USB 3.0 Host Controller
                vendor: Etron Technology, Inc.
                physical id: 0
                bus info: pci@0000:05:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:55 memory:fa500000-fa507fff
        *-pci:5
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 7
             vendor: Intel Corporation
             physical id: 1c.6
             bus info: pci@0000:00:1c.6
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:45 memory:fa400000-fa4fffff
           *-usb
                description: USB controller
                product: EJ168 USB 3.0 Host Controller
                vendor: Etron Technology, Inc.
                physical id: 0
                bus info: pci@0000:06:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:56 memory:fa400000-fa407fff
        *-pci:6
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 8
             vendor: Intel Corporation
             physical id: 1c.7
             bus info: pci@0000:00:1c.7
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:46 ioport:a000(size=8192) memory:fa200000-fa3fffff ioport:dc100000(size=1048576)
           *-pci
                description: PCI bridge
                product: PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch
                vendor: PLX Technology, Inc.
                physical id: 0
                bus info: pci@0000:07:00.0
                version: ba
                width: 32 bits
                clock: 33MHz
                capabilities: pci normal_decode bus_master cap_list
                configuration: driver=pcieport
                resources: irq:47 memory:fa300000-fa31ffff ioport:a000(size=8192) memory:fa200000-fa2fffff ioport:dc100000(size=1048576)
              *-pci:0
                   description: PCI bridge
                   product: PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch
                   vendor: PLX Technology, Inc.
                   physical id: 1
                   bus info: pci@0000:08:01.0
                   version: ba
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pci normal_decode bus_master cap_list
                   configuration: driver=pcieport
                   resources: irq:48
              *-pci:1
                   description: PCI bridge
                   product: PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch
                   vendor: PLX Technology, Inc.
                   physical id: 4
                   bus info: pci@0000:08:04.0
                   version: ba
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pci normal_decode bus_master cap_list
                   configuration: driver=pcieport
                   resources: irq:49
                 *-pci
                      description: PCI bridge
                      product: ASM1083/1085 PCIe to PCI Bridge
                      vendor: ASMedia Technology Inc.
                      physical id: 0
                      bus info: pci@0000:0a:00.0
                      version: 01
                      width: 32 bits
                      clock: 33MHz
                      capabilities: pci normal_decode bus_master cap_list
              *-pci:2
                   description: PCI bridge
                   product: PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch
                   vendor: PLX Technology, Inc.
                   physical id: 5
                   bus info: pci@0000:08:05.0
                   version: ba
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pci normal_decode bus_master cap_list
                   configuration: driver=pcieport
                   resources: irq:50 ioport:b000(size=4096) memory:fa200000-fa2fffff
                 *-firewire
                      description: FireWire (IEEE 1394)
                      product: VT6315 Series Firewire Controller
                      vendor: VIA Technologies, Inc.
                      physical id: 0
                      bus info: pci@0000:0c:00.0
                      version: 01
                      width: 64 bits
                      clock: 33MHz
                      capabilities: ohci bus_master cap_list
                      configuration: driver=firewire_ohci latency=0
                      resources: irq:16 memory:fa200000-fa2007ff ioport:b000(size=256)
              *-pci:3
                   description: PCI bridge
                   product: PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch
                   vendor: PLX Technology, Inc.
                   physical id: 6
                   bus info: pci@0000:08:06.0
                   version: ba
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pci normal_decode bus_master cap_list
                   configuration: driver=pcieport
                   resources: irq:51 ioport:a000(size=4096) ioport:dc100000(size=1048576)
                 *-network
                      description: Ethernet interface
                      product: RTL8111/8168 PCI Express Gigabit Ethernet controller
                      vendor: Realtek Semiconductor Co., Ltd.
                      physical id: 0
                      bus info: pci@0000:0d:00.0
                      logical name: eth0
                      version: 06
                      serial: 00:25:22:fb:10:a4
                      size: 1Gbit/s
                      capacity: 1Gbit/s
                      width: 64 bits
                      clock: 33MHz
                      capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                      configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168e-2.fw ip=10.172.58.78 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
                      resources: irq:58 ioport:a000(size=256) memory:dc104000-dc104fff memory:dc100000-dc103fff
              *-pci:4
                   description: PCI bridge
                   product: PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch
                   vendor: PLX Technology, Inc.
                   physical id: 7
                   bus info: pci@0000:08:07.0
                   version: ba
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pci normal_decode bus_master cap_list
                   configuration: driver=pcieport
                   resources: irq:52
              *-pci:5
                   description: PCI bridge
                   product: PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch
                   vendor: PLX Technology, Inc.
                   physical id: 8
                   bus info: pci@0000:08:08.0
                   version: ba
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pci normal_decode bus_master cap_list
                   configuration: driver=pcieport
                   resources: irq:53
              *-pci:6
                   description: PCI bridge
                   product: PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch
                   vendor: PLX Technology, Inc.
                   physical id: 9
                   bus info: pci@0000:08:09.0
                   version: ba
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pci normal_decode bus_master cap_list
                   configuration: driver=pcieport
                   resources: irq:54
        *-usb:1
             description: USB controller
             product: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:f6106000-f61063ff
        *-isa
             description: ISA bridge
             product: P67 Express Chipset Family LPC Controller
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
             product: 6 Series/C200 Series Chipset Family SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: storage ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:57 ioport:f070(size=8) ioport:f060(size=4) ioport:f050(size=8) ioport:f040(size=4) ioport:f020(size=32) memory:f6105000-f61057ff
        *-serial UNCLAIMED
             description: SMBus
             product: 6 Series/C200 Series Chipset Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 05
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f6104000-f61040ff ioport:f000(size=32)
     *-scsi:0
          physical id: 2
          logical name: scsi0
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DRW-24B3ST
             vendor: ASUS
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/cdrom1
             logical name: /dev/cdrw1
             logical name: /dev/dvd1
             logical name: /dev/dvdrw1
             logical name: /dev/sr0
             logical name: /cdrom
             version: 1.00
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,noatime state=mounted status=ready
           *-medium
                physical id: 0
                logical name: /dev/cdrom1
                logical name: /cdrom
                capabilities: partitioned partitioned:dos
                configuration: mount.fstype=iso9660 mount.options=ro,noatime signature=5da4864d state=mounted
              *-volume UNCLAIMED
                   description: Windows FAT volume
                   vendor: mkdosfs
                   physical id: 2
                   version: FAT12
                   serial: 5a1d-ceb6
                   size: 15EiB
                   capabilities: primary boot fat initialized
                   configuration: FATs=2 filesystem=fat
     *-scsi:1
          physical id: 3
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr1
             capabilities: audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: status=nodisc
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
kubuntu@kubuntu:~$
```

---

### Post by DeadlyOats on 2013-08-05
Help!  I'm drowning, here! (Bump, with dramatic effects attached)

---

### Post by TheFu on 2013-08-06
Well, I don't know the answer.  I did google for "ubuntu Marvell SE9120". Seems that over the years, the kernel has had issues a few times. Usually, the next kernel release seems to fix it. Have you tried booting a different kernel?  There were some forum posts on a tech site that were related. Saw it on a different system and can't find it now. The only other idea I have is to swap the cable.

What other commands have you tried?  Please use the **Adv Reply** and "code" tag so it is easier to read. Whitespace will be properly retained. Also, removing non-relevant stuff from the output would help others.

---

### Post by DeadlyOats on 2013-08-06
You're saying that the problem might be with the Marvell SE9120 eSATA controller on the motherboard, and not the JMicron RAID SATA controller in the Vantec HDD external enclosure?  I've tried other mobo settings, turning EFI off and using legacy BIOS.  The result was always the same.  'buntu couldn't see the JMicron RAID SATA controller.

With my current CPU, Intel i5, I only have SATA II and USB II capability on this mobo, an ASRock P67 Extreme4 Gen3.  I suppose, I'll try USB II connection for the external enclosure, but I'm afraid that USB II might give me less through put than SATA II.  It'll end up being a bottleneck and slow things down for me....  It's not a good long term solution, but I'll try it and see what happens.

---

### Post by TheFu on 2013-08-06
USB2 is unacceptable - it is barely acceptable on a 1G flash drive. Too slow.

The simple answer is you need to
*  know all the hardware on the system involved with the problem.
*  verify that drivers for each are available in the kernel being used.
*  be able to mount the drives/RAID using normal Linux commands.
*  validate that any configuration options - usually stored in files - are correct for the way you are trying to use the hardware AND each driver.

I've made a few suggestions, but don't know if you've tried them, don't understand what I'm asking or think they are stupid. That's fine. I can wait.

It appears you've been here awhile, so I'm assuming you are comfortable with Linux CLI, switching kernels and loading kernel drivers.  If not, please speak up.

---

### Post by oldfred on 2013-08-06
I do not know much about RAID as there seem to be many different types. But the standard desktop installer does not support RAID. They were going to add it when they did away with the alternative installer, but did not. I think the newest may install but grub still does not see the drives correctly.
You may need dmraid driver or mdadm drivers.

---

### Post by TheFu on 2013-08-06
Hi Oldfred,   I'm pretty good with mdadm stuff.  That usually means JBOD setups and all the RAID happens in software.  No RAID drivers, nothing but individual disks are seen by the OS, then the mdadm program is used to put those disks together into RAID0 thru 10 configurations.

I don't think JBOD is what the OP was using.

I think he has an external array using eSATA-MP connector - it is unclear to me where the RAID is happening - on the external array or using a built-in MB RAID.  It doesn't appear to be a FakeRAID, so I'm inclined to think the RAID is happening external to the MB.

Or I could be completely wrong. I get confused sometimes and the format of the data provided so far is difficult to read. A clear description of the setup would help me draw a mental picture. I don't have that yet.

---

### Post by DeadlyOats on 2013-08-06
The RAID is in the Vantec external HDD enclosure.  The RAID is built and configured in the external enclosure.  It's a JMicron SATA RAID controller built into the external HDD enclosure, outside of the motherboard's control.  You have to flip physical switches on the enclosure body to configure the RAID.

It is connected to the mobo via eSATA.  Windows7 sees the RAID.  'buntu cannot see the RAID, but it can't see the individual drives in the external enclosure either.  I'm starting to think it's the eSATA controller on the motherboard that 'buntu can't see, a Marvell SE9120 SATA controller on an ASRock P67 Extreme4 Gen3 mobo.

Is there a way to verify this?

I have to get some sleep.  I've been awake all night and need sleep.  I'll try installing Kubuntu onto the RAID via USB, to see if 'buntu can see the RAID via USB.  But right now, I need sleep.  Thanks for your help so far, please bear with me a bit longer.

---

### Post by TheFu on 2013-08-06
The fact that everything works across the 
** RAID - eSATA-MP - Cable - eSATA-MP - Windows **
tells me that it is likely a driver issue or proprietary RAID format.

There was a time when Linux couldn't boot from RAID-anything, so we had to put our /boot partitions on non-RAID storage. Just getting to the point that Ubuntu can see the storage device(s) would be good.

A few commands 
- lspci -t
- lspci -k

Please post respecting whitespace and remove non-storage parts.

---

### Post by redmk2 on 2013-08-06
> **DeadlyOats said:**
> You're saying that the problem might be with the Marvell SE9120 eSATA controller on the motherboard, and not the JMicron RAID SATA controller in the Vantec HDD external enclosure?  I've tried other mobo settings, turning EFI off and using legacy BIOS.  The result was always the same.  'buntu couldn't see the JMicron RAID SATA controller.

With my current CPU, Intel i5, I only have SATA II and USB II capability on this mobo, an ASRock P67 Extreme4 Gen3.  I suppose, I'll try USB II connection for the external enclosure, but I'm afraid that USB II might give me less through put than SATA II.  It'll end up being a bottleneck and slow things down for me....  It's not a good long term solution, but I'll try it and see what happens.

This sounds suspiciously like the problem solved here: [[COLOR="#FF8C00"]http://ubuntuforums.org/showthread.php?t=1822763[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1822763").

---

### Post by DeadlyOats on 2013-08-07
O.K.  Here's what's happened.  Thinking that it might be the Marvell SATA controller, I took a look at it and found that it's settings were correct: *AHCI, bootable – Yes*.  Correct for Windows, but – it turns out – not for 'buntu.  I changed it to *IDE, bootable – Yes*.  Now 'buntu sees the RAID array, and can create and configure partitions.  I switched between EFI and Legacy ROM, as well, to see if that had any bearing on intsallation of 'buntu.  It did not.  The only issue was the Marvell SATA controller set to AHCI.  So, changing that setting to IDE fixed the 'buntu can't see the RAID on eSATA issue.

So, in my case, the problem was that 'buntu could not see *Marvell SE9120* SATA controller when set to *AHCI* mode.  Incedentally, in the mobo book, it's _Marvell SE9120_, but during POST, it showed up as _Marvell 88SE91xx_.  'buntu, or perhaps Linux in general, probably needs a driver for this Marvell SATA controller in AHCI mode.

Thank you, TheFlu, for your time and help.  Some of your comments helped me think this through better and to zone in on the issue, and thanks to you, I also learned some new commands to list hardware on a computer ( lshw (I'll take a look at what lspci – t & k do as well)).  Thank you oldfred, for poking your nose in the door and offering your expertise as well.

SOLVED.

On a seperate issue, not only did 'buntu install successfully, but GRUB2 could see my original Win7 install (the one on the internal HDD's, not the one I installed on the external enclosure, as well as the new Win7 install in the external enclosure.  GRUB 2 started both Win7's and Kubuntu successfully.  So, I guess that the EFI and Win7 boot manager hurdles have been cleared by the FOSS community and seems to be getting Linux to work on the new hardware again - against MS's wishes....  Eat that, MS!  Ha!  (Or as Homer would say, "In your face, Flanders!")  So, my anticipated *next problem*, _how to dualboot 'buntu & Win7_ was Solved before I got to that point.  Yay!

redmk2, hmmmm.....  It does seem very similar.  Same problem, but in reverse.  He had to change his from IDE to AHCI...  But I solved it before you posted, so.....  Thanks for posting though.  If I hadn't figured it out already, that would have helped.

---

