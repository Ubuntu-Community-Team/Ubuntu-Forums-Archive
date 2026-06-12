---
title: "Multiple X displays : Suspending AIGLX clients for VT switch"
date: 2014-07-08
forum: General Help
---

### Post by yann7 on 2014-07-08
[FONT=arial]Hi everyone, (sorry for my english)
i got a running ubuntu server 64bit (14.04) without desktop environnement (no gnome, no kde).
I use it to run some services (i.e apache, mail server...) and a media center application (xbmc).

All is fine at this point, and i can x11vnc the xbmc 

But my problem is i want to run a second X display to run a lightweight window manager (flux box) and access it via x11vnc.
So i setup an upstart script :
[/FONT] ```
[FONT=Courier]exec su -c "xinit /usr/bin/fluxbox $DISPLAY -- /usr/bin/X :$DISPLAY vt8 -bs -nolisten tcp" xbmc[/FONT]
```[FONT=Courier]
note that $DISPLAY is set to a value different of 0 because "xbmc" already use it.

It works because I can then see a flux box WM running on the new display, **BUT** the first display (XBMC) is then freezed and i can see in Xorg.0.log the following message :
[/FONT]```
[COLOR=#4C2F2D][FONT=Courier]II) AIGLX: Suspending AIGLX clients for VT switch[/FONT][/COLOR]
```[FONT=Courier]

Note that i have a radeon card (HD6450) with radeon oss driver setup for Xorg. I also tried with FBDEV driver but the problem is the same, so i don't think it's driver related.

Any one could help me ?

Many thanks to you ![/FONT]

---

### Post by yann7 on 2014-07-10
UP !

After googling for hours, it seems to be related to KMS and the "nomodeset" option.
So, if i set "nomodeset" to command line (in GRUB for exemple), the radeon oss driver is not loaded and X server uses FBDEV, that i don't want.

Anyone could help ?

---

### Post by yann7 on 2014-07-12
Hi all !
i found myself the trick. For those who are interested, here are the steps :
1) You must install and use XDummy driver (improved version of xfvb) in Xorg to create a virtual X display, so it will not switch to another VT and then doesn't suspend the active screen (says the one i can see on my monitor/TV)
2) Create a custom xorg.conf file and put it in /etc/X11
3) Start a new X display using "xinit" and with at least the "-config" param to use custom config file, my startup script to create the display is ```
[COLOR=#4C2F2D][FONT=Courier]exec su -c "xinit /usr/bin/startfluxbox -- /usr/bin/X :$DISPLAY -config xorg.xdummy.conf -nolisten tcp" $USER[/FONT][/COLOR]
```
4) run a x11vnc server on this display : ```
[COLOR=#4C2F2D][FONT=Courier]exec su -c "/usr/bin/X11/x11vnc -display WAIT:$DISPLAY -modtweak -xkb -cursor arrow -forever -rfbauth $PWD_FILE -repeat" $USER[/FONT][/COLOR]
```
=> set $DISPLAY to the display sets in step 3
=> set $USER the user that must run the x11vnc command
=> set $PWD_FILE to the X11VNC password file generated with ```
x11vnc **-storepasswd**
```


