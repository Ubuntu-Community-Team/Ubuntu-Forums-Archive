---
title: "X is using xorg.conf.failsafe"
date: 2007-10-20
forum: General Help
---

### Post by Aikon- on 2007-10-20
I installed Gutsy last night and everything has been going great. I have an ATI Radeon 9600XT, and I used the proprietary drivers because I need the XvOverlay option to prevent screen-tearing when watching videos.

Today I decided to go back to the open-source radeon driver, because apparently it *does* have support for XV, and I thought I may as well give it a try with Compiz and see how I like it.

So, through the restricted-drivers manager, I disabled the proprietary driver I had just installed and rebooted. After some playing with Compiz etc., I decided I wanted to go back to the fglrx driver, so I went back to the restricted-drivers manager and re-enabled it and rebooted.

When X started up, I got the following message: "Ubuntu is running in low-graphics mode. Your screen and graphics card could no be detected. To use a higher resolution, visual effects or multiple screens, you have to configure the display yourself."

This has never been an issue for me before, whether in Hoary, Dapper, or (until now), Gutsy. Basically my computer is running at 800x600 instead of 1920x1200. I double-checked and re-double-checked xorg.conf and couldn't find anything wrong; I sudo dpkg-reconfigure xserver-xorg twice, once using what I would normally enter and again using advanced options to prevent it from having to "guess". Still, same thing.

Then I opened Xorg.0.log and I saw this little gem:

```
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Oct 20 19:15:36 2007
(==) Using config file: "/etc/X11/xorg.conf.failsafe"
```

It seems my computer is insisting on loading xorg.conf.failsafe instead of xorg.conf. As a test, I made a backup of xorg.conf-failsafe and copied my existing xorg.conf over top of it. Now, when I restart X, it loads "xorg.conf.failsafe", but that file is exactly the same as my normal xorg.conf, and everything works just fine.

Why is my system trying to use the failsave xorg.conf instead of the regular one? How can I set it back to using the regular one the way it should be?

Let me know if you need any more information.

-Aikon

---

### Post by orbital13 on 2007-10-20
I have a similar problem. I've outlined it in this post: [http://ubuntuforums.org/showthread.php?t=583455](http://ubuntuforums.org/showthread.php?t=583455)

It's insanely frustrating since I can't find any reason for this to happen. I've triple checked all the logs: xorg, gdm, syslog, etc. Can't find anything. It even looks like the screen is being recognized as 1680x1050 but for some reason being displayed at 800x600.

---

### Post by Aikon- on 2007-10-20
Iteresting.. once I finally tricked it into loading the graphics properly by making my "failsafe" xorg completely un-"fail-safe", on the next reboot it loaded the regular xorg.conf.

Looks like it may have been a one-off thing.. I'll keep you posted if it happens to me again. Sorry this wasn't any help for your own problem, orbital.

-Aikon

---

### Post by orbital13 on 2007-10-20
I tried doing the same thing, it didn't help. Looking in the latest xorg logs I can see everything being loaded perfectly, except for this one nasty line : )

```
 
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(II) NVIDIA(0): Setting mode "800x600"


```

---

### Post by orbital13 on 2007-10-20
I was able to get this halfway working by bumping down my refresh rate to 50Hz. I wonder if I've set my H and V refresh rates correctly in xorg.conf. I have:

```

Section "Monitor"
        Identifier      "Dell 2005FPW"
        Vendorname      "Generic LCD Display"
        Modelname       "LCD Panel 1680x1050"
        Horizsync       30.0-83.0
        Vertrefresh     56.0-75.0
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
  modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
  modeline  "1600x1024@60" 136.36 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
  modeline  "1680x1050@60" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
        Gamma   1.0
EndSection


```

---

### Post by burningbed on 2007-10-21
I have had a perhaps somewhat similar problems (see [http://ubuntuforums.org/showthread.php?t=583642]("http://ubuntuforums.org/showthread.php?t=583642")) and they were all solved by uninstalling xserver-xgl.
I'd try running running apt-get remove xserver-xgl and see if it helps.

---

