---
title: "Create terminal program on login"
date: 2012-11-07
forum: General Help
---

### Post by euphoric_anomaly on 2012-11-07
I would like to create a "script" or something of the sort that will run a xrandr script to change my resolution while logging in.

I've tried the start-up applications program, but that didn't seem to help.

I've received suggestions to edit the xorg.conf file, however others say that 12.04 doesn't use that file. I just upgraded to 12.10 tonight, so I'm sure it still applies.

Here is what I would like the terminal to run when I log in:

xrandr --newmode "1280x1024_60.00" 109.00 1280 1368 1496 1712 1024 1027 1034 1063 -hsync +vsync
xrandr --addmode VGA1 1280x1024_60.00
xrandr --output VGA1 --mode 1280x1024_60.00

Usually I just open up the text file and drag it into the terminal, and it changes the resolution automatically without having to press enter. 

Any help would be greatly appreciated :)

---

### Post by rnerwein on 2012-11-07
> **euphoric_anomaly said:**
> I would like to create a "script" or something of the sort that will run a xrandr script to change my resolution while logging in.

I've tried the start-up applications program, but that didn't seem to help.

I've received suggestions to edit the xorg.conf file, however others say that 12.04 doesn't use that file. I just upgraded to 12.10 tonight, so I'm sure it still applies.

Here is what I would like the terminal to run when I log in:

xrandr --newmode "1280x1024_60.00" 109.00 1280 1368 1496 1712 1024 1027 1034 1063 -hsync +vsync
xrandr --addmode VGA1 1280x1024_60.00
xrandr --output VGA1 --mode 1280x1024_60.00


Usually I just open up the text file and drag it into the terminal, and it changes the resolution automatically without having to press enter. 

Any help would be greatly appreciated :)

hi
just a proposal: store your commands into the ~/.bashrc or ~/.profile

---

### Post by Habitual on 2012-11-07
```
#!/bin/bash
xrandr --newmode "1280x1024_60.00" 109.00 1280 1368 1496 1712 1024 1027 1034 1063 -hsync +vsync
xrandr --addmode VGA1 1280x1024_60.00
xrandr --output VGA1 --mode 1280x1024_60.00
```save as say, ~/fixres.sh
terminal >
chmod 700 ~/fixres.sh
Session (under Preferences?) > autostart* >
new > command could be
gnome-terminal -e "/home/$user/fixres.sh"

I don't use Ubuntu, so the "session > autostart" is quite generic. But it should get you started. :)
"$user" is your loginID. (whoami at console or terminal)

---

### Post by euphoric_anomaly on 2012-11-10
Alright, I figured it out. I made a .sh file, added the #bash tag to it, did a little chmod +x command thing, and added the .sh file to my startup programs. Works like a charm.

thanks for your assistance :)

---

