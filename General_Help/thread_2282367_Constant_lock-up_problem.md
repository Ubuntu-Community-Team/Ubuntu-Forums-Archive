---
title: "Constant lock-up problem"
date: 2015-06-13
forum: General Help
---

### Post by EdLesMann on 2015-06-13
Greetings,

I have a fully updated Lubuntu 15.04 system that I installed shortly after the release. I have had no issues with this install until now. Approximately one week ago I started having weird issues where I experience a lockup of the system. If I am using the system at the time of the lock up, then it is just like my screen froze. Nothing happens. Can't ping it. Can't move the mouse. Can't turn the caps lock light on and off. Nothing. I can't "do something" to force the lock up, but the system hasn't made 8 hour uptime without a lockup in the past week while running this OS. This is on my primary system where I typically get /months/ of uptime.

I really thought I was having some bad hardware or something. I used an older Lubuntu 14.04 LTS live CD _and_ I let Boinc crunch on the CPU to force some workload. It ran just fine all day.

Huh. That is weird...rebooted into 15.04 this morning and within the last 6 hours I have had two complete lock ups. I am really thinking this is a software issue....

Here is where I am getting stuck. I see things like this:
```
Jun 13 07:30:01 DK systemd[1]: Starting Run anacron jobs...^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@
``` (I actually trimmed a _lot_ of those ^@...whatever those mean...)
and
```
"Jun 13 14:41:27 DK systemd-logind[662]: Removed session c3."
```

Those were the very last entries moments before the lock up. In fact, digging through the syslog file it seems that nearly every time systemd something was the last entry. I went poking around in systemd journalctl but I can't find anything of any use whatsoever. All I really see is current boot. The few blog posts that gave commands to look at previous boots had no results for me.

My google-fu is failing me and I can't seem to find an answer to the question "How do I get systemd to tell me what was going on prior to the crash?" I found some stuff for systemd debug mode, but from what I saw I don't think that is the information I am after.

I am really thinking that this is a software issue, but I literally have zero idea what is triggering it. If it is a software issue, I would at least like to narrow the problem down so I can file a bug report.

Can anyone help by suggesting where to look for the issue?

Thanks!

[Edit] Quick edit to say that it doesn't appear to be triggering apport either. At least I can't find any relevant crash reports. Also, the lock up happens at times where there isn't much going on. The last crash happened while I only had Firefox up.

---

### Post by ventrical on 2015-06-13
Could you try:
```

lshw

```
at the terminal and post it.

 I am suspecting it is probably an update in the video driver that is causing this.

Regards..

---

