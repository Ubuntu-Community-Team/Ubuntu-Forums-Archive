---
title: "Can't hear iheartradio on Lubuntu, but can on Ubuntu"
date: 2014-08-21
forum: General Help
---

### Post by bro brian on 2014-08-21
Hey y'all. I just installed Lubuntu 14.04.1 (32 bit install, i386) on a really old computer w/40 gig hard drive. Using firefox browser, I can't figure out why **iheartradio** won't play on it. I tried listening to it on my main Ubuntu desktop 12.04, and it works fine. What would be so different as to cause **iheartradio** not to play on the Lubuntu? Any thoughts on this will be certainly appreciated.
I have tried installing gnash, but no difference. Also tried installing the Chrominium browser, but Chrominium locked up, and didn't open. Hmmm... Could this be a case of just simply not enough ram or something? I imagine that this old desktop is only running about 128 MB of ram or something.

---

### Post by mörgæs on 2014-08-22
Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by bro brian on 2014-08-22
> **mörgæs said:**
> Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

My apologies. I did run ```
sudo lshw -sanitize > lshw.txt
```
but I don't know how to post lshw.txt in CODE tags. How is this done?
If you were suggesting that I run the above script in terminal, and post the lshw.txt here in this thread, I'm almost sure that nothing showed up after I ran [ sudo lshw -sanitize > lshw.txt ] in terminal.

---

### Post by mörgæs on 2014-08-22
How does lshw.txt look if you open it?

---

### Post by bro brian on 2014-08-22
> **mörgæs said:**
> How does lshw.txt look if you open it?

