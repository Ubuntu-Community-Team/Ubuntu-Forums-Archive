---
title: "Toshiba Satellite A60"
date: 2014-03-08
forum: General Help
---

### Post by amjjawad on 2014-03-08
Hi,

I got a very old laptop from a friend who would like to try Linux after I have talked about it a lot.

The laptop is:

```
lubuntu
    description: Portable Computer
    product: Satellite A60
    vendor: TOSHIBA
    version: PSA60E-00H01
    serial: 84639689G
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: administrator_password=disabled boot=normal chassis=portable power-on_password=disabled uuid=8D91C860-D549-11D8-A70E-00A0D1DDEF02
  *-core
       description: Motherboard
       product: Portable PC
       vendor: TOSHIBA
       physical id: 0
       version: Version A0
       serial: 0000000000
     *-firmware
          description: BIOS
          vendor: TOSHIBA
          physical id: 0
          version: Version 1.40
          date: 07/01/2004
          size: 84KiB
          capacity: 448KiB
          capabilities: isa pci pcmcia pnp upgrade shadowing cdboot socketedrom pcmciaboot edd int13floppynec int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi agp zipboot smartbattery netboot
     *-cpu
          description: CPU
          product: Mobile Intel(R) Pentium(R) 4     CPU 2.80GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.2.9
          slot: mFCPGA
          size: 2793MHz
          capacity: 3200MHz
          width: 32 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pebs bts cid xtpr cpufreq
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 8KiB
             capacity: 32KiB
             capabilities: burst pipeline-burst internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: burst pipeline-burst external write-back
     *-memory:0
          description: System Memory
          physical id: 11
          slot: System board or motherboard
          capacity: 1536MiB
        *-bank:0
             description: DIMM DDR EDO 266 MHz (3.8 ns)
             physical id: 0
             slot: DRAM Slot 0
             size: 1GiB
             width: 64 bits
             clock: 266MHz (3.8ns)
        *-bank:1
             description: DIMM DDR Synchronous 266 MHz (3.8 ns)
             physical id: 1
             slot: DRAM Slot 1
             size: 256MiB
             width: 64 bits
             clock: 266MHz (3.8ns)
     *-memory:1 UNCLAIMED
          description: Video Memory
          physical id: 12
          slot: System board or motherboard
          capacity: 64MiB
     *-memory:2 UNCLAIMED
          description: Flash Memory
          physical id: 13
          slot: System board or motherboard
          capacity: 512KiB
     *-memory:3 UNCLAIMED
          description: Cache Memory
          physical id: 14
          slot: System board or motherboard
          capacity: 1MiB
     *-memory:4 UNCLAIMED
          physical id: 1
     *-memory:5 UNCLAIMED
          physical id: 2
     *-pci
          description: Host bridge
          product: RS250 Host Bridge
          vendor: Advanced Micro Devices, Inc. [AMD/ATI]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 05
          width: 32 bits
          clock: 66MHz
          configuration: driver=agpgart-ati latency=64
          resources: irq:0 memory:b0000000-b3ffffff memory:b4000000-b4000fff
        *-pci:0
             description: PCI bridge
             product: RS200/RS250 AGP Bridge
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:c000(size=8192) memory:e0000000-efffffff memory:a0000000-afffffff
           *-display
                description: VGA compatible controller
                product: RS250 [Mobility Radeon 7000 IGP]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: agp agp-2.0 pm vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=64 mingnt=8
                resources: irq:16 memory:a0000000-a7ffffff ioport:c000(size=256) memory:e0000000-e000ffff memory:a8000000-a801ffff
        *-usb:0
             description: USB controller
             product: OHCI USB Controller #1
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=64
             resources: irq:19 memory:f0001000-f0001fff
        *-usb:1
             description: USB controller
             product: OHCI USB Controller #2
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=64
             resources: irq:19 memory:f0002000-f0002fff
        *-usb:2
             description: USB controller
             product: EHCI USB Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci-pci latency=64
             resources: irq:19 memory:f0003000-f0003fff
        *-serial
             description: SMBus
             product: SMBus
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 18
             width: 32 bits
             clock: 66MHz
             configuration: driver=piix4_smbus latency=0
             resources: irq:0 ioport:e000(size=16) memory:f0000000-f00003ff
        *-ide
             description: IDE interface
             product: Dual Channel Bus Master PCI IDE Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=pata_atiixp latency=64
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:8070(size=16)
        *-isa
             description: ISA bridge
             product: Advanced Micro Devices, Inc. [AMD/ATI]
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:1
             description: PCI bridge
             product: IXP200 3COM 3C920B Ethernet Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
             resources: ioport:a000(size=8192) memory:d0000000-dfffffff memory:90000000-9fffffff
           *-pcmcia
                description: CardBus bridge
                product: PCI1410 PC card Cardbus Controller
                vendor: Texas Instruments
                physical id: 6
                bus info: pci@0000:02:06.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: irq:19 memory:d4000000-d4000fff ioport:a400(size=256) ioport:a800(size=256) memory:90000000-93ffffff memory:d8000000-dbffffff
           *-network
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 7
                bus info: pci@0000:02:07.0
                logical name: eth0
                version: 10
                serial: 00:a0:d1:dd:ef:02
                size: 10Mbit/s
                capacity: 100Mbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
                resources: irq:18 ioport:a000(size=256) memory:d0008000-d00080ff
           *-firewire
                description: FireWire (IEEE 1394)
                product: TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
                vendor: Texas Instruments
                physical id: a
                bus info: pci@0000:02:0a.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=64 maxlatency=4 mingnt=2
                resources: irq:19 memory:d0000000-d00007ff memory:d0004000-d0007fff
        *-multimedia
             description: Multimedia audio controller
             product: IXP150 AC'97 Audio Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=snd_atiixp latency=64 mingnt=2
             resources: irq:17 memory:f0000400-f00004ff
        *-communication
             description: Modem
             product: IXP AC'97 Modem
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.6
             bus info: pci@0000:00:14.6
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: generic bus_master
             configuration: driver=snd_atiixp_modem latency=64 mingnt=2
             resources: irq:17 memory:f0000500-f00005ff
     *-scsi:0
          physical id: 3
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: IC25N040ATMR04-0
             vendor: Hitachi
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: MO2O
             serial: MRG2DFKBD0GMNP
             size: 37GiB (40GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=000d9cd6
           *-volume
                description: Linux filesystem partition
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                version: 1.0
                serial: d6e64a03-4602-4418-95ff-314f0745e07a
                size: 10GiB
                capacity: 10GiB
                capabilities: primary extended_attributes large_files ext2 initialized
                configuration: filesystem=ext2 modified=2014-03-08 09:12:21 state=clean
     *-scsi:1
          physical id: 5
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD reader
             product: DW-224E-B
             vendor: TEAC
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             logical name: /cdrom
             version: M.6A
             capabilities: removable audio cd-r cd-rw dvd
             configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,noatime state=mounted status=ready
           *-medium
                physical id: 0
                logical name: /dev/cdrom
                logical name: /cdrom
                capabilities: partitioned partitioned:dos
                configuration: mount.fstype=iso9660 mount.options=ro,noatime signature=69d12c62 state=mounted
              *-volume UNCLAIMED
                   description: Hidden HPFS/NTFS partition
                   physical id: 1
                   capacity: 695MiB
                   capabilities: primary bootable hidden
  *-battery
       product: DR36
       vendor: Duracell
       physical id: 1
       version: 01/06/97
       serial: 0042
       slot: Smart Battery Conn J37
       configuration: voltage=0.0V
  *-remoteaccess UNCLAIMED
       vendor: Manufacturer Name
       physical id: 2


```

