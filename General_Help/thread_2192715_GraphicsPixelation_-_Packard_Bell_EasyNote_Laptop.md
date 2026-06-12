---
title: "Graphics/Pixelation - Packard Bell EasyNote Laptop"
date: 2013-12-09
forum: General Help
---

### Post by amjjawad on 2013-12-09
Hi,

```
sudo lshw 
packard-bell              
    description: Pizza Box Computer
    product: Packard Bell EasyNote
    vendor: NEC Computers International
    version: PB22C00061
    serial: 610700440237
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: administrator_password=disabled boot=normal  chassis=pizzabox power-on_password=disabled  uuid=B87434C6-3C97-DA11-8000-4E45435F4349
  *-core
       description: Motherboard
       product: NEC Versa Premium
       vendor: NEC COMPUTERS INTERNATIONAL
       physical id: 0
       version: 5a
     *-firmware
          description: BIOS
          vendor: Insyde Software Corporation
          physical id: 0
          version: R1.05
          date: 09/20/2005
          size: 84KiB
          capacity: 448KiB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing cdboot  bootselect socketedrom edd int13floppynec int13floppytoshiba  int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial  int17printer int10video acpi usb agp smartbattery biosbootspecification  netboot
     *-cpu
          description: CPU
          product: AMD Turion(tm) 64 Mobile Technology ML-32
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 15.4.2
          serial: Processor Serial Number
          slot: uPGA 754
          size: 1600MHz
          capacity: 1800MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce  cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2  syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow pni lahf_lm cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: burst pipeline-burst internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: burst pipeline-burst internal write-back
     *-memory:0
          description: System Memory
          physical id: c
          slot: System board or motherboard
          capacity: 768MiB
        *-bank:0
             description: SODIMM DDR 133 MHz (7.5 ns)
             physical id: 0
             slot: DRAM Slot 1
             size: 512MiB
             width: 64 bits
             clock: 133MHz (7.5ns)
        *-bank:1
             description: SODIMM DDR 133 MHz (7.5 ns)
             physical id: 1
             slot: DRAM Slot 2
             size: 512MiB
             width: 64 bits
             clock: 133MHz (7.5ns)
     *-memory:1 UNCLAIMED
          description: Video Memory
          physical id: d
          slot: System board or motherboard
          capacity: 64MiB
     *-memory:2 UNCLAIMED
          description: Flash Memory
          physical id: e
          slot: System board or motherboard
          capacity: 2MiB
     *-memory:3 UNCLAIMED
          physical id: 1
     *-memory:4 UNCLAIMED
          physical id: 2
     *-pci:0
          description: Host bridge
          product: RS480/RS482/RS485 Host Bridge
          vendor: Advanced Micro Devices, Inc. [AMD/ATI]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 01
          width: 32 bits
          clock: 66MHz
          configuration: latency=64
        *-pci:0
             description: PCI bridge
             product: RC4xx/RS4xx PCI Bridge [int gfx]
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci ht normal_decode bus_master cap_list
             resources: ioport:c000(size=8192) memory:c0000000-cfffffff ioport:90000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: RS480M [Mobility Radeon Xpress 200]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: pm vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=64 mingnt=8
                resources: irq:17 memory:90000000-97ffffff  ioport:c000(size=256) memory:c0000000-c000ffff memory:98000000-9801ffff
        *-pcmcia
             description: CardBus bridge
             product: PCI4510 PC card Cardbus Controller
             vendor: Texas Instruments
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
             resources: irq:17 memory:40000000-40000fff  ioport:1800(size=256) ioport:1c00(size=256) memory:44000000-47ffffff  memory:48000000-4bffffff
        *-firewire
             description: FireWire (IEEE 1394)
             product: PCI4510 IEEE-1394 Controller
             vendor: Texas Instruments
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=firewire_ohci latency=128 maxlatency=4 mingnt=2
             resources: irq:18 memory:d0000000-d00007ff memory:d0004000-d0007fff
        *-network:0
             description: Wireless interface
             product: RT2500 Wireless 802.11bg
             vendor: Ralink corp.
             physical id: 15
             bus info: pci@0000:00:15.0
             logical name: wlan0
             version: 01
             serial: 00:10:60:63:4a:2f
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical wireless
             configuration: broadcast=yes driver=rt2500pci  driverversion=3.11.0-12-generic firmware=N/A latency=128 link=no  multicast=yes wireless=IEEE 802.11bg
             resources: irq:18 memory:d0008000-d0009fff
        *-pci:1
             description: PCI bridge
             product: M5249 HTT to PCI Bridge
             vendor: ULi Electronics Inc.
             physical id: 19
             bus info: pci@0000:00:19.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci ht normal_decode bus_master cap_list
             resources: ioport:a000(size=8192) memory:b8000000-bfffffff memory:88000000-8fffffff
        *-network:1
             description: Ethernet interface
             product: ULi 1689,1573 integrated ethernet.
             vendor: ULi Electronics Inc.
             physical id: 1b
             bus info: pci@0000:00:1b.0
             logical name: eth0
             version: 50
             serial: 00:40:d0:87:8f:60
             capacity: 100Mbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes  driver=uli526x driverversion=0.9.3 latency=128 link=no maxlatency=40  mingnt=20 multicast=yes port=MII
             resources: irq:20 ioport:e000(size=256) memory:d000a000-d000a0ff
        *-usb:0
             description: USB controller
             product: USB 1.1 Controller
             vendor: ULi Electronics Inc.
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=64 maxlatency=80
             resources: irq:17 memory:f8002000-f8002fff
        *-usb:1
             description: USB controller
             product: USB 1.1 Controller
             vendor: ULi Electronics Inc.
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=64 maxlatency=80
             resources: irq:18 memory:f8003000-f8003fff
        *-usb:2
             description: USB controller
             product: USB 2.0 Controller
             vendor: ULi Electronics Inc.
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=128 maxlatency=32 mingnt=16
             resources: irq:23 memory:40001000-400010ff
        *-multimedia
             description: Multimedia audio controller
             product: M5455 PCI AC-Link Controller Audio Device
             vendor: ULi Electronics Inc.
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 20
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_intel8x0 latency=128 mingnt=64
             resources: irq:23 ioport:e100(size=256) memory:d000b000-d000bfff
        *-communication UNCLAIMED
             description: Modem
             product: M5457 AC'97 Modem Controller
             vendor: ULi Electronics Inc.
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 20
             width: 32 bits
             clock: 33MHz
             capabilities: pm generic cap_list
             configuration: latency=0 mingnt=64
             resources: memory:d000c000-d000cfff ioport:e200(size=256)
        *-isa
             description: ISA bridge
             product: PCI to LPC Controller
             vendor: ULi Electronics Inc.
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 31
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0 maxlatency=24 mingnt=1
        *-bridge UNCLAIMED
             description: Bridge
             product: M7101 Power Management Controller [PMU]
             vendor: ULi Electronics Inc.
             physical id: 1e.1
             bus info: pci@0000:00:1e.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bridge
             configuration: latency=0
        *-ide
             description: IDE interface
             product: M5229 IDE
             vendor: ULi Electronics Inc.
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: c7
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=pata_ali latency=32
             resources: irq:255 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:1100(size=16)
     *-pci:1
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0
     *-scsi:0
          physical id: 3
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD600UE-22HC
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 09.0
             serial: WD-WXEZ05327384
             size: 55GiB (60GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=000d0945
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: 223e8b6f-79c6-4dad-ac54-c4b893f0a093
                size: 14GiB
                capacity: 14GiB
                capabilities: primary bootable journaled  extended_attributes large_files huge_files dir_nlink extents ext4 ext2  initialized
                configuration: created=2013-10-18 00:29:02  filesystem=ext4 lastmountpoint=/ modified=2013-10-21 01:51:26  mount.fstype=ext4  mount.options=rw,relatime,errors=remount-ro,data=ordered  mounted=2013-10-21 01:45:21 state=mounted
           *-volume:1
                description: EXT4 volume
                vendor: Linux
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                logical name: /home
                version: 1.0
                serial: 0b507dbf-06cf-4edd-892d-db381fd960b0
                size: 38GiB
                capacity: 38GiB
                capabilities: primary journaled extended_attributes  large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2013-10-18 00:29:07  filesystem=ext4 lastmountpoint=/home modified=2013-10-21 01:51:28  mount.fstype=ext4 mount.options=rw,relatime,data=ordered  mounted=2013-10-21 01:51:28 state=mounted
           *-volume:2
                description: Linux swap volume
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                version: 1
                serial: 518ad65f-ba2b-4e0d-a055-74f26121fad9
                size: 2047MiB
                capacity: 2047MiB
                capabilities: primary nofs swap initialized
                configuration: filesystem=swap pagesize=4096
     *-scsi:1
          physical id: 5
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD writer
             product: DVD+-RW ND-6650A
             vendor: _NEC
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: 1.62
             serial: [
             capabilities: removable audio cd-r cd-rw dvd dvd-r
             configuration: ansiversion=5 status=nodisc
  *-battery
       description: Lithium Ion Battery
       physical id: 1
       slot: BACK
       configuration: voltage=11.1V
  *-remoteaccess UNCLAIMED
       vendor: Manufacturer Name
       physical id: 2
  *-network
       description: Wireless interface
       physical id: 3
       bus info: usb@1:1
       logical name: wlan1
       serial: 00:1f:1f:a8:e5:21
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb  driverversion=3.11.0-12-generic firmware=0.29 ip=x.x.x.x link=yes  multicast=yes wireless=IEEE 802.11bgn


```

