---
title: "Slow downloading speed?"
date: 2012-11-27
forum: General Help
---

### Post by Winter1337 on 2012-11-27
Hey guys, I just switched from Windows to Ubuntu yesterday, I've been experiencing very slow download speed. Even when I use my school's wifi, the speed get reduced from 100+kb/s to 200~600b/s, what is causing this problem? Even I tried to use my high speed internet to download from Software Center, using terminal to download, the speed get reduced to bytes...I can't stand all these. Anyone experiencing this problem too? Or have any solution to this problem? I've tried downloading other stuff via browsers, there is no problem.

---

### Post by lincoln32 on 2012-11-27
not normally an issue but I can give a few things to test
first open a terminal and type lspci and post the results
back here that will tell us what kind of wireless card you have
to see if there are any known issues with or upgraded drivers:guitar:

---

### Post by Winter1337 on 2012-11-28
> **lincoln32 said:**
> not normally an issue but I can give a few things to test
first open a terminal and type lspci and post the results
back here that will tell us what kind of wireless card you have
to see if there are any known issues with or upgraded drivers:guitar:
winter@Satellite-L510:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode] (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

This is the result I get from the command. @@ not only me, my friend tried to download the ubuntu iso from thye website and the download speed automatically reduced to bytes too.

---

### Post by varunendra on 2012-11-28
Was it all the output? Nothing left out? Because I don't see any wireless interface in that. Are you using a USB wireless dongle? Sometimes even an internal device may be connected on a USB bus. So if you are sure that's all the output of lspci, please also post output of -
```
lsusb
```
While posting th output, please wrap it in 'Code' tags as given in example here (ignore the initial part, scroll down to "**PS:**" part)- [http://ubuntuforums.org/showpost.php?p=12368389](http://ubuntuforums.org/showpost.php?p=12368389)

Also, was the speed slow only for the iso you were downloading or everywhere? Because sometimes servers may get slow when they are under heavy pressure.

> **Winter1337 said:**
> not only me, my friend tried to download the ubuntu iso from thye website and the download speed automatically reduced to bytes too.What was common? The laptop or the target download (iso)? As far as downloading the Ubuntu ISO is concerned, it is recommended to download via torrent. Not only it is fast, but also ensures the integrity of the downloaded content, thanks to the inherent 'hash checking' feature of torrent protocols.

Official links for torrent download - [http://www.ubuntu.com/download/desktop/alternative-downloads](http://www.ubuntu.com/download/desktop/alternative-downloads)

You want the 'desktop' iso which can be run as a live cd. The 'alternate' iso is for GUI-less install-only cd, although same as 'desktop' once installed, can't be used as a live cd. 'Server' is, obviously, a 'text-only' interface meant for servers.

I'd recommend 12.04 - 64 bit

---

### Post by Winter1337 on 2012-11-28
> **varunendra said:**
> Was it all the output? Nothing left out? Because I don't see any wireless interface in that. Are you using a USB wireless dongle? Sometimes even an internal device may be connected on a USB bus. So if you are sure that's all the output of lspci, please also post output of -
```
lsusb
```
While posting th output, please wrap it in 'Code' tags as given in example here (ignore the initial part, scroll down to "**PS:**" part)- [http://ubuntuforums.org/showpost.php?p=12368389](http://ubuntuforums.org/showpost.php?p=12368389)

Also, was the speed slow only for the iso you were downloading or everywhere? Because sometimes servers may get slow when they are under heavy pressure.

What was common? The laptop or the target download (iso)? As far as downloading the Ubuntu ISO is concerned, it is recommended to download via torrent. Not only it is fast, but also ensures the integrity of the downloaded content, thanks to the inherent 'hash checking' feature of torrent protocols.

Official links for torrent download - [http://www.ubuntu.com/download/desktop/alternative-downloads](http://www.ubuntu.com/download/desktop/alternative-downloads)

You want the 'desktop' iso which can be run as a live cd. The 'alternate' iso is for GUI-less install-only cd, although same as 'desktop' once installed, can't be used as a live cd. 'Server' is, obviously, a 'text-only' interface meant for servers.

I'd recommend 12.04 - 64 bit
Owh, thanks. But I'm using 12.10, should I change to 12.04? About the slow downloading speed, I've solved it by changing the source server to the Main Server, and now everything works fine. Originally it comes with the "Malaysia Server".

---

### Post by varunendra on 2012-11-28
Glad it solved. That was certainly an 'overloaded server' issue, happens sometimes, then solves itself. Changing server at such a time is a good idea.

> **Winter1337 said:**
> Owh, thanks. But I'm using 12.10, should I change to 12.04?
Not necessary. It depends on 'how good' the 12.10 performs for you. 12.04 is 'supposed' to be more stable, but that is not necessarily true for all people. So if 12.10 treats you well, there's no need to switch. Besides, there's no guaranty that 12.04 'will' be better.

However, you should be aware that interim releases (like 12.10) are supported for 18 months only (You won't get updates afterwards), while an LTS, from 12.04 onwards, is supported for 5 years. This may be another deciding factor for you. More info on releases : [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