### Post by EdLesMann on 2015-06-13
```
                
    description: Computer
    width: 64 bits
    capabilities: smbios-2.4 vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory:0
          description: System memory
          physical id: 3
          size: 7983MiB
     *-cpu
          product: AMD Phenom(tm) II X4 945 Processor
          vendor: Advanced Micro Devices [AMD]
          physical id: 7
          bus info: cpu@0
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp x86-64 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt hw_pstate npt lbrv svm_lock nrip_save vmmcall
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: MCP55 Memory Controller
          vendor: NVIDIA Corporation
          physical id: 0
          bus info: pci@0000:00:00.0
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: MCP55 LPC Bridge
          vendor: NVIDIA Corporation
          physical id: 1
          bus info: pci@0000:00:01.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
     *-serial
          description: SMBus
          product: MCP55 SMBus Controller
          vendor: NVIDIA Corporation
          physical id: 1.1
          bus info: pci@0000:00:01.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: pm cap_list
          configuration: driver=nForce2_smbus latency=0
          resources: irq:255 ioport:ff00(size=64) ioport:1c00(size=64) ioport:1c40(size=64)
     *-usb:0
          description: USB controller
          product: MCP55 USB Controller
          vendor: NVIDIA Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pm ohci bus_master cap_list
          configuration: driver=ohci-pci latency=0 maxlatency=1 mingnt=3
          resources: irq:23 memory:fe02f000-fe02ffff
        *-usbhost
             product: OHCI PCI host controller
             vendor: Linux 3.19.0-20-generic ohci_hcd
             physical id: 1
             bus info: usb@2
             logical name: usb2
             version: 3.19
             capabilities: usb-1.10
             configuration: driver=hub slots=10 speed=12Mbit/s
           *-usb
                description: Mouse
                product: Optical USB Mouse
                vendor: Logitech
                physical id: 3
                bus info: usb@2:3
                version: 3.40
                capabilities: usb-2.00
                configuration: driver=usbhid maxpower=100mA speed=2Mbit/s
     *-usb:1
          description: USB controller
          product: MCP55 USB Controller
          vendor: NVIDIA Corporation
          physical id: 2.1
          bus info: pci@0000:00:02.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm ehci bus_master cap_list
          configuration: driver=ehci-pci latency=0 maxlatency=1 mingnt=3
          resources: irq:22 memory:fe02e000-fe02e0ff
        *-usbhost
             product: EHCI Host Controller
             vendor: Linux 3.19.0-20-generic ehci_hcd
             physical id: 1
             bus info: usb@1
             logical name: usb1
             version: 3.19
             capabilities: usb-2.00
             configuration: driver=hub slots=10 speed=480Mbit/s
           *-usb
                description: Mass storage device
                product: Mass Storage Device
                vendor: Generic
                physical id: 6
                bus info: usb@1:6
                logical name: scsi8
                version: 1.00
                serial: 058F63626376
                capabilities: usb-2.00 scsi emulated scsi-host
                configuration: driver=usb-storage maxpower=100mA speed=480Mbit/s
              *-disk:0
                   description: SCSI Disk
                   physical id: 0.0.0
                   bus info: scsi@8:0.0.0
                   logical name: /dev/sdc
                   configuration: logicalsectorsize=512 sectorsize=512
              *-disk:1
                   description: SCSI Disk
                   physical id: 0.0.1
                   bus info: scsi@8:0.0.1
                   logical name: /dev/sdd
                   configuration: logicalsectorsize=512 sectorsize=512
              *-disk:2
                   description: SCSI Disk
                   physical id: 0.0.2
                   bus info: scsi@8:0.0.2
                   logical name: /dev/sde
                   configuration: logicalsectorsize=512 sectorsize=512
              *-disk:3
                   description: SCSI Disk
                   physical id: 0.0.3
                   bus info: scsi@8:0.0.3
                   logical name: /dev/sdf
                   configuration: logicalsectorsize=512 sectorsize=512
     *-ide:0
          description: IDE interface
          product: MCP55 IDE
          vendor: NVIDIA Corporation
          physical id: 4
          bus info: pci@0000:00:04.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
          resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:fc00(size=16)
     *-ide:1
          description: IDE interface
          product: MCP55 SATA Controller
          vendor: NVIDIA Corporation
          physical id: 5
          bus info: pci@0000:00:05.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm msi ht bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:21 ioport:9f0(size=8) ioport:bf0(size=4) ioport:970(size=8) ioport:b70(size=4) ioport:f700(size=16) memory:fe02d000-fe02dfff
     *-ide:2
          description: IDE interface
          product: MCP55 SATA Controller
          vendor: NVIDIA Corporation
          physical id: 5.1
          bus info: pci@0000:00:05.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm msi ht bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:20 ioport:9e0(size=8) ioport:be0(size=4) ioport:960(size=8) ioport:b60(size=4) ioport:f200(size=16) memory:fe02c000-fe02cfff
     *-ide:3
          description: IDE interface
          product: MCP55 SATA Controller
          vendor: NVIDIA Corporation
          physical id: 5.2
          bus info: pci@0000:00:05.2
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm msi ht bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:23 ioport:f100(size=8) ioport:f000(size=4) ioport:ef00(size=8) ioport:ee00(size=4) ioport:ed00(size=16) memory:fe02b000-fe02bfff
     *-pci:0
          description: PCI bridge
          product: MCP55 PCI bridge
          vendor: NVIDIA Corporation
          physical id: 6
          bus info: pci@0000:00:06.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pci ht subtractive_decode bus_master cap_list
     *-multimedia
          description: Audio device
          product: MCP55 High Definition Audio
          vendor: NVIDIA Corporation
          physical id: 6.1
          bus info: pci@0000:00:06.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm msi ht bus_master cap_list
          configuration: driver=snd_hda_intel latency=0 maxlatency=5 mingnt=2
          resources: irq:21 memory:fe024000-fe027fff
     *-bridge
          description: Ethernet interface
          product: MCP55 Ethernet
          vendor: NVIDIA Corporation
          physical id: 8
          bus info: pci@0000:00:08.0
          logical name: eth0
          version: a3
          serial: 00:1e:8c:3e:1c:ed
          size: 1000000000
          capacity: 1000000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge pm msix msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=192.168.4.100 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=1Gbit/s
          resources: irq:25 memory:fe02a000-fe02afff ioport:ec00(size=8) memory:fe029000-fe0290ff memory:fe028000-fe02800f
     *-pci:1
          description: PCI bridge
          product: MCP55 PCI Express bridge
          vendor: NVIDIA Corporation
          physical id: f
          bus info: pci@0000:00:0f.0
          version: a3
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:24 ioport:d000(size=4096) memory:f8000000-fbffffff ioport:d8000000(size=268435456)
        *-display
             description: VGA compatible controller
             product: GF100 [GeForce GTX 470]
             vendor: NVIDIA Corporation
             physical id: 0
             bus info: pci@0000:02:00.0
             version: a3
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
             configuration: driver=nvidia latency=0
             resources: irq:26 memory:f8000000-f9ffffff memory:d8000000-dfffffff memory:e4000000-e7ffffff ioport:dc00(size=128) memory:fbf00000-fbf7ffff
        *-multimedia
             description: Audio device
             product: GF100 High Definition Audio Controller
             vendor: NVIDIA Corporation
             physical id: 0.1
             bus info: pci@0000:02:00.1
             version: a1
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:16 memory:fbffc000-fbffffff
     *-pci:2
          description: Host bridge
          product: Family 10h Processor HyperTransport Configuration
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 100
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Family 10h Processor Address Map
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 101
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Family 10h Processor DRAM Controller
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 102
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: Family 10h Processor Miscellaneous Control
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 103
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k10temp
          resources: irq:0
     *-pci:6
          description: Host bridge
          product: Family 10h Processor Link Control
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 104
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-scsi:0
          physical id: 9
          logical name: scsi2
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVDRAM GH24NS90
             vendor: HL-DT-ST
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: IN00
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
     *-scsi:1
          physical id: a
          logical name: scsi3
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD20EARS-00M
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@3:0.0.0
             logical name: /dev/sda
             version: AB51
             serial: WD-WCAZA8108006
             size: 1863GiB (2TB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=56523b41-a4af-48e1-8888-d681f44972af logicalsectorsize=512 sectorsize=4096
           *-volume
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@3:0.0.0,1
                logical name: /dev/sda1
                logical name: /media/storage
                version: 1.0
                serial: 06eef21b-0103-42e0-883b-508efc05375f
                size: 1863GiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2012-06-12 22:24:22 filesystem=ext4 label=storage lastmountpoint=/media/storage modified=2015-06-13 20:01:15 mount.fstype=ext4 mount.options=rw,relatime,data=ordered mounted=2015-06-13 20:01:15 state=mounted
     *-scsi:2
          physical id: b
          logical name: scsi4
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: KINGSTON SH103S3
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdb
             version: C4
             serial: 50026B773A00D027
             size: 111GiB (120GB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=72d92cc3-e375-11e2-9459-0019b92c2342 logicalsectorsize=512 sectorsize=512
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@4:0.0.0,1
                logical name: /dev/sdb1
                logical name: /
                version: 1.0
                serial: e8bd12a6-c4a1-4244-96b5-9f6ffc5c2c11
                size: 36GiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuration: created=2015-05-10 20:10:45 filesystem=ext4 lastmountpoint=/ modified=2015-06-13 17:06:29 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2015-06-13 17:06:29 state=mounted
           *-volume:1
                description: Linux swap volume
                vendor: Linux
                physical id: 2
                bus info: scsi@4:0.0.0,2
                logical name: /dev/sdb2
                version: 1
                serial: 6bf08967-5b70-4ac5-86a9-9408753d777f
                size: 4095MiB
                capacity: 4095MiB
                capabilities: nofs swap initialized
                configuration: filesystem=swap pagesize=4095
           *-volume:2
                description: EXT4 volume
                vendor: Linux
                physical id: 3
                bus info: scsi@4:0.0.0,3
                logical name: /dev/sdb3
                logical name: /tmp
                version: 1.0
                serial: b3b42d2e-8d59-4012-a7f1-a05ff8a95299
                size: 10GiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2014-01-20 13:44:32 filesystem=ext4 lastmountpoint=/tmp modified=2015-06-13 20:01:15 mount.fstype=ext4 mount.options=rw,relatime,data=ordered mounted=2015-06-13 20:01:15 state=mounted
           *-volume:3
                description: EXT4 volume
                vendor: Linux
                physical id: 4
                bus info: scsi@4:0.0.0,4
                logical name: /dev/sdb4
                logical name: /home
                version: 1.0
                serial: 4715de90-d53c-4ea6-8f29-60151230f4f6
                size: 61GiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2014-01-20 11:19:14 filesystem=ext4 label=home lastmountpoint=/home modified=2015-06-13 20:01:15 mount.fstype=ext4 mount.options=rw,relatime,data=ordered mounted=2015-06-13 20:01:15 state=mounted

```

