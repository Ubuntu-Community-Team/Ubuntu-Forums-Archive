---
title: "xgl + dpms/power management problems"
date: 2007-08-30
forum: General Help
---

### Post by weak on 2007-08-30
i'm having some trouble to get power management working properly with xgl/compiz. i'm running feisty on a Targa Traveller 826 (ati x700 with fglrx drivers).

one problem is that the screen won't tun off properly. the screens goes black but the backlight stays on.
second problem is that power management kicks in during movies. screen goes blank while vlc/movie player is running.

the cause for this problems seems to be that xgl has problems with dpms. xgl is running on display 1, which reports no dpms. i can however still use dpms of display 0.
i can turn off the display with
```
DISPLAY=:0 xset dpms force off
```

so a workaround is to set dpms for display 0 at startup. (eg: 'DISPLAY=:0 xset dpms 600 600 600')

this will turn the screen off after the specified idle time. but i can't use gnome-power-manager to set the time (or different times for ac and battery). and i still can't watch movies properly.

there's got to be a better solution?

thx, weak

---

### Post by jocko on 2007-08-30
I had the same problem as you with the monitor and TVout signal blanking during movies. To get rid of it I added the following lines to the "serverflags" section of my /etc/X11/xorg.conf:

```
Section "ServerFlags"
    Option        "blank time"    "0"
    Option        "standby time"    "0"
    Option        "suspend time"    "0"
    Option        "off time"    "0"
EndSection
```

This will turn off dpms completely, though...

---

### Post by weak on 2007-08-30
thx, but i'd like to use dpms :)

---

