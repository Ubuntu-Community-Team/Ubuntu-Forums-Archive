---
title: "System program problem detected"
date: 2014-05-27
forum: General Help
---

### Post by happyytilton on 2014-05-27
These popup at boot up or when loging back on from sleep mode.
When going into sleep mode Firefox crashes... So am I to assume that these notifications are Firefox related?
[ATTACH=CONFIG]253485[/ATTACH]

---

### Post by whitesmith on 2014-05-27
By sleep you means suspend, n'est pas? Have you tried suspending from the live CD? Please let us know if that works. I get similar error messages sometimes on my production system without ill effects, but you say your machine crashes. That is definitely an ill effect, so let us know what happens when the live CD has a go at your system.  If the result is the same, you may be facing a hardware incompatibility. Regards.

---

### Post by happyytilton on 2014-05-27
> **whitesmith said:**
> By sleep you means suspend,

No not suspend, when I said sleep, I used a poor choice of words. Sorry about that.
It actually goes "dark screen", but a shake of the mouse brings the Desktop up.
Firefox has crashed, no launcher showing and the PW login screen is up. Once I enter my PW, that's when I see those "Sys Program Problem" msg's.

---

### Post by happyytilton on 2014-05-27
These happen when the desktop goes dark or... Perhaps it's a the FFx crash that's causing it.
I'm never around looking at it when it happens. In fact, it just happened again, between these last 2 posts, while I was getting some coffee.
I came back after 4-6 min and found it, dark screened. Shook the mouse, it lit up, entered the PW and the desktop comes up with 3 of those error screens showing.

---

### Post by whitesmith on 2014-05-27
I understand you now. First of all we need to know if FF is behind this error, so remove it (uninstall the application, in Windows-speak) from your system. You can do this by going to the Ubuntu Software Center and selecting Firefox Web Browser. This will bring up a Remove button. Click it. Put the machine through its paces for a while and see what errors, if any, appear. If all goes well, we've traced the source to FF. If errors continue, go back to the Software Center and Install FF again. Please post the result of this detective work. Stay with me and I'll help you as much as I possibly can.

---

### Post by happyytilton on 2014-05-27
> **whitesmith said:**
> I understand you now. First of all we need to know if FF is behind this error, so remove it (uninstall the application, in Windows-speak) from your system.

Doing it now... Hate to, but doing it. I can put it back easy enough.

---

### Post by happyytilton on 2014-05-27
OK, it's done and installed chromium in its place so I wouldn't have to boot back & forth to Windows.

---

### Post by happyytilton on 2014-05-27
OK, it's done and installed chromium in its place so I wouldn't have to boot back & forth to Windows.
But it is still doing it... I read the log of the error report and saw a mention of the NVIDIA GeForce 7900 card.
Will be reinstalling  FFx back for the next few minuets.

---

