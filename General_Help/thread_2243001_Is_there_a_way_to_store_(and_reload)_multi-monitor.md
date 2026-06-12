---
title: "Is there a way to store (and reload) multi-monitor display configurations?"
date: 2014-09-05
forum: General Help
---

### Post by StevePerkins on 2014-09-05
I have a laptop with two external monitors, for a total of 3 displays sitting on my desk at work.  Two of them are oriented horizontally, and one is oriented vertically.  So I have to do a ton of clicking to get them arranged in the right order, and enable rotation on the vertical monitor (I'm using XFCE, so I do this under "Settings"->"Display").

Several times a week, I have to disconnect my laptop from my desk and take it to a conference room... where I hook up an HDMI cable to yet another screen for presentations to a group.

It is REALLY painful to manually re-build my display settings every time I move from one locatation to another.  I sometimes have to redo this even when rebooting the machine in the same location!  The settings aren't detected and memorized as smoothly as they are under MS-Windows.

Is there a way, either through a GUI tool or even a bash script on the command line, to store display settings and restore them later?

---

### Post by TheFu on 2014-09-05
/etc/X11/xorg.con is where video/monitor settings go.  Normally, a default config is what people use (empty), but for something special, create the file.  Be certain to backup any prior file, so you can put it back if needed.  It is hard to get this working for the uninitiated.  Might be worth starting with the wikipedia article on this stuff first. [https://en.wikipedia.org/wiki/Xorg.conf](https://en.wikipedia.org/wiki/Xorg.conf)

The issue is when the connections to monitors changed. xorg isn't designed for dynamic changes like that.  You could script something to swap in/out the desired xorg.conf as desired, but I think a reboot is needed to force it reinitialized with new settings.

There are lots of example settings for xorg.conf on the internet - be careful to understand everything you put into yours.  The wrong settings don't do physical damage to monitors like it did in the old days, but ...

---

