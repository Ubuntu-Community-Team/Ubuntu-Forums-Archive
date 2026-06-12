---
title: "Minor issues with Lubuntu 13.04"
date: 2013-09-03
forum: General Help
---

### Post by Bloodorest on 2013-09-03
Hello, I recently moved to Lubuntu on an old laptop I have (used to have Win XP) with a 1,6 Ghz cpu and 512MB of ram (it's an [Acer Aspire 1360]("http://www.miniputer.com/Acer/Aspire_1360.html")). Indeed, I've seen differences regarding ram usage. It finally runs decently (while on XP it was struggling with two open tabs in Google Chrome!). I think I'm falling in love with Lubuntu.

The only issues I noticed so far:

[LIST]
[*]It takes a while to load most programs, but once it does everything is working fine, with periodic small freezings (probably a CPU issue?)
[*]Youtube videos are laggy unless if I watch them in small view. And again, they are not 100% smooth (false GPU drivers?)
[*]The laptop power button doesn't work when I press it to shut down Lubuntu
[*]I can't find an easy way to create shortcuts (for example, from Wine programs) on desktop
[/LIST]

If you have an easy solution for one of the above (actually the last three ones), that would be great. :)

---

### Post by Crusty Old Fart on 2013-09-03
> **Bloodorest said:**
> ...
[LIST]
[*]Youtube videos are laggy unless if I watch them in small view. And again, they are not 100% smooth (false GPU drivers?)[/LIST]... 
My guess is that your onboard graphics controller just doesn't have enough "oomph" in terms of memory or processing power to handle larger views of youtube videos.
However, if you post the output from the following command, it might give an indication of whether or not you have a driver issue:
```

sudo lshw

```

> **Bloodorest said:**
> ...
[LIST]
[*]I can't find an easy way to create shortcuts (for example, from Wine programs) on desktop 
[/LIST]...
Try creating "launchers". They are essentially equivalent to what Windows calls "desktop shortcuts". I'm not running  Lubuntu, so I can't tell you exactly where to start a launcher creation. Perhaps a "right click" on some open space on your desktop will have a "Create Launcher" selection in the menu that appears--or you may be able to start the creation by "right clicking" on a panel (menu bar) and selecting: "add to panel" from the menu that appears.

---

