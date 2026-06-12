---
title: "Thinkpad X31"
date: 2015-03-21
forum: General Help
---

### Post by pellicle on 2015-03-21
Hi  trying to get ubuntu going on my X31 and eventually wound my way back to version 9 because of screen flicker problems, however when trying to install Google Chrome I download the i386 version and get a message "could not open, may be corrupt"  so I'm typing this from my XP box which works   Thanks for any advice as to what I may need to do to get it going.  :-)

---

### Post by sammiev on 2015-03-21
You would need at least ubuntu12.04 or 14.04

Also depends on the specs from your computer. You may need ( l or x ) ubuntu.

The first thing to do is post all your specs and hardware from your computer.

---

### Post by mörgæs on 2015-03-22
Yes, please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags. 

An X31 is old stuff so we might need some tricks to make it run well.

---

### Post by pellicle on 2015-03-22
Hi  > **mörgæs said:**
> An X31 is old stuff so we might need some tricks to make it run well.  definitely a good point .. so before going wild, is it worth trying ubuntu 12 or do you think that'll have the same screen flicker issues.  I'm hoping to use the lappie for some time yet and so having it work with as later version of ubuntu as possible is advantageous.  next I'll get those results up  thanks

Hi

> **mörgæs said:**
> Yes, please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags. 