### Post by whitesmith on 2014-05-27
Nvidia 7900 is auto-detected, but requires a driver (we call it a module). This link gives info about your card: [http://ubuntuforums.org/archive/index.php/t-1014098.html](http://ubuntuforums.org/archive/index.php/t-1014098.html)
Try this as well: [http://www.ubuntuask.com/q/answers-list-of-supported-graphics-cards-for-ubuntu-10-04-lts-64bit-167752.html](http://www.ubuntuask.com/q/answers-list-of-supported-graphics-cards-for-ubuntu-10-04-lts-64bit-167752.html)
If all else fails, you might consider installing something known to be compatible. This is straight from the horse's mouth, so to speak:
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsNvidia](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsNvidia)
Video problems can make the mild-mannered become rabid. I'll keep checking back to see how you're progressing.

EDIT: If and when your problem is satisfactorily resolved, please use Thread Tools (top of page at the right) to mark the thread as closed. This will help others with similar issues. Thanks!

---

### Post by happyytilton on 2014-05-27
Here's a ScrSht of the driver that's in use.
It appears that's the proper one.

---

### Post by happyytilton on 2014-05-27
Is there any way to copy the error report from the next time and paste it here?

---

### Post by whitesmith on 2014-05-28
OK. Nvidia is well known for touchiness. Try their proprietary version. I'm signing out until around 1500 UTC Wednesday.

---

### Post by happyytilton on 2014-05-28
Don't know if this is of any help, but after being idle for 2hrs, this is what I found.
the only app I had open at the time was FFx.

---

### Post by whitesmith on 2014-05-28
At the very bottom I cannot read the final part, 
"kernel panic - not syncing: fatal exception in Internet
???????  ???????: panic occurred, switching back to text console"
What are the two words I can't make out?

This is some nutty hardware issue. Try running this command in a window (without FF running!)```
sudo lshw >hardware_list
``` Post back the contents of the hardware_list file between code tags, if it fits. If it doesn't let me know. Thanks.

---

### Post by happyytilton on 2014-05-28
At a Dr's appt right now. Should be home in ~1 1/2hrs and will try it then. 
I'll see if I can read that line when I get home,  or there could be another screen up like that one.

---

### Post by happyytilton on 2014-05-28
> **whitesmith said:**
> ???????  ???????: panic occurred, switching back to text console"
What are the two words I can't make out?

It's actually 3 sets of letters, "**drm_kms_helpe**r**:**". I zoomed in on the original .jpg, so I was just able to read them.
Will post back the results of your code in a few minuets.

---

### Post by happyytilton on 2014-05-28
With no apps running, except the normal startup apps... It didn't return anything:
```
hap@Maypop:~$ sudo lshw >hardware_list
[sudo] password for hap: 
hap@Maypop:~$
```

---

### Post by whitesmith on 2014-05-28
I wanted you to post the output from the file itself, not just run it. Also, try running FF in safe mode and tell me what happens then. Maybe the problem is coming from an add-on. To do that: Help->Restart With Add-ons Disabled. If problems go away you can enable add-ons one-by-one and find the offender, making the lshw step unnecessary. Give this a try first. Back around 1100 UTC Thursday.

---

### Post by happyytilton on 2014-05-29
> **whitesmith said:**
> I wanted you to post the output from the file itself, not just run it.
There was no output. That's why I pasted it into the post like that, so you could see there was no output.

> **whitesmith said:**
> Also, try running FF in safe mode...
We already tried running it with FFx uninstalled and it was still doing it, so trying it with FFx in safe mode isn't going to change the outcome.

---

### Post by whitesmith on 2014-05-29
I had you run the lshw command with redirection (>) to a file (hardware_list) so that output from lshw would not uselessly scroll by on your screen. What I wanted was for you to post the *output of the redirection *between code tags so that I could have a peek. My mistake, I thought you knew how to do that. Here's what you need to do: get the generated output (the hardware_list file) into a text editor (open hardware_list in Applications->Accessories->Text Editor). Click somewhere on the screen, then hit Ctrl-A and follow that by Ctrl-C. It is this output that I want you to paste (Ctrl-V) between code tags. I'm giving the outcome a very slim chance of success, but I might see something that's awry. You never know. If it fails, there's still method to my madness.

Does the *identical* problem show up under other circumstances? Try downloading Chromium (use a friend's computer if you have to) and see if the issue reproduces. Also try Opera for the same reason. If those browsers also fail, probably you have a hardware incompatibility or a failure that may even be related to browsers in some bizarre way (perhaps system hooks peculiar to this category of applications), which is why I wanted you to try safe mode. Before doing that you should clear memory of all Firefox-related code. To do that:```
ps ajfx | grep firefox
``` (Make sure this is a copy-and-paste job because ps with these arguments is about as dangerous as it gets!) If failure persists try installing a different version of Ubuntu on your computer (I'll be able to recommend one after I see the tons of output that you're going to post).

I know this has been a long slog, but I should be able to recommend something definitive today. Cheers!

---

### Post by happyytilton on 2014-05-29
Was this what you were looking for? If not I'm lost and also I've had very little experience using the command line.
```
hap@Maypop:~$ sudo lshw >hardware_list
[sudo] password for hap: 
PCI (sysfs) 
```


Just where do I clk to to select, copy and paste into the txt editor?

---

### Post by happyytilton on 2014-05-30
I sure hope this is what you wanted me to C & P here.

**hardware list**...

```
amaypop
    description: Portable Computer
    product: MP061 ()
    vendor: Dell Inc.
    serial: BTM17C1
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4
    configuration: boot=normal chassis=portable uuid=44454C4C-5400-104D-8031-C2C04F374331
  *-core
       description: Motherboard
       vendor: Dell Inc.
       physical id: 0
       serial: .BTM17C1.              .
     *-firmware
          description: BIOS
          vendor: Dell Inc.
          physical id: 0
          version: A10
          date: 08/26/2009
          size: 64KiB
          capacity: 512KiB
          capabilities: isa pci pcmcia pnp upgrade shadowing cdboot bootselect int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 CPU         T5600  @ 1.83GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 6.15.6
          serial: 0000-06F6-0000-0000-0000-0000
          slot: Microprocessor
          size: 1833MHz
          capacity: 2130MHz
          width: 64 bits
          clock: 166MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm tpr_shadow cpufreq
          configuration: cores=2 enabledcores=2 id=0 threads=2
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 32KiB
             capacity: 32KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 2MiB
             capacity: 2MiB
             clock: 66MHz (15.0ns)
             capabilities: pipeline-burst internal varies unified
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 64 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM DDR Synchronous 667 MHz (1.5 ns)
             product: HYMP512S64CP8-Y5
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 0
             serial: 00003115
             slot: DIMM_A
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM DDR Synchronous 667 MHz (1.5 ns)
             product: HYMP512S64CP8-Y5
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 1
             serial: 00007030
             slot: DIMM_B
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-pci
          description: Host bridge
          product: Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:e000(size=4096) memory:ed000000-efefffff ioport:d0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: G71M [GeForce Go 7900 GS]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nouveau latency=0
                resources: irq:44 memory:ed000000-edffffff memory:d0000000-dfffffff memory:ee000000-eeffffff ioport:ef00(size=128) memory:efe00000-efe1ffff
        *-multimedia
             description: Audio device
             product: NM10/ICH7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:45 memory:efffc000-efffffff
        *-pci:1
             description: PCI bridge
             product: NM10/ICH7 Family PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:2000(size=4096) memory:80000000-801fffff ioport:80200000(size=2097152)
        *-pci:2
             description: PCI bridge
             product: NM10/ICH7 Family PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:3000(size=4096) memory:ecf00000-ecffffff ioport:80400000(size=2097152)
           *-network
                description: Network controller
                product: BCM4311 802.11b/g WLAN
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:0c:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=b43-pci-bridge latency=0
                resources: irq:17 memory:ecffc000-ecffffff
        *-pci:3
             description: PCI bridge
             product: NM10/ICH7 Family PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:43 ioport:d000(size=4096) memory:ecc00000-ecefffff ioport:e0000000(size=2097152)
        *-usb:0
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:20 ioport:bf80(size=32)
        *-usb:1
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:bf60(size=32)
        *-usb:2
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:22 ioport:bf40(size=32)
        *-usb:3
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:bf20(size=32)
        *-usb:4
             description: USB controller
             product: NM10/ICH7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:20 memory:ffa80000-ffa803ff
        *-pci:4
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e1
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: memory:ecb00000-ecbfffff
           *-network
                description: Ethernet interface
                product: BCM4401-B0 100Base-TX
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 02
                serial: 00:14:22:f4:5d:5b
                size: 10Mbit/s
                capacity: 100Mbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10Mbit/s
                resources: irq:17 memory:ecbfe000-ecbfffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: R5C832 IEEE 1394 Controller
                vendor: Ricoh Co Ltd
                physical id: 1
                bus info: pci@0000:03:01.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=64 maxlatency=4 mingnt=2
                resources: irq:19 memory:ecbfd800-ecbfdfff
           *-generic:0
                description: SD Host controller
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 1.1
                bus info: pci@0000:03:01.1
                version: 19
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci-pci latency=64
                resources: irq:18 memory:ecbfd500-ecbfd5ff
           *-generic:1
                description: System peripheral
                product: R5C592 Memory Stick Bus Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 1.2
                bus info: pci@0000:03:01.2
                version: 0a
                width: 32 bits
                clock: 33MHz
                capabilities: pm cap_list
                configuration: driver=r592 latency=0
                resources: irq:18 memory:ecbfd600-ecbfd6ff
           *-generic:2
                description: System peripheral
                product: xD-Picture Card Controller
                vendor: Ricoh Co Ltd
                physical id: 1.3
                bus info: pci@0000:03:01.3
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: pm cap_list
                configuration: driver=r852 latency=0
                resources: irq:18 memory:ecbfd700-ecbfd7ff
        *-isa
             description: ISA bridge
             product: 82801GBM (ICH7-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide
             description: IDE interface
             product: 82801GBM/GHM (ICH7-M Family) SATA Controller [IDE mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:17 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:bfa0(size=16)
        *-serial UNCLAIMED
             description: SMBus
             product: NM10/ICH7 Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:10c0(size=32)
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD1600BEKT-0
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 01.0
             serial: WD-WX21A2354174
             size: 149GiB (160GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=e686f016
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                version: 3.1
                serial: f25b5d3d-4335-d743-90bd-5b47b83d8ef7
                size: 29GiB
                capacity: 29GiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2013-05-27 19:27:56 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
           *-volume:1
                description: Windows NTFS volume
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                version: 3.1
                serial: 2eb43544-f9ea-bf4b-bb0d-00ac2e628153
                size: 40GiB
                capacity: 40GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2010-05-03 23:24:57 filesystem=ntfs label=Documents state=clean
           *-volume:2
                description: Extended partition
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                size: 79GiB
                capacity: 79GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   description: Hidden HPFS/NTFS partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 19GiB
                   capabilities: hidden
              *-logicalvolume:1
                   description: HPFS/NTFS partition
                   physical id: 6
                   logical name: /dev/sda6
                   capacity: 10236MiB
              *-logicalvolume:2
                   description: Linux swap / Solaris partition
                   physical id: 7
                   logical name: /dev/sda7
                   capacity: 2044MiB
                   capabilities: nofs
              *-logicalvolume:3
                   description: Linux filesystem partition
                   physical id: 8
                   logical name: /dev/sda8
                   logical name: /
                   capacity: 47GiB
                   configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered state=mounted
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD writer
             product: DVD+-RW TS-L632D
             vendor: TSSTcorp
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: DE03
             capabilities: removable audio cd-r cd-rw dvd dvd-r
             configuration: ansiversion=5 status=nodisc
  *-battery
       product: DELL 00
       vendor: PS2
       physical id: 1
       slot: Sys. Battery Bay
       capacity: 78000mWh
       configuration: voltage=11.1V
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:18:f3:ee:3c:b7
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.13.0-27-generic firmware=666.2 ip=192.168.0.21 link=yes multicast=yes wireless=IEEE 802.11bg
```

---

### Post by happyytilton on 2014-06-01
**whitesmith...**

You haven't given up on me have you?... It's just been a few days.

---

### Post by howefield on 2014-06-01
Hello happyytilton, just scanning the thread to find out what version of Ubuntu you are running and are you fully updated ?

---

### Post by happyytilton on 2014-06-01
Version 14.04

---

### Post by happyytilton on 2014-06-01
**whitesmith** was leaning towards it being browser related, but with FFx uninstalled, it still did it.
I can do a restart and do nothing but let it sit until it goes into its power saving mode, then a shake of the mouse, is when I get the little notification popups.
I did a restart like that even with the browser removed and it still produced those same popups.
So its got to be something else other than browser related.

---

### Post by happyytilton on 2014-06-01
I hate to try any other distro, since we had such a hard time connecting to the internet.
See: [http://ubuntuforums.org/showthread.php?t=2225781](http://ubuntuforums.org/showthread.php?t=2225781)

---

### Post by howefield on 2014-06-01
Try in a terminal

```
sudo rm /var/crash/*
```

If it happens again after rebooting, try looking in that folder for crash details.

---

### Post by happyytilton on 2014-06-01
Here's what I got with that:
```
hap@Maypop:~$ sudo rm /var/crash/*
rm: cannot remove ‘/var/crash/*’: No such file or directory
hap@Maypop:~$ 
```

---

### Post by dragonfly41 on 2014-06-01
I'm arriving late to this party ..

but when I get these "System program problem detected" messages you posted

> These popup at boot up or when logging back on from sleep mode.

I usually click through on "Report problem" and then take note of the
information provided.  This should give clues to the source of the problem.

Take a screenshot and post here to help in diagnosis.

Another suggestion is to login to Ubuntu through a fresh new unencumbered account .. such as "guest" .. to see if you get the same popups. This helps in narrowing down where to look.

---

### Post by happyytilton on 2014-06-01
Both... Logon and wake from sleep... But _**does not**_ do it from the Guest account.
[ATTACH=CONFIG]253660[/ATTACH]

---

### Post by happyytilton on 2014-06-01
Also get the popup, after boot up at the login screen.

---

### Post by dragonfly41 on 2014-06-02
The screenshot you posted does not show the clues from the crash report 
See below example of follow through on clicking a "report problem".
In my example I have deliberately edited a python lib file to assist me in debugging some python code.

...

The "delete logs in /var/crash/" tip is explained here ...

[http://askubuntu.com/questions/133385/getting-system-program-problem-detected-pops-up-regularly-after-upgrade](http://askubuntu.com/questions/133385/getting-system-program-problem-detected-pops-up-regularly-after-upgrade)

Advice given ...

Open your terminal (Ctrl + Alt +T .... or Applications > Accessories > Terminal) 
and type:

gksudo gedit /etc/default/apport

And hit Enter.

Change enabled=1 to enabled=0, then save and exit.


See also: How do I enable or disable Apport?

[http://askubuntu.com/questions/93457/how-do-i-enable-or-disable-apport](http://askubuntu.com/questions/93457/how-do-i-enable-or-disable-apport)

....


However this just stops the reports and the root cause of the crashes still need to be tracked down.

...

In your case you will need to systematically shut down various apps which automatically launch at login until you have a leaner system which does not generate these messages. i.e. like your guest account.

You have eliminated Firefox (plus add-ons) as a root cause.

Since there are no error messages with guest account this does suggest that this crash report is not caused by video drivers (since drivers are used in guest account).

...

Useful keywords from one of your posts ...

"unable to handle kernel paging request"

"kernel panic not syncing: Fatal exception in interrupt"


These keywords point to this ...

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

but grub tweaking is "beyond my ken".

You could try tips in this post ...

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

...

There are two packages which makes grub options editing easier ...

First 

Applications > Ubuntu Software Centre > search "boot-repair" and install

installed into ...

Applications > System tools > Administration > Boot Repair

Run this and click on "Create a bootinfo summary (to get help by email or forum)" after report is generated take note of the url in popup message

Please write on a paper the following URL:
[http://paste.ubuntu.com/xxxxxxx/](http://paste.ubuntu.com/xxxxxxx/)

and copy the url for us to read.   We can then see what kernels you have (current and old).

...

The next useful package is ..

Applications > Ubuntu Software Centre > search "grub customizer" and install.
installed into ...

Applications > System tools > Administration > Grub Customizer

Perhaps try booting with an earlier kernel chosen in grub customizer.

Or you could try ramping up the guest account to match the apps running in your normal (problematic) user account until you find an application which crashes.

...

Hope there is something above which helps to solve this puzzle. The working guest account at least gives you a marker to work from.

---

### Post by happyytilton on 2014-06-03
[**[COLOR=#000000]dragonfly41[/COLOR]**]("http://ubuntuforums.org/member.php?u=1261878")

Sorry about not getting back to you, but I had an outpatient "day surgery" that took all day Monday and I'm moving rather slowly today.

You must understand that I'm new to Linux, having used Windows all my computer life, so you must explain most everything ([COLOR=#800000]**step by step**[/COLOR]) as if I don't know anything.
[COLOR=#800000]**Please don't worry... I won't be offended.** **I'm trying to learn.**[/COLOR] Also I'm not used to using the command line or terminal, so extra explaining is needed that area.

I'm now reading your last post to try and figure out just what you want me to do... It's a little advanced to me, but I'm trying.

---

### Post by happyytilton on 2014-06-03
Ok... just deleted the logs and disabled "apport".
Moving on to the next portion/section of your post.

---

### Post by happyytilton on 2014-06-03
Couldn't find "boot-repair" or "grub customizer"...

---

### Post by dragonfly41 on 2014-06-03
Don't wrap the search names in quotes .. just use **boot-repair** and **Grub Customizer**

Also, note that Ubuntu Software Centre can be case sensitive.

While you are in **Ubuntu Software Centre** I suggest that you also install **Krusader** and **Thunar  **as file managers in preparation for future tips to follow here (Krusader is similar to Total Commander in Windows).

---

### Post by happyytilton on 2014-06-04
I got the exact same result when searching for **boot-repair and [B]Grub Customizer**[/B] without the quotes.

But I did get** Krusader** and **Thunar** installed. It took **Krusader** forever to install, so I walked away last night, returning this morning.
Resuming from sleep, I entered the PW and everything came back as I had left it. No popups and no crashed apps.

---

### Post by dragonfly41 on 2014-06-04
I'm running Ubuntu 12.04 so possibly boot-repair and Grub Customizer are not in 14.04 Trusty Tahr repo.   

In fact this confirms this ..

[http://ubuntuforums.org/showthread.php?t=2210685](http://ubuntuforums.org/showthread.php?t=2210685)

But we'll park this idea for the moment .. you could look around for "boot-repair on 14.04" references in this forum.

The reason I suggested Krusader was to give you a GUI which in some ways fits into your "windows comfort zone".  If you still use Windows try Total Commander in Windows.

Krusader allows many user file management functions to be executed without touching the command line terminal.

Note that in Krusader there is "Tools" in the menubar and from there you can "Start Root Mode Krusader" when you need to access files with sudo permissions. The default launched version of Krusader has your user permissions (not root permissions).

Another point to look at is "View" where you can tick "Show Hidden Files" when you need to.

As explained disabling "apport" simply removes the annoying messages.   But the root cause of the crashes (if they continue) may need to be investigated. 

I would continue trying Ubuntu until you next hit some problem.

Use Krusader as your tool to navigate around the file system.  You could use Nautilus but it does not have twin panel.

---