Please, see the attached 3 pictures

When I turn it ON, there is a Beed Sound every 1-2 second and then when it is on the Desktop, beep stops.
As you can see, the screen is not clear and I am afraid this is a hardware issue but thought to double check before give my neighbor the bad news!

Thank you

---

### Post by philinux on 2013-12-09
Looks like gpu problem for sure.

Search for the motherboard model beep codes.

Maybe try take out gpu and reseat a couple of times.

---

### Post by amjjawad on 2013-12-11
> **philinux said:**
> Maybe try take out gpu and reseat a couple of times.

Hi and thanks for posting!

How to do that? this is not a PC/Desktop but a Laptop and I personally have never done that before. I know how to play with RAMs and HDDs but haven't played with a 'Laptop Graphics Card' before :)

Thank you!

---

### Post by amjjawad on 2013-12-16
Could it be [**the overheating problem**]("http://ubuntuforums.org/showthread.php?t=2182281") that laptop has did kill the graphics card?

---

### Post by amjjawad on 2013-12-26
Hi,

After two weeks or more, I decided to give that laptop another chance, hopefully I can do something. So, I decided to take it out with my 'air blower' to clean it.


[ATTACH=CONFIG]248914[/ATTACH]



After that, came back in, plugged the charger and turn it on. To me shock and surprise, the laptop seems to be fine now:

