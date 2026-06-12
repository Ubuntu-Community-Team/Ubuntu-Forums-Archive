---
title: "How can I make Counter-Strike work with Wine?"
date: 2007-06-15
forum: General Help
---

### Post by miLl3niUm on 2007-06-15
Does it need any configuration? I think it will, I am installing it now btw

EDIT: I installed the cracked version. To launch CS, you open Half-Life (icon created on desktop), then you press change game in the menu and select Count-Strike.
Here is the problem, the menu is invisible but I can still click it. All of the small windows which appear when I click something on the menu, they don't have a title and the button labels are empty.

---

### Post by dfreer on 2007-06-15
Basically, you will need to do a few things, but it should work fairly decently. Here's a checklist:
(1) Make sure your video card driver is installed correctly, and Direct rendering/3D acceleration is enabled. If the output of this command doesn't say Yes, then you need to get your driver installed correctly.
```
glxinfo | grep rendering
```
(2) Download the SteamInstall.exe from here:
[http://www.steampowered.com/download/SteamInstall.exe](http://www.steampowered.com/download/SteamInstall.exe)
(You should be able to use the SteamInstall.msi with the newest Wine, but if you find it doesn't work, why not just use the .exe?)
(3) Find a copy of Tahoma.ttf floating around the internet, or do a search for it on your windows box, it should be located at C:\windows\fonts\
(4) Install wine
(5) Configure wine with this command:
```
winecfg
```
(6) Copy the tahoma.ttf file to ~/.wine/drive_c/windows/fonts/ Make sure it is readable to everyone (might need write/execute as well, sometimes it is picky)
(7) Install steam with this command:
```
wine SteamInstall.exe
```
(8) When steam finally installs and lauches for the first time, if all the text is missing this is because there is something wrong with tahoma.ttf, either in the wrong location, corrupted, or it has the wrong permissions
(9) pwn some n00bs liek hard on CS!

---

### Post by miLl3niUm on 2007-06-15
> **dfreer said:**
> Basically, you will need to do a few things, but it should work fairly decently. Here's a checklist:
(1) Make sure your video card driver is installed correctly, and Direct rendering/3D acceleration is enabled. If the output of this command doesn't say Yes, then you need to get your driver installed correctly.
```
glxinfo | grep rendering
```
(2) Download the SteamInstall.exe from here:
[http://www.steampowered.com/download/SteamInstall.exe](http://www.steampowered.com/download/SteamInstall.exe)
(You should be able to use the SteamInstall.msi with the newest Wine, but if you find it doesn't work, why not just use the .exe?)
(3) Find a copy of Tahoma.ttf floating around the internet, or do a search for it on your windows box, it should be located at C:\windows\fonts\
(4) Install wine
(5) Configure wine with this command:
```
winecfg
```
(6) Copy the tahoma.ttf file to ~/.wine/drive_c/windows/fonts/ Make sure it is readable to everyone (might need write/execute as well, sometimes it is picky)
(7) Install steam with this command:
```
wine SteamInstall.exe
```
(8) When steam finally installs and lauches for the first time, if all the text is missing this is because there is something wrong with tahoma.ttf, either in the wrong location, corrupted, or it has the wrong permissions
(9) pwn some n00bs liek hard on CS!

I installed the cracked version but I will also try this, I have many games (legal) on Steam. Thank you

EDIT: i get this "direct rendering: No", what should I do?

---

### Post by dfreer on 2007-06-15
"cracked" version? ... Your ideas intrigue me and I wish to learn more :twisted:

Ok, well you'll need to install your video driver. What sort of video card do you have? Are you running Feisty 7.04? If so, go to System > Administration > Restricted Drivers Manager and see if it will automatically install the correct video drivers for you (makes things a lot eaiser!)

p.s. although discussing cd cracks and the like are not permitted on this forum lol so I'm afraid I'm stuck paying for my games

---

### Post by miLl3niUm on 2007-06-15
Ok ok, I want to install Steam, I used the cracked because I was bored to install steam (I mean warez, wth you call it). Ok, let's start with the drivers. Yes, I use 7.04 (latest). I get this error:
[IMG]http://i18.tinypic.com/525ri46.png[/IMG]

EDIT: The installation wizard for Steam can run, should I install it to finish with that?

EDIT: I mean SteamInstall.exe

---

### Post by miLl3niUm on 2007-06-15
Sorry for double post, I installed Steam and it seems to working fine, here is a screenshot:

[IMG]http://i13.tinypic.com/4ucsweu.png[/IMG]

Should I install the game I want now? I am asking because I am afraid to install it, maybe it needs a configuration before installing it.

---

### Post by miLl3niUm on 2007-06-15
Please? I got to go soon.

---

### Post by dfreer on 2007-06-15
Go ahead and install it! there's no point in waiting, all it's going to do is download the *.gcf files. Even if your system does need configuring, those *.gcf files are going to be fine.

But you will problem experience extremely laggy gameplay simply because you don't have 3D acceleration. What video card do you have?

EDIT: Sorry I didn't get back to you, I was sleeping ZZZ When I said "cracked", I meant that cuz I didn't realize that the steam games had really been hacked, all your downloads are tied in to your login name. Of course I may just not have checked on it for awhile since I've already bought my games, but interesting to know

---

### Post by miLl3niUm on 2007-06-15
> **dfreer said:**
> Go ahead and install it! there's no point in waiting, all it's going to do is download the *.gcf files. Even if your system does need configuring, those *.gcf files are going to be fine.

But you will problem experience extremely laggy gameplay simply because you don't have 3D acceleration. What video card do you have?

EDIT: Sorry I didn't get back to you, I was sleeping ZZZ When I said "cracked", I meant that cuz I didn't realize that the steam games had really been hacked, all your downloads are tied in to your login name. Of course I may just not have checked on it for awhile since I've already bought my games, but interesting to know

I am downloading CSS now, I clicked it to see what will happen and it says to update my video card. I gives me a link and I go here [http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html)
I click Linux x86, now I am not sure what driver I have (I am trying to find the CDs for the drivers when I had windows but can't find them). I click ATI, then Radeon, but dunno which one I have. How can I found out?

Note: I am not even sure if I have Radeon (for ATI I am 95% sure)

EDIT: Here is a screenshot if you want it:
[img]http://img354.imageshack.us/img354/153/screenynt3.png[/img]

---

### Post by miLl3niUm on 2007-06-15
Come on, don't tell me you are offline! :(:(:(

---

### Post by miLl3niUm on 2007-06-16
Sorry, I want to bring up my post, I installed it but I can't see it normally. I think it's the resolution, I tried to change it from CSS options but I didn't make it. Here is a screenshot:
[IMG]http://i16.tinypic.com/4mulhxh.png[/IMG]

EDIT: It must be the resolution because the size of this FULL screenshot is different of the other above. My screen resolution is 1280x1024 and this screenshot is 800x600

---

### Post by dnzz on 2007-06-16
I solved same problem with my Nvidia 6200 go

First i updated my nvidia driver.

In this article: [http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam&back=HOWTO+INDEX+Wine+Games](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam&back=HOWTO+INDEX+Wine+Games)
> 
2.3. Downloading Microsoft core fonts

Steam requires the tahoma.ttf font. It is NOT included in the Microsoft core fonts package, so you have to get it separately.
For example, google for "filetype:ttf inurl:tahoma", download it and put it into your ~/.wine/drive_c/windows/fonts directory.

I also installed tahoma font to ubuntu itself
[http://ubuntuforums.org/archive/index.php/t-82318.html](http://ubuntuforums.org/archive/index.php/t-82318.html)

Also you can force HL2 to use DirectX 7.0 it helps too.

---

### Post by miLl3niUm on 2007-06-16
Hope you can help, please read the posts above, I forgot what video card I have (I think it's ATI but not sure what model) and I don't know how to find it. Is there any way to find out with Windows?


Note: I haven't updated the video card as Steam suggests me and I ran CSS. (maybe that's why the screenshot above looks strange)

---

### Post by dnzz on 2007-06-16
i find a menu called Hardware Information in System-Preferences in Gnome.

Can you find your Video card from there?

---

### Post by dnzz on 2007-06-16
> lshw

This code can help. (I forgot sorry :D )

---

### Post by miLl3niUm on 2007-06-16
> **dnzz said:**
> This code can help. (I forgot sorry :D )
This is what I get:

```
alter@millenium:~$ lshw 
WARNING: you should run this program as super-user.
millenium                 
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 1010MB
     *-cpu
          product: Intel(R) Pentium(R) 4 CPU 2.80GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 15.3.3
          serial: 0000-0F33-0000-0000-0000-0000
          size: 18EHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc pni monitor ds_cpl cid
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 32 bits
             capabilities: logical
     *-pci
          description: Host bridge
          product: 82875P/E7210 Memory Controller Hub
          vendor: Intel Corporation
          physical id: fc000000
          bus info: pci@00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          resources: iomemory:fc000000-fdffffff
        *-pci:0
             description: PCI bridge
             product: 82875P Processor to AGP Controller
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@00:01.0
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display:0
                description: VGA compatible controller
                product: RV280 [Radeon 9200 SE]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@01:00.0
                version: 01
                size: 128MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                configuration: latency=64 mingnt=8
                resources: iomemory:f0000000-f7ffffff ioport:b000-b0ff iomemory:fe8f0000-fe8fffff irq:17
           *-display:1 UNCLAIMED
                description: Display controller
                product: RV280 [Radeon 9200 SE] (Secondary)
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@01:00.1
                version: 01
                size: 128MB
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master cap_list
                configuration: latency=64 mingnt=8
                resources: iomemory:e8000000-efffffff iomemory:fe8e0000-fe8effff
        *-pci:1
             description: PCI bridge
             product: 82875P/E7210 Processor to PCI to CSA Bridge
             vendor: Intel Corporation
             physical id: 3
             bus info: pci@00:03.0
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-network
                description: Ethernet interface
                product: 82547EI Gigabit Ethernet Controller
                vendor: Intel Corporation
                physical id: 1
                bus info: pci@02:01.0
                logical name: eth0
                version: 00
                serial: 00:0e:a6:a5:8a:1c
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=e1000 driverversion=7.3.15-k2-NAPI firmware=N/A ip=192.168.1.101 latency=0 mingnt=255 multicast=yes
                resources: iomemory:fe9e0000-fe9fffff ioport:cf80-cf9f irq:16
        *-usb:0
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:ef00-ef1f irq:17
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:1
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:ef20-ef3f irq:18
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:2
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:ef40-ef5f irq:16
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:3
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:ef80-ef9f irq:17
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:4
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: iomemory:febffc00-febfffff irq:19
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.20-16-generic ehci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=8 speed=480.0MB/s
        *-pci:2
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@00:1e.0
             version: c2
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-firewire
                description: FireWire (IEEE 1394)
                product: IEEE 1394 Host Controller
                vendor: VIA Technologies, Inc.
                physical id: 3
                bus info: pci@03:03.0
                version: 80
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=32
                resources: iomemory:feaff800-feafffff ioport:dc00-dc7f irq:20
           *-communication UNCLAIMED
                description: Communication controller
                product: HSF 56k HSFi Modem
                vendor: Conexant
                physical id: 9
                bus info: pci@03:09.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=64
                resources: iomemory:feae0000-feaeffff ioport:dfe0-dfe7 irq:5
        *-isa
             description: ISA bridge
             product: 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801EB/ER (ICH5/ICH5R) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@00:1f.1
             logical name: scsi1
             logical name: scsi0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated scsi-host
             configuration: driver=ata_piix latency=0
             resources: ioport:1f0-1f7 ioport:3f4-3f3 ioport:170-177 ioport:374-373 ioport:fc00-fc0f iomemory:50000000-500003ff irq:16
           *-cdrom:0
                description: DVD reader
                product: DVD-ROM PX-116A2
                vendor: PLEXTOR
                physical id: 0.0.0
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.00
                capabilities: removable audio dvd
                configuration: ansiversion=5
              *-disc
                   physical id: 0
                   logical name: /dev/cdrom
           *-cdrom:1
                description: DVD reader
                product: DVDR   PX-504A
                vendor: PLEXTOR
                physical id: 0.1.0
                bus info: scsi@1:0.1.0
                logical name: /dev/scd1
                logical name: /dev/sr1
                version: 1i01
                serial: [PLEXTOR DVDR   PX-504A  1i0103022400
                capabilities: removable audio cd-r cd-rw dvd
                configuration: ansiversion=5
              *-disc
                   physical id: 0
                   logical name: /dev/scd1
        *-ide:1
             description: IDE interface
             product: 82801EB (ICH5) SATA Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@00:1f.2
             logical name: scsi2
             logical name: scsi3
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master scsi-host
             configuration: driver=ata_piix latency=0
             resources: ioport:efe0-efe7 ioport:efac-efaf ioport:efa0-efa7 ioport:efa8-efab ioport:ef60-ef6f irq:16
        *-serial UNCLAIMED
             description: SMBus
             product: 82801EB/ER (ICH5/ICH5R) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:400-41f irq:11
        *-multimedia
             description: Multimedia audio controller
             product: 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Intel ICH latency=0
             resources: ioport:e800-e8ff ioport:ee80-eebf iomemory:febff800-febff9ff iomemory:febff400-febff4ff irq:21
alter@millenium:~$ 
```

EDIT: Thanks I found it!!
```
           *-display:0
                description: VGA compatible controller
                product: RV280 [Radeon 9200 SE]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@01:00.0
                version: 01
                size: 128MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                configuration: latency=64 mingnt=8
                resources: iomemory:f0000000-f7ffffff ioport:b000-b0ff iomemory:fe8f0000-fe8fffff irq:17
           *-display:1 UNCLAIMED
                description: Display controller
                product: RV280 [Radeon 9200 SE] (Secondary)
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@01:00.1
                version: 01
                size: 128MB
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master cap_list
                configuration: latency=64 mingnt=8
                resources: iomemory:e8000000-efffffff iomemory:fe8e0000-fe8effff
```

EDIT: Ok, now, what should I download?

[http://ati.amd.com/support/drivers/linux/linux-radeon-prer200.html](http://ati.amd.com/support/drivers/linux/linux-radeon-prer200.html)

EDIT: It says to download and run a Check.sh file but when I open it, it opens in gedit.

---

### Post by dnzz on 2007-06-16
>  *-display:0
                description: VGA compatible controller
                product: RV280 [Radeon 9200 SE]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@01:00.0
                version: 01
                size: 128MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                configuration: latency=64 mingnt=8
                resources: iomemory:f0000000-f7ffffff ioport:b000-b0ff iomemory:fe8f0000-fe8fffff irq:17


This is the part we want. You have Radeon 9200 SE. 

[http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html)

New driver, new hope ;)

---

### Post by miLl3niUm on 2007-06-16
I know, look the post above.

---

### Post by dnzz on 2007-06-16
You must download:

Linux86-Radeon-9200 series

Edit: Sorry first one 
ATI Driver Installer

---

### Post by miLl3niUm on 2007-06-16
To be sure, give me link. This?
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.28.8.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.28.8.run)

---

### Post by dnzz on 2007-06-16
Yes that one

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.28.8.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.28.8.run)

---

### Post by miLl3niUm on 2007-06-16
Holy.............. it's 50 MB, will you be here in 10 mins?

---

### Post by dnzz on 2007-06-16
Before you run I want to warn you. I've damaged my Xserver many times while doing driver update because of lack of experience. Please backup your /etc/X11/xorg.conf

Yeah i can wait :)

---

### Post by dfreer on 2007-06-16
> **miLl3niUm said:**
> 
           *-display:0
                description: VGA compatible controller
**                product: RV280 [Radeon 9200 SE]**
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@01:00.0
                version: 01
                size: 128MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                configuration: latency=64 mingnt=8
                resources: iomemory:f0000000-f7ffffff ioport:b000-b0ff iomemory:fe8f0000-fe8fffff irq:17
           *-display:1 UNCLAIMED
                description: Display controller
**                product: RV280 [Radeon 9200 SE] (Secondary)**
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@01:00.1
                version: 01
                size: 128MB
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master cap_list
                configuration: latency=64 mingnt=8
                resources: iomemory:e8000000-efffffff iomemory:fe8e0000-fe8effff

Hmmm. seems you are using the ATI Radeon 9200. Can you do a quick check and post the output of this command?
```
glxinfo | head
```

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Ok, basically this site says that cards below 9500 are not supported by the official ATi drivers (curse you ati for crappy drivers!!1!), so you cannot use the "fglrx" driver (which is probably why the Restricted Drivers Manager wouldn't install your drivers). The open-source "radeon" driver is not so bad, and you may be able to get 3D acceleration working with it from what I hear. 

Your best bet is to search on a way to get 3D working with a 9200, make a new thread specifically pertaining to the 9200 if there are no others, complain to ATi how they should help out the OSS community by making better drivers, or buying a card from a company that supports linux at least half-way. 

*BTW, counter-strike looks fully installed*, your problem is now just getting your video card drivers working. As for changing the resolution of CS, check out the AppsDB at winehq, they have one specifically for counter-strike 1.6 and I know there is a decent guide in there for using command-line arguments with steam (such as launching the game with a preferred resolution).

EDIT:
> **dnzz said:**
> Before you run I want to warn you. I've damaged my Xserver many times while doing driver update because of lack of experience. Please backup your /etc/X11/xorg.conf

Best advice ever. always do this, and make sure you know how to restore your backup from the CLI

DOUBLE EDIT: what the godd*mn ****?! I fall asleep while typing, finally hit submit, and there is a whole new page of posts sheesh lol

---

### Post by miLl3niUm on 2007-06-16
Ok, I backuped it, but how can I restore it if it get damaged. And what will happen? It will be cmd?

---

### Post by miLl3niUm on 2007-06-16
> **dfreer said:**
> Hmmm. seems you are using the ATI Radeon 9200. Can you do a quick check and post the output of this command?
```
glxinfo | head
```

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Ok, basically this site says that cards below 9500 are not supported by the official ATi drivers (curse you ati for crappy drivers!!1!), so you cannot use the "fglrx" driver (which is probably why the Restricted Drivers Manager wouldn't install your drivers). The open-source "radeon" driver is not so bad, and you may be able to get 3D acceleration working with it from what I hear. 

Your best bet is to search on a way to get 3D working with a 9200, make a new thread specifically pertaining to the 9200 if there are no others, complain to ATi how they should help out the OSS community by making better drivers, or buying a card from a company that supports linux at least half-way. 

*BTW, counter-strike looks fully installed*, your problem is now just getting your video card drivers working. As for changing the resolution of CS, check out the AppsDB at winehq, they have one specifically for counter-strike 1.6 and I know there is a decent guide in there for using command-line arguments with steam (such as launching the game with a preferred resolution).

EDIT:

Best advice ever. always do this, and make sure you know how to restore your backup from the CLI

What if I follow dnzz instructions?

.....This is what I get
```
alter@millenium:~$ glxinfo | head
name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
```

EDIT: And where should I backup xorg.conf?

---

### Post by dfreer on 2007-06-16
> **miLl3niUm said:**
> What if I follow dnzz instructions?

.....This is what I get
```
alter@millenium:~$ glxinfo | head
name of display: :0.0
display: :0  screen: 0
direct rendering: No
**server glx vendor string: SGI**
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
```

EDIT: And where should I backup xorg.conf?

Yeah, I definitely fell asleep and posted late (5 am here). Great job dnzz, I don't have ATi cards, didn't know there where new drivers out and for the 9200 too! Yeah listen to dnzz, ignore my previous post.
According to this, you are using neither the open-source radeon driver OR the official ati fglrx driver, unless they changed vendor strings along with the new drivers....

EDIT: to backup xorg.conf
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

to restore backup when x server crashes... (might wanna write this down)
(1) hit <Ctrl><Alt><F5>, it should bring you to a ttyl login screen
(2) login, and then type these two commands (first one restores backup, second one restarts GDM so you can login normally):
```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
sudo /etc/init.d/gdm restart
```

---

### Post by dnzz on 2007-06-16
I usually backup to my home folder because its easy to write "~/" in CLI :D

If you copy your xorg.conf to home folder:
> sudo cp ~/xorg.conf /etc/X11/xorg.conf
This should recover your xorg.

PS: Thanks dfreer :D

EDIT: Please write this codes to a paper before you start installing
and dont forget ctrl+alt+F2 lets you login from CLI if you stuck use this
"startx" command lets you start xserver
and use "nano" to edit text files in CLI

---

### Post by miLl3niUm on 2007-06-16
I will that:
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

And if it crashes:
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
sudo /etc/init.d/gdm restart


And yes, I will write it down. Ok, am I ready now? Should I open the *.run file?

EDIT: How can I print the post?

---

### Post by dnzz on 2007-06-16
Try running but nvidia drivers doesnt let you run installer while xserver is running. Im not sure about radeon drivers

If you need to kill xserver do it then try it again

---

### Post by miLl3niUm on 2007-06-16
> **dnzz said:**
> EDIT: Please write this codes to a paper before you start installing
and dont forget ctrl+alt+F2 lets you login from CLI if you stuck use this
"startx" command lets you start xserver
and use "nano" to edit text files in CLI

I know how to use every command except of nano. I don't think I really need it since I created a backup, do I? But what should I type? Is this correct

```
nano /etc/X11/xorg.conf
```

EDIT: How do I kill xserver and then run it?

---

### Post by dfreer on 2007-06-16
> **dnzz said:**
> I usually backup to my home folder because its easy to write "~/" in CLI :D

If you copy your xorg.conf to home folder:

This should recover your xorg.

PS: Thanks dfreer :D

EDIT: Please write this codes to a paper before you start installing
and dont forget ctrl+alt+F2 lets you login from CLI if you stuck use this
"startx" command lets you start xserver
and use "nano" to edit text files in CLI

Yeah, back it up where ever it is most convenient :D 
The <ctrl><alt><F1-F6> works, whichever one ya want to use.
However, restarting GDM is generally the best way to recover from x crashing. startx only restarts the x server, and when you restart GDM (the login manager basically), it restarts itself and x server, bringing your system back to pretty much to the login screen you normally see. startx won't cause any problems though.

---

### Post by dnzz on 2007-06-16
Yes thats right

---

### Post by miLl3niUm on 2007-06-16
Ok, I am starting now, wish me good luck lol.

by the way, dfreer, can you help here please? [http://ubuntuforums.org/showthread.php?t=474469&page=2](http://ubuntuforums.org/showthread.php?t=474469&page=2)

---

### Post by miLl3niUm on 2007-06-16
Holy ****. How do I run it?

[IMG]http://i19.tinypic.com/62rua9g.png[/IMG]

---

### Post by dnzz on 2007-06-16
```
sudo sh <file name>
```

---

### Post by miLl3niUm on 2007-06-16
> **dnzz said:**
> ```
sudo sh <file name>
```
Doesn't work

> alter@millenium:~$ sudo sh ati-driver-installer-8.28.8.run
sh: Can't open ati-driver-installer-8.28.8.run

---

### Post by dnzz on 2007-06-16
Are you in the same directory with your ati driver?

If the file is in your Desktop
```
sudo sh ~/Desktop/ati-driver-installer-8.28.8.run
```

---

### Post by dfreer on 2007-06-16
also if the above command doesn't work make it executable and try again:
```
sudo chmod a+x *yourfilename.run*
```

EDIT: blarg, I be tired

---

### Post by miLl3niUm on 2007-06-16
Yes, I just forgot the extension sorry. Is it installed?

(uploading the pic)
here you go:
[IMG]http://i9.tinypic.com/4kclxdt.png[/IMG]

EDIT: There's an error I think

---

### Post by dnzz on 2007-06-16
No its not
But i dont have any idea for this problem.
Dfreer do you have any idea?

I remember there were some packages needed to compile im trying to find that

---

### Post by miLl3niUm on 2007-06-16
There is an error for sure because I still get Steam's "error" to update my video card.

[IMG]http://img354.imageshack.us/img354/153/screenynt3.png[/IMG]

---

### Post by dfreer on 2007-06-16
> **dnzz said:**
> No its not
But i dont have any idea for this problem.
Dfreer do you have any idea?

I remember there were some packages needed to compile im trying to find that

```
sudo apt-get install build-essential
``` 
and then try the install maybe? I don't have an ATi card myself, all of my experience with ATi is from helping other people's machines and this forum.

---

### Post by dfreer on 2007-06-16
> **miLl3niUm said:**
> There is an error for sure because I still get Steam's "error" to update my video card.

[IMG]http://img354.imageshack.us/img354/153/screenynt3.png[/IMG]

Steam will do that probably no matter what. it is a windows program complaining about not finding windows drivers... any link it would give you would just point to windows drivers, it can't sense that is installed in linux really. Gotta get some sleep for tonight (what's left of it), will check back in the morning.

---

### Post by miLl3niUm on 2007-06-16
I'll am installing build-essential now.

DAAAAAAAAAAAAAAAAAAAAM, holy ****

> Media change: please insert the disc labeled                                   
 'Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)'
in the drive '/cdrom/' and press enter

I had this problem with many packages also and I didn't fix the problem.

(posting the link now)
EDIT: [http://ubuntuforums.org/showthread.php?t=467904](http://ubuntuforums.org/showthread.php?t=467904)

---

### Post by dnzz on 2007-06-16
```
sudo apt-get install module-assistant build-essential debhelper debconf dh-make fakeroot libstdc++5 linux-headers-generic
```

Aha i found this

---

### Post by dnzz on 2007-06-16
I found a guide
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI?highlight=%28drivers%29%7C%28ati%29%7C%28binary%29](https://help.ubuntu.com/community/BinaryDriverHowto/ATI?highlight=%28drivers%29%7C%28ati%29%7C%28binary%29)
>  Install from ati.com (latest version of drivers)
Instructions for 7.04 (Feisty)
Preparation

Although it is possible to use the instructions for 6.10 on 7.04, there is a simpler and possibly more painless way to install of 7.04. First, download the drivers installer (not the rpms) from [WWW] ati.amd.com. It is recommended to save it to an empty directory since the installer will create a bunch of files. Next, in order to build the packages, we need some basic developer tools. To get these tools, first enable the universe and restricted sections of Ubuntu (see AddingRepositoriesHowto for help). Once the repositories are enabled, install the needed developer tools with sudo apt-get install module-assistant build-essential debhelper debconf dh-make fakeroot libstdc++5 linux-headers-generic
Installation

Build Ubuntu packages from the installer by opening a terminal, entering the directory that you saved the installer to, and running bash ./ati-driver-installer-<version>.run --buildpkg Ubuntu/feisty

where <version> is the version number of the driver you downloaded. This will take a short time. After finishing, the installer will create several debs. Use the command "dpkg -i <filename>" to install the fglrx-kernel-source<something>.deb and the xorg-driver-fglrx<something>.deb. The other two debs created will be fglrx development headers which you probably will not need and the AMD Control Panel which doesn't work.

After installing the kernel source and xorg driver, you will now need to compile the fglrx kernel module in order to get 3-d rendering. Do so with the following commands:

sudo m-a prepare,update 
sudo m-a build,install fglrx-kernel (or module-assistant -f to force a rebuild if needed)
sudo depmod
sudo rm -f /usr/src/fglrx-kernel*.deb

Configuration

Ubuntu 7.04 ships with a utility to automate configuration of fglrx. Open it at "System -> Administration -> Restricted Drivers Manager" (you may have to install the restricted-manager and linux-restricted-modules-generic package). Select "ATI accelerated graphics driver" and hit apply. The Restricted Drivers Manager will then automagically change xorg.conf and several other files. However, even at this point, the setup is not finished. At next boot, Ubuntu will load an old version of fglrx, so you have to blacklist it by changing /etc/default/linux-restricted-modules-common to include DISABLED_MODULES="somemodule2 fglrx" where somemodule2 is the old contents of that line. When you have finished this last change, reboot and (hopefully) enjoy your 3-d acceleration.
After kernel updates

After every update of the kernel (linux-image-<arch>), you will need to recompile the kernel module (make sure to get the latest linux-headers too) as explained under the installation section. After you recompile the module, you can regain direct rendering by logging into a console (ctrl+alt+f1) and typing:

sudo /etc/init.d/gdm stop (kdm if you use Kubuntu)
sudo rmmod fglrx (even if this command fails, go on)
sudo modprobe fglrx
sudo /etc/init.d/gdm start (again, Kubuntu users type kdm)



I found a guide
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI?highlight=%28drivers%29%7C%28ati%29%7C%28binary%29](https://help.ubuntu.com/community/BinaryDriverHowto/ATI?highlight=%28drivers%29%7C%28ati%29%7C%28binary%29)

---

### Post by miLl3niUm on 2007-06-16
Wth is all that? Let me try it.

Which of your 2 latest posts should I try/

---

### Post by dfreer on 2007-06-16
> **miLl3niUm said:**
> I'll am installing build-essential now.

DAAAAAAAAAAAAAAAAAAAAM, holy ****



I had this problem with many packages also and I didn't fix the problem.

(posting the link now)
EDIT: [http://ubuntuforums.org/showthread.php?t=467904](http://ubuntuforums.org/showthread.php?t=467904)

posted response to this problem in that thread, by golly ubuntu is sure giving it to you rough, most users have 1-2 problems you've had like 10 lol

---

### Post by dnzz on 2007-06-16
First one is written in the second one :)

Second one looked complicated to me. 
I think if you do the first one our problem will be solved. I posted second one for further help

---

### Post by miLl3niUm on 2007-06-16
Lol I know

EDIT: I am at "Install from ati.com (latest version of drivers)" at the site you gave me.

EDIT: I am here "sudo apt-get install module-assistant build-essential debhelper debconf dh-make fakeroot libstdc++5 linux-headers-generic"; I must wait 1 min

EDIT: Done going to the next step

---

### Post by miLl3niUm on 2007-06-16
FUUUUUUUUUUUUUUUUUUUUUUUCK, bitch, gay, homo. I am ******* angry ](*,)

I get the same SHIIIIT

[IMG]http://img388.imageshack.us/img388/5462/fuuuuuckjm9.png[/IMG]

EDIT: btw, [http://ubuntuforums.org/showthread.php?t=474469&page=2](http://ubuntuforums.org/showthread.php?t=474469&page=2)

EDIT: Sorry, I just got tired

---

### Post by dnzz on 2007-06-16
I dont know how to solve this problem but you can try:

[http://www.google.com.tr/search?q=.%2Fati-installer.sh%3A+165%3A+Syntax+error%3A+Bad+substitution&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a](http://www.google.com.tr/search?q=.%2Fati-installer.sh%3A+165%3A+Syntax+error%3A+Bad+substitution&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a)

---

### Post by miLl3niUm on 2007-06-16
Are you from Turkey?

---

### Post by dnzz on 2007-06-16
Yep :D

---

### Post by miLl3niUm on 2007-06-16
I am from Cyprus. Ya ya, you know

Anyway, here is my problem, [http://www.linuxquestions.org/questions/showthread.php?t=555145](http://www.linuxquestions.org/questions/showthread.php?t=555145)

(post 6)

EDIT: Also here [http://ubuntuforums.org/showthread.php?t=286769](http://ubuntuforums.org/showthread.php?t=286769)

EDIT: And here! [https://answers.launchpad.net/ubuntu/+source/yelp/+question/7258](https://answers.launchpad.net/ubuntu/+source/yelp/+question/7258)

---

### Post by miLl3niUm on 2007-06-16
I think this is the solution but it's for Edgy:
[http://ubuntuforums.org/archive/index.php/t-243342.html](http://ubuntuforums.org/archive/index.php/t-243342.html)

EDIT: look malac's post [http://ubuntuforums.org/showthread.php?t=286769](http://ubuntuforums.org/showthread.php?t=286769)

---

### Post by dnzz on 2007-06-16
> I was recently trying to install the latest ATI drivers in edgy, following all the normal guides.
However, when it comes to:
sudo ./ati-driver-installer-8.28.8.run --buildpkg Ubuntu/edgy

I was getting an error message about bad substitution on line 165.

The exact message:
./ati-installer.sh: 165: Syntax error: Bad substitution

I searched around and eventually found the fix on the Ubuntu french forums (forum.ubuntu-fr.org), which basically involves forcing the script to use BASH, not SH.

Normally I guess this wouldn't be a good thing to do, but this is the development release after all :P

So, here's the solution:

sudo mv /bin/sh /bin/SH
sudo ln -s /bin/bash /bin/sh


Afterwards, once you've finished with ATI's script:

sudo mv /bin/SH /bin/sh

And all should be well again.

I just thought I should post it here for anyone else having the same issue.

Did you see this in the first link (#4 post)

---

### Post by miLl3niUm on 2007-06-16
> **dnzz said:**
> Did you see this in the first link (#4 post)

Yes, that's the problem I have

EDIT: Should I do this? (it's for Edgy and I have Feisty)

> I was recently trying to install the latest ATI drivers in edgy, following all the normal guides.
However, when it comes to:
sudo ./ati-driver-installer-8.28.8.run --buildpkg Ubuntu/edgy

I was getting an error message about bad substitution on line 165.

The exact message:
./ati-installer.sh: 165: Syntax error: Bad substitution

I searched around and eventually found the fix on the Ubuntu french forums (forum.ubuntu-fr.org), which basically involves forcing the script to use BASH, not SH.

Normally I guess this wouldn't be a good thing to do, but this is the development release after all :P

So, here's the solution:

sudo mv /bin/sh /bin/SH
sudo ln -s /bin/bash /bin/sh


Afterwards, once you've finished with ATI's script:

sudo mv /bin/SH /bin/sh

And all should be well again.

I just thought I should post it here for anyone else having the same issue.

---

### Post by dnzz on 2007-06-16
Why dont you try the solution at the end of the post? :lolflag:

Yeah give it a try. Its not important edgy or feisty because in the end the structure is the same.

---

### Post by miLl3niUm on 2007-06-16
> **dnzz said:**
> Why dont you try the solution at the end of the post? :lolflag:

Lol, are you kidding me? there is no solution at the last post.
Do you mean this? [http://www.linuxquestions.org/linux/answers/Hardware/Installing_ATIs_Proprietary_Drivers](http://www.linuxquestions.org/linux/answers/Hardware/Installing_ATIs_Proprietary_Drivers)

---

### Post by scotty32 on 2007-06-16
sorry to hijack someone elses thread, but, when i try to install CSS it installs fine, then i hit "launch" and it says "No Permission" then closes down, then when i go to Steam, it says i havent paid for it. and then i have to uninstall steam for it to all work again.

also, the 'browser' in Steam doesnt work, when CSS says its not been paid for.

maybe its some kind of connection issue? firewall? though it works fine untill i try to load CSS

---

### Post by miLl3niUm on 2007-06-16
Or maybe yo didn't pay for it??

EDIT: And please wait to solve my problem, I am tired.

---

### Post by miLl3niUm on 2007-06-16
I did that but still doesn't work

[http://ubuntuforums.org/showthread.php?t=243342](http://ubuntuforums.org/showthread.php?t=243342)

---

### Post by dnzz on 2007-06-16
> **scotty32 said:**
> sorry to hijack someone elses thread, but, when i try to install CSS it installs fine, then i hit "launch" and it says "No Permission" then closes down, then when i go to Steam, it says i havent paid for it. and then i have to uninstall steam for it to all work again.

also, the 'browser' in Steam doesnt work, when CSS says its not been paid for.

maybe its some kind of connection issue? firewall? though it works fine untill i try to load CSS

Did steam connect to internet after installing? May be it didnt confirm the key properly

---

### Post by scotty32 on 2007-06-16
i dont have a disk (my friend does) but i paid for it through steam, and i just install it by downloading. yet once its finished downloading, it messes it all up. how would i make sure it installs / checks its reg'd or wot over its doing properly

---

### Post by dnzz on 2007-06-16
I had installation problems (it give an error while changing to cd3) so i installed it in Windows and copied all the folder to Wine. If you can take your cd from your friend try this one may be it could fix permission problem.

---

### Post by miLl3niUm on 2007-06-17
Go here [http://ubuntuforums.org/showthread.php?p=2859987](http://ubuntuforums.org/showthread.php?p=2859987)
I changed the title, maybe more members will come.

---

### Post by miLl3niUm on 2007-06-17
I installed it but it's slow, is here anything I can do?
(go to the link above)

---

### Post by thegoodsteer on 2007-07-03
Hey, I am trying to click and drag the font file, but it doesn't allow me. Also, I am not sure if I am bringing it to the correct directory. Can you please clarify a bit.

---

### Post by Macca86 on 2007-12-19
I get the same problem. But I only just updated my driver, and the driver that they want me to install is the exact same. Must be something thought because CS runs so slow and chunky.

---

### Post by texas.andy on 2007-12-24
I have a similar issue but I have Steam and CSS installed already.  However, when I laugh STEAM, I get the Steam frame work with "NO" "NADA" "NOTHING" with regards to fonts on the screen.  I see the boxes but no FONTS so i don't know what to type in where...

Any suggestions?  I am a total rookie here...

I am running ubuntu 7.10 on a P4 2.8MHZ with 2 gig RAM.  HELP!!!

---

### Post by dlegend on 2007-12-24
> **texas.andy said:**
> I have a similar issue but I have Steam and CSS installed already.  However, when I laugh STEAM, I get the Steam frame work with "NO" "NADA" "NOTHING" with regards to fonts on the screen.  I see the boxes but no FONTS so i don't know what to type in where...

Any suggestions?  I am a total rookie here...

I am running ubuntu 7.10 on a P4 2.8MHZ with 2 gig RAM.  HELP!!!

You need to properly install the microsoft fonts by adding them into the wine folder, then the text should show up fine.

> 
Downloading Microsoft core fonts

Steam requires the tahoma.ttf font. It is NOT included in the Microsoft core fonts package, so you have to get it separately.
For example, google for "filetype:ttf inurl:tahoma", download it and put it into your ~/.wine/drive_c/windows/fonts directory.

From: [http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam)

---

### Post by texas.andy on 2007-12-24
Thanks, its working great now.

---