### Post by vasa1 on 2013-09-03
For people who want a GUI for creating .desktop files or launchers, MenuLibre is worth trying: [https://launchpad.net/~menulibre-dev/+archive/devel](https://launchpad.net/~menulibre-dev/+archive/devel). Works on 12.04, 12.10 and 13.04.
```
[08:10 AM] ~ $ apt-cache search menulibre
menulibre - advanced menu editor with quicklist support
[08:11 AM] ~ $ apt-cache show menulibre
Package: menulibre
Priority: extra
Section: python
Installed-Size: 744
Maintainer: Julien Lavergne <gilir@ubuntu.com>
Architecture: all
Version: 13.01.04+repack-0ubuntu1~ppa3
Depends: python (>= 2.7.1-0ubuntu2), python (<< 2.8), gir1.2-glib-2.0, gir1.2-gtk-3.0, python-gi, gir1.2-gdkpixbuf-2.0, yelp
Filename: pool/main/m/menulibre/menulibre_13.01.04+repack-0ubuntu1~ppa3_all.deb
Size: 312504
MD5sum: c7d231258b7353483bb914bf1e6c3c6b
SHA1: 4c135fafe45e18857cee6ec65acb1c2f63c55e18
SHA256: 17e6a51e7732aeb35018efff0de1886b06a4650b0892f6885d685fcdf01c7dfd
Description: advanced menu editor with quicklist support
 An advanced menu editor that provides modern features and full quicklist
 support. Avoids GNOME dependencies so it can be suitable for lightweight
 distributions (Lubuntu, Xubuntu) as well.

```

---

### Post by mörgæs on 2013-09-04
The 1360 works well with Lubuntu. I have used one myself, but it had 2 GB memory.

Try to find some used memory sticks to give that poor thing. Should not cost much.

---

### Post by vasa1 on 2013-09-04
> **Bloodorest said:**
> ...
[LIST]
[*]The laptop power button doesn't work when I press it to shut down Lubuntu
[/LIST]

What happens when you press the power button?

---

### Post by Bloodorest on 2013-09-04
Wow thanks for your answers guys! So first things first...

> **Crusty Old Fart said:**
> My guess is that your onboard graphics controller just doesn't have enough "oomph" in terms of memory or processing power to handle larger views of youtube videos.
However, if you post the output from the following command, it might give an indication of whether or not you have a driver issue:
```

sudo lshw

```


Try creating "launchers". They are essentially equivalent to what Windows calls "desktop shortcuts". I'm not running  Lubuntu, so I can't tell you exactly where to start a launcher creation. Perhaps a "right click" on some open space on your desktop will have a "Create Launcher" selection in the menu that appears--or you may be able to start the creation by "right clicking" on a panel (menu bar) and selecting: "add to panel" from the menu that appears.

I tried to do the right click option "create a shortcut" but didn't seem to do anything... And about the command you said, these are the results, I hope it helps :):

```

acer                      
    description: Computer
    product: Aspire 1360
    vendor: Acer
    version: -1
    serial: LXA3605245450C11B8M000
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: administrator_password=enabled boot=oem-specific cpus=1 frontpanel_password=unknown keyboard_password=unknown power-on_password=disabled uuid=9F878A60-4A14-11D9-9FE1-9076BB98335A
  *-core
       description: Motherboard
       product: Aspire 1360
       vendor: Acer
       physical id: 0
       version: Rev.A
       serial: LXA3605245450C11B8M000
     *-firmware
          description: BIOS
          vendor: Phoenix
          physical id: 0
          version: V1.09
          date: 10/26/2004
          size: 111KiB
          capacity: 448KiB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing escd usb smartbattery biosbootspecification
     *-cpu
          description: CPU
          product: Mobile AMD Sempron(tm) Processor 2800+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 15.8.2
          slot: Socket 754
          size: 800MHz
          capacity: 2500MHz
          width: 32 bits
          clock: 800MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext 3dnowext 3dnow lahf_lm cpufreq
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: L1 Cache
             size: 128KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: L2 Cache
             size: 256KiB
             capacity: 1MiB
             capabilities: synchronous external write-through
     *-memory
          description: System Memory
          physical id: 21
          slot: System board or motherboard
          size: 512MiB
        *-bank:0
             description: DIMM DRAM Synchronous
             physical id: 0
             slot: S1
             size: 512MiB
             width: 32 bits
        *-bank:1
             description: DIMM DRAM [empty]
             physical id: 1
             slot: S2
     *-pci:0
          description: Host bridge
          product: K8M800 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: driver=agpgart-amd64 latency=8
          resources: irq:0 memory:e0000000-efffffff
        *-pci
             description: PCI bridge
             product: VT8237/8251 PCI bridge [K8M890/K8T800/K8T890 South]
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci pm normal_decode bus_master cap_list
             resources: memory:d1000000-d1ffffff memory:f0000000-f3ffffff
           *-display UNCLAIMED
                description: VGA compatible controller
                product: K8M800/K8N800/K8N800A [S3 UniChrome Pro]
                vendor: VIA Technologies, Inc.
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 01
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 vga_controller bus_master cap_list
                configuration: latency=64 mingnt=2
                resources: memory:f0000000-f3ffffff memory:d1000000-d1ffffff
        *-pcmcia:0
             description: CardBus bridge
             product: PCI7420 CardBus Controller
             vendor: Texas Instruments
             physical id: b
             bus info: pci@0000:00:0b.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
             resources: irq:17 memory:20000000-20000fff ioport:2000(size=256) ioport:2400(size=256) memory:24000000-27ffffff memory:28000000-2bffffff
        *-pcmcia:1
             description: CardBus bridge
             product: PCI7420 CardBus Controller
             vendor: Texas Instruments
             physical id: b.1
             bus info: pci@0000:00:0b.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
             resources: irq:18 memory:2c000000-2c000fff ioport:2800(size=256) ioport:2c00(size=256) memory:30000000-33ffffff memory:34000000-37ffffff
        *-firewire
             description: FireWire (IEEE 1394)
             product: PCI7x20 1394a-2000 OHCI Two-Port PHY/Link-Layer Controller
             vendor: Texas Instruments
             physical id: b.2
             bus info: pci@0000:00:0b.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=firewire_ohci latency=64 maxlatency=4 mingnt=2
             resources: irq:19 memory:d0005000-d00057ff memory:d0000000-d0003fff
        *-usb:0
             description: USB controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=64
             resources: irq:21 ioport:1c00(size=32)
        *-usb:1
             description: USB controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=64
             resources: irq:21 ioport:1c20(size=32)
        *-usb:2
             description: USB controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.2
             bus info: pci@0000:00:10.2
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=64
             resources: irq:21 ioport:1c40(size=32)
        *-usb:3
             description: USB controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 10.3
             bus info: pci@0000:00:10.3
             version: 82
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci-pci latency=64
             resources: irq:21 memory:d0005800-d00058ff
        *-isa
             description: ISA bridge
             product: VT8235 ISA Bridge
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa pm bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: 11.1
             bus info: pci@0000:00:11.1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=pata_via latency=64
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:1c60(size=16)
        *-multimedia
             description: Multimedia audio controller
             product: VT8233/A/8235/8237 AC97 Audio Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.5
             bus info: pci@0000:00:11.5
             version: 50
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: driver=snd_via82xx latency=0
             resources: irq:22 ioport:1000(size=256)
        *-communication
             description: Communication controller
             product: AC'97 Modem Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.6
             bus info: pci@0000:00:11.6
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: driver=snd_via82xx_modem latency=0
             resources: irq:22 ioport:1400(size=256)
        *-network
             description: Ethernet interface
             product: VT6102 [Rhine-II]
             vendor: VIA Technologies, Inc.
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: eth0
             version: 74
             serial: 00:0a:e4:a1:79:35
             size: 100Mbit/s
             capacity: 100Mbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.5.0 duplex=full ip=192.168.2.5 latency=64 link=yes maxlatency=8 mingnt=3 multicast=yes port=MII speed=100Mbit/s
             resources: irq:23 ioport:1800(size=256) memory:d0005c00-d0005cff
     *-pci:1
          description: Host bridge
          product: K8M800 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 101
          bus info: pci@0000:00:00.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8M800 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 102
          bus info: pci@0000:00:00.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8M800 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 103
          bus info: pci@0000:00:00.3
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8M800 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 104
          bus info: pci@0000:00:00.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: K8M800 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 105
          bus info: pci@0000:00:00.7
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 106
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 107
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:8
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 108
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:9
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 109
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: HTS424030M9AT00
             vendor: Hitachi
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: MAAO
             serial: MPAA41QBCDR89A
             size: 27GiB (30GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=34fe34fd
           *-volume:0
                description: EXT3 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: 81c7581d-9cee-444c-bfb0-7418d4eb0532
                size: 13GiB
                capacity: 13GiB
                capabilities: primary bootable journaled extended_attributes large_files recover ext3 ext2 initialized
                configuration: created=2013-08-16 13:55:05 filesystem=ext3 modified=2013-08-16 15:17:59 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,user_xattr,acl,barrier=1,data=ordered mounted=2013-09-05 00:13:51 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 14GiB
                capacity: 14GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   description: W95 FAT32 partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 13GiB
              *-logicalvolume:1
                   description: Linux swap / Solaris partition
                   physical id: 6
                   logical name: /dev/sda6
                   capacity: 963MiB
                   capabilities: nofs
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD writer
             product: DVDRW SOSW-852S
             vendor: Slimtype
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: PRS9
             capabilities: removable audio cd-r cd-rw dvd dvd-r
             configuration: ansiversion=5 status=nodisc

```


> **vasa1 said:**
> For people who want a GUI for creating .desktop files or launchers, MenuLibre is worth trying: [https://launchpad.net/~menulibre-dev/+archive/devel](https://launchpad.net/~menulibre-dev/+archive/devel). Works on 12.04, 12.10 and 13.04.
```
[08:10 AM] ~ $ apt-cache search menulibre
menulibre - advanced menu editor with quicklist support
[08:11 AM] ~ $ apt-cache show menulibre
Package: menulibre
Priority: extra
Section: python
Installed-Size: 744
Maintainer: Julien Lavergne <gilir@ubuntu.com>
Architecture: all
Version: 13.01.04+repack-0ubuntu1~ppa3
Depends: python (>= 2.7.1-0ubuntu2), python (<< 2.8), gir1.2-glib-2.0, gir1.2-gtk-3.0, python-gi, gir1.2-gdkpixbuf-2.0, yelp
Filename: pool/main/m/menulibre/menulibre_13.01.04+repack-0ubuntu1~ppa3_all.deb
Size: 312504
MD5sum: c7d231258b7353483bb914bf1e6c3c6b
SHA1: 4c135fafe45e18857cee6ec65acb1c2f63c55e18
SHA256: 17e6a51e7732aeb35018efff0de1886b06a4650b0892f6885d685fcdf01c7dfd
Description: advanced menu editor with quicklist support
 An advanced menu editor that provides modern features and full quicklist
 support. Avoids GNOME dependencies so it can be suitable for lightweight
 distributions (Lubuntu, Xubuntu) as well.

```

Thanks, I'm going to try it soon!

> **mörgæs said:**
> The 1360 works well with Lubuntu. I have used one myself, but it had 2 GB memory.

Try to find some used memory sticks to give that poor thing. Should not cost much.

Yeah... But until I do, fortunately Lubuntu can handle things even with that little ram...

> **vasa1 said:**
> What happens when you press the power button?

Absolutely nothing. (Once I googled it a little bit and someone said that there is a file to edit to change the command of the power button... But this file requires root access or something?)

---

### Post by ant2 on 2013-09-04
> **Bloodorest said:**
> 
[LIST]
[*]The laptop power button doesn't work when I press it to shut down Lubuntu.
[/LIST]

 How is the option 'When power button is pressed:' set under Menu > Preferences > Power Manager  ?
 
Mine is set to 'Ask' as default in Lubuntu. Although personally I always Shutdown using Menu > Logout > Shutdown.

---

### Post by vasa1 on 2013-09-04
@ant2, thanks for the pointer! I've never looked at Power Manager so far. I shutdown the same way you do.

@Bloodorest, re. "*someone said that there is a file to edit to change the command of the power button... But this file requires root access or something*?"
To my mind, that file is [FONT=Courier New]~/.config/openbox/lubuntu-rc.xml[/FONT] and the section of relevance maybe this:
```
    <!-- Launch logout when push on the shutdown button -->
    <keybind key="XF86PowerOff">
      <action name="Execute">
        <command>lubuntu-logout</command>
      </action>
    </keybind>

```
Just in case, [FONT=Courier New]~/.config[/font] is a hidden folder. If you want to see it, you need to enable viewing of hidden files and folders by pressing Ctrl+H while in your file manager (or use **ls -a** instead of just **ls** in the terminal).
If you aren't averse to reading, [http://pclosmag.com/html/Issues/201107/page08.html](http://pclosmag.com/html/Issues/201107/page08.html) is a great article on what lubuntu-rc.xml is all about (even though it refers to "rc.xml" which is more generic.)

---

### Post by claracc on 2013-09-05
About the youtube videos, you can try to use viewtube script [http://userscripts.org/scripts/show/87011](http://userscripts.org/scripts/show/87011) from userscripts.org web. This script is valid for chromium and firefox through greasy monkey addon.

The script will not use the adobe flash player, so, in this way you will use much less ram to see videos. The script works in more video pages apart from youtube.

---

### Post by Bloodorest on 2013-09-06
> **ant2 said:**
> How is the option 'When power button is pressed:' set under Menu > Preferences > Power Manager  ?
 
Mine is set to 'Ask' as default in Lubuntu. Although personally I always Shutdown using Menu > Logout > Shutdown.

Thanks for pinpointing that! Mine is set to "Ask" too, but still, the power button doesn't to anything. That's weird... 

> **vasa1 said:**
> @Bloodorest, re. "*someone said that there is a file to edit to change the command of the power button... But this file requires root access or something*?"
To my mind, that file is [FONT=Courier New]~/.config/openbox/lubuntu-rc.xml[/FONT] and the section of relevance maybe this:
```
    <!-- Launch logout when push on the shutdown button -->
    <keybind key="XF86PowerOff">
      <action name="Execute">
        <command>lubuntu-logout</command>
      </action>
    </keybind>

```
Just in case, [FONT=Courier New]~/.config[/FONT] is a hidden folder. If you want to see it, you need to enable viewing of hidden files and folders by pressing Ctrl+H while in your file manager (or use **ls -a** instead of just **ls** in the terminal).
If you aren't averse to reading, [http://pclosmag.com/html/Issues/201107/page08.html](http://pclosmag.com/html/Issues/201107/page08.html) is a great article on what lubuntu-rc.xml is all about (even though it refers to "rc.xml" which is more generic.)

Thanks, I will read this article. It might help. My [FONT=Courier New]lubuntu-rc.xml [/FONT]is exactly as the code you posted above. What can I say... Perhaps it's just not responding? But if l go back on the log in screen it's shutting down when I press the power button.

> **claracc said:**
> About the youtube videos, you can try to use viewtube script [http://userscripts.org/scripts/show/87011](http://userscripts.org/scripts/show/87011) from userscripts.org web. This script is valid for chromium and firefox through greasy monkey addon.

The script will not use the adobe flash player, so, in this way you will use much less ram to see videos. The script works in more video pages apart from youtube.

Thanks, I tried it but I get a message from Chromium "Couldn't load *mplayerplug-in is now gecko-mediaplayer 1.0.8* addon". This one must be a Chromium issue.

On one more question... Does Alt+Tab work for you? I can't switch windows using this key combination.

---

### Post by vasa1 on 2013-09-08
> **Bloodorest said:**
> ...
On one more question... Does Alt+Tab work for you? I can't switch windows using this key combination.
Works for me. I don't even know what to suggest to troubleshoot :(

---

### Post by sudodus on 2013-09-08
Welcome as a Lubuntu user Bloodorest :-)

Considering you are a beginner, you manage it quite well.

And after a month and a half, a new version, Lubuntu 13.10 will be released. Late in October I think you will be ready for upgrading to that version, and take advantage of the zRAM feature, that helps with low RAM. But don't upgrade before you have tried the new version live (booted from a CD/DCD/USB drive), trying but not installing. There might be issues, for example with your old VIA.

But as mörgæs wrote, try getting more RAM, at least add 512 MB to get 1 GB!

---

### Post by mörgæs on 2013-09-08
A possible workaround: If you right-click the bottom panel, can you then add an alternative shutdown button? 

I'm not on Lubuntu now so this is just from memory. Not necessarily exact.

---

### Post by ohiomoto on 2013-09-12
> **Bloodorest said:**
> 
[*]The laptop power button doesn't work when I press it to shut down Lubuntu

```
xev | grep "keycode"
```

[https://help.ubuntu.com/community/Lubuntu/Boot_Install_Login#I_want_to_bind_the_power-button_to_change_computer_state.2C_how_do_I_do_it.3F](https://help.ubuntu.com/community/Lubuntu/Boot_Install_Login#I_want_to_bind_the_power-button_to_change_computer_state.2C_how_do_I_do_it.3F)

---

