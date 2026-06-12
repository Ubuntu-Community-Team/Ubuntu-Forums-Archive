---
title: "Wireless no longer works in Hardy"
date: 2008-05-02
forum: General Help
---

### Post by klaasvanschelven on 2008-05-02
I've upgraded my system to Hardy from Gutsy... I say updated but I've really done a clean install. Wireless worked straight out of the box in Gutsy but no longer works. No networks show up in my networkmanager applet nor is it possible to directly connect. lshw gives me some reason to think my card is recognized:

```
lenovo
    description: Notebook
    product: 0768FPG
    vendor: LENOVO
    version: 3000 N100
    serial: L3MA995
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: administrator_password=disabled boot=oem-specific chassis=notebook cpus=2 frontpanel_password=unknown keyboard_password=unknown power-on_password=disabled uuid=77478253-AE3C-11DB-91B8-000FB0D2EB60
  *-core
       description: Motherboard
       product: CAPELL VALLEY(NAPA) CRB
       vendor: LENOVO
       physical id: 0
       version: Not Applicable
       serial: 41W8025Z1ZCZ97261YA
       slot: PCI Express Slot J7C1
     *-firmware
          description: BIOS
          vendor: LENOVO
          physical id: 0
          version: 63ET60WW (03/26/07)
          size: 95KiB
          capacity: 960KiB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing escd cdboot acpi usb agp biosbootspecification
     *-cpu:0
          description: CPU
          product: Intel(R) Core(TM) Duo CPU      T2350  @ 1.86GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.14.12
          serial: 0000-06EC-0000-0000-0000-0000
          slot: U2E1
          size: 1867MHz
          capacity: 2048MHz
          width: 32 bits
          clock: 133MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon bts pni monitor est tm2 xtpr cpufreq
          configuration: id=1
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 2MiB
             capacity: 2MiB
             capabilities: burst external write-back
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 32 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 13
          slot: System board or motherboard
          size: 1GiB
          capacity: 3GiB
        *-bank:0
             description: SODIMM Synchronous
             physical id: 0
             slot: M1
             size: 512MiB
             width: 32 bits
        *-bank:1
             description: SODIMM Synchronous
             physical id: 1
             slot: M2
             size: 512MiB
             width: 32 bits
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.14.12
          serial: 0000-06EC-0000-0000-0000-0000
          size: 1867MHz
          capacity: 1867MHz
          capabilities: ht cpufreq
          configuration: id=1
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             capabilities: logical
     *-pci
          description: Host bridge
          product: Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display:0 UNCLAIMED
             description: VGA compatible controller
             product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list
             configuration: latency=0
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
        *-multimedia
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:0
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:1
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Wireless interface
                product: PRO/Wireless 3945ABG Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wmaster0
                version: 02
                serial: 00:19:d2:b3:fc:37
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g
        *-usb:0
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801G (ICH7 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:2
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e2
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-network
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 1
                bus info: pci@0000:05:01.0
                logical name: eth0
                version: 10
                serial: 00:0f:b0:d2:eb:60
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.2.103 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
           *-pcmcia
                description: CardBus bridge
                product: CB1410 Cardbus Controller
                vendor: ENE Technology Inc
                physical id: 4
                bus info: pci@0000:05:04.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192 module=yenta_socket
           *-firewire
                description: FireWire (IEEE 1394)
                product: R5C832 IEEE 1394 Controller
                vendor: Ricoh Co Ltd
                physical id: 6
                bus info: pci@0000:05:06.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=2 module=ohci1394
           *-system:0
                description: SD Host controller
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 6.1
                bus info: pci@0000:05:06.1
                version: 19
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci latency=64 module=sdhci
           *-system:1 UNCLAIMED
                description: System peripheral
                product: R5C592 Memory Stick Bus Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 6.2
                bus info: pci@0000:05:06.2
                version: 0a
                width: 32 bits
                clock: 33MHz
                capabilities: pm cap_list
                configuration: latency=0
           *-system:2 UNCLAIMED
                description: System peripheral
                product: xD-Picture Card Controller
                vendor: Ricoh Co Ltd
                physical id: 6.3
                bus info: pci@0000:05:06.3
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: pm cap_list
                configuration: latency=0
        *-isa
             description: ISA bridge
             product: 82801GBM (ICH7-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801GBM/GHM (ICH7 Family) SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-disk
                description: ATA Disk
                product: FUJITSU MHV2120B
                vendor: Fujitsu
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 0084
                serial: NW9ST7428WEB
                size: 111GiB (120GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=80b74e0e
              *-volume
                   description: Extended partition
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   size: 111GiB
                   capacity: 111GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /home
                      capacity: 58GiB
                      configuration: mount.fstype=reiserfs mount.options=rw,relatime state=mounted
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      logical name: /boot
                      capacity: 101MiB
                      configuration: mount.fstype=ext2 mount.options=rw,relatime state=mounted
                 *-logicalvolume:2
                      description: Linux swap / Solaris partition
                      physical id: 7
                      logical name: /dev/sda7
                      capacity: 10001MiB
                      capabilities: nofs
                 *-logicalvolume:3
                      description: Linux filesystem partition
                      physical id: 8
                      logical name: /dev/sda8
                      logical name: /
                      logical name: /dev/.static/dev
                      capacity: 10001MiB
                      configuration: mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered state=mounted
           *-cdrom
                description: DVD-RAM writer
                product: DVD-RAM UJ-850
                vendor: MATSHITA
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: RB31
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=open
        *-serial UNCLAIMED
             description: SMBus
             product: 82801G (ICH7 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02

             width: 32 bits
             clock: 33MHz
             configuration: latency=0

```
Ideas?

