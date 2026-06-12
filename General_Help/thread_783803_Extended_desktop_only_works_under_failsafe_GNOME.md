---
title: "Extended desktop only works under failsafe GNOME"
date: 2008-05-06
forum: General Help
---

### Post by ezramorris on 2008-05-06
Hi,
I've been trying to set up dual monitors/extended desktop on my laptop (ATI card). I almost got it working using
```
sudo aticonfig --dtop horizontal
```
I restarted the computer, and tried to log on, but got this message:
> Your session only lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of disk space. Try logging in with one of the failsafe sessions to see if you can fix this problem.

/etc/gdm/Xsession: Beginning session setup...
Setting IM through in-switch for locale=en_GB.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
Checking for nVidia: not present.
Starting Xgl with options:  -accel xv:pbuffer -accel glx:pbuffer -nolisten tcp -fullscreen -br +xinerama
Waiting 10 more seconds for Xgl to start...
xmodmap: unable to open display ':**[COLOR="Red"]4[/COLOR]**'
cannot open display:
Run '/usr/bin/seahorse-agent --help' to see a full list of available command line options.

**[COLOR="Red"]4[/COLOR]**: this number changed each time I tried to log on.

I then tried what it suggested, and logged on to failsafe GNOME. To my surprise, the extended desktop ran perfectly.

Unfortunately, I could still not log on normally after unplugging the external monitor, but I fixed this by running:
```
sudo aticonfig --dtop single
```
So, is there any way to fix this, or disable startup programs to find the culprit? I disabled compiz starting at logon, but the problem still existed.

Thanks in advance.

---

### Post by ezramorris on 2008-05-15
After playing around with some startup programs, I managed to get an extended desktop sort of working, provided compiz was disabled.

However, one issue still exists.
My monitor setup is as follows:
```
--------------- -----------------
|Laptop screen| |    Monitor    |
|  1280x800   | |   1280x1024   |
|             | |               |
--------------- |               |
                |               |
                -----------------
```
Since I used 
```
aticonfig --dtop horizontal
```
the screens now seem to both have an 1280x800 resolution, resulting in the external monitor looking stretched.

However, in "Screen resolution" and "Screens and graphics", it appears as if I have one monitor with a 2560x800 resolution, so I cannot change the resolution. Is there any solution for this?
Thanks.

---

### Post by sfenton on 2008-05-19
Can you provide some specifics on how you fixed it? I'm experiencing the same problems when I try to attach an external monitor. It's a laptop with the ATI Radian Mobility X1300 card.

---

### Post by ezramorris on 2008-05-20
> **sfenton said:**
> Can you provide some specifics on how you fixed it? I'm experiencing the same problems when I try to attach an external monitor. It's a laptop with the ATI Radian Mobility X1300 card.

I **think** this is what I did (did several things which didn't work).
[LIST=1]
[*]Firstly make sure you have the accelerated graphics driver (if applicable) enabled in System>Admin>Hardware Drivers. Restart computer if required.
[*]From a terminal, run: ```
sudo aticonfig --initial
```. This sorts out xorg.conf.
[*]Restart your computer making sure you have the second monitor plugged in.
[*]Assuming you can log in OK, open a terminal and type ```
sudo aticonfig --dtop horizontal
```
[*]Log out and log back in again, and you should have an extended desktop.
[/LIST]
Notes: 
[LIST]
[*]To go back to a single monitor, type ```
sudo aticonfig --dtop single
```
[*]If you have some really weird, unusable graphics, press Ctrl-Alt-Backspace to restart X, log in to failsafe terminal, then run that command ^^.
[*]Using this method, the monitors will have the same resolution, but the screen resolution settings will think you just have one really wide monitor.
[/LIST]
Hope this helps. Let me know how you get on. You can view all the options for aticonfig by simply typing:
```
aticonfig
```

---

### Post by zeny on 2008-05-20
I'm having the same problem with my setup. I'm using an Nvidia card though. Basically my main screen is my monitor and I wish to "Extend" onto my TV, however this doesn't work. I can only create a second workstation screen with Twinx, and even then it crashs.

---

### Post by ezramorris on 2008-06-19
> **zeny said:**
> I'm having the same problem with my setup. I'm using an Nvidia card though. Basically my main screen is my monitor and I wish to "Extend" onto my TV, however this doesn't work. I can only create a second workstation screen with Twinx, and even then it crashs.

Don't know much about nvidia, but I think the equivalent command is:
```
sudo nvidia-settings
```
I think you can run it as normal user, but the settings will reset after a reboot.

You may have to install it first
```
sudo apt-get install nvidia-settings
```

---