below
```
computer
    description: Notebook
    product: 2672CBM
    vendor: IBM
    version: ThinkPad X31
    serial: [REMOVED]
    width: 32 bits
    capabilities: smbios-2.33 dmi-2.33
    configuration: administrator_password=disabled boot=normal chassis=notebook frontpanel_password=unknown keyboard_password=disabled power-on_password=disabled uuid=723CB201-457D-11CB-A524-D1E211B7FD86
  *-core
       description: Motherboard
       product: 2672CBM
       vendor: IBM
       physical id: 0
       version: Not Available
       serial: [REMOVED]
     *-firmware
          description: BIOS
          vendor: IBM
          physical id: 0
          version: 1QET65WW (2.03 ) (10/10/2003)
          size: 144KiB
          capacity: 960KiB
          capabilities: pci pcmcia pnp apm upgrade shadowing escd cdboot bootselect edd int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) M processor 1400MHz
          vendor: Intel Corp.
          physical id: 6
          bus info: cpu@0
          version: 6.9.5
          slot: None
          size: 1400MHz
          capacity: 1400MHz
          width: 32 bits
          clock: 400MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr mce cx8 sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 tm pbe up bts est tm2 cpufreq
        *-cache:0
             description: L1 cache
             physical id: a
             slot: Internal L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: b
             slot: Internal L2 Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: burst internal write-back unified
     *-memory
          description: System Memory
          physical id: 28
          slot: System board or motherboard
          size: 1GiB
          capacity: 1GiB
        *-bank:0
             description: SODIMM DDR Synchronous
             physical id: 0
             slot: DIMM 1
             size: 512MiB
             width: 64 bits
        *-bank:1
             description: SODIMM DDR Synchronous
             physical id: 1
             slot: DIMM 2
             size: 512MiB
             width: 64 bits
     *-pci
          description: Host bridge
          product: 82855PM Processor to I/O Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-pci:0
             description: PCI bridge
             product: 82855PM Processor to AGP Controller
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
           *-display UNCLAIMED
                description: VGA compatible controller
                product: Radeon Mobility M6 LY
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: agp agp-2.0 pm bus_master cap_list
                configuration: latency=66 mingnt=8
        *-usb:0
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:1
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master
           *-pcmcia:0
                description: CardBus bridge
                product: RL5c476 II
                vendor: Ricoh Co Ltd
                physical id: 0
                bus info: pci@0000:02:00.0
                version: aa
                width: 64 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=128 module=yenta_socket
                resources: iomemory:b00603020-b0060301f
           *-pcmcia:1
                description: CardBus bridge
                product: RL5c476 II
                vendor: Ricoh Co Ltd
                physical id: 0.1
                bus info: pci@0000:02:00.1
                version: aa
                width: 64 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=128 module=yenta_socket
                resources: iomemory:b00707020-b0070701f
           *-firewire
                description: FireWire (IEEE 1394)
                product: R5C552 IEEE 1394 Controller
                vendor: Ricoh Co Ltd
                physical id: 0.2
                bus info: pci@0000:02:00.2
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=2 module=ohci1394
           *-network:0
                description: Wireless interface
                product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
                vendor: Intel Corporation
                physical id: 2
                bus info: pci@0000:02:02.0
                logical name: eth1
                version: 04
                serial: [REMOVED]
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw2100 driverversion=git-1.2.2 firmware=712.0.3:3:00000001 ip=[REMOVED] latency=64 link=yes maxlatency=34 mingnt=2 module=ipw2100 multicast=yes wireless=IEEE 802.11b
           *-network:1
                description: Ethernet interface
                product: 82801DB PRO/100 VE (MOB) Ethernet Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:02:08.0
                logical name: eth0
                version: 81
                serial: [REMOVED]
                size: 10MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k6-NAPI duplex=half firmware=N/A latency=66 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s
        *-isa
             description: ISA bridge
             product: 82801DBM (ICH4-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801DBM (ICH4-M) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
           *-disk
                description: ATA Disk
                product: HTS541080G9AT00
                vendor: Hitachi
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: MB4O
                serial: [REMOVED]
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000e84ab
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: [REMOVED]
                   size: 71GiB
                   capacity: 71GiB
                   capabilities: primary bootable journaled extended_attributes large_files ext3 ext2 initialized
                   configuration: created=2015-03-22 11:44:15 filesystem=ext3 modified=2015-03-22 13:02:34 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2015-03-22 22:22:09 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 2933MiB
                   capacity: 2933MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 2933MiB
                      capabilities: nofs
        *-serial UNCLAIMED
             description: SMBus
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=0 module=snd_intel8x0
        *-communication UNCLAIMED
             description: Modem
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: [REMOVED]
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

---

### Post by Bucky Ball on 2015-03-22
Well, Ubuntu 9.** is well (years) out of date and unsupported so there's little chance of getting much help with it. Keep in mind it has not received security updates for around four years so it also creates a security vulnerability if the machine's online.

Install a supported release, perhaps one of the long-term support releases 12.04 LTS or 14.04 LTS (support until 2017 and 2019 respectively) and we'll take it from there.

You may get Ubuntu running on that machine, but might not be such a pleasant computing experience, even if you can. As suggested, try Xubuntu or Lubuntu for something more satisfactory.

---

### Post by pellicle on 2015-03-22
Hi

> **Bucky Ball said:**
> ... try Xubuntu or Lubuntu for something more satisfactory.

ahh, so that's what x or l was meaning ... I don't know anything about them, so that's a research topic in itself

I'll try 12 and see if it supports my video card ... pitty 9 runs fast!

thanks :-)

---

### Post by mörgæs on 2015-03-22
Better to try Lubuntu 14.04.2 as a first attempt. Old software including 12.04 is only an emergency solution.

The processor doesn´t have PAE which calls for a special setup. Please see this: [https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE)

More advice in the link in my signature.

---

### Post by Bucky Ball on 2015-03-22
Yes, my mistake. Lubuntu 12.04 is no longer supported either. It is not LTS, and Xubuntu will be out of support this year. Try 14.04 LTS, as morgaes suggests. ;)

PS: Either Xubuntu or Lubuntu is going to look a lot more like what you are used to with 9.04. Ubuntu uses Unity as its desktop environment now and that is nothing like what you are using now.

---

### Post by kerry_s on 2015-03-22
> **pellicle said:**
> Hi



ahh, so that's what x or l was meaning ... I don't know anything about them, so that's a research topic in itself

I'll try 12 and see if it supports my video card ... pitty 9 runs fast!

thanks :-)

1.4mhz & 1gb ram should be fine with normal desktops ie: lubuntu, xubuntu, ubuntu-mate
you want to stay away from the 3d stuff ie: unity, gnome shell

---

### Post by pellicle on 2015-03-22
Hi
> **mörgæs said:**
> Better to try Lubuntu 14.04.2 as a first attempt. Old software including 12.04 is only an emergency solution.

The processor doesn´t have PAE which calls for a special setup. Please see this: [https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE)

thanks for the help ... downloading 14.04.2 now

:-)

also, can anyone point me at links describing what is go with this the xbuntu and lbuntu stuff? (that might be more succinct than me just googling it)

thanks again

---

### Post by kerry_s on 2015-03-22
xubuntu & lubuntu are just different environments, the gui you interact with.
personally i go with xubuntu, lubuntu just never feels right to me.

---

### Post by Bucky Ball on 2015-03-22
Desktop environment and default apps. Lubuntu uses the Lxde desktop environment, Xubuntu uses xfce4. I also use xfce4. Xubuntu is very and easily customisable, but may be sluggish on your machine.

---

### Post by pellicle on 2015-03-22
> **mörgæs said:**
> Better to try Lubuntu 14.04.2 as a first attempt. Old software including 12.04 is only an emergency solution.

The processor doesn´t have PAE which calls for a special setup. Please see this: [https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE)


I got the ISO down and found it baulked on the install saying an error about PAE ... so peraps I can edit the files in the ISO before installing??

I'm currently on 11 and have just downloaded lubuntu 12 and 14 to see

---

### Post by mörgæs on 2015-03-23
Did you read the link?

---

### Post by pellicle on 2015-03-23
> **mörgæs said:**
> Did you read the link?

it was about 11pm Australian time and so I read some of it before then thinking "ok, well I'll burn the ISO and install it and then get back to it" ... I hadn't expected that the link was about how to get the installer going, so much as how to get the installation (once installed) going.

I will try the lubuntu tonight and read the link in more detail

thanks for your patience

PS: I see I was "this close" and so will try again tonight

Hi again

> **mörgæs said:**
> Did you read the link?

I did ... and it implies something can be chosen:
At the boot menu screen the options are 

[LIST]
[*]Install  
[*]Command-line options 
[*]Advanced options 
[*]Help 
[/LIST]
With the cursor on the top choice press F6.
[img]https://help.ubuntu.com/community/PAE?action=AttachFile&do=get&target=forcepae-vivid.png[/img]


but I got only this:
[img]https://farm9.staticflickr.com/8715/16902386901_e2afb5cf8a_o.jpg[/img]

which is where I got to last night (a bit later than now) .. and why I thought there must be something to modify in the ISO

---

### Post by kerry_s on 2015-03-23
your choices are very limited with out pae, so apparently your best bet is 12 lts version.
i recommend [http://elementary.io/](http://elementary.io/)

---

### Post by Bucky Ball on 2015-03-23
Does this help at all?

> The "forcepae" option must be entered twice, before and after the delimiter "-- ", so that it is applied to both the kernel on the ISO and the kernel on the system after installation. 

 From [here]("https://help.ubuntu.com/community/PAE"). Have a look at the bottom of that page at the last section after the line also. 

I have the PAE kernel running on a desktop with a 14.04 minimal install. It is a P4 32bit and needs it to recognise the RAM.

---

### Post by mörgæs on 2015-03-23
All Pentium 4's (as well as 3 and 2) have PAE, so there's no problem here.

Pellicle, which ISO did you try?

---

### Post by pellicle on 2015-03-23
Hi
> **mörgæs said:**
> Pellicle, which ISO did you try?

14.04.2-desktop.iso

mirror.rakcentral.com.au/ubuntu-releases/14.04.2/ ....

---

### Post by mörgæs on 2015-03-24
I can't open the link.
Are you sure it's Lubuntu and not Ubuntu?

---

### Post by pellicle on 2015-03-24
> **mörgæs said:**
> I can't open the link.

sorry, the link was not intended for opening, but as a guide. I typed it in by hand from my other computer

its this one
[http://mirror.rackcentral.com.au/ubuntu-releases/trusty/ubuntu-14.04-desktop-i386.iso](http://mirror.rackcentral.com.au/ubuntu-releases/trusty/ubuntu-14.04-desktop-i386.iso)

> Are you sure it's Lubuntu and not Ubuntu?

I have no idea ... I had never heard of lubuntu before I looked for what you advised when you said go straight for 14
> **mörgæs said:**
> Better to try Lubuntu 14.04.2 as a first attempt

and now quoting that I see you wrote lubuntu ... thats what you get when you have only ever known ubuntu, never heard of lubuntu and so my mind just error corrected Lubuntu back to Ubuntu (which look optically similar to me)

---

### Post by pellicle on 2015-03-25
Hi

ok, things get "strange" here ... lastnight I installed the above Lubuntu 14 onto my system and the behavior of the installer was exactly like that given in the link about PAE ... so I thought "*maybe I did something wrong*" and so went back and tried to install the regular Ubuntu 14 and had exactly the same problem at CD boot ... the error message about PAE *before* it got to the menu.

So, what gives?

---

### Post by mörgæs on 2015-03-26
It's not relevant how Ubuntu behaves. 
Several posters have already pointed out that it's too heavy for such old gear.

---

### Post by pellicle on 2015-03-26
> **mörgæs said:**
> It's not relevant how Ubuntu behaves. 

true, but it is relevant how the installer behaves.

lubuntu 14.10 installs.

Uncertain I like it, will post questions in related forum

thanks all for assistance given

---