Ah - Thanks mörgæs. Here is what lshw.txt looks like:
```
computer
    description: Desktop Computer
    product: VT8363
    vendor: VIA Technologies, Inc.
    width: 32 bits
    capabilities: smbios-2.2 dmi-2.2
    configuration: boot=normal chassis=desktop
  *-core
       description: Motherboard
       product: 8363-686A
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 6.00 PG
          date: 09/23/2002
          size: 128KiB
          capacity: 192KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot virtualmachine
     *-cpu
          description: CPU
          product: AMD Athlon(tm) XP 1800+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 6.8.1
          slot: Socket A
          size: 1533MHz
          width: 32 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow
        *-cache:0
             description: L1 cache
             physical id: a
             slot: Internal Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: b
             slot: External Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: synchronous external write-back
     *-memory
          description: System Memory
          physical id: 22
          slot: System board or motherboard
          size: 1GiB
          capacity: 2GiB
        *-bank:0
             description: DIMM
             physical id: 0
             slot: BANK_0
             size: 512MiB
        *-bank:1
             description: DIMM
             physical id: 1
             slot: BANK_1
             size: 512MiB
        *-bank:2
             description: DIMM [empty]
             physical id: 2
             slot: BANK_2
        *-bank:3
             description: DIMM [empty]
             physical id: 3
             slot: BANK_3
     *-pci
          description: Host bridge
          product: VT8363/8365 [KT133/KM133]
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-via latency=8
          resources: irq:0 memory:e8000000-ebffffff
        *-pci
             description: PCI bridge
             product: VT8363/8365 [KT133/KM133 AGP]
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci pm normal_decode bus_master cap_list
             resources: ioport:9000(size=4096) memory:ec000000-ec0fffff memory:e0000000-e7ffffff
           *-display
                description: VGA compatible controller
                product: RV100 [Radeon 7000 / Radeon VE]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: agp agp-2.0 pm vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=32 mingnt=8
                resources: irq:5 memory:e0000000-e7ffffff ioport:9000(size=256) memory:ec020000-ec02ffff memory:ec000000-ec01ffff
        *-isa
             description: ISA bridge
             product: VT82C686 [Apollo Super South]
             vendor: VIA Technologies, Inc.
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 40
             width: 32 bits
             clock: 33MHz
             capabilities: isa pm bus_master cap_list
             configuration: driver=parport_pc latency=0
             resources: irq:0
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: 7.1
             bus info: pci@0000:00:07.1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=pata_via latency=32
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:a000(size=16)
        *-usb:0
             description: USB controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 7.2
             bus info: pci@0000:00:07.2
             version: 1a
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:10 ioport:a400(size=32)
        *-usb:1
             description: USB controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 7.3
             bus info: pci@0000:00:07.3
             version: 1a
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:10 ioport:a800(size=32)
        *-bridge UNCLAIMED
             description: Bridge
             product: VT82C686 [Apollo Super ACPI]
             vendor: VIA Technologies, Inc.
             physical id: 7.4
             bus info: pci@0000:00:07.4
             version: 40
             width: 32 bits
             clock: 33MHz
             capabilities: bridge pm cap_list
             configuration: latency=0
        *-multimedia
             description: Multimedia audio controller
             product: VT82C686 AC97 Audio Controller
             vendor: VIA Technologies, Inc.
             physical id: 7.5
             bus info: pci@0000:00:07.5
             version: 50
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: driver=snd_via82xx latency=0
             resources: irq:11 ioport:ac00(size=256) ioport:b000(size=4) ioport:b400(size=4)
        *-usb:2
             description: USB controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: a
             bus info: pci@0000:00:0a.0
             version: 61
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:11 ioport:b800(size=32)
        *-usb:3
             description: USB controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: a.1
             bus info: pci@0000:00:0a.1
             version: 61
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:11 ioport:bc00(size=32)
        *-usb:4
             description: USB controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: a.2
             bus info: pci@0000:00:0a.2
             version: 63
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci-pci latency=32
             resources: irq:10 memory:ec103000-ec1030ff
        *-network:0
             description: Ethernet interface
             product: RTL8139 Ethernet
             vendor: D-Link System Inc
             physical id: b
             bus info: pci@0000:00:0b.0
             logical name: eth0
             version: 10
             serial: [REMOVED]
             size: 100Mbit/s
             capacity: 100Mbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=[REMOVED] latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
             resources: irq:11 ioport:c000(size=256) memory:ec102000-ec1020ff
        *-network:1
             description: Wireless interface
             product: RT2500 Wireless 802.11bg
             vendor: Ralink corp.
             physical id: c
             bus info: pci@0000:00:0c.0
             logical name: wlan0
             version: 01
             serial: [REMOVED]
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical wireless
             configuration: broadcast=yes driver=rt2500pci driverversion=3.13.0-34-generic firmware=N/A latency=32 link=no multicast=yes wireless=IEEE 802.11bg
             resources: irq:10 memory:ec100000-ec101fff
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-cdrom
             description: CD-R/CD-RW writer
             product: RW-241040
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: 1.02
             serial: [REMOVED]
             capabilities: removable audio cd-r cd-rw
             configuration: ansiversion=5 status=nodisc
        *-disk
             description: ATA Disk
             product: MAXTOR 6L040J2
             vendor: Maxtor
             physical id: 0.1.0
             bus info: scsi@0:0.1.0
             logical name: /dev/sda
             version: AR1.
             serial: [REMOVED]
             size: 37GiB (40GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=000b4f97
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.1.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: [REMOVED]
                size: 36GiB
                capacity: 36GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2014-08-19 09:25:58 filesystem=ext4 lastmountpoint=/ modified=2014-08-22 19:41:09 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2014-08-22 19:41:09 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.1.0,2
                logical name: /dev/sda2
                size: 510MiB
                capacity: 510MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 510MiB
                   capabilities: nofs
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: SCSI CD-ROM
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/sr1
             capabilities: audio
             configuration: status=nodisc

```

---

### Post by mörgæs on 2014-08-23
This is indeed old hardware, but still you have 1 GB of memory, not 128 MB. I don't know Iheartradio but if you can't even open Chromium I guess it's simply a matter of the app (or the contents) being too heavy.

Maybe someone who knows more about Iheartradio can give better advice.

---

### Post by tgalati4 on 2014-08-23
iHeartRadio probably uses a flash player to stream the radio channels.  I would check the versions of flash between the machines.

In Firefox go to Add-ons-->Plug-ins, Shockwave Flash.  I'm running 11.2.202.356 on Firefox 29 on Linux Mint MATE (based on Ubuntu 12.10).

---

### Post by mörgæs on 2014-08-23
If that's the case we have an explanation. You have a Socket A processor which does not run the latest Flash.

---

### Post by bro brian on 2014-08-24
Thanks for your patience, as It's been a few days since I've been here.
The os is running Firefox 31.0, and the Shockwave Flash plugin ( version 11.2.202.400 ) is activated. Still nothing.

