---
title: "Lirc keeps crashing with 14.04"
date: 2014-05-01
forum: General Help
---

### Post by wardy277 on 2014-05-01
I have been using lirc with xbmc using my me remote for a few years now.

After wiping and installing a fresh copy of Ubuntu 14.04 everything was working until lirc stopped reading my remotes input. irw now longer logs any button presses. After a reboot it all works fine for a while then stoops again.

This only happened with Ubuntu 14.04 so hopefully it's just a new configuration or something. Any help with this would be greatly appreciated.

ir-keytable returns:

Found /sys/class/rc/rc0/ (/dev/input/event2) with: Driver mceusb, table rc-rc6-mce Supported protocols: NEC RC-5 RC-6 JVC SONY SANYO LIRC other Enabled protocols: LIRC Name: Media Center Ed. eHome Infrared bus: 3, vendor/product: 0471:0815, version: 0x0000 Repeat delay = 500 ms, repeat period = 125 ms

sudo mode2 -d /dev/lirc0 returns to of output on key press so I can see that the hardware is all connected and sort of working. It's just lirc which isn't working

---

### Post by elrilas on 2014-08-19
I am having this same issue, have had to go back to using keyboard to control XBMC until I can figure it out.  Has anyone else had luck fixing this?

---

### Post by wardy277 on 2014-08-19
I have managed to fix this. It seems that there is a kernel issue with usb or something. It seems very complicated but the fix was found here:
[http://forum.xbmc.org/showthread.php?tid=197639&pid=1733746#pid1733746](http://forum.xbmc.org/showthread.php?tid=197639&pid=1733746#pid1733746)

Aparently turning on irqpoll on boot stops it, and it hasnt crashed since (been a few days now).

I gave up here due to no replies and went to the xbmc forums.

---

