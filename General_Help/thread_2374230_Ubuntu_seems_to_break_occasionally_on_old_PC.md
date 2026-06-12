---
title: "Ubuntu seems to break occasionally on old PC"
date: 2017-10-13
forum: General Help
---

### Post by adhdluke on 2017-10-13
I have an old PC from 2009 with really odd specs. 4 sticks of RAM adding up to around three GB, two 512MB sticks and 2 1024 sticks, all DDR2 ram
Nettle2 board, with an AMD Athlon 64 X2 2511 MHz CPU
I cannot figure out what it used for graphics, as much as I know it uses or used Nvidia driver's.
I have tried both Lubuntu 17.04 33-bit and Ubuntu MATE 16.04 64-bit, and both have encountered this issue. It only happens presumably randomly after long periods of time sitting there doing nothing, although it did once happen after trying to open and use Abiword on Lubuntu for a few seconds. Nothing odd happenes before it does this, it's just sudden. [https://ibb.co/h5rjYw](https://ibb.co/h5rjYw) this is a picture of what they sort of looks like when it crashed on the desktop. The system is completely unresponsive and I have to force it off with the power button or unplug it to use it again. After that, it boots and runs anything normally. 
It doesn't seem to fix itself after any amount of time.
I wouldn't consider this a big issue as this isn't my main computer, but I lost the rescue disk and Windows Vista product key it came with initially, so there's no going back.

---