It does not support booting from USB so I'm using the LiveCD of Lubuntu 13.10 and have tried before Ubuntu 10.04 LiveCD (yes, I know, was just trying to see what will happen).

I can do some few steps then the laptop is 'frozen' and does not do anything unless I turn it OFF by pressing the Power Button.

I just managed before I post this to create new partition table using GParted and created the 3 needed partitions:
Root
Swap
Home

Once I clicked on 'Install Lubuntu 13.10', the whole machine is frozen now.

When I tried to skip "Try without installation" and chose "Install Lubuntu", it was frozen right from the first moment it showed the wallpaper of the system with the circle as a mouse cursor.

So, with "Try without Installation" and "Install Lubuntu", I got the same thing. Something is stopping this machine to breathe Linux.

Yes, same happened with me with Ubuntu 10.04 LiveCD even before I click any thing.

What could be the reason? 
The machine has enough memory to run any Ubuntu Installer for any flavour so not sure what is wrong?

Thoughts?

Thank you :)

---

### Post by mörgæs on 2014-03-08
Hi, good to see that the 'convert to Lubuntu' project is still going strong.

I only see one partition and it's ext2. I doubt that's what you intended. 

It is not uncommon that the standard ISO does not work on old iron. I suggest trying the [alternate]("https://help.ubuntu.com/community/Lubuntu/Alternate_ISO") and / or [minimal ISO]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall") and letting Lubuntu take care of partitioning during installation.