you'll can find below my xorg.xdummy.conf file as example :
```
[COLOR=#4C2F2D][FONT=Courier]# This xorg configuration file is meant to be used by xpra[/FONT][/COLOR][COLOR=#4C2F2D][FONT=Courier]# to start a dummy X11 server.[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]# For details, please see:[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]# https://xpra.org/Xdummy.html[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]
[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]Section "ServerFlags"[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]  Option "DontVTSwitch" "true"[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]  Option "AllowMouseOpenFail" "true"[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]  Option "PciForceNone" "true"[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]  Option "AutoEnableDevices" "false"[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]  Option "AutoAddDevices" "false"[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]EndSection[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]
[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]Section "InputDevice"[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]  Identifier "dummy_mouse"[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]  Option "CorePointer" "true"[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]  Driver "void"[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]EndSection[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]
[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]Section "InputDevice"[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]  Identifier "dummy_keyboard"[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]  #Option "CoreKeyboard" "true"[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]  #Driver "void"[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]
[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]    Driver "kbd"[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]    Option "CoreKeyboard"[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]    Option "XkbRules" "xorg"[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]    Option "XkbModel" "apple"[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]EndSection[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]
[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]Section "Device"[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]  Identifier "dummy_videocard"[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]  Driver "dummy"[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]  Option "ConstantDPI" "true"[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]  #VideoRam 4096000[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]  #VideoRam 256000[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]  VideoRam 192000[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]EndSection[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]
[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]Section "Monitor"[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]  Identifier "dummy_monitor"[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]  HorizSync   5.0 - 1000.0[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]  VertRefresh 5.0 - 200.0[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]  #This can be used to get a specific DPI, but only for the default resolution:[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]  #DisplaySize 508 317[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]  #NOTE: the highest modes will not work without increasing the VideoRam[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]  # for the dummy video card.[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]  Modeline "1920x1440" 69.47 1920 1960 2152 2384 1440 1441 1444 1457[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]  Modeline "1920x1200" 26.28 1920 1952 2048 2080 1200 1229 1231 1261[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]  Modeline "1920x1080" 23.53 1920 1952 2040 2072 1080 1106 1108 1135[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]  Modeline "1680x1050" 20.08 1680 1712 1784 1816 1050 1075 1077 1103[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]  Modeline "1600x1200" 22.04 1600 1632 1712 1744 1200 1229 1231 1261[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]  Modeline "1600x900" 33.92 1600 1632 1760 1792 900 921 924 946[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]  Modeline "1440x900" 30.66 1440 1472 1584 1616 900 921 924 946[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]  ModeLine "1366x768" 72.00 1366 1414 1446 1494  768 771 777 803[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]  Modeline "1280x1024" 31.50 1280 1312 1424 1456 1024 1048 1052 1076[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]  Modeline "1280x800" 24.15 1280 1312 1400 1432 800 819 822 841[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]  Modeline "1280x768" 23.11 1280 1312 1392 1424 768 786 789 807[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]  Modeline "1360x768" 24.49 1360 1392 1480 1512 768 786 789 807[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]  Modeline "1024x768" 18.71 1024 1056 1120 1152 768 786 789 807[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]  Modeline "768x1024" 19.50 768 800 872 904 1024 1048 1052 1076[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]
[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]
[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]  #common resolutions for android devices (both orientations):[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]  Modeline "800x1280" 25.89 800 832 928 960 1280 1310 1315 1345[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]  Modeline "1280x800" 24.15 1280 1312 1400 1432 800 819 822 841[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]  Modeline "720x1280" 30.22 720 752 864 896 1280 1309 1315 1345[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]  Modeline "1280x720" 27.41 1280 1312 1416 1448 720 737 740 757[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]  Modeline "768x1024" 24.93 768 800 888 920 1024 1047 1052 1076[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]  Modeline "1024x768" 23.77 1024 1056 1144 1176 768 785 789 807[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]  Modeline "600x1024" 19.90 600 632 704 736 1024 1047 1052 1076[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]  Modeline "1024x600" 18.26 1024 1056 1120 1152 600 614 617 631[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]  Modeline "536x960" 16.74 536 568 624 656 960 982 986 1009[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]  Modeline "960x536" 15.23 960 992 1048 1080 536 548 551 563[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]  Modeline "600x800" 15.17 600 632 688 720 800 818 822 841[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]  Modeline "800x600" 14.50 800 832 880 912 600 614 617 631[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]  Modeline "480x854" 13.34 480 512 560 592 854 873 877 897[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]  Modeline "848x480" 12.09 848 880 920 952 480 491 493 505[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]  Modeline "480x800" 12.43 480 512 552 584 800 818 822 841[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]  Modeline "800x480" 11.46 800 832 872 904 480 491 493 505[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]  #resolutions for android devices (both orientations)[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]  #minus the status bar[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]  #38px status bar (and width rounded up)[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]  Modeline "800x1242" 25.03 800 832 920 952 1242 1271 1275 1305[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]  Modeline "1280x762" 22.93 1280 1312 1392 1424 762 780 783 801[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]  Modeline "720x1242" 29.20 720 752 856 888 1242 1271 1276 1305[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]  Modeline "1280x682" 25.85 1280 1312 1408 1440 682 698 701 717[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]  Modeline "768x986" 23.90 768 800 888 920 986 1009 1013 1036[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]  Modeline "1024x730" 22.50 1024 1056 1136 1168 730 747 750 767[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]  Modeline "600x986" 19.07 600 632 704 736 986 1009 1013 1036[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]  Modeline "1024x562" 17.03 1024 1056 1120 1152 562 575 578 591[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]  Modeline "536x922" 16.01 536 568 624 656 922 943 947 969[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]  Modeline "960x498" 14.09 960 992 1040 1072 498 509 511 523[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]  Modeline "600x762" 14.39 600 632 680 712 762 779 783 801[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]  Modeline "800x562" 13.52 800 832 880 912 562 575 578 591[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]  Modeline "480x810" 12.59 480 512 552 584 810 828 832 851[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]  Modeline "848x442" 11.09 848 880 920 952 442 452 454 465[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]  Modeline "480x762" 11.79 480 512 552 584 762 779 783 801[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]EndSection[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]
[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]Section "Screen"[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]  Identifier "dummy_screen"[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]  Device "dummy_videocard"[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]  Monitor "dummy_monitor"[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]  DefaultDepth 24[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]  SubSection "Display"[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]    Viewport 0 0[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]    Depth 24[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]    #Modes "32768x32768" "32768x16384" "16384x8192" "8192x4096" "5120x3200" "3840x2880" "3840x2560" "3840x2048" "2048x2048" "2560x1600" "1920x1440" "1920x1200" "1920x1080" "1600x1200" "1680x1050" "1600x900" "1400x1050" "1440x900" "1280x1024" "1366x768" "1280x800" "1024x768" "1024x600" "800x600" "320x200"[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]    Modes "1920x1440" "1920x1200" "1920x1080" "1600x1200" "1680x1050" "1600x900" "1400x1050" "1440x900" "1280x1024" "1366x768" "1280x800" "1024x768" "1024x600" "800x600" "320x200"[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]    #Virtual 32000 32000[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]    #Virtual 16384 8192[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]    Virtual 1920 1080[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]    #Virtual 5120 3200[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]  EndSubSection[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]EndSection[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]
[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]Section "ServerLayout"[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]  Identifier   "dummy_layout"[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]  Screen       "dummy_screen"[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]  InputDevice  "dummy_mouse"[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]  InputDevice  "dummy_keyboard"[/FONT][/COLOR]
[COLOR=#4C2F2D][FONT=Courier]EndSection[/FONT][/COLOR]

```

---

