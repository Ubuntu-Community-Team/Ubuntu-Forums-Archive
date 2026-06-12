---
title: "Hardware sensors?"
date: 2006-07-02
forum: General Help
---

### Post by Just4 on 2006-07-02
Linux and Ubuntu have been great thus far, I'm using it quite frequently (and more often than Windows it seems anymore.) but there are a few things I'm missing in it, one is the ability to monitor hardware (Temperature, etc) in windows I use SpeedFan for all my monitoring, but is there a way to do it within Linux? (And create a tray icon so I can keep informed about the temps?) - Also, the ability to check the hard drives SMART status would be nice as well. Any ways I can do this? Any programs/addons? - Thanks in advance for any help.

---

### Post by scxtt on 2006-07-02
check out lm-sensors (temps) and hddtemp (smart) ... lm-sensors can be a pain, (x)mbmon works well w/o modules ... if you want to integrate it w/ gnome, lm-sensors is your best bet (i'm using it now to monitor my CPU temp [ also works w/ mb and chipset ]) ...

---

### Post by kripkenstein on 2006-07-02
lm-sensors isn't fun to set up, but it works. 

You can use [fancontrol]("http://www.ubuntuforums.org/showthread.php?t=42737") to control the speed of your fans.

---

### Post by Just4 on 2006-07-02
Any good tutorials anywhere on how to setup lm-sensors?

---

### Post by scxtt on 2006-07-02
i've fought w/ it in the past (mainly in Fedora), but in Ubuntu all i had to do was install the package (lm-sensors), run "sensors-detect" and then make sure the module was loaded @ boot time (add it to /etc/modules) -- even when it wasn't i could easily run "sudo modprobe w83627hf" and get it loaded, then "sensors" worked like a charm and i could use the gnome applet to see anything i wanted ... give that a shot, see what you get ...

---