---

### Post by amjjawad on 2014-03-08
> **mörgæs said:**
> Hi, good to see that the 'convert to Lubuntu' project is still going strong.

Hi my good friend :)

I see you change the title of this thread? no problem, maybe it is better.

No, my project is NOT to convert to Lubuntu but it is all about the whole family ;)

[StartUbuntu]("https://wiki.ubuntu.com/StartUbuntu")
[StartUbuntu in real life]("http://amjjawad.blogspot.com/2014/01/2014-report-project-convert-my.html")

Lubuntu is just one of the options we have and use ;)


>  I only see one partition and it's ext2. I doubt that's what you intended. 
Oh, I managed after that to create 3 but still can't install or go further.

> It is not uncommon that the standard ISO does not work on old iron. I suggest trying the [alternate]("https://help.ubuntu.com/community/Lubuntu/Alternate_ISO") and / or [minimal ISO]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall") and letting Lubuntu take care of partitioning during installation.

1.2GB RAM is very very good for Ubuntu Installer :)
It failed with Ubuntu 10.04 LiveCD as well. 

I'm wondering if this is an issue with the installer? because while I was trying to do a RAM test from the LiveCD, the machine was turned off after 30 mins or less form running the test.

I couldn't yet figured out whether it is the installer? or the machine itself? if you know what I mean.

Thank you!

---

### Post by mörgæs on 2014-03-08
I change a lot of thread titles, trying to make them short and exact and suitable for a mobile device with a small screen. 

There are many reasons for the standard ISO to fail, and lack of memory is just one of them. I only use it for special purposes like rescuing files from a wrecked system; when installing I always begin with one of the two ISO's I mentioned. 

It's a pity that the alternate was shut down for the other Buntus. 

> **amjjawad said:**
> I couldn't yet figured out whether it is the installer? or the machine itself? 


There's only one way to find out...

---

### Post by amjjawad on 2014-03-08
> **mörgæs said:**
> I change a lot of thread titles, trying to make them short and exact and suitable for a mobile device with a small screen. 
Hi,

While I appreciate that, I don't really think that the current title can really tells what is going on inside that thread :)
But that is your call, that is your job, I have nothing to do about it ;)

> There are many reasons for the standard ISO to fail, and lack of memory is just one of them. I only use it for special purposes like rescuing files from a wrecked system; when installing I always begin with one of the two ISO's I mentioned. 

It does not support booting from USB, that is why I had to go for the old school stuff :)

>  It's a pity that the alternate was shut down for the other Buntus. 
Well, I don't know ... maybe it is, maybe it is not.


> There's only one way to find out...
My current only way is to take the HDD out and go through the same headache I had with [this]("http://ubuntuforums.org/showthread.php?t=1590614").

Problem is, I have no time to go and keep trying so many alternatives. 

I will try to download [the Alternate]("https://help.ubuntu.com/community/Lubuntu/Alternate_ISO") and waste one more CD :P
If that didn't help, I will take the HDD out and plug it to another machine.

Thank you!

P.S.
Unless you have a better suggestion ;)

---

### Post by 3rdalbum on 2014-03-08
Freezes are often caused by bad RAM. If this computer is from 2004 its RAM sticks may have reaches the end of their lives.

---

### Post by amjjawad on 2014-03-08
> **3rdalbum said:**
> Freezes are often caused by bad RAM. If this computer is from 2004 its RAM sticks may have reaches the end of their lives.

Hi and thanks for posting :)

I have this RAM for 'different' machine and it works and the machine works.

[ATTACH=CONFIG]250954[/ATTACH]

I tried to test the RAM for this machine (Toshiba A60) from the LiveCD of Lubuntu 13.10 but the machine turned off by itself?! I don't know why?

---

### Post by upchucky on 2014-03-08
I would suggest trying to live boot an older knoppix cd, I think version 5.0 is compatable with older toshibas. if knoppix does boot then it is a hardware issue that lubuntu does not like.
All is not lost though, I struggled with an older toshiba and because they do funky things with the monitors I found that I could not run any modern distros on it.
I, through trial and error found that I could not install anything higher than ubuntu 11.04 on a toshiba 2410 CDS. that toshiba was new in 2004. Once I discovered that an upgrade would stop the toshiba from working I set it to never upgrade and it has been working perfectly ever since.
Search the forums for the "ugly black bar on a toshiba display" there is plenty of information about the monitor problems with toshibas and the way to get them to work.

