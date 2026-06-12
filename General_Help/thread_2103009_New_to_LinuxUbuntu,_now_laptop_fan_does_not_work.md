---
title: "New to Linux/Ubuntu, now laptop fan does not work"
date: 2013-01-08
forum: General Help
---

### Post by eckliptic on 2013-01-08
I have an old Dell Latitude D420 that I installed Xubuntu on.  I just realized that ever since the reinstall the laptop fan has completely stopped working.

I poked around online and have tried lm-sensors, which detects the CPU temp but doesnt see any fans.  I tried pwmconfig and it says I dont have any pwm-capable sensor modules installed.  Ive looked in my BIOS but there are not fan control settings available.

Any help would be appreciated.

---

### Post by rrich1974 on 2013-01-09
are you sure that is not working? what the lm-sensors shows? 
the lm-sensors doesnt detect my fan too, but it detects the temp of my cpu. 
maybe your fan is working very slow. if your fan woudnt working at all, be sure that you will experience shutdown due to the overheating. on the other hand, use a vacuum cleaner to clean up the dust and lint from your fan and keyboard.

---

### Post by eckliptic on 2013-01-09
Definitely not working.  Prior to going from windows to linux the fan has always been quite loud and easy to hear, now i hear nothing.  Idle temps are around 50C and goes to 60C with use.  Use to be 10 degrees less before that.

sensors: (i just started up my laptop so the CPU is still warming up

acpitz-virtual-0
Adapter: Virtual device
temp1:        +43.5°C  (crit = +107.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +40.0°C  (crit = +100.0°C)
Core 1:       +44.0°C  (crit = +100.0°C)

---

### Post by rrich1974 on 2013-01-10
the only thing i can say is that you can try other distribution. you can try fedora 17 gnome and see what is going on.

---

### Post by black veils on 2013-01-14
try bodhi linux, maybe it has better driver support for your old hardware.

you will want to install preferred desktop environment, and all applications as it deliberately minimal. if you install lubuntu-desktop for example, it should pull most or all necessary software in for you.

you may want to install gnome-system-tools

if you feel there is something missing, have a look at xubuntu-desktop dependancies for ideas on what other applications to install.

i had a similar problem, the fan worked but very little, and something else was making the cpu hot, bodhi was the only ubuntu based distro i tried that worked. i installed xfwm4 to replace openbox window manager, and xfce4-settings-manager to configure window manager. you can make menu shortcuts to the bin files for those settings. i couldnt switch the proper way though, i had to add xfwm4 --replace to the startup applications file, located at /etc/xdg/lxsession/Lubuntu/autostart

---