### Post by mörgæs on 2017-10-14
Let's see the hardware details. Please copy and paste ```
sudo lshw -sanitize > lshw.txt
``` to the terminal, run it and post lshw.txt in CODE tags.

---

### Post by adhdluke on 2017-10-15
```
computer
    description: Desktop Computer
    product: KC746AA-ABA a6333w (KC746AA#ABA)
    vendor: HP-Pavilion
    serial: [REMOVED]
    width: 64 bits
    capabilities: smbios-2.4 dmi-2.4 vsyscall32
    configuration: boot=normal chassis=desktop family=103C_53316J sku=KC746AA#ABA uuid=[REMOVED]
  *-core
       description: Motherboard
       product: Nettle2
       vendor: ECS
       physical id: 0
       version: 1.0
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 5.22
          date: 01/03/2008
          size: 128KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification netboot
     *-cpu
          description: CPU
          product: AMD Athlon(tm) 64 X2 Dual Core Processor 4800+
          vendor: Advanced Micro Devices [AMD]
          physical id: 3
          bus info: cpu@0
          version: AMD Athlon(tm) 64 X2 Dual Core Processor 4800+
          slot: Socket M2
          size: 1GHz
          capacity: 3GHz
          width: 64 bits
          clock: 201MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow rep_good nopl extd_apicid eagerfpu pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch vmmcall lbrv cpufreq
        *-cache:0
             description: L1 cache
             physical id: c
             slot: Internal Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back
             configuration: level=1
        *-cache:1
             description: L2 cache
             physical id: e
             slot: External Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous internal write-back
             configuration: level=2
     *-cache:0
          description: L1 cache
          physical id: 6
          slot: Internal Cache
          size: 128KiB
          capacity: 128KiB
          capabilities: synchronous internal write-back
          configuration: level=1
     *-cache:1
          description: L2 cache
          physical id: f
          slot: External Cache
          size: 512KiB
          capacity: 512KiB
          capabilities: synchronous internal write-back
          configuration: level=2
     *-memory:0
          description: System Memory
          physical id: 25
          slot: System board or motherboard
          size: 3GiB
        *-bank:0
             description: DIMM 800 MHz (1.2 ns)
             product: M3 78T6464QZ3-CF7
             vendor: Samsung
             physical id: 0
             serial: [REMOVED]
             slot: A0
             size: 512MiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:1
             description: DIMM 800 MHz (1.2 ns)
             product: M3 78T6464QZ3-CF7
             vendor: Samsung
             physical id: 1
             serial: [REMOVED]
             slot: A2
             size: 512MiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:2
             description: DIMM 800 MHz (1.2 ns)
             product: M3 78T2863QZS-CF7
             vendor: Samsung
             physical id: 2
             serial: [REMOVED]
             slot: A4
             size: 1GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:3
             description: DIMM 800 MHz (1.2 ns)
             product: M3 78T2863QZS-CF7
             vendor: Samsung
             physical id: 3
             serial: [REMOVED]
             slot: A6
             size: 1GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: MCP61 Memory Controller
          vendor: NVIDIA Corporation
          physical id: a
          bus info: pci@0000:00:00.0
          version: a1
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: MCP61 LPC Bridge
          vendor: NVIDIA Corporation
          physical id: 1
          bus info: pci@0000:00:01.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
     *-serial
          description: SMBus
          product: MCP61 SMBus
          vendor: NVIDIA Corporation
          physical id: 1.1
          bus info: pci@0000:00:01.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm cap_list
          configuration: driver=nForce2_smbus latency=0
          resources: irq:255 ioport:fc00(size=64) ioport:1c00(size=64) ioport:f400(size=64)
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: MCP61 Memory Controller
          vendor: NVIDIA Corporation
          physical id: 1.2
          bus info: pci@0000:00:01.2
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-usb:0
          description: USB controller
          product: MCP61 USB 1.1 Controller
          vendor: NVIDIA Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: pm ohci bus_master cap_list
          configuration: driver=ohci-pci latency=0 maxlatency=1 mingnt=3
          resources: irq:22 memory:fe02f000-fe02ffff
        *-usbhost
             product: OHCI PCI host controller
             vendor: Linux 4.8.0-36-generic ohci_hcd
             physical id: 1
             bus info: usb@2
             logical name: usb2
             version: 4.08
             capabilities: usb-1.10
             configuration: driver=hub slots=10 speed=12Mbit/s
           *-usb:0
                description: Mass storage device
                product: MITSUMI USB FDD
                vendor: MITSUMI
                physical id: 1
                bus info: usb@2:1
                logical name: scsi6
                version: 1.00
                capabilities: usb-1.10 floppy emulated scsi-host
                configuration: driver=usb-storage maxpower=500mA speed=12Mbit/s
              *-disk
                   description: SCSI Disk
                   physical id: 0.0.0
                   bus info: scsi@6:0.0.0
                   logical name: /dev/sdb
                   configuration: logicalsectorsize=512 sectorsize=512
           *-usb:1
                description: Mouse
                product: USB Receiver
                vendor: Logitech
                physical id: 2
                bus info: usb@2:2
                version: 22.00
                capabilities: usb-2.00
                configuration: driver=usbhid maxpower=98mA speed=12Mbit/s
     *-usb:1
          description: USB controller
          product: MCP61 USB 2.0 Controller
          vendor: NVIDIA Corporation
          physical id: 2.1
          bus info: pci@0000:00:02.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm ehci bus_master cap_list
          configuration: driver=ehci-pci latency=0 maxlatency=1 mingnt=3
          resources: irq:21 memory:fe02e000-fe02e0ff
        *-usbhost
             product: EHCI Host Controller
             vendor: Linux 4.8.0-36-generic ehci_hcd
             physical id: 1
             bus info: usb@1
             logical name: usb1
             version: 4.08
             capabilities: usb-2.00
             configuration: driver=hub slots=10 speed=480Mbit/s
           *-usb:0
                description: Video
                product: DVC FINE PC Camera
                vendor: Vimicro Corp.
                physical id: 3
                bus info: usb@1:3
                version: 1.00
                capabilities: usb-2.00
                configuration: driver=snd-usb-audio maxpower=128mA speed=480Mbit/s
           *-usb:1 UNCLAIMED
                description: Generic USB device
                product: 802.11ac WLAN Adapter
                vendor: Realtek
                physical id: 6
                bus info: usb@1:6
                version: 2.00
                serial: [REMOVED]
                capabilities: usb-2.10
                configuration: maxpower=500mA speed=480Mbit/s
           *-usb:2
                description: Mass storage device
                product: Mass Storage Device
                vendor: Generic
                physical id: 9
                bus info: usb@1:9
                logical name: scsi7
                version: 1.00
                serial: [REMOVED]
                capabilities: usb-2.00 scsi emulated scsi-host
                configuration: driver=usb-storage maxpower=100mA speed=480Mbit/s
              *-disk:0
                   description: SCSI Disk
                   physical id: 0.0.0
                   bus info: scsi@7:0.0.0
                   logical name: /dev/sdc
                   configuration: logicalsectorsize=512 sectorsize=512
              *-disk:1
                   description: SCSI Disk
                   physical id: 0.0.1
                   bus info: scsi@7:0.0.1
                   logical name: /dev/sdd
                   configuration: logicalsectorsize=512 sectorsize=512
              *-disk:2
                   description: SCSI Disk
                   physical id: 0.0.2
                   bus info: scsi@7:0.0.2
                   logical name: /dev/sde
                   configuration: logicalsectorsize=512 sectorsize=512
              *-disk:3
                   description: SCSI Disk
                   physical id: 0.0.3
                   bus info: scsi@7:0.0.3
                   logical name: /dev/sdf
                   configuration: logicalsectorsize=512 sectorsize=512
     *-pci:0
          description: PCI bridge
          product: MCP61 PCI bridge
          vendor: NVIDIA Corporation
          physical id: 4
          bus info: pci@0000:00:04.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pci ht subtractive_decode bus_master cap_list
          resources: ioport:b000(size=4096) memory:fd800000-fd8fffff memory:fdf00000-fdffffff
        *-communication UNCLAIMED
             description: Communication controller
             product: HSF 56k Data/Fax Modem
             vendor: Conexant Systems, Inc.
             physical id: 5
             bus info: pci@0000:01:05.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:fd8e0000-fd8effff ioport:bc00(size=8)
        *-firewire
             description: FireWire (IEEE 1394)
             product: VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller
             vendor: VIA Technologies, Inc.
             physical id: 9
             bus info: pci@0000:01:09.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=firewire_ohci latency=64 maxlatency=32
             resources: irq:19 memory:fd8ff000-fd8ff7ff ioport:b800(size=128)
     *-multimedia
          description: Audio device
          product: MCP61 High Definition Audio
          vendor: NVIDIA Corporation
          physical id: 5
          bus info: pci@0000:00:05.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm msi ht bus_master cap_list
          configuration: driver=snd_hda_intel latency=0 maxlatency=5 mingnt=2
          resources: irq:21 memory:fe024000-fe027fff
     *-ide:0
          description: IDE interface
          product: MCP61 IDE
          vendor: NVIDIA Corporation
          physical id: d
          bus info: pci@0000:00:06.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
          resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:f000(size=16)
     *-bridge
          description: Ethernet interface
          product: MCP61 Ethernet
          vendor: NVIDIA Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          logical name: enp0s7
          version: a2
          serial: [REMOVED]
          capacity: 100000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII
          resources: irq:27 memory:fe02d000-fe02dfff ioport:ec00(size=8)
     *-ide:1
          description: IDE interface
          product: MCP61 SATA Controller
          vendor: NVIDIA Corporation
          physical id: 8
          bus info: pci@0000:00:08.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm msi ht bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:23 ioport:9f0(size=8) ioport:bf0(size=4) ioport:970(size=8) ioport:b70(size=4) ioport:d800(size=16) memory:fe02c000-fe02cfff
     *-ide:2
          description: IDE interface
          product: MCP61 SATA Controller
          vendor: NVIDIA Corporation
          physical id: 8.1
          bus info: pci@0000:00:08.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm msi ht bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:23 ioport:9e0(size=8) ioport:be0(size=4) ioport:960(size=8) ioport:b60(size=4) ioport:c400(size=16) memory:fe02b000-fe02bfff
     *-pci:1
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: NVIDIA Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:24 ioport:a000(size=4096) memory:fde00000-fdefffff ioport:fdd00000(size=1048576)
     *-pci:2
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: NVIDIA Corporation
          physical id: b
          bus info: pci@0000:00:0b.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:25 ioport:9000(size=4096) memory:fdc00000-fdcfffff ioport:fdb00000(size=1048576)
     *-pci:3
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: NVIDIA Corporation
          physical id: c
          bus info: pci@0000:00:0c.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:26 ioport:8000(size=4096) memory:fda00000-fdafffff ioport:fd900000(size=1048576)
     *-display
          description: VGA compatible controller
          product: C61 [GeForce 6150SE nForce 430]
          vendor: NVIDIA Corporation
          physical id: e
          bus info: pci@0000:00:0d.0
          version: a2
          width: 64 bits
          clock: 66MHz
          capabilities: pm msi vga_controller bus_master cap_list rom
          configuration: driver=nouveau latency=0
          resources: irq:22 memory:fb000000-fbffffff memory:e0000000-efffffff memory:fc000000-fcffffff memory:c0000-dffff
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 100
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 101
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 102
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 103
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0
     *-scsi:0
          physical id: 10
          logical name: scsi2
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: SAMSUNG HD501LJ
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sda
             version: 0-10
             serial: [REMOVED]
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=d244b28e
           *-volume:0
                description: Linux filesystem partition
                vendor: Linux
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sda1
                logical name: /boot
                version: 1.0
                serial: [REMOVED]
                size: 487MiB
                capacity: 487MiB
                capabilities: primary bootable extended_attributes large_files ext2 initialized
                configuration: filesystem=ext2 lastmountpoint=/boot modified=2017-10-14 02:01:08 mount.fstype=ext2 mount.options=rw,relatime,block_validity,barrier,user_xattr,acl mounted=2017-10-13 17:15:45 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@2:0.0.0,2
                logical name: /dev/sda2
                size: 465GiB
                capacity: 465GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux filesystem partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 465GiB
     *-scsi:1
          physical id: 11
          logical name: scsi3
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVD-RAM GH10L
             vendor: HL-DT-ST
             physical id: 0.0.0
             bus info: scsi@3:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: FC09
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
```

---

### Post by mörgæs on 2017-10-15
Another Nvidia 6150. They are well-known around here: 

[https://ubuntuforums.org/showthread.php?t=2342498&p=13567392&viewfull=1#post13567392](https://ubuntuforums.org/showthread.php?t=2342498&p=13567392&viewfull=1#post13567392)

---

### Post by adhdluke on 2017-10-15
I have a Lubuntu 17.04 disk, do you think I should just reinstall everything and throw that on there instead? How would I select any specific drivers during installation?

---

### Post by mörgæs on 2017-10-15
A reinstall is very likely to work but first you could try looking for closed-source drivers in the software updater. I find the reinstall approach easier but I'm sure there are other opinions.

---

### Post by adhdluke on 2017-10-16
I may just reinstall and throw Lubuntu on it, but i have to figure out how to get it connected to the Internet first

---

### Post by HermanAB on 2017-10-16
Hmm, old computer crashes are almost always due to a bad PSU, or bad capacitors on the MB, causing power fluctuations and spikes on the MB.

Silicon doesn't wear out, but capacitors do.

So, yes, you can re-install and any modern version of Linux will likely work perfectly for a while, but the problem will likely persist.

---

### Post by leunam12 on 2017-10-16
Looks like it is hardware related, it looks like a bad power supply issue to me, voltage fluctuations and stuff like that. It could be a bad graphics card also. Does it happen at a specific time of day?

---

### Post by adhdluke on 2017-10-16
I don't use the computer often mostly due to the fact I can't connect it to the internet and the limited hardware specs, so I don't use it much. But it doesn't seem to have a specific time that it happens.
It has been repaired a few years ago for bad capacitors, so I wouldn't rule that out either.

---

### Post by mörgæs on 2017-10-16
Why can't you connect to the net? The lshw output shows that an ethernet adaptor is present.

---

### Post by leunam12 on 2017-10-16
I remember a while ago I had a computer with those symptoms and I solved it with a new power supply. For some reason it always did that like around 5:00 PM, very strange.

---

### Post by adhdluke on 2017-10-16
It's a heavy old desktop PC, and it's located a good distance from the router. I would plug it in directly, but the router is in a very inconvenient spot (behind the living room TV). I could hook it up there briefly if I absolutely needed, but it's easier to share the connection between my laptop and the desktop. Problem is, it can never access anything outside LAN no matter what I try with Linux (I've tried connection sharing in both windows 10 and Linux on my laptop)

---

### Post by VMC on 2017-10-16
> **adhdluke said:**
> It's a heavy old desktop PC, and it's located a good distance from the router. I would plug it in directly, but the router is in a very inconvenient spot (behind the living room TV). I could hook it up there briefly if I absolutely needed, but it's easier to share the connection between my laptop and the desktop. Problem is, it can never access anything outside LAN no matter what I try with Linux (I've tried connection sharing in both windows 10 and Linux on my laptop)
@adhdluke,
You have almost the exact same setup as mine. Xubuntu is what I'be been using for a long time now. If you install Chrome, then you need nvidia driver:
```
sudo apt-get update & [COLOR=#111111][FONT=Consolas]sudo apt-get upgrade[/FONT][/COLOR]
[COLOR=#111111][FONT=Consolas]sudo apt-get install nvidia-304[/FONT][/COLOR]
```

edit: I'm not sure what else may cause problems, but chrome will. If just using firefox then nouveau works fine. They have upgrade nouveau recently.

---

### Post by adhdluke on 2017-10-17
Is it possible I can get the driver online and put it on a USB stick to transfer it to my computer? I still can't get it connected to the internet

---

### Post by VMC on 2017-10-17
> **adhdluke said:**
> Is it possible I can get the driver online and put it on a USB stick to transfer it to my computer? I still can't get it connected to the internet
From your output:
> [COLOR=#000000][FONT=&quot]*-bridge
[/FONT][/COLOR][COLOR=#000000][FONT=&quot]          description: Ethernet interface[/FONT][/COLOR]

It appears your using onboard network. Have you tried ping'ing to see the response?

---

### Post by kurt18947 on 2017-10-18
Do you have an old router for which there is *wrt support? If so you could set up a wireless-ethernet bridge (I think that's the right term). That way the PC doesn't need wifi, it can use an ethernet cable. That wouldn't help with any intermittent hardware issues though.

---

### Post by adhdluke on 2017-10-19
I bought an old wireless card for cheap and installed it in the computer, and works like a dream. So no more internet problems.

---

### Post by mörgæs on 2017-10-20
Does that mean that everything is working now?

---

### Post by adhdluke on 2017-10-22
Everything is working great right now. Thanks.

---

### Post by mörgæs on 2017-10-22
Good, then please mark the thread solved.

---