---

### Post by TeoBigusGeekus on 2008-05-02
Try WICD.
[http://wicd.sourceforge.net/]("http://wicd.sourceforge.net/")

---

### Post by Zorael on 2008-05-02
Owie. There's a whole lot of unclaimed devices in there.

Does it work off a Hardy live CD?

---

### Post by p_quarles on 2008-05-02
Yes, there are some unclaimed devices, but the wireless isn't one of them, and that particular card has excellent Linux support. At the same time, Ubuntu 8.04 adopted the newer version of the Linux driver, which has been giving some people some problems (I've had a few with mine, as well). 

Anyway, I would recommend testing its network detection from the command line. First, find the device name ("eth1" is used a likely answer below, but this may need to be changed), then run this:
```
sudo iwlist eth1 scan
```
If it gives you a list of essids in the area, you know it's working at least a little.

---

### Post by klaasvanschelven on 2008-05-02
Sorry for the long delay in reply... I've been messing up my system even further.

[emotional dump]
I really love Ubuntu and want to stay on the newest releases but I get very very %^&^%&* Q$U#@O$ from having to spend more then a full day restoring my system after every upgrade
[/dump]

I've implemented the first advice...(WICD) this took my working (wired) network connection out because deinstalling networkmanager and not replacing it with anything that I found to work. I can't manage to reinstall it now so am without internet all together (working from second pc here). How do I instruct aptitude to use the cdrom? Aptitude update keeps saying Ign: cdrom.....

More on topic:
* It doesn't work off live CD (that should have been a sign)

I'll post the code for "sudo iwlist eth1 scan" once I get wired internet back to work....

---

### Post by klaasvanschelven on 2008-05-02
From the live CD:

```
ubuntu@ubuntu:~$ sudo iwlist eth1 scan
eth1      Interface doesn't support scanning.

ubuntu@ubuntu:~$ sudo iwlist eth0 scan
eth0      Interface doesn't support scanning.

ubuntu@ubuntu:~$ sudo iwlist wlan scan
wlan      Interface doesn't support scanning.

```

Doesn't look too good...

---

### Post by Zorael on 2008-05-02
Well, you're not alone. I officially contest iwl3945 working excellently, but if you say there's a bug with the Hardy-introduced driver, I guess that'd explain things. Also, when everyone could get their interface running with ipw3945, it was simply impossible for my second card, whereas it was a breeze with my first. Conclusion: hardware differences, though works in Windows.