---

### Post by amjjawad on 2014-03-08
Hi,

As I thought and expected, it is the hardware not the LiveCD.

I took the HDD out, plugged it to my P4 desktop, installed Lubuntu 13.10, put the HDD back inside the Toshiba machine.

It worked for 30mins or maybe more then stopped again.

Turned it ON, tried to check the RAM for errors but yet again, while it is testing, the machined turned off all by itself.

Could be a RAM failure or could be something else ... again, didn't yet figure it out.

The only difference I noticed that it worked this time for longer time than when I tried to use the LiveCD. But the result is the same, frozen machine.

---

### Post by 3rdalbum on 2014-03-08
The screenshot you posted of MemTest shows failed RAM. All those red lines.

---

### Post by amjjawad on 2014-03-09
> **3rdalbum said:**
> The screenshot you posted of MemTest shows failed RAM. All those red lines.

Hi,

Yes, my friends on facebook told me that too. But [the machine]("http://phillw.net/hardware/p7x41Lgx") that I'm using that RAM on is working without any issue whatsoever.

As for Toshiba Satellite A60 - this thread - it is not allowing me to test the RAM at all.
Every time I do that, it turns off after 10 mins or so.

I posted that picture about the RAM (for the other machine) as I'm wondering how come with all these errors, that other machine works?

And, why I can't test the RAM on Toshiba laptop?

I think the only way to rule out the RAM issue is to use another RAM. Not sure if I have a spare stick that could work on that machine ...

---

### Post by Topsiho on 2014-03-09
The memory test failed, as is obvious from the screen picture that you showed. It checks also with that your RAM-test stops after a while. If your RAM is OK that doesn't happen, as far as I know.
That means that the RAM is bad, OR that the slot in which the RAM sits is bad, OR the motherboard is bad.
If the RAM is OK in another computer (as I seem to understand from your previous post), that means the slot or the MB are bad, OR that the top part of the RAM has not been used so far, in that other computer, and the defect is in that top part.

Sometimes it helps if you blow the slot clean with compressed air, and try again. If the slot is dirty.

I was also thinking of the possibility that your processor is non-pae (physical address extension), and so not fit for the modern Ubuntu's. I have a A50, and that laptop has this problem, but runs Xubuntu 12.04 quite well. But then you would get a message telling you that you need pae.

Topsiho

---

### Post by amjjawad on 2014-03-09
Hi and thanks for posting :)

> **Topsiho said:**
> The memory test failed, as is obvious from the screen picture that you showed. 
I'm sorry if that was so confusing but I have explained on my previous post about that picture I posted. The picture for that RAM test is for different RAM stick. The picture I posted is not for the RAM stick of the Toshiba laptop.

Why then I posted it?
I did that to say or explain my point - which is:
Even though the RAM test shows many error, the RAM stick was working fine.

What this has to do with this thread?
I'm trying to say if 'different' RAM on 'different' machine is working fine so ... could it be that Toshiba Laptop's problem is a bad RAM as well?


> It checks also with that your RAM-test stops after a while. If your RAM is OK that doesn't happen, as far as I know.
I have done that test many times on so many different RAM sticks and usually, the test last for 12 hours or more without the machine turning itself off. Yes, some of these tests were showing many errors, just like the picture I posted it.

So, not sure what is going on?

>  That means that the RAM is bad, OR that the slot in which the RAM sits is bad, OR the motherboard is bad.
Could be, not sure ...

> 
If the RAM is OK in another computer (as I seem to understand from your previous post), that means the slot or the MB are bad, OR that the top part of the RAM has not been used so far, in that other computer, and the defect is in that top part.
No, I have not tried Toshiba's RAM on different machine yet. Not sure if I can do that as there are different types of RAMs. And, No, I didn't used different RAM on the Toshiba Laptop yet for the same reason. I have to look around in case I have a spare RAM and will report back.


>  Sometimes it helps if you blow the slot clean with compressed air, and try again. If the slot is dirty.
I will look into this too.

