---
title: "System freezes with 8.04 low visual effects, freezes with 7.10 at normal effects"
date: 2008-06-07
forum: General Help
---

### Post by Isoss on 2008-06-07
HI. 
I've got a problem with ubuntu 8.04 on my LG laptop.
After reinstallation, although using static, low graphical effects, I get my system frozen, upon overloading of apps (4 or 5) and typing fast on some apps like Pidgin, anything that "seems" to be memory consuming gets my system completely frozen, mouse is frozen and won't logout by Ctrl+Alt+BkSp that I have to switch power off (which once caused mother board to be broken, cost me $400 to fix it!) .. I even get the same problem with 7.10 when using "Normal" Visual effects (Not "None").

What is wrong with my laptop? 
It has 768MB of RAMS and lspci shows:
```

00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 81)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
02:04.0 Ethernet controller: Atheros Communications, Inc. AR2413 802.11bg NIC (rev 01)
02:06.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
02:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```

By the way, hope you'd check this thread that I created regarding another issue with my laptop that might be related:
[boot screen and ubuntu loading are dim and not shown untill login screen.]("http://ubuntuforums.org/showthread.php?p=5133419#post5133419")

---

### Post by nick_h on 2008-06-07
> I have to switch power off (which once caused mother board to be broken, cost me $400 to fix it!) ..

Have you tried the [Magic SysRq](http://ubuntuforums.org/showthread.php?t=617349) keys to shutdown safely?

Do you get the problem if you disable Visual Effects completely?

---