Anyway, isn't the interface named wlan0? Just try omitting any interface names when scanning.
```
$ sudo iwlist scan
```



To be a kill-joy, here's my output when trying to connect.
```
zorael@sunspire:~$ sudo iwconfig wlan0 essid any
zorael@sunspire:~$ sudo iwconfig wlan0
wlan0     IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Tx-Power=27 dBm
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

zorael@sunspire:~$ sudo iwconfig wlan0 essid lappskole
zorael@sunspire:~$ sudo ifup wlan0
There is already a pid file /var/run/dhclient.wlan0.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:18:de:6e:39:9a
Sending on   LPF/wlan0/00:18:de:6e:39:9a
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
zorael@sunspire:~$ sudo iwlist wlan0 scan
wlan0     No scan results

zorael@sunspire:~$ sudo iwlist wlan0 scan
wlan0     No scan results
```
It doesn't see the essid, it's not hidden, and I bet my left foot it's *there*. My phone, next to my computer, connects to it with ~40% signal strength.

Tagging and subscribing for interest.

See [http://www.intellinuxwireless.org/bugzilla/show_bug.cgi?id=1579](http://www.intellinuxwireless.org/bugzilla/show_bug.cgi?id=1579).

---

### Post by MongooseCage on 2008-05-02
I have exactly the same problem too! any clues? Mine is a Lenovo Thinkpad R60 and the ipw3945 driver is suppose to work but it doesnt WORK! I have tried downloading the iso twice and burning it twice on a dvd, twice on a cd, The first CD didnt work and the First DVD crashed after a couple of days(kernel panic at boot), So i did a fresh install with the second CD and its still not working. I also tried all that restricted-modules stuff... Didn't help at all.

---

### Post by Zorael on 2008-05-02
I used the following script to get iwl3945 working marvellously under Gutsy, but I haven't tried it under Hardy; I'm not using the wireless much at present, so I thought I'd leave it in this broken state to help debug the issue. I'm not getting much response over at that bug report linked earlier, though.

[http://linuxwireless.org/en/users/Download](http://linuxwireless.org/en/users/Download)

If you do try it (in Hardy), please report if it worked for you.

---

### Post by klaasvanschelven on 2008-05-02
iwlist scan w/o params:

```
$ sudo iwlist scan

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Failed to read scan data : Resource temporarily unavailable

```

I'm going to try this ([http://linuxwireless.org/en/users/Download](http://linuxwireless.org/en/users/Download)) now and will report on it in a bit... though I'm not sure why new action is required in hardy as opposed to gutsy. Did you say they're using a new driver?

---

### Post by rupali_4 on 2008-05-02
You can do everything you want to do in a day on [www.baajaa.com](www.baajaa.com). You can look at job openings, find a date, rent an apartment, sell your bike and buy used items. And if you are interested in showbiz you can post your profile along with pics and your video as well. Also Balaji Telefilms is conducting auditions on [www.baajaa.com](www.baajaa.com) . All this and lots more on [www.baajaa.com](www.baajaa.com) !

One of the new features added on [www.baajaa.com](www.baajaa.com) is Yellow Pages. You can create a simple listing of your business for free. But what is really interesting is that you can Create Your Own Website (with your Logo, 5 pics, Company Profile, List of Products & Services, Video) and you get a Free Premium Yellow Page listing. For just Rs.3999/- !
 
Thanks,

---

### Post by Dennis Beekman on 2008-05-02
just use ndiswrapper en the manufacturer drivers, this always works for me...with my atheros wireless chipset.

Even with version 8.04 LTS the device is found and listen and the driver ath_pci is used for it...but it doesn't actually work.

I have to blacklist the ath_pci driver and use ndiswrapper to get the wireless going on my "Acer Aspire 5103WLMI" 

what chipset do you have and is it found at all ?
If not => have your turned of your wireless in any way ? laptop often have an on and of button or button-combination...:lolflag:

the new ndiswrapper software is very easy to install and use under ubuntu... if you have it working and want it to be loaded as standard just add "modprobe ndiswrapper" to "/etc/rc.local"

---

### Post by Zorael on 2008-05-02
Believe me, I've tried it all. :>

I've some confidence in being able to set up networking settings and disabling/enabling modules, so I dare say the issue lies with the module itself. Point in case; I had an 3945 card which worked marvellously on my laptop, then I sent it in for repairs (motherboard busted), and upon return it *refused* to work. No go, whatsoever. Spammed "Detected Geography" in dmesg.

I found a workaround wherein I had to toggle the module to get another chance at connecting, but then the connection inevitably died after a while and I had to do it again. Upon mucking about I apparently made some change that made this workaround stop working. It worked briefly in a Hardy beta, so I googled around and found that script and got it working without flaws in Gutsy.

edit: Relevant chipset for both me and the OP is the Intel Wireless PRO/3945ABG, earlier using the ipw3945 module and in Gutsy and onwards the iwl3945 one.

---

### Post by klaasvanschelven on 2008-05-02
when running the above script at [http://linuxwireless.org/en/users/Download](http://linuxwireless.org/en/users/Download) I get stuck at this point:

```

$ sudo make load
Unloading iwl3945...
Unloading cfg80211...
FATAL: Module cfg80211 is in use.
make: *** [unload] Error 1
```

---

### Post by Zorael on 2008-05-02
> **klaasvanschelven said:**
> when running the above script at [http://linuxwireless.org/en/users/Download](http://linuxwireless.org/en/users/Download) I get stuck at this point:

```

$ sudo make load
Unloading iwl3945...
Unloading cfg80211...
FATAL: Module cfg80211 is in use.
make: *** [unload] Error 1
```
```
$ sudo /etc/init.d/networking stop
```
Failing that, add a line saying **blacklist cfg80211** to **/etc/modprobe.d/blacklist**. Reboot, install, remove line, reboot.

---

### Post by MongooseCage on 2008-05-02
> **Zorael said:**
> I used the following script to get iwl3945 working marvellously under Gutsy, but I haven't tried it under Hardy; I'm not using the wireless much at present, so I thought I'd leave it in this broken state to help debug the issue. I'm not getting much response over at that bug report linked earlier, though.

[http://linuxwireless.org/en/users/Download](http://linuxwireless.org/en/users/Download)

If you do try it (in Hardy), please report if it worked for you.

Yeah, I tried it, at first I was confused but I got through,
But I am stuck, **Please Help**! This might be my breaking point!

So I did:
```

sudo make install

```
after going through all those steps, and then i had a very large blah blah thing going on.

```
 mongoose@The-Heron:~/Desktop/compat-wireless-2008-05-02$ sudo make load
Unloading cfg80211...
FATAL: Module cfg80211 is in use.
make: *** [unload] Error 1

```

This is where i am stuck at how do i get the module to stop working or something as its saying?

---

### Post by Zorael on 2008-05-02
Tried what I suggested in the last post?

---

### Post by klaasvanschelven on 2008-05-02
I will give the above suggestion a try as soon as I've got Hardy running again (trashed boot partition by now).

Meanwhile another approach seems easier to me (though I have no idea how to do it). Since Gutsy offered me a non-free driver to accept, is there no way to install exactly what already worked in Gutsy on the Hardy side? Which files or packages should I look for in Gutsy?

---

### Post by MongooseCage on 2008-05-02
> **Zorael said:**
> Tried what I suggested in the last post?

Whoa, just noticed that... Excuse my extreme noobness but how do I tell it to put the module into the blacklist?

I am extremely sorry, I have only tried 7.10 for 1 month and now i am on hardy

---

### Post by Zorael on 2008-05-02
:>

Did you try disabling networking manually first?
```
$ sudo /etc/init.d/networking stop
$ sudo modprobe -r cfg80211
$ sudo modprobe -r iwl3945
*<run script>*
```

Else, just pop up a text editor with superuser permissions and edit **/etc/modprobe.d/blacklist**. Alt+F2, 'gksu gedit /etc/modprobe.d/blacklist'.

Then add a line saying **blacklist cfg80211** at the bottom. You'll be removing this line once you manage to install the driver.

Reboot.

---

### Post by MongooseCage on 2008-05-02
> **Zorael said:**
> :>

Did you try disabling networking manually first?
```
$ sudo /etc/init.d/networking stop
$ sudo modprobe -r cfg80211
$ sudo modprobe -r iwl3945
*<run script>*
```

Else, just pop up a text editor with superuser permissions and edit **/etc/modprobe.d/blacklist**. Alt+F2, 'gksu gedit /etc/modprobe.d/blacklist'.

Then add a line saying **cfg80211** at the bottom. You'll be removing this line once you manage to install the driver.

Reboot.

so 
```

blacklist cfg80211

```

Yeah? I am seriously confused because I have never edited my system files...

---

### Post by Zorael on 2008-05-02
Probably should've mentioned prepending 'blacklist', in retrospect.

Yes, try that. I don't remember having to do it myself (think it just worked after stopping networking and unloading the modules), but that should do the trick.

---

### Post by klaasvanschelven on 2008-05-02
Hi,

I've:

* Blacklisted the mentioned file
* Reboot
* sudo make load (no errors, list of drivers)
* Remove from blacklist
* Reboot

Nothing.

I'm getting tired of this... back to the Gibbon.

Any listings I could post to help someone debug this? Anyone who could/should be interested by this (i.e. bugreports)?

Also, I'm repeating my earlier question: shouldn't it be possible to use the restricted driver in Hardy, and if so, how?

---

### Post by MongooseCage on 2008-05-02
how do i gain superuser permission?

---

### Post by MongooseCage on 2008-05-02
> **Zorael said:**
> ```
$ sudo /etc/init.d/networking stop
```
Failing that, add a line saying **blacklist cfg80211** to **/etc/modprobe.d/blacklist**. Reboot, install, remove line, reboot.

Hey, the

```
 sudo /etc/init.d/networking stop 
```

worked! And I was able to compile it

But unfortunatley nothing happened either... Everything worked and then the wireless didnt have an effect. :(

I really like hardy...:confused:
I think I will try once again...

---

### Post by Zorael on 2008-05-02
Okay, so, I'm beside myself with joy right now.

I had no luck with compiling the drivers themselves, but then I stumbled upon this, and it worked right away.

[http://ubuntuforums.org/showthread.php?p=4612681](http://ubuntuforums.org/showthread.php?p=4612681)

---

### Post by MongooseCage on 2008-05-03
> **Zorael said:**
> Okay, so, I'm beside myself with joy right now.

I had no luck with compiling the drivers themselves, but then I stumbled upon this, and it worked right away.

[http://ubuntuforums.org/showthread.php?p=4612681](http://ubuntuforums.org/showthread.php?p=4612681)

hmmm... didnt work for me but I didnt bother doing that WCID part. I got those drivers compiled but I still dont get it. I have blacklisted the non-existant ipw3945 just incase, And i have added iwl3945 to the modules list. I have tried using the terminal to turn on the wireless but its not working at all. It almost seems like the drivers don't even exist. I have tried modprobe iwl3945 and modprobe -r ipw3945. I have tried using the linux-generic-backport stuff. But I havent got it to work at all. Its really strange now... I am going to work on this one more day and thats it. Gutsy FTW.

---

### Post by MongooseCage on 2008-05-03
I found this in /etc/udev/rules.d called 70-persistent-net.rules I got this from some thread that closed down due to the fact that it was no longer in testing.

```

# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x14e4:0x167d (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:16:d3:2f:c7:14", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x8086:0x4227 (iwl3945)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:18:de:b1:a9:d4", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

```

Any Ideas or Clues?

---

### Post by Zorael on 2008-05-03
That's for naming the interfaces, I think. Early iwl3945 builds ended up naming them wmaster0 and wlan0_rename.

To reproduce what's on my system now:
[list][*]Make sure you've removed any compiled drivers. Go into the directory where you compiled them, then do the following.
[list=1][*]sudo make unload
[*]sudo uninstall.[/list]


[*]Make sure you have linux-backports-modules-hardy installed.
[*]Create /etc/modprobe.d/iwl3945 with the following content. You will need superuser permissions to write to the folder (gksu gedit /etc/modprobe.d/iwl3945).  Don't bother with wicd yet.
```
alias wlan0 iwl3945
options iwl3945 disable_hw_scan=1
```
[*]sudo modprobe iwl3945
[*]sudo ifconfig wlan0 up
[*]sudo iwlist scan[/list]

---

### Post by MongooseCage on 2008-05-03
> **Zorael said:**
> That's for naming the interfaces, I think. Early iwl3945 builds ended up naming them wmaster0 and wlan0_rename.

To reproduce what's on my system now:
[list][*]Make sure you've removed any compiled drivers. Go into the directory where you compiled them, then do the following.
[list=1][*]sudo make unload
[*]sudo uninstall.[/list]


[*]Make sure you have linux-backports-modules-hardy installed.
[*]Create /etc/modprobe.d/iwl3945 with the following content. You will need superuser permissions to write to the folder (gksu gedit /etc/modprobe.d/iwl3945).  Don't bother with wicd yet.
```
alias wlan0 iwl3945
options iwl3945 disable_hw_scan=1
```
[*]sudo modprobe iwl3945
[*]sudo ifconfig wlan0 up
[*]sudo iwlist scan[/list]

Would a reinstallation do just fine? Then following up the steps? There isn't any more to this right? Like all these previous steps of blacklisting modules and enabling modules?

---

### Post by Zorael on 2008-05-03
A reinstallation would do the trick, yes. You may want to backup your home folder if you don't want to redo desktop settings.

Then grab linux-backports-modules-hardy, create the /etc/modprobe.d/iwl3945 file, and disable and enable the module with the commands listed at the end there.

---

### Post by MongooseCage on 2008-05-03
> **MongooseCage said:**
> Would a reinstallation do just fine? Then following up the steps? There isn't any more to this right? Like all these previous steps of blacklisting modules and enabling modules?

Ok so i followed your steps, and so i got this:

```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Failed to read scan data : Resource temporarily unavailable

```

I am going to try to restart now and I will report back to you if my wifi has started working or not.

---

### Post by MongooseCage on 2008-05-03
DUDE!!! IT WORKED! THIS IS AMAZING! SORRY FOR BEING RATHER INFORMAL BUT THIS IS JUST GREAT!!!! THANKS BIG TIME! AFTER SPENDING 2 DAYS ON THIS ITS FINALLY WORKING! YES!

Thanks for all your help, I am extremely grateful. I finally have a well working amazing Ubuntu 8.04 Hardy Heron laptop.

---

### Post by Zorael on 2008-05-03
Awesome, cheers. :>

May want to mark thread as solved, under thread tools.


edit: Doh.

---

### Post by p_quarles on 2008-05-03
> **Zorael said:**
> Awesome, cheers. :>

May want to mark thread as solved, under thread tools.
That feature is still missing from the new version of vBulletin. It's being worked on, though.

---

### Post by promise239 on 2008-05-08
For those of you still stuck on this issue, my issue was magically resolved in hardy when I used the bootloader to load the older kernel instead...  I believe the issue lies with this new linux kernel.

---

### Post by MongooseCage on 2008-05-09
> **promise239 said:**
> For those of you still stuck on this issue, my issue was magically resolved in hardy when I used the bootloader to load the older kernel instead...  I believe the issue lies with this new linux kernel.

Yeah, the new Kernel especially conflicts with emulators. I tried Virtual Box. The minute I installed the new modules, wireless gone, sound gone. The next day I noticed two copies of my Ubuntu in the GRUB bootloader!:confused:

The second Ubuntu works too! like properly! Its crazy...

---