---

### Post by EdLesMann on 2015-06-13
It is definately getting worse....3 times in the last 2 hours. Now I am just trying random things....any thoughts or suggestions?

Thanks!

---

### Post by ventrical on 2015-06-14
> **EdLesMann said:**
> It is definately getting worse....3 times in the last 2 hours. Now I am just trying random things....any thoughts or suggestions?

Thanks!


 I would first try to remove nvidia driver and run off nouveau.

```

sudo apt-get remove nvidia*

```

reboot

then let PC run on nouveau driver.

If problem persists then try to re-install nvidia driver. Looks like you have a GPU lock up. I would say the GPU is getting really hot. Looks like you have a lot of time on Ubuntu boards. Then you know to install lm-sensors to check out thermal or just use nvidia settings and see what that reports.

nvidia has been a problem on lubunu (on some of my machines) and it why I am very happy with nouveau.

---

### Post by EdLesMann on 2015-06-14
Greetings,

I agree that the nouveau drivers have improved significantly. I run them on other machines. However, I am teaching myself some basic cuda which requires the NVidia drivers. I installed the drivers through Preferences->Additional Drivers so that I have properly build drivers for the kernel

I did check the temp on the video card and it is running much hotter than I think it should. I will add some cooling to it and see if that helps.

One thing I did last night, was I booted into a different kernel. I have three of them:
3.19.0-16 : NVidia drivers are all kinds of messed up...I don't know why.
3.19.0-18 : Check out my uptime! 08:28:39 I really think that is a record this week!!!
3.19.0-20 : This is the kernel that I was on all weekend where I was experiencing lock ups frequently.

