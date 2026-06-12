---
title: "Intel Atom N2800 and GMA 3600 Xubuntu Graphics"
date: 2013-05-10
forum: General Help
---

### Post by mgblake7 on 2013-05-10
Hi

I recently got a little 10" netbook and decided to put Xubuntu 13.04 (i386) on it.
It installed perfectly, and seems quite fast, however on startup there is a delay with a black screen followed by the following prompt: 

gpu: power management timed out

I also noticed that if I suspend the system, when I wake it up the screen is just a bunch of distorted coloured lines.

After a bit of googling it seems the problem lies in the graphics driver for the Atom N2800/GMA 3600 (if this isn't the case please let me know!)
I would really like to fix this as I'm sure the system will work a lot better if I do.

Any assistance would be much appreciated!!

---

### Post by mgblake7 on 2013-05-10
Update: the system also freezes and/or restarts periodically, I think this is related to the graphics issue as well.
the netbook I'm using is a Gigabyte Q2006

---

### Post by mgblake7 on 2013-05-14
Still no luck.


Touch pad also freezes every now and then, not sure if this is related. Would really like to get this working 100%


More Info:
lspci -k gives me this:


00:00.0 Host bridge: Intel Corporation Atom Processor D2xxx/N2xxx DRAM Controller (rev 04)
Subsystem: CLEVO/KAPOK Computer Device 2100
00:02.0 VGA compatible controller: Intel Corporation Atom Processor D2xxx/N2xxx Integrated Graphics Controller (rev 0b)
Subsystem: CLEVO/KAPOK Computer Device 2100
Kernel driver in use: gma500
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 02)
Subsystem: CLEVO/KAPOK Computer Device 2100
Kernel driver in use: snd_hda_intel
00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 02)
Kernel driver in use: pcieport
00:1c.1 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 2 (rev 02)
Kernel driver in use: pcieport
00:1c.2 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 3 (rev 02)
Kernel driver in use: pcieport
00:1c.3 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 4 (rev 02)
Kernel driver in use: pcieport
00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 02)
Subsystem: CLEVO/KAPOK Computer Device 2100
Kernel driver in use: uhci_hcd
00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 02)
Subsystem: CLEVO/KAPOK Computer Device 2100
Kernel driver in use: uhci_hcd
00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 02)
Subsystem: CLEVO/KAPOK Computer Device 2100
Kernel driver in use: uhci_hcd
00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 02)
Subsystem: CLEVO/KAPOK Computer Device 2100
Kernel driver in use: uhci_hcd
00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 02)
Subsystem: CLEVO/KAPOK Computer Device 2100
Kernel driver in use: ehci-pci
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
Subsystem: CLEVO/KAPOK Computer Device 2100
Kernel driver in use: lpc_ich
00:1f.2 SATA controller: Intel Corporation NM10/ICH7 Family SATA Controller [AHCI mode] (rev 02)
Subsystem: CLEVO/KAPOK Computer Device 2100
Kernel driver in use: ahci
00:1f.3 SMBus: Intel Corporation NM10/ICH7 Family SMBus Controller (rev 02)
Subsystem: CLEVO/KAPOK Computer Device 2100
01:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8723AE PCIe Wireless Network Adapter
Subsystem: Realtek Semiconductor Co., Ltd. Device 0726
Kernel driver in use: rtl8723ae
03:00.0 Ethernet controller: JMicron Technology Corp. JMC260 PCI Express Fast Ethernet Controller (rev 05)
Subsystem: CLEVO/KAPOK Computer Device 2100
Kernel driver in use: jme
03:00.1 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 90)
Subsystem: CLEVO/KAPOK Computer Device 2100
Kernel driver in use: sdhci-pci
03:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 90)
Subsystem: CLEVO/KAPOK Computer Device 2100
03:00.3 System peripheral: JMicron Technology Corp. MS Host Controller (rev 90)
Subsystem: CLEVO/KAPOK Computer Device 2100
Kernel driver in use: jmb38x_ms


Details of boot message:


gpu: power management timed out
[ 24.2487421] gma500 0000:00:02.0: trying to get vblank count for disabled pipe 0
[ 24.248769] gma500 0000:00:02.0: trying to get vblank count for disabled pipe 0

---

### Post by mastablasta on 2013-05-14
your intel GPU is actually not made by intel but by a third party and that one is causing troubles. wikipedia:

