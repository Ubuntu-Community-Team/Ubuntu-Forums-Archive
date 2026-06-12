---
title: "Losing display with radeon OSS driver when switching HDMI input using an AV receiver"
date: 2014-11-12
forum: General Help
---

### Post by julien-hirel on 2014-11-12
Hi all,

I recently upgraded my HTPC (which has an AMD A6-3500 CPU with integrated AMD graphics chip) to xubuntu 14.10. I decided to give the OSS radeon driver a try since it seems to be better supported than the fglrx driver in recent XBMC releases. 'for video hardware acceleration)

I encountered a problem which I did not have with the proprietary driver : I can't get the display back when I switch to another HDMI input on my AV receiver (Yamaha RX 675) and then back to my HTPC HDMI input. Here are the steps:
1) Boot the HTPC with the AV receiver set on the HDMI input corresponding to the HTPC -> Display OK
2) Switch the AV receiver to another HDMI input (e.g. blu-ray player)
3) Switch the HDMI input back to HTPC on the AV receiver -> No display (receiver gets no input signal)

I can still reach my htpc using ssh when the display is off after I switched. I can even gett the display back using the xrandr command:
```
DISPLAY=:0 xrandr --output HDMI-0 --auto
```

I just have no idea why the display is somehow deactivated as soon as the receiver is switched and not reactivated afterwards. I have not really been able to find any information about this particular case on the web.

I would greatly appreciate it if anyone could point me in the right direction. Switching to the proprietary driver could be a solution but I would rather try to solve my problem with the OSS driver since AMD has apparentely decided to drop all support for older cards in their recent drivers ...

Thanks !

---