[ATTACH=CONFIG]248913[/ATTACH]

Am I seeing that correctly?

That was a wonderful news.

I installed 'lm-sensors' and 'xsensors' and did:

```
apt-get update && apt-get upgrade -y && apt-get dist-upgrade -y
```

Temp is between: 45c - 52c (now, it is 52c).

BAD NEWS:
The screen went back to that purple or pink colours and the Pixelation is back :(

The laptop still working though. Still updating the system. But, the screen is bad.

It is either a hardware issue and if so, I am afraid I can't put a smile on my neighbour's face. She was so happy and dazzled when her old machine breathed Linux 2 months ago and was so fast. Now, I guess she will be sad.

Or
It is an overheating issue that is causing this behaviour.

I removed the laptop from my rug that you see on the above picture and kept it on the floor. The Screen back to normal. Few mins and it is bad again.

I touched it, it is not hot. Temp is below 55c.

What could be the reason? any thoughts? 

Help is highly appreciated!

---

### Post by amjjawad on 2013-12-27
Hi again,

I thought to do a RAM test and I found this:

[ATTACH=CONFIG]248942[/ATTACH]


I have two old RAM (256MB both).
The ones on this picture (below) with orange label/sticker are the RAM on that Laptop. The one with white sticker is mine and the one now on the Laptop where the above picture is testing (256MB RAM) is mine.

[ATTACH=CONFIG]248943[/ATTACH]

I have checked the 4 each on its own. ALL gave me the same screen as you can see on the first picture.

I have never seen that before on my own machines. And, I am wondering why all the RAMs I am using are giving me the same screen? some with 8 errors and some with 81? could it be all the RAMs are bad? or there is something else?

---

### Post by amjjawad on 2013-12-29
Update:

For two days now, I have been testing the RAMs and it gives me many errors the moment the test starts. When I press "C" for 'Configuration' and choose one of the available options then "7" for restart the test, all the errors disappear.

Was just running a test for both RAMs (total 1GB) which last for +9 hours without any errors and the screen was crystal clear.

I thought to stop it, login to the desktop and test the system and:

[ATTACH=CONFIG]249009[/ATTACH]

I am sure you can see:
CPU at 100%
and Temp is 70c

Once it started to get high, the issue is back.

The machine was perfect for two days. Once I tested Firefox with ONE opened tab (YouTube), this is what happened.

WHAT is going on?

1- Software Issue?
2- Overheating Issue?
3- Hardware Issue?

I am out of ideas :/

---

### Post by amjjawad on 2013-12-29
[ATTACH=CONFIG]249012[/ATTACH]

1- Firefox Closed
2- Temp dropped down at once
3- Screen became better with few pixelation and these funny colours
4- Refreshed the wallpaper + the two running apps that you can see on the screenshot
5- everything is back to normal

Most likely, it is a software issue that is causing the overheating which is causing the funny screen with weird colours.

I don't think at all it is a hardware failure because if it is, it should not be fine the very moment I close Firefox.

What do you suggest?

---

### Post by sudodus on 2013-12-29
Well, maybe a combination. If the cpu is working hard, there is not enough cooling.

- Are all the fans working?
- Have you removed dust from the inside of the computer?
- Are the incoming and outgoing openings for air clear, so that the air can circulate?
- Maybe you need new cooling paste between the cpu and the cooler.
- Can the computer be moved to a cooler place (no direct sun etc)?
- Maybe you can add a fan.

---

### Post by amjjawad on 2013-12-30
Hi my friend and thanks to jump in, finally someone else is posting :D I was kind of having the feeling that I am talking to myself only!

> **sudodus said:**
> Well, maybe a combination. If the cpu is working hard, there is not enough cooling.

- Are all the fans working?


There is only one fan and yes, it is working.

> - Have you removed dust from the inside of the computer?
Definitely :)
Check please [my previous post]("http://ubuntuforums.org/showthread.php?t=2192715&p=12883236#post12883236")!

