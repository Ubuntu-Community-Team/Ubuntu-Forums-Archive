---
title: "Not shutting down properly"
date: 2013-01-01
forum: General Help
---

### Post by Zane Pepper on 2013-01-01
Almost every time I shut down my laptop running Ubuntu, it will not fully power off. It goes through all the usual stuff, but after the screen turns off and the HDD spins down, the power LED stays on and I have to hold down the power button until it fully powers off. Any idea what is causing this?

---

### Post by coldcritter64 on 2013-01-02
What make / model is your laptop? May be a searchable hardware incompatibility.

I had a specific motherboard in a tower (desktop) that no matter what BIOS settings were chosen would behave exactly like that, requiring hard power down or it would never go fully off, lasted over several OS releases. 

It only worked properly again when the motherboard got swapped out.

---

### Post by ivotkl on 2013-01-02
I agree with coldcritter64. Do you see your motherboard listed on hardware incompatibility list sticky thread?

---

### Post by Zane Pepper on 2013-01-02
I am using a Dell Latitude D630. I am not sure exactly what make and model the motherboard is.

---

### Post by coldcritter64 on 2013-01-02
Check out this thread from last year, one of the links/ideas in it may be of help to you, it isn't apparent if it is solved though,

[http://ubuntuforums.org/showthread.php?t=1974973](http://ubuntuforums.org/showthread.php?t=1974973)

---

### Post by Zane Pepper on 2013-01-02
> **coldcritter64 said:**
> Check out this thread from last year, one of the links/ideas in it may be of help to you, it isn't apparent if it is solved though,

[http://ubuntuforums.org/showthread.php?t=1974973](http://ubuntuforums.org/showthread.php?t=1974973)

I don't think the problem was solved, but I will try some of the stuff said and see if I have any luck when I get back to my machine.

---

### Post by papibe on 2013-01-02
Hi Zane Pepper.

Do you have an Nvidia card and you are using the proprietary driver by any chance?

Regards.

---

### Post by Zane Pepper on 2013-01-02
> **papibe said:**
> Hi Zane Pepper.

Do you have an Nvidia card and you are using the proprietary driver by any chance?

Regards.
  
Yes to both.

---

### Post by papibe on 2013-01-02
I'm having similar problems on my Toshiba laptop (although not in my desktop).

I filled this bug: [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/1030630]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/1030630").

I hasn't have too much attention, so if you feel it is the same, and you have the time and the will, please mark it as "affecting you" and also make some comments explaining your particular case.

Regards.

---

### Post by mc4man on 2013-01-02
If no luck & on a 12.04 **32 bit** install then possibly consider any of below - 

Use nouveau (though nouveau is much better in 12.10/upcoming 13.04

Do a 64 bit install - here on a Dell 1330m (nvidia 8400m) the shutdown issues went away on a 64 bit install.

Modify nvidia-current_290.10-0ubuntu2_i386 to install on 12.04
( i did so but far enough removed from 12.04 to exactly remember how - screen 1

Slightly more specific bug I had filed during 12.04 dev,(8400m on Dell), unresolved..
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/940564](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/940564)

---

### Post by Zane Pepper on 2013-01-02
> **papibe said:**
> I'm having similar problems on my Toshiba laptop (although not in my desktop).

I filled this bug: [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/1030630](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/1030630).

I hasn't have too much attention, so if you feel it is the same, and you have the time and the will, please mark it as "affecting you" and also make some comments explaining your particular case.

Regards.

Sure, I will when I get home. Bring more attention to a problem and it increases the chance of having it solved.

---

### Post by ivotkl on 2013-01-02
Could file /etc/inittab have ben modified by any chance? Can you post the pastebin output of it?

---

### Post by Zane Pepper on 2013-01-06
> **ivotkl said:**
> Could file /etc/inittab have ben modified by any chance? Can you post the pastebin output of it?

I can't seem to find that file :/

Sorry for the late reply everyone, I was having some personal problems and did not have time nor was I in the mood to work on my computer. I think I fixed the problem though, I will have to do more testing. I think it was a problem with Bluetooth. I have Bluetooth off in BIOS, but the Bluetooth program was still running on Ubuntu and waiting for the Bluetooth hardware to shut off when I shutdown.

---

### Post by ivotkl on 2013-01-07
You are right, I could not find it either. I was reading a book about this, but perhaps it was outdated or has an error.

However, I could find /etc/init/shutdown.conf. It is very dangerous to modify files inside /etc/init/, so use it at your own risk. I would recommend you to make a system backup/image before doing this.

Let's do something better. What happens if you type this on terminal?

```
sudo shutdown -P now
```

[This](http://pastebin.com/FuC2GGdE) is what's written on my shutdown.conf file. What is written on yours?

Let me know if you get any error (or the same thing happens) with that command and which is the content inside your shutdown.conf file.

I'm also thinking it might be some option inside BIOS. If you have not modified it that much, usually there's an option called "Load optimised defaults" that should do it. If you have never modified it, then leave it as is.

---

### Post by Zane Pepper on 2013-01-08
> **ivotkl said:**
> You are right, I could not find it either. I was reading a book about this, but perhaps it was outdated or have an error.

However, I could find /etc/init/shutdown.conf. It is very dangerous to modify files inside /etc/init/, so use it at your own risk. I would recommend you to make a system backup/image before doing this.

Let's do something better. What happens if you type this on terminal?

```
sudo shutdown -P now
```[This]("http://pastebin.com/FuC2GGdE") is what's written on my shutdown.conf file. What is written on yours?

Let me know if you get any error (or the same thing happens) with that command and which is the content inside your shutdown.conf file.

I'm also thinking it might be some option inside BIOS. If you have not modified it that much, usually there's an option called "Load optimised defaults" that should do it. If you have never modified it, then leave it as is.

My shutdown.conf says what it is supposed to. It did the same thing it usually does when I ran that command.
I poked around my BIOS and I did not see "Load optimised defaults" anywhere. :(

---

### Post by ivotkl on 2013-01-08
Hmmm... I see.

Then only thing I can think about is of recent hardware changes or another OS or program that prevents it from going completely off.

Do you use wake on lan on BIOS setup? Perhaps that's what's causing this (although it shouldn't, but...)

I am currently out of ideas so depending on your answer to the above questions I might not be able to assist you anymore. I'm not that expert.

---

### Post by Zane Pepper on 2013-01-10
> **ivotkl said:**
> Hmmm... I see.

Then only thing I can think about is of recent hardware changes or another OS or program that prevents it from going completely off.

Do you use wake on lan on BIOS setup? Perhaps that's what's causing this (although it shouldn't, but...)

I am currently out of ideas so depending on your answer to the above questions I might not be able to assist you anymore. I'm not that expert.

I turned off Wake Up On Lan and it made no difference :(

---

### Post by ivotkl on 2013-01-10
Uhm... Ok.

Then, I'm out of ideas. Sorry.

Just one more thing, can you post your hardware and OS specs?

You can go to terminal and type:
```
sudo lshw
```

---

### Post by dannyboy79 on 2013-01-10
have you tried this from a command line?
```
sudo shutdown -h now
```

---

### Post by Zane Pepper on 2013-01-10
> **ivotkl said:**
> Uhm... Ok.

Then, I'm out of ideas. Sorry.

Just one more thing, can you post your hardware and OS specs?

You can go to terminal and type:
```
sudo lshw
```

```
zane@zane-Latitude-D630:~$ sudo lshw
[sudo] password for zane: 
zane-latitude-d630        
    description: Portable Computer
    product: Latitude D630 ()
    vendor: Winbond Electronics
    serial: 3X3MTG1
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4
    configuration: boot=normal chassis=portable uuid=44454C4C-5800-1033-804D-B3C04F544731
  *-core
       description: Motherboard
       product: 0WM416
       vendor: Winbond Electronics
       physical id: 0
       serial: .3X3MTG1.CN129618534296.
     *-firmware
          description: BIOS
          vendor: Winbond Electronics
          physical id: 0
          version: A17
          date: 01/04/2010
          size: 64KiB
          capacity: 1984KiB
          capabilities: isa pci pcmcia pnp upgrade shadowing cdboot bootselect int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     T7500  @ 2.20GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 6.15.11
          serial: 0000-06FB-0000-0000-0000-0000
          slot: Microprocessor
          size: 800MHz
          capacity: 800MHz
          width: 64 bits
          clock: 200MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm ida dtherm tpr_shadow vnmi flexpriority cpufreq
          configuration: cores=2 enabledcores=2 id=1 threads=2
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 32KiB
             capacity: 32KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 4MiB
             capacity: 4MiB
             clock: 66MHz (15.0ns)
             capabilities: pipeline-burst internal varies unified
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 64 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM DDR Synchronous 667 MHz (1.5 ns)
             product: F2-6400CL5-2GBSQ
             vendor: 7F7F7F7FCD000000
             physical id: 0
             serial: 00000000
             slot: DIMM_A
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM DDR Synchronous 667 MHz (1.5 ns)
             product: F2-6400CL5-2GBSQ
             vendor: 7F7F7F7FCD000000
             physical id: 1
             serial: 00000000
             slot: DIMM_B
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-pci
          description: Host bridge
          product: Mobile PM965/GM965/GL960 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 0c
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Mobile PM965/GM965/GL960 PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 0c
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:d000(size=4096) memory:f2000000-f6efffff ioport:e0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: G86M [Quadro NVS 135M]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:16 memory:f5000000-f5ffffff memory:e0000000-efffffff memory:f2000000-f3ffffff ioport:df00(size=128) memory:f4000000-f401ffff
        *-usb:0
             description: USB controller
             product: 82801H (ICH8 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:20 ioport:6f20(size=32)
        *-usb:1
             description: USB controller
             product: 82801H (ICH8 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:6f00(size=32)
        *-usb:2
             description: USB controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:22 memory:fed1c400-fed1c7ff
        *-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:45 memory:f6ffc000-f6ffffff
        *-pci:1
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:5000(size=4096) memory:f0400000-f05fffff ioport:f0600000(size=2097152)
        *-pci:2
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:4000(size=4096) memory:f1f00000-f1ffffff ioport:f0200000(size=2097152)
           *-network
                description: Wireless interface
                product: PRO/Wireless 3945ABG [Golan] Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:0c:00.0
                logical name: wlan0
                version: 02
                serial: 00:1f:3c:6a:1f:f7
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwl3945 driverversion=3.2.0-35-generic-pae firmware=15.32.2.9 ip=10.0.2.155 latency=0 link=yes multicast=yes wireless=IEEE 802.11abg
                resources: irq:44 memory:f1fff000-f1ffffff
        *-pci:3
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:43 ioport:3000(size=4096) memory:f1e00000-f1efffff ioport:f0000000(size=2097152)
           *-network
                description: Ethernet interface
                product: NetXtreme BCM5755M Gigabit Ethernet PCI Express
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:09:00.0
                logical name: eth0
                version: 02
                serial: 00:1c:23:4f:f9:b5
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.121 firmware=5755m-v3.29 latency=0 link=no multicast=yes port=twisted pair
                resources: irq:46 memory:f1ef0000-f1efffff
        *-usb:3
             description: USB controller
             product: 82801H (ICH8 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:20 ioport:6f80(size=32)
        *-usb:4
             description: USB controller
             product: 82801H (ICH8 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:6f60(size=32)
        *-usb:5
             description: USB controller
             product: 82801H (ICH8 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:22 ioport:6f40(size=32)
        *-usb:6
             description: USB controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:20 memory:fed1c000-fed1c3ff
        *-pci:4
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: f2
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: ioport:2000(size=4096) memory:f1d00000-f1dfffff
           *-pcmcia
                description: CardBus bridge
                product: Cardbus bridge
                vendor: O2 Micro, Inc.
                physical id: 1
                bus info: pci@0000:03:01.0
                version: 21
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: irq:19 memory:fc000000-fc000fff ioport:2400(size=256) ioport:2000(size=256) memory:f0800000-f0bfffff memory:f0c00000-f0ffffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: Firewire (IEEE 1394)
                vendor: O2 Micro, Inc.
                physical id: 1.4
                bus info: pci@0000:03:01.4
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=64
                resources: irq:19 memory:f1dff000-f1dfffff memory:f1dfe800-f1dfefff
        *-isa
             description: ISA bridge
             product: 82801HM (ICH8M) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:6fa0(size=16)
           *-cdrom
                description: DVD-RAM writer
                product: DVD+-RW TS-L632H
                vendor: TSSTcorp
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/sr0
                version: D400
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-ide:1
             description: IDE interface
             product: 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [IDE mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:6eb0(size=8) ioport:6eb8(size=4) ioport:6ec0(size=8) ioport:6ec8(size=4) ioport:6ee0(size=16) ioport:eff0(size=16)
           *-disk
                description: ATA Disk
                product: ST9500325AS
                vendor: Seagate
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: 0001
                serial: 6VEQMP2M
                size: 465GiB (500GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=c1c9002d
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 7e70-bb3f
                   size: 98MiB
                   capacity: 100MiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2012-08-11 01:43:54 filesystem=ntfs label=System Reserved state=clean
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   version: 3.1
                   serial: 96dbc253-c805-7346-826d-b684dbc6cc8d
                   size: 109GiB
                   capacity: 109GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2012-08-11 01:44:00 filesystem=ntfs label=Windows 7 state=clean
              *-volume:2
                   description: Extended partition
                   physical id: 3
                   bus info: scsi@2:0.0.0,3
                   logical name: /dev/sda3
                   size: 55GiB
                   capacity: 55GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /
                      capacity: 46GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,barrier=1,data=ordered state=mounted
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      logical name: /home
                      capacity: 5GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,user_xattr,barrier=1,data=ordered state=mounted
                 *-logicalvolume:2
                      description: Linux swap / Solaris partition
                      physical id: 7
                      logical name: /dev/sda7
                      capacity: 4095MiB
                      capabilities: nofs
              *-volume:3
                   description: Windows NTFS volume
                   physical id: 4
                   bus info: scsi@2:0.0.0,4
                   logical name: /dev/sda4
                   logical name: /media/Data
                   version: 3.1
                   serial: 16579d00-e268-6149-833a-64291b4ae9ad
                   size: 299GiB
                   capacity: 300GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2012-05-02 11:20:48 filesystem=ntfs label=Data mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 state=mounted
        *-serial UNCLAIMED
             description: SMBus
             product: 82801H (ICH8 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f6ffbf00-f6ffbfff ioport:10c0(size=32)
  *-battery
       product: DELL KP42281
       vendor: Sanyo
       physical id: 1
       slot: Sys. Battery Bay
       capacity: 78000mWh
       configuration: voltage=11.1V

```

---

### Post by Zane Pepper on 2013-01-13
> **dannyboy79 said:**
> have you tried this from a command line?
```
sudo shutdown -h now
```

I have tried it the last couple of shutdowns. I still get the same problem.

---

