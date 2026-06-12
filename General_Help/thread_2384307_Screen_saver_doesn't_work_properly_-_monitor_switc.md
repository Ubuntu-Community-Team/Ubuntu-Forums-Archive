---
title: "Screen saver doesn't work properly - monitor switches back on (16.04 arm64)"
date: 2018-02-05
forum: General Help
---

### Post by xrayed on 2018-02-05
[COLOR=#000000]Hi there,[/COLOR]
[COLOR=#000000]I am using Ubuntu 16.04 on a Arm64 type of system (Nvidia Jetson).[/COLOR]
[COLOR=#000000]Unfortunately I experience the following issue - after a period of inactivity the monitor goes off (as intended), but after roughly 10 seconds in turns on again, but completely blackened (sometimes with a mouse cursor visible).[/COLOR]
[COLOR=#000000]I have experimented a lot so far:[/COLOR]
[COLOR=#000000]- tried to disable gnome-screensaver (including chmod -x /usr/bin/gnome-screensaver)[/COLOR]
[COLOR=#000000]- experimented with "xset dpms" settings and "xset s" settings [/COLOR]

[COLOR=#000000]Nothing helped. The monitor just turns back on. I read about "vbetool", but it's not available on Arm64.[/COLOR]

[COLOR=#000000]Any ideas/hints what to try? As it seems the problem is somewhere in X11, not in Gnome. As even "xset dpms force off" doesn't work properly. Especially weird - after "xset s noblank; xset dpms force off" the screen turns back on with a strange grey picture. After "xset s noexpose; xset dpms force off" the screen turns on again and showing the desktop, but after hitting a key it turns for 1-2 seconds off again and then on. "xset s off" doesn't help either.[/COLOR]

[COLOR=#000000]I've also tried:[/COLOR]
[COLOR=#000000]setterm -blank 5 -powersave powerdown -powerdown 5[/COLOR]

[COLOR=#000000]setterm: terminal xterm-256color does not support --blank[/COLOR]
[COLOR=#000000]setterm: cannot (un)set powersave mode: Inappropriate ioctl for device[/COLOR]


[COLOR=#000000]Many thanks for any help!!![/COLOR]

---

### Post by xrayed on 2018-02-05
In addition, this is the contents of my xorg.conf file:

Section "Module"
    Disable     "dri"
    SubSection  "extmod"
    Option  "omit xfree86-dga"
    EndSubSection
EndSection


Section "Device"
    Identifier  "Tegra0"
    Driver      "nvidia"
    Option      "AllowEmptyInitialConfiguration" "true"
EndSection


Section "Monitor"
   Identifier "DSI-0"
   Option    "Ignore"
EndSection

---

### Post by ajgreeny on 2018-02-05
Try xscreensaver in place of gnome-screensaver; it is much more configurable with many more options as far as I'm aware, and I think some of the comments in [https://askubuntu.com/questions/64086/how-can-i-change-or-install-screensavers](https://askubuntu.com/questions/64086/how-can-i-change-or-install-screensavers) may give you some more useful info.

I am not using unity and Ubuntu but I believe it does not, by default, use a screensaver any more.

---

### Post by xrayed on 2018-02-13
> **ajgreeny said:**
> Try xscreensaver in place of gnome-screensaver; it is much more configurable with many more options as far as I'm aware, and I think some of the comments in [https://askubuntu.com/questions/64086/how-can-i-change-or-install-screensavers](https://askubuntu.com/questions/64086/how-can-i-change-or-install-screensavers) may give you some more useful info.

I am not using unity and Ubuntu but I believe it does not, by default, use a screensaver any more.

Thanks, I just tried this. Uninstalled gnome-screensaver, installed xscreensaver. Unfortunately exactly the same problem - the monitor turns off for about 10 seconds, then back on and remains black...

---