> 
I was also thinking of the possibility that your processor is non-pae (physical address extension), and so not fit for the modern Ubuntu's. I have a A50, and that laptop has this problem, but runs Xubuntu 12.04 quite well. But then you would get a message telling you that you need pae.

Topsiho

Well, as per the first post and the output of:

```
sudo lshw
```

It is PAE and indeed, if it was a NON-PAE, there should be an error message which I never seen so it is PAE machine.

Thank you!

---

### Post by amjjawad on 2014-03-09
[ATTACH=CONFIG]250991[/ATTACH]

This is the RAM stick inside the Toshiba Laptop.

I found another old RAM stick inside my drawer but it is 256MB RAM.

Now, I'm running the Memory Test on the Toshiba Laptop with different RAM (256MB) not the one shown above (which belongs to the Toshiba laptop).

There is something weird ... I'm 100% sure the RAM stick which I just replaced with the above one on the picture is 256MB but the memory test is showing:
Memory: 448M - 567 MB/s

Same when I was testing the above RAM stick on the picture (which is 1GB). It was showing 1.2GB RAM instead of just 1GB.

What is going on? is there a hidden RAM on that machine? 

I will take a picture to the laptop screen and will post it.

Edit:

[ATTACH=CONFIG]250992[/ATTACH]

This is for the replacement RAM - was in my drawer - (256MB) which is different from the one on the first picture (which belongs to the Toshiba).
Note that it shows 448MB NOT 256MB!

---

### Post by mörgæs on 2014-03-09
If you look at the initial lshw you will notice that the computer originally had two memory sticks: One 1 GB and another 256 MB. 

If you remove one stick, add 256 MB and have 512 (more or less) left it means that you removed the 1 GB one. There's nothing strange about it.

---

### Post by amjjawad on 2014-03-09
> **mörgæs said:**
> If you look at the initial lshw you will notice that the computer originally had two memory sticks: One 1 GB and another 256 MB. 

If you remove one stick, add 256 MB and have 512 (more or less) left it means that you removed the 1 GB one. There's nothing strange about it.

Hi,

Yes, I know and I noticed. I'm confused because I can't find the other RAM? I looked around but couldn't find any ... that is why it is strange :)

By the way, the RAM test for the 256MB Stick that I put to replace the 1GB Stick ... is still working ... 1 hour and 15 mins and the machine is not yet off.

---

### Post by amjjawad on 2014-03-09
Hi,

5 hours and 33 mins - Pass 10 - no errors found. The machine didn't turn off by itself at all.

So, it appears that the 1GB RAM stick has a problem.

I will try to stop the RAM Test and put the 1GB RAM stick back in. If the machine will be frozen and/or turned off by itself, then it means we found out what is wrong.

Thank you!

---

### Post by Topsiho on 2014-03-09
Looks like the 1 GB stick is bad.
You exchanged it for a 256 MB stick, having another 256 MB stick present, adds to 512 MB total (which is not enough for Ubuntu, but probably enough for Lubuntu or Xubuntu).
Your memory test shows 448 MB, which really is 448 MiB (binary megabytes):
This is because manufacturers reckon with GB's and MB's in the decimal system: kilo = 1000, mega = 10^6 and giga is 10^9, while in computer science one reckons in binary: kilo = 2^10 = 1024, mega = 10^20 = 1024^2, and giga=2^30 = 1024^3. Manufacturers want bigger numbers ...

So your 512 MB really is 512/1.024/1.024 = 488 MiB

The memory test shows 448 MiB, maybe 40 Mib are used by the graphics card?

Anyway: you found the cause of your problem :)

Topsiho

---

### Post by amjjawad on 2014-03-09
Hi,

Okay, this is very frustrating and a huge headache.

The laptop is yet again, frozen.

What is going on?
I can't find the other RAM ... not sure where is it ... that IF the RAM is the reason behind all this ... sigh!

---

