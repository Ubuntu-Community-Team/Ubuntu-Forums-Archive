---
title: "flash crashing when playing youtube videos"
date: 2007-10-13
forum: General Help
---

### Post by jman623 on 2007-10-13
Hi all just bought a new PC, installed ubuntu but much to my displeasure firefox and flash freeze whenever I try to play youtube and other kinds of videos. I installed flash when firefox prompted me, so I know I am running the latest version, did anyone else run into this problem, I am huge fan of ubuntu and linux, but I may have to gack to Vista because I am absolutely addicted to youtube :-(

Output from LSPCI:

```
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
02:02.0 Ethernet controller: D-Link System Inc RTL8139 Ethernet (rev 10)
```

---

### Post by GhostZrydA on 2007-10-13
This is a known issue, happens to lots of people including myself.

Did you try installing the flash player using the add/remove option on the main menu, and searching for "ubuntu restricted extras".

After installing, use the flash test website [http://www.adobe.com/shockwave/welcome/](http://www.adobe.com/shockwave/welcome/) it should show as having version 9.0.48.0 installed.

Over the last month or so, i have noticed not as many crashes, with firefox/youtube.
Most of the crashs/lockups are when you start to watch a clip then change your mind, and use the back button, then firefox locks up.

Check to see if you have that version installed, and see how it goes.

Pretty sure that the new version of Ubuntu next week has a new flash player as well.

GhostZrydA

---

### Post by FuturePilot on 2007-10-13
Yes, this is a known issue. And only Adobe can fix this](*,)
[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/98688]("https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/98688")

---