I don't know why I didn't think about the kernel earlier. Although, I didn't install the 3.19.0-20 kernel until Thursday according to my apt log...So while I believe that the issue has gotten worse on the 20 kernel (every hour or two), I fully expect to see the lockup again on the 19 later today. Possibly the threshold is higher on 19? I need to go dig through the kernel logs and see if something pops up.

Thanks!

---

### Post by ventrical on 2015-06-14
> **EdLesMann said:**
> Greetings,

I agree that the nouveau drivers have improved significantly. I run them on other machines. However, I am teaching myself some basic cuda which requires the NVidia drivers. I installed the drivers through Preferences->Additional Drivers so that I have properly build drivers for the kernel

I did check the temp on the video card and it is running much hotter than I think it should. I will add some cooling to it and see if that helps.

Thanks!

I am interested in what temp you got.

Regards..

---

### Post by EdLesMann on 2015-06-14
It seems to be bouncing around between 60C and 64C. My processor tends to hover around 40C.

Due to location in the house, my office tends to run a bit warmer than the rest of the house anyway. I just got a window unit to cool the office a bit more...maybe today is a good day to hook it up. :-)

---

### Post by ventrical on 2015-06-14
> **EdLesMann said:**
> It seems to be bouncing around between 60C and 64C. My processor tends to hover around 40C.

