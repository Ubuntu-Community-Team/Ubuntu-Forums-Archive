---
title: "First time installation of Linux"
date: 2007-05-07
forum: General Help
---

### Post by mopepom on 2007-05-07
I have decided to become a Linux user.

As of this point in time, I am downloading ubuntu-6.10-deskto[-i386.iso (698MB).

I am experienced user of Windows XP, which will remain my production operating system, until further notice.

I have:

- reserved an entire hard disk (76GB) for Linux;

- set up my Initial load procedure to permit booting from either this hard drive (for Linux) or Windows XP from my main hard drive (76GB, C:, 47% free space);

- available an additional 160GB external hard disk space, which is used for backup of data;

- a wireless/ ethernet cable LAN for our home;

- other Windows XP machines connected by wire and wirelessly to the LAN, and hence to the web.

- a Netgear router to connect the LAN via a Surfbeam modem to the Telesat internet network (d/l @ 512KB);

- a 56KB modem and associated ISP linkage and account for land-line backup to the web, when the satellite goes out, very occasionally;

- a preferred s/w environment of Firefox 2.0.0.3 and Thunderbird 2.0;

- AVG antivirus (purchased version);

- Comodo firewall (purchased version);

Ideally, I would like to switch with ease from my fully functional productional XP environment to a working Linux-Ubuntu environment, including full web access), that can be used increasingly to permit weaning off Microsoft s/w.

I need some straightforward instructions on what options are available and how to achieve my objective quickly.

Perhaps readers of this forum can help.

Many Thanks.

---

### Post by rai4shu2 on 2007-05-07
You should probably take a good look at VMware and QEmu/KVM. A good VM would allow you to use Windows within Linux. Lots of programs for Windows can also work with Wine or CrossOver.

---

### Post by Wiebelhaus on 2007-05-07
Installation
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

First thing after installation:

Gpu drivers:
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)


Ntfs/Fat32 read / write
The easy way , Install [Automatix]("http://www.getautomatix.com/wiki/index.php?title=Installation")

Install the Read&write Ntfs/Fat32 Utility

Install Ntfs3 (open term, type, sudo apt-get install ntfs-3g) And configure via system tools.

the rest of your essential software can quickly be obtained from this nifty little app:
[http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)

now your setup and can continue to learn Linux without banging your head in an unfamiliar enviroment without that essential software , Firefox/swiftfox,thunderbird,wine,media plugins,IM etc.

---

### Post by newlinux on 2007-05-07
The following link might help you with your transition:

[http://www.linuxrsp.ru/win-lin-soft/table-eng.html](http://www.linuxrsp.ru/win-lin-soft/table-eng.html)

It is a listing of linux replacements for windows software. Any particular reason you aren't using Feisty (7.04), the latest ubuntu release (nothing wrong with edgy, I run it on 2 of my computers).

---

### Post by mopepom on 2007-05-07
> **rai4shu2 said:**
> You should probably take a good look at VMware and QEmu/KVM. A good VM would allow you to use Windows within Linux. Lots of programs for Windows can also work with Wine or CrossOver.

Thank you for this. I am exploring VMWare, so this seems to fit with your advice.

I will get back on this thread to report progress.

---

### Post by mopepom on 2007-05-07
Thanks to Sx66gns - I appreciate your comprehensive reply. I will report progress on this thread.

Thanks to newlinux - I am not going with 7.07, only because of my ignorance.

---

### Post by liorwohl on 2007-05-07
> **mopepom said:**
> I have decided to become a Linux user.

As of this point in time, I am downloading ubuntu-6.10-deskto[-i386.iso (698MB).


why you download 6.10 when 7.04 is available?

---

### Post by mopepom on 2007-05-07
Pure ignorance on my part - I wouldn't know 6.10 from 7.04 if I met them on the street.:)

---

### Post by mopepom on 2007-05-19
This has been an interesting one way trip - so far.

After much advice from another forum, I decided to go for an install of ubuntu 7.04 from a LiveCD.

I first cleared my Linux Drive of my previous test version of Debian 3.1.

I powered off my Windows HDD and ran the install from the LiveCD for ubuntu 7.04.

After much, MUCH fiddling around with my BIOS settings, and **powering on my Windows HDD**, I can now boot into ubuntu 7.04 on my Linux HDD. I have even added some of my favourite extensions to the FF browser. These appear to be working very well, and it is almost like I am back in business.

Except for one small thing - I can't boot into my Windows XP drive - just my Linux drive.

So far, i have been unable to locate clear and current instructions on setting the BIOS parameters (Award Software, Inc. ASUS P4S533-MX ACPI BIOS Revision 1006)

Help would be appreciated.

Many thanks.

---

### Post by mopepom on 2007-05-20
BIOS documentation was found at the ASUS website. It is a fairly long PDF file for the P4S533-MX motherboard - about p.40 for the BIOS section.

---

