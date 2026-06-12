---
title: "Youtube lagging very, very badly on chrome"
date: 2014-10-06
forum: General Help
---

### Post by aeternalis11 on 2014-10-06
Hello,

I recent have started to have a ton of trouble with youtube. Every single video makes the entire tab lag, even if it's just a still image. 

The lag is not network-like lag, it simply refreshes the video every 5 seconds or so and when I scroll or pause the video it takes ages to work. I've tried re-installing everything, no dice.

I never had this issue on windows. It just now started to happen on this about a month ago.

---

### Post by Mark Phelps on 2014-10-06
> I never had this issue on windows.That could easily be due to Windows having better video drivers.

If you don't know the make and model video chipset on your PC, then open a terminal, enter "lspci" (without the quotes), look for the line containing "VGA" -- and post that information back here.  That will tell us the video chipset in use on your PC.

It's likely that all you will have to do is update or replace your video drivers.

---

### Post by wantdownload on 2014-10-06
Like Mark said, this could be video drivers although you could try clearing the cache in Chrome, that usually helps me out.

---

### Post by aeternalis11 on 2014-10-08
> **Mark Phelps said:**
> That could easily be due to Windows having better video drivers.

If you don't know the make and model video chipset on your PC, then open a terminal, enter "lspci" (without the quotes), look for the line containing "VGA" -- and post that information back here.  That will tell us the video chipset in use on your PC.

It's likely that all you will have to do is update or replace your video drivers.


00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82562V-2 10/100 Network Connection (rev 02)
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA Controller [IDE mode] (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA Controller [IDE mode] (rev 02)

---