As mörgæs has stated, it could be the processor? According to the owner of this desktop, iheartradio used to play on it when it had Windows xp on it, but I'm not sure if he's correct on thinking that.

---

### Post by bro brian on 2014-08-24
I can say that I have gone to another website, [http://darkmatterradio.net/](http://darkmatterradio.net/), which has the option of listening with either Flash Player, or with HTML5 Player. When I click on the Flash Player tab, the flash player never shows up.
If I click on the HTML5 Player, it does show up, and I can play & hear it.

---

### Post by tgalati4 on 2014-08-24
The darkmatter site is a good way to compare overhead:  flashplayer uses 25% CPU, html5 player uses 13-19% CPU for the same content.  I'm running flash 11.2.202.356 on a Pentium Dual T2310 1.4 GHz.  Not sure why your AMD processor would have an issue.  There are lots of flash testers on the web:  [http://www.chemgapedia.de/vsengine/help/en/flash/index.html](http://www.chemgapedia.de/vsengine/help/en/flash/index.html)

---

### Post by bro brian on 2014-08-24
> **tgalati4 said:**
> The darkmatter site is a good way to compare overhead:  flashplayer uses 25% CPU, html5 player uses 13-19% CPU for the same content.  I'm running flash 11.2.202.356 on a Pentium Dual T2310 1.4 GHz.  Not sure why your AMD processor would have an issue.  There are lots of flash testers on the web:  [http://www.chemgapedia.de/vsengine/help/en/flash/index.html](http://www.chemgapedia.de/vsengine/help/en/flash/index.html)

Yeah, I don't quite know what to think of it. It's really ridiculous. I don't know why this iheartradio doesn't have an html5 player. One would think that they would have that option.

---

### Post by tgalati4 on 2014-08-24
Send them an email and post the reply.  Haven't had a good laugh today yet.

---

### Post by bro brian on 2014-08-24
> **tgalati4 said:**
> Send them an email and post the reply.  Haven't had a good laugh today yet.
Okay - I sent iheartradio the following question:

"I can't listen to iheartradio using a flash player. I could if you had the HTML5 option. Why don't you have the HTML5 option?"

I'll see if they come back with a satisfactory answer, but I also noticed that I can't watch any Youtube videos, either. I've looked in [ /.mozilla/firefox/t0zwv1nz.default/pluginreg.dat ], and everything is there. This is what is shows: 
```
[PLUGINS]
libflashplayer.so:$
/usr/lib/flashplugin-installer/libflashplayer.so:$
11.2.202.394:$
1405080241000:0:0:0:$
Shockwave Flash 11.2 r202:$
Shockwave Flash:$
```

*There is one thing that makes me wonder. At the end of the pluginreg.dat file, it says, " [INVALID] ". Hmmm...

---

### Post by mörgæs on 2014-08-25
> **tgalati4 said:**
> Not sure why your AMD processor would have an issue.

Because it does not offer SSE2, which the latest Flash player requires. One can get an old Flash environment to run but it's not an ideal solution. More info in the link in my signature.

---

### Post by bro brian on 2014-08-25
> **mörgæs said:**
> Because it does not offer SSE2, which the latest Flash player requires. One can get an old Flash environment to run but it's not an ideal solution. More info in the link in my signature.

I've got a buddy that I helped put Lubuntu 14.04.1 on his older desktop. We had added 2 gigs of ram to it (totalling 3 gigs), and it has a 250 gig hard drive, so I imagine that the processor is bigger (less obsolete) than the one I'm having problems with.

We both have the Teamviewer 9 (remote access) installed on our computers, so I went onto his computer (with Lubuntu 14.04.1 installed on it), and went to the iheartradio site. It had no problem playing with flash.

So, there it is. It's definitely the computer. I did try loading a Linux Lite live cd onto it, and tried to get it to play, and it didn't play on the live cd, either. It's just too old of a computer (processor) to handle flash. If iheartradio had the html5 option, it would've been great. I haven't heard back from iheartradio on offering an html5 option yet, but when I do, I'll be sure to post their reply.

So this problem with the flash is somewhat solved, and the Lubuntu os isn't the issue. Unless there's a way (protocol) for installing an older flash onto firefox, it's probably best just to forget about watching or listening to things online that involve Flash, and stick with HTML5 friendly sites when it comes to prehistoric computers. Again, thanks to all for helping me through this, and figuring out exactly what the problem is. =d>

---

### Post by mörgæs on 2014-08-25
> **bro brian said:**
> Unless there's a way (protocol) for installing an older flash onto firefox...

Did you read my post above?

---

### Post by bro brian on 2014-08-25
> **mörgæs said:**
> Did you read my post above?

Yes, mörgæs. The thread on bringing old computers back to life? 
I did install the lubuntu-restricted-extras, and it made no difference. I don't know if I want to reinstall with Lubuntu 12.04, but that may give me an older flash, and may work. Not sure.
I hope that I'm referring to the same thing you are.

---

### Post by mörgæs on 2014-08-26
Better to install 14.04.1 and add an older Flash environment. 
The package can be downloaded [here]("http://www65.zippyshare.com/v/78802631/file.html"). Be aware that the package is old so security bugs are not necessarily fixed.

---

### Post by bro brian on 2014-08-26
> **mörgæs said:**
> Better to install 14.04.1 and add an older Flash environment. 
The package can be downloaded [here]("http://www65.zippyshare.com/v/78802631/file.html"). Be aware that the package is old so security bugs are not necessarily fixed.

Great, mörgæs! It worked. iheartradio is now playing on it. Youtube is playing on it.
Thanks so much for guiding me through this. I wouldn't have been able to figure out just which download I needed or where to get it.
I did uninstall the version of adobe flashplayer installer (that came with Lubuntu 14.04.1) before installing the earlier version. I don't know if I had to do that, but I did.
This thread is definitely solved.

---

### Post by mörgæs on 2014-08-26
You're welcome. Now is your turn to help people with old hardware :-)

---

### Post by bro brian on 2014-08-26
> **mörgæs said:**
> You're welcome. Now is your turn to help people with old hardware :-)
Yes - I have bookmarked the page for the older flash version.
The desktop with the Lubuntu 14.04.1 is actually someone elses. The previously installed Windows XP had many glitches going on with it, and wasn't playing the flash videos, either, so I've been helping someone all along.
It's running quite nicely now with a new operating system on it. The system monitor is showing only 11% (or 4.4 GB) of the 40 GIG hard drive being used after all being installed. I deleted some applications, and added others.
Another dinosaur rides again (thanks to all of us) :guitar:

---

### Post by mörgæs on 2014-08-26
**sudo apt-get clean **and **sudo apt-get autoremove** might free even more space.

---

### Post by bro brian on 2014-08-26
Thanks again! I did do the **sudo apt-get clean**, but opted to pass on the **sudo apt-get autoremove **for the moment. Not sure if I might screw something up, so I left that one alone.
I also bookmarked the old hardware link.

---

### Post by bro brian on 2014-08-26
Back to the iheartradio correspondence - 
I had asked them the following question, "I can't listen to iheartradio using a flash player. I could if you had the HTML5 option. Why don't you have the HTML5 option?"
This is their reply: > **Gareth, iHeartRadio Guru replied:**
                           Hello Brian,
 Thank you for your message. Are you attempting to play a station from  a standalone flash player? Please be aware that iHeartRadio does not  currently support players of this nature, however, the iHeartRadio  webpage does require the use of Flash Plugins to stream. You can always  listen to iHeartRadio by visiting us on the web at [www.iheart.com]("http://www.iheart.com"). I hope this helps, but let us know if you need anything further!
                             
They basically skirted over the HTML5 part completely. I take it that they have no intention on offering an HTML5 option anytime soon.:evil:

---

### Post by mörgæs on 2014-08-27
If autoremove were dangerous I wouldn't have posted it. Quite the opposite, it's a polite procedure which warns and waits for your confirmation before anything is deleted.

If you want to run 14.04 for the whole three years of support you will end up with lots of space wasted by old kernels. Remember that the hard disk is small.

---

### Post by bro brian on 2014-08-27
Thanks for a more detailed explanation on "**sudo apt-get autoremove**". I had googled it, and found several links to posts stating to be very cautious when using the command, so I opted against doing it.
I'd just got that desktop running smoothly, and opted not to risk removing something by mistake.
Just before giving it back to my coworker/friend, I did check the amount of HD disk space being used, and it's now at 10%, or 4GB, which is unreal (os install, applications, etc.). I couldn't be happier with this low number.
I have made a mental note on the autoremove command, however, and may use it at some point in the future.

---

