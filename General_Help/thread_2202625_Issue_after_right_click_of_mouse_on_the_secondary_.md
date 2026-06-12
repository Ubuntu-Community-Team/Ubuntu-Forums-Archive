---
title: "Issue after right click of mouse on the secondary display"
date: 2014-01-30
forum: General Help
---

### Post by yevhen2 on 2014-01-30
Hi, All,

I installed second monitor customizing xorg.conf file.(second monitor wasn`t detected automaticly). But after all I am experiencing very strange issue. After pressing right button on the secondary display nothing responses, except I still can move the cursor. As I am new to Linux, and google doesn`t know about similar issues, I am asking you, what could be a problem.

My Ubuntu version - Linaro 11.10

Changes in xorg.conf:

[COLOR=#000000][FONT=Ubuntu Beta]Section "InputDevice"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]        Identifier      "Generic Keyboard"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]        Driver          "kbd"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]        Option          "XkbRules"      "xorg"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]        Option          "XkbModel"      "pc105"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]        Option          "XkbLayout"     "us"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]EndSection[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta] [/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta] [/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]Section "InputDevice"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]        Identifier      "Mouse1"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]        Driver          "mouse"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]        Option          "CorePointer"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]        Option          "Buttons"       3[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]EndSection[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta] [/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]Section "Device"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]        Identifier      "LVDS"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]       Driver          "fbdev"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]        Option          "fbdev"         "/dev/fb0"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]EndSection[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta] [/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]Section "Device"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]        Identifier      "HDMI"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]        Driver          "fbdev"                        [/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]        Option          "fbdev"         "/dev/fb2"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]EndSection[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta] [/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]Section "Monitor"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]        Identifier      "LVDS Monitor"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]EndSection[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]Section "Monitor"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]        Identifier      "HDMI Monitor"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]EndSection[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta] [/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta] [/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]Section "Screen"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]        Identifier      "LVDS Screen"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]        Monitor         "LVDS Monitor"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]        Device          "LVDS"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]EndSection[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta] [/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]Section "Screen"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]        Identifier      "HDMI Screen"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]        Monitor         "HDMI Monitor"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]        Device          "HDMI"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]EndSection[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta] [/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]Section "ServerLayout"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]        Identifier      "Dual Layout"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]        Screen 0        "LVDS Screen"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]        Screen 1        "HDMI Screen" RightOf "LVDS Screen"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]        InputDevice     "Mouse1"    "CorePointer"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]        Option          "Xinerama"  "of"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]EndSection



[/FONT][/COLOR]Respond to sudo grep -F "(EE)" /var/log/Xorg.0.log :

    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[  4317.491] (EE) SIGMACHIP USB Keyboard: failed to initialize for relative axes.

Thank you in advance,
Yevhen

P.S. Sorry for my poor English

---

