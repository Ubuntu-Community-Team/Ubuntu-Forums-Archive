---
title: "Device manager - Network card need to ID"
date: 2007-11-18
forum: General Help
---

### Post by desertboy on 2007-11-18
I've just reinstalled vista to play gears of war but it won't recognize my network card, how do I ID the network card in ubuntu so I can download the right drivers (In ubuntu).

Thanks

---

### Post by scrooge_74 on 2007-11-18
you can type lspci  and look for the name of your card, I also imagine you can get the name from Vista also

---

### Post by desertboy on 2007-11-19
Device manager in Vista lists it as ethernet controller (No other info)

lspci gives this

00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801H (ICH8 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G80 [GeForce 8800 GTS] (rev a2)
02:02.0 Mass storage controller: Integrated Technology Express, Inc. ITE 8211F Single Channel UDMA 133 (rev 11)
02:06.0 Ethernet controller: Hangzhou Silan Microelectronics Co., Ltd. Unknown device 2031 (rev 01)


When I search in google for hangzhou silan microelectronics ethernet it points to 8139, which is the drivers I have installed no luck. Going to have to take the PC apart I think.

---

### Post by scrooge_74 on 2007-11-19
That is a hard one, you have some Chinese who knows what type of card in there. You got  yourself a tough nut there.

I see something about a module that supports that card [http://hardware4linux.info/module/sc92031/](http://hardware4linux.info/module/sc92031/)

Also it seems that by compiling by hand a Debian Lenny kernel it should work (so I imagine you can do that in Ubuntu also), but maybe loading the module should also work

[http://hardware4linux.info/component/26522/](http://hardware4linux.info/component/26522/)

I see you can either try the module or get a new card since it seems is a fake brand card

[http://www.linuxforums.org/forum/slackware-linux-help/106320-system-doesnt-detect-lan-card.html](http://www.linuxforums.org/forum/slackware-linux-help/106320-system-doesnt-detect-lan-card.html)
[http://www.linuxforums.org/forum/linux-networking/103640-backtrack-cannot-identify-my-network-card.html](http://www.linuxforums.org/forum/linux-networking/103640-backtrack-cannot-identify-my-network-card.html)

---