Due to location in the house, my office tends to run a bit warmer than the rest of the house anyway. I just got a window unit to cool the office a bit more...maybe today is a good day to hook it up. :-)

Thats pretty warm. To close for comfort. When the GPU gets any extra stress it will heat up way to fast and , voila' thermal runaway= GPU lockup.

Regards..

---

### Post by EdLesMann on 2015-06-15
Greetings,

I am really thinking it is a kernel/driver issue at play. Yesterday, I wanted to know what kind of temps I was dealing with before I added more cooling (so I could know if it was actually doing anything). I tinkered with the 20 kernel and got a lock up at 58C within an hour. I booted into the 18 kernel and couldn't get a lockup by playing games, so I fired up BOINC and my old Einstein@Home account. I have been crunching on the GPU and CPU for over 21 hours and I am rocking a 91C temp on the GPU right now!!! :-)

I don't think it is the GPU or its temp that is the real cause. I am really thinking this is a kernel or driver issue. I think I might just hold off until the next kernel comes out and see if I can better sort out the issue. I still haven't figured out how to get journalctl to tell me much of anything useful at the time of the crash.

Thanks!

---

### Post by kryten35 on 2015-06-15
Severity of error or greater since last boot.
```
journalctl -b -p err
```
Entries between times given
```
journalctl --since 07:30 --until 09:00
```
Last 8 entries
```
journalctl -n 8 
```

---

### Post by EdLesMann on 2015-06-17
> **kryten35 said:**
> Severity of error or greater since last boot.
```
journalctl -b -p err
```


Is there one for "Severity of error or greater FROM PREVIOUS boot."?? That is what I really need so I can figure out why it crashed.

Thanks! Those are useful commands for me to make note of.


Also, I think I am going to mark this as "Solved" and here is why.

I came home from work yesterday and noticed that 3.19.0-21 was available. I watched the install as it did its thing with the DKMS NVidia driver update while installing the kernel. I rebooted into the new kernel and there was _nothing_ running except my mail client Thunderbird. 15 minutes later, I am working on an email while the box is darn near as idle as can be and.....LOCKUP! Boot up again into the new kernel, start poking around attempting to find something and within 10 minutes on a box that is darn near idle...LOCKUP AGAIN! Grr.....

That really annoyed me. So I booted into the new kernel, switched to the nouveau drivers, rebooted into the new kernel+nouveau drivers, scrubbed everything NVidia I could find, then reinstalled the NVidia drivers from the "Additional drivers" application. I rebooted into the new kernel once more with the reinstalled NVidia drivers and everything seemed to be happy. Just for grins, I kicked on BOINC to beat up the GPU/CPU before going to bed. It has only been about 7 hours, but it is still up and running and crunching.

I have no idea if it was the driver or an issue with the DKMS build. However, I have at least narrowed the scope of the problem. The next kernel update, I will try to capture more of the logs/output for the kernel update / DKMS build. If it happens again, maybe I can have more details to provide.

Thanks for all the help!

---

