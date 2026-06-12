---
title: "External (HDMI) monitor issues on laptop upgrade to Ubuntu 17.10"
date: 2017-10-25
forum: General Help
---

### Post by fh-faraz-hussain on 2017-10-25
Hi, I'm having issues using in controlling the laptop and external monitor screens after updating to Ubuntu 17.10.

When Ubuntu starts, during the lightdm stage, the external monitor is recognized and is placed to the right of the laptop screen (non-mirorred). At this point, both screens are functional. 

Once I log in, I usually want to turn off the laptop screen. That is the part that doesn't work. When I attempt this, it turns off the external monitor too. More frustratingly,  I have a hard time turning it back on. I have tried this both using xrandr and using one of gnome's tools.  I see this problem on both X and wayland.

What seems to work is unplugging the HDMI cable and replugging it. But its a pain to have to do this all the time. 

This is the command I was using in 17.04 to turn off the laptop screen and use only the external monitor:

```
xrandr --output HDMI1 --auto --output eDP1 --off
```

Unfortunately, it now turns off both. But later, after trying this and arandr multiple times, it starts working.

---

