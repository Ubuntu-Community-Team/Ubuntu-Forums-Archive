---
title: "Setting primary monitor system wide, is there a way?"
date: 2016-04-22
forum: General Help
---

### Post by jerome1232 on 2016-04-22
I have an Nvidia 450 using a vga output for the right most monitor and dvi output for my leftmost monitor.

In BIOS my left most monitor is the only display used, when I'm booted into Ubuntu at my login screen however the order of my monitors is reversed, it thinks my rightmost monitor is on the left and my leftmost on the right. Once I login it swaps them back because I set them up in System Settings-Displays the correct way.

I would like them to be correct at the login screen as well though, I suspect this is an Ubuntu config as my Nvidia card seems to use the dvi connected monitor as the primary display during boot, showing first an nvidia bios screen then my regular POST all on that monitor.

[ATTACH=CONFIG]268523[/ATTACH][ATTACH=CONFIG]268524[/ATTACH]

---

### Post by jerome1232 on 2016-04-23
I found a working solution to setup lightdm's monitor configuration.

If you are logged in as an adminstrative user with the monitor setup you want lightdm to have, you can copy the configuration straight over.

```
sudo cp ~/.config/monitors.xml /var/lib/lightdm/.config/

```

Solution was found here:
[http://askubuntu.com/questions/360886/personalize-monitor-position-before-login](http://askubuntu.com/questions/360886/personalize-monitor-position-before-login)

---

