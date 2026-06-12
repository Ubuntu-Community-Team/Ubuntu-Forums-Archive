---
title: "Run Terminal command on login"
date: 2012-10-18
forum: General Help
---

### Post by euphoric_anomaly on 2012-10-18
I was wondering if there was a way to create a terminal command that would run as soon as I log into Ubuntu.

I have a text file with my "max resolution" settings (xrandr..etc) that I copy n paste into terminal to change the resolution. Ubuntu cannot detect my monitor because I have a DVI output from the computer going into a VGA connector on the monitor (I didn't set it up that way, just the way it came from the person I bought it from).

I tried to create a startup program that would run Terminal with the xrandr lines to change the res, no luck. It didn't do anything as far as I can tell.

All I want it to do is take over the copy/paste job that I have to do each time I log in.

Any suggestions would be greatly appreciated! Thank you

---

### Post by papibe on 2012-10-18
Hi euphoric_anomaly.

Try Startup Applications. Read more about it [here]("https://help.ubuntu.com/community/AddingProgramToSessionStartup").

Regards.

---

### Post by Wim Sturkenboom on 2012-10-18
Have you tried to create a xorg configuration file with the appropriate settings?

---

### Post by 2F4U on 2012-10-18
Is the script working when you manually execute it in a terminal? I guess it would be best if you post the script to prevent any misunderstanding.

---

### Post by euphoric_anomaly on 2012-10-18
this is what i have to copy and paste into terminal each time i want to change the res:

xrandr --newmode "1280x1024_60.00" 109.00 1280 1368 1496 1712 1024 1027 1034 1063 -hsync +vsync
xrandr --addmode VGA1 1280x1024_60.00
xrandr --output VGA1 --mode 1280x1024_60.00

---

