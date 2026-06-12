---
title: "Wrong resolution when booting with screen off"
date: 2013-10-15
forum: General Help
---

### Post by BertusG on 2013-10-15
I use my PC (ATI Radeon 6130 HD on ASRock E350 Mini-ITX) as an HTPC with Ubuntu minimal and XBMC. When I power on my PC while my TV is on there are no issues. DFP1 is selected as primary monitor and I get the right resolution (1920x1080).

However when the PC starts and the TV is off I get the wrong resolution (1400x1050). When I look in the Xorg.0.log I see the following issue:
```
fglrx(0): Output DFP1 disconnected
fglrx(0): Output DFP2 disconnected
fglrx(0): Output CRT1 connected
```

Strange enough there is no CRT1 connected and my TV (DFP1) is the only connected screen/monitor. I think this the reason I got the wrong resolution. I tried to add modelines to xorg.conf, trying to overrule the 'wrong' resolution but unfortunately it didn't help. I tried customedid, modelines etc. etc.

Does anybody have a clue why this goes wrong?

Current xorg.conf
[http://pastebin.com/hizG91G6](http://pastebin.com/hizG91G6)

Xorg.0.log (when it goes wrong and TV is off)
[http://pastebin.com/TTFDQa31](http://pastebin.com/TTFDQa31)

Xorg.0.log (when it goes right and TV is on)
[http://pastebin.com/micWArzR](http://pastebin.com/micWArzR)

---

### Post by sudodus on 2013-10-16
My experience is that the default behaviour of the Ubuntu family system's graphics are set during boot. Depending on what it finds and recognizes, the drivers are selected (unless fixed in the case of proprietary drivers (as in the case of fglrx)). Also the resolution is set depending on the hardware. I notice this often, because I have a KVM switch to use the same monitor, keyboard, mouse and speakers for several computers. Starting a computer when the monitor is connected to another one, results in some low default graphics (maybe vesa graphics). I think your 1400x1050 is also a vesa graphics mode.

It is probably possible to fix that issue with the config file for X, but I don't know how to do it.

---