> - Are the incoming and outgoing openings for air clear, so that the air can circulate?
I know that trick so half of the base of the laptop is actually on the air (I am putting it on a small table) and the other half is sitting on the table. So, there should be enough circulation.
In fact, I even removed the cover (when I was testing the RAMs) and the stuff inside were super hot that I couldn't touch for a second. However, the screen was fine. Note that the screen is funny NOT only on Lubuntu BUT also when I turn the machine ON on the POST stage where there is NO OS is loaded still. However, that was before I clean it with my air blower. After I did clean it, it became fine but after a while on the desktop, the issue is back.

>  - Maybe you need new cooling paste between the cpu and the cooler.
I don't know!

>  - Can the computer be moved to a cooler place (no direct sun etc)?
It is already in a place where the room temp is around 25c-27c max and there is a fan I keep running so there is enough air on the room.

> - Maybe you can add a fan.
Add a fan? how to add a fan? you mean use laptop cooler? that thing attached to the base of the laptop? I am not sure this will help.

I have turned the laptop one a while ago. The Temp was below 40C.

You know, Lubuntu is still turns the monitor off after 10 mins so when it went off, I moved the cursor and I noticed the temp has jumped to above 50C and the issue is back.

Computer (Laptop) is totally idle. I am not running anything except System Monitor and XSensors

Thank you!

---

### Post by sudodus on 2013-12-30
[Sorry if I repeat what was written in earlier posts]

- Have you tried running the computer in text mode (to test if it is an issue with the graphics chip)?

- Is there a difference between versions (12.04 LTS versus 13.10)? Or some completely different distro?

- Of course it could also be that some electronic component is failing and causing the overheating.

---

### Post by amjjawad on 2014-01-11
> **sudodus said:**
> [Sorry if I repeat what was written in earlier posts]

- Have you tried running the computer in text mode (to test if it is an issue with the graphics chip)?

It happened when I was testing the RAM with the memory test specially when the machine got hot.

>  - Is there a difference between versions (12.04 LTS versus 13.10)? Or some completely different distro?
Lubuntu 13.10 was the only system I tried and installed. I don't want to format and re-install anything else. Lubuntu as you know has 'no' LTS version anyway.

> - Of course it could also be that some electronic component is failing and causing the overheating.
Why would that happen when the temp is above 50c ???

---

### Post by amjjawad on 2014-02-20
Hi,

I'm sorry, I forgot to update this thread.

_**Summary or wrap up post:**_
1- The issue is back again.
2- The owner of the laptop didn't wish to carry on with any further step. She said "Don't waste more time on it. You have done already more than what you supposed to do." and she thanked me for everything and decided to leave it as it is.
3- I insisted to keep trying perhaps with different system or older Kernel version (in case) - I was thinking about Xubuntu 12.04.3 but she didn't wish that.

So, I guess I shall mark this as SOLVED but PLEASE NOTE it is NOT solved. I have done all what I could when the laptop was with me and that didn't help.

Thank you for everything!

---