> GMA 3600 [edit]This integrated graphics system was released in Intel Atom (Cedar Trail, 32 nm) and based on PowerVR SGX545


> **PowerVR based [[edit]("http://ubuntuforums.org/w/index.php?title=Intel_GMA&action=edit&section=13")]**

Intel developed a new set of low power graphics architecture based on [PowerVR]("http://ubuntuforums.org/wiki/PowerVR").
The available Linux drivers do not support much of this



> [h=4]PowerVR based chips on Linux [[edit]("http://ubuntuforums.org/w/index.php?title=Intel_GMA&action=edit&section=25")][/h]GMA 500, GMA 600, GMA 3600, GMA 3650 are PowerVR based chips incompatible with Intel Graphics Media Accelerator main architecture. There are no Intel supported [FOSS]("http://ubuntuforums.org/wiki/FOSS") drivers. The current available FOSS drivers (included in Linux 3.3 onwards) only support 2D acceleration (not 3D acceleration).[SUP][[SIZE=2][25][/SIZE]]("http://ubuntuforums.org/#cite_note-Poulsbo_-_ArchWiki-25")[/SUP]
Ubuntu supports GMA500 (Poulsbo) through the ubuntu-mobile and gma500 repositories on [Launchpad]("http://ubuntuforums.org/wiki/Launchpad_(website)"). Support is present in an experimental way for 11.10 and 12.04, but the installation procedure is not as simple as other drivers and can lead to many bugs. Ubuntu 12.10 has 2D support included.[SUP][[SIZE=2][52][/SIZE]]("http://ubuntuforums.org/#cite_note-52")[/SUP]
[Joli OS]("http://ubuntuforums.org/wiki/Joli_OS"), a Linux based OS optimized for netbooks, has a driver for the GMA500 built in.
PixieLive, a GNU/Linux live distribution optimized for GMA500 netbooks, it can boot from USB Pendrive, SD Card or HardDisk.
Intel releases official Linux drivers through the IEGD (Intel Embedded Graphic Driver) supporting some Linux distributions dedicated to the embedded market.[SUP][[SIZE=2][53][/SIZE]]("http://ubuntuforums.org/#cite_note-53")[/SUP]
In November 2009, the [Linux Foundation]("http://ubuntuforums.org/wiki/Linux_Foundation") released the details of a new, rewritten Linux driver that would support this chipset and Intel's other upcoming chipsets. The [Direct Rendering Manager]("http://ubuntuforums.org/wiki/Direct_Rendering_Manager") and [X.org]("http://ubuntuforums.org/wiki/X.Org_Server") parts would be free software, but the 3D component (using [Gallium3D]("http://ubuntuforums.org/wiki/Gallium3D")) will still be proprietary


you can try lower (12.04) or higher version of graphics drivers (PPA?!) if it get's any better. i remember reading some workarrounds for these chips that improve performance a bit.

---

### Post by mgblake7 on 2013-05-14
Thanks very much for this!

I have tried different versions, including 12.04 with the same result.
It seems gma500 came built in with 13.04 on Xubuntu.

I read somewhere about editing the graphics config file which helped someone, will try that as well.
Incredibly annoying that PowerVR won't release linux drivers!!

---

### Post by mgblake7 on 2013-05-15
I found this:

[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)

Will try the workarounds and let you know if they work.

---

### Post by woodan on 2013-05-27
Hi,

I am new to the forum.  I recently picked up exactly the same errors on a Gigabyte Q2006 machine; having just installed Lubuntu.  Have confirmed the machine is running gma500_gfx driver.

Did you manage to find any work arounds to the errors on startup, and associated instabilities?

Regards
Andrew

---

### Post by mgblake7 on 2013-05-27
Hi Andrew

From what I can tell gma500_gfx is the best driver available for this machine. I havent been able to find any methods that get rid of the startup errors or instabilities.

Hopefully there is an easier solution than re-coding the driver.

---

### Post by woodan on 2013-05-28
Hi,

For what it's worth I have removed splash, and added console=tty1.

It still gives me the same errors on bootup, but will see if stability improves.

Regards
Andrew

---

### Post by furkan2 on 2014-05-12
Hi,

Have your problems been solved somehow?

I am experiencing the same issues.

---