### Post by mörgæs on 2014-03-09
Some common problems for the A60:
[http://www.laptoprepair101.com/laptop/2007/04/27/toshiba-satellite-a60-a65-problems/](http://www.laptoprepair101.com/laptop/2007/04/27/toshiba-satellite-a60-a65-problems/)

Does it also freeze with only the built-in memory?

---

### Post by amjjawad on 2014-03-09
> **mörgæs said:**
> Some common problems for the A60:
[http://www.laptoprepair101.com/laptop/2007/04/27/toshiba-satellite-a60-a65-problems/](http://www.laptoprepair101.com/laptop/2007/04/27/toshiba-satellite-a60-a65-problems/)

Does it also freeze with only the built-in memory?

Hi and thanks for posting :)

I have removed the external RAM (256MB Stick), turn the machine ON, ran Memtest86 and it is working now.

It is reporting 192MB - 567 MB/s

Will report back ...

---

### Post by walterorlin on 2014-03-09
I am thinking that could be the slot on the motherboard in the laptop for external ram may be bad which is not good. Testing the 1gb ram in another comp did it pass?

---

### Post by amjjawad on 2014-03-09
> **walterorlin said:**
> I am thinking that could be the slot on the motherboard in the laptop for external ram may be bad which is not good. Testing the 1gb ram in another comp did it pass?

Hi,

Sadly, I don't have any laptop around here that accept that 1GB RAM. It is old enough that the machines I have around can't accept that RAM ... so, I can't test it on different machine :(

By the way, Pass 2 now (35mins) and there is no error for the built-in RAM (192MB).

---

### Post by sudodus on 2014-03-09
I read mörgæs's link with some common problems for this computer.

Bad RAM is (was?) an issue. How is it working without the bad RAM stick?

Another issue might be the graphics card, old Radeon cards are not always well supported.

---

### Post by amjjawad on 2014-03-10
Good Morning, my friend :)

Thanks for posting!

> **sudodus said:**
> I read mörgæs's link with some common problems for this computer.

Bad RAM is (was?) an issue. How is it working without the bad RAM stick?

I did read that link. The only thing that I didn't try yet is cleaning the fans, just in case it is an overheating issue.

As for the RAM, just like I mentioned on my previous post, I'm now scanning the RAM (the internal hidden one - 192MB) using Memtest86 and the last test was clear without any errors, I'm doing it again this morning :)

> Another issue might be the graphics card, old Radeon cards are not always well supported.
Graphics Card could cause such total freeze that nothing can be done except turning the machine off from the power button? well, that is news to me.

It happened with Ubuntu 10.04 LiveCD
It happened with Lubuntu 13.10 LiveCD
It happened after installing Lubuntu 13.10

Not sure if trying another system will make any difference because I don't really think it is a software issue but that just a thought.

---

### Post by sudodus on 2014-03-10
If you want a simple answer you can get one: 'Something is wrong with the hardware'

---

### Post by amjjawad on 2014-03-10
> **sudodus said:**
> If you want a simple answer you can get one: 'Something is wrong with the hardware'

Hi,

Yes, I know ;) I figured that out :D
However, I couldn't really tell which part is bad?!

---

### Post by sudodus on 2014-03-10
> **amjjawad said:**
> Hi,

Yes, I know ;) I figured that out :D
However, I couldn't really tell which part is bad?!

Sometimes that is difficult. If you find errors with memtest it is easy. In principle it is 'easy' to tell if a plug-in unit is bad or not: Replace it and test! But errors caused by the CPU and mobo are hard to pin-point (unless you are prepared to replace the CPU). Some errors occur only at a certain temperature ...

---

### Post by amjjawad on 2014-03-10
> **sudodus said:**
> Sometimes that is difficult. If you find errors with memtest it is easy. In principle it is 'easy' to tell if a plug-in unit is bad or not: Replace it and test! But errors caused by the CPU and mobo are hard to pin-point (unless you are prepared to replace the CPU). Some errors occur only at a certain temperature ...

While the machine was testing the 192MB RAM, it turned off by itself.

I guess it is time to blow the dust and let's see if that will make any difference ... this machine is giving me hard time ...

---

### Post by amjjawad on 2014-03-11
Hi,

Cleaning the dust is done.
Laptop was working more than 12 hours on Memtest86 without turning off and there is no errors whatsoever.
I put the 1GB RAM (the one that was originally there) and there were no errors at all.

Now, I just turn it ON and once I logged in to Lubuntu 13.10 desktop, it is frozen again O_o

What is going on?
And, we thought it is a hardware issue?

I thought I solved the problem. After cleaning the dust, it appears that it was overheating but when I login now to the system (Lubuntu 13.10), it is frozen without doing anything at all.

Hmm, it is getting harder ...

---

### Post by amjjawad on 2014-03-11
Hi,

It is too late now and I'm fed up with the freezing thing and no real solution has been found yet. That said, I'm going to try another system and most likely older Kernel, in case that will make any difference. I have no idea whether this is a hardware issue or software? no matter what I do, the machine is frozen and Lubuntu 13.10 is not helping so I don't really have time to keep trying this or that.

