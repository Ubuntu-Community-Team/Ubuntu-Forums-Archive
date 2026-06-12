---
title: "Set resolution for a headless machine at startup"
date: 2018-07-12
forum: General Help
---

### Post by hollov.ub on 2018-07-12
Hi guys,

I have a headless Lubuntu machine which I manage with TeamViewer. The screen resolution is 1024x768 by default. I can set it to 1920x1080 with this 3 lines of command

```
[COLOR=#000000][FONT=Courier New]xrandr --newmode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync[/FONT][/COLOR][COLOR=#000000][FONT=Courier New]
[/FONT][/COLOR][COLOR=#000000][FONT=Courier New]xrandr --addmode VIRTUAL1 1920x1080_60.00[/FONT][/COLOR][COLOR=#000000][FONT=Courier New]
[/FONT][/COLOR][COLOR=#000000][FONT=Courier New]xrandr --output VIRTUAL1 --mode 1920x1080_60.00[/FONT][/COLOR]
```

But this only works if I run the lines one-by-one, and gives me error when I try to put it in a bash script.
I'd like to create a bash script and run it automatically at machine startup.
Can you help me with this?

---

### Post by TheFu on 2018-07-12
I've never used teamviewer.

Have you tried putting a delay between the commands?  sleep 2s

You can't put these into the machine startup. It has to happen after VNC is running.  But isn't there a way to have the VNC client specify the resolution you want?  I don't use VNC, but with rdesktop and x2go, the resolution is a client-side setting.

---

### Post by hollov.ub on 2018-07-13
Ohhh sorry...maybe my post was misleading...
TeamViewer is irrelevant. These commands are not TeamViewer specific commands.

1024x768 is the default resolution because there's no monitor connected to the machine. So I'd just like to add a fullHD mode to my machine (not to TeamViewer)

Anyway! I've found something that seems useful. I don't need to create a bash script and run it at startup. I just need to make these xrandr commands persistent as described here:
[https://wiki.ubuntu.com/X/Config/Resolution#Setting_xrandr_changes_persistently](https://wiki.ubuntu.com/X/Config/Resolution#Setting_xrandr_changes_persistently)

Haven't tested it yet. Hope it'll work

---

### Post by TheFu on 2018-07-13
You shouldn't  mention things that have NOTHING to do with the issue.  I was thinking that xrandr only deals with the local X/Server so it wouldn't have any impact for any remote desktop, but because I don't use teamviewer, I wasn't 100% positive that it didn't somehow grab the settings from there.

If there isn't a monitor connected, why does the resolution matter at all? You've lost me again. For quick resolution changes, I've found nothing easier than lxrandr, if you want a tiny, effective, GUI control.  I use it all the time to help connect my laptop with projectors before presentations. Easily enables/disabled and has controls for resolutions and refresh rates.  Very handy, though for a machine that doesn't move, a little xrandr script is easier, especially if automated.

Lots of things around the display management are changing. 17.10 switched from X11 to Wayland as the default.  I doubt the xorg settings will work. 18.04 switched back to xorg as the default, however.

---