I'm looking at Xubuntu 12.04.4 or something else.

Will keep you informed.

Thank you!

---

### Post by mörgæs on 2014-03-11
There are more things than memory sticks which can make the system crash. If you have a spare hard disk to swap it would be interesting to see if it makes a difference.

---

### Post by amjjawad on 2014-03-12
> **mörgæs said:**
> There are more things than memory sticks which can make the system crash. If you have a spare hard disk to swap it would be interesting to see if it makes a difference.

Hi, 

No, sadly I don't have a spare Hard Drive that could fit on that old machine which is using IDE not SATA. Either way, I don't have.

As per the tests, HDD is fine and healthy. 

I can't complain as the StartUbuntu Project in Real Life is giving me a huge experience; I'm learning a lot of stuff every single day. However, it is a headache, sometimes ... specially when you have no idea what is going on.

I've been busy today to covert two more machines to Ubuntu GNOME (total now 37 machines on my neighbourhood) and if this Toshiba will work fine, it would be no. 38 so I'm so much interested to get it up and running.

Can't think of better option than Xubuntu 12.04.4 and I just need to create LiveCD/DVD and try it.

Thank you!

P.S.
When I took the HDD out, put it into my PC and installed Lubuntu 13.10 there, it worked without any issue at all. Never frozen. So, I don't think it is the hard drive.

---

### Post by 3rdalbum on 2014-03-12
You mention that the computer "turns off" - that sounds unusual for all problems except overheating and power supply.

You say you've cleaned out the dust, well, I think it might be the power circuitry inside the computer that's at fault. If it's on the way out it might deliver a fluctuating level of voltage which will cause crashes. If the voltage level gets really low the computer might turn off.

Without a multimeter and opening up the computer case there's not really any way of being sure, unless you eliminate all other possibilities.

And yes, any piece of bad hardware (including graphics card) can potentially cause a crash or freeze. However, graphics cards themselves are not known to cause a computer to spontaneously shut off.

---

### Post by amjjawad on 2014-03-12
> **3rdalbum said:**
> You mention that the computer "turns off" - that sounds unusual for all problems except overheating and power supply.

You say you've cleaned out the dust, well, I think it might be the power circuitry inside the computer that's at fault. If it's on the way out it might deliver a fluctuating level of voltage which will cause crashes. If the voltage level gets really low the computer might turn off.

Without a multimeter and opening up the computer case there's not really any way of being sure, unless you eliminate all other possibilities.

And yes, any piece of bad hardware (including graphics card) can potentially cause a crash or freeze. However, graphics cards themselves are not known to cause a computer to spontaneously shut off.

Hi and thanks for posting :)

So, before I go ahead and wipe Lubuntu 13.10 and install Xubuntu 12.04.4, what do you suggest?

---

### Post by 3rdalbum on 2014-03-12
I would suggest giving up on this computer.

---

### Post by upchucky on 2014-03-15
I once had a toshiba that had poor sockets for the ram, i solved the loose ram socket problem by inserting layers of thin cardboard cut to size on top of the ram sticks and allowing pressure of the access door to hold the cardboard tight to the ram sticks against the sockets

---

### Post by amjjawad on 2014-04-24
Hi,

Now that 14.04 LTS is out, I'm going to give it one last chance. If nothing will happen, I will return this machine to its owner with a sorry message that nothing can be done.

Will report back once I have time to test 14.04 LTS on that machine.

---

### Post by piotrasbl on 2014-04-26
hi [SIZE=3][FONT=arial][COLOR=#000000][B]amjjawad

[/B][/COLOR][/FONT][/SIZE]Just to inform you, I got the very same Toshiba Satellite A60, with 768 MB of RAM :)
well, at leats it should be like that :)

I've been through serious downs with installation on this one, but today, finally, lubuntu 14.04 was successfully installed :)
What I have done was:
delete all the partitions with some old RIP Linux, set the BIOS for default settings, format whole drive into ext2 filesystem, placed CD with lubuntu...and it's fine now :)
Make sure you press F6 on boot screen ad choose first 3 options: acpi=off noapic nolapic.
After installation is completed, you may remove from grub apic=off option, but noapic and nolapic need to stay as those arrange proccessor management, and that is the cause of all those freezes.
I'm now installing all neccessary apps on that one, and it works really nice as for almost decade-old machine :)
Good luck man :)

---

