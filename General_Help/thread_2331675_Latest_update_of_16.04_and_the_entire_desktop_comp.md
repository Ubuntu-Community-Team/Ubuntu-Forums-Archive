---
title: "Latest update of 16.04 and the entire desktop completely disappeared?"
date: 2016-07-24
forum: General Help
---

### Post by psychedelicwonders2 on 2016-07-24
I did the latest update of 16.04 and the entire desktop, sidebar, top bar etc is completely gone.

The only thing left is my background picture & my files that I saved to the desktop itself.

Any idea what the heck happened and how to fix this?

Thanks.

---

### Post by psychedelicwonders2 on 2016-07-27
bump

---

### Post by psychedelicwonders2 on 2016-08-08
Anyone at all?  I've been completely unable to use Ubuntu because of this latest update.

Thanks.

---

### Post by CantankRus on 2016-08-08
Can you access a terminal at the desktop?

---

### Post by W7DAH on 2016-08-08
Same issue here. Tried all the various suggestions on related threads. Sitting here contemplating whether to reload Ubuntu or load some new, more stable flavor of Linux, coz this is just nuts considering that it has been reported so many times previously but is still occurring.

---

### Post by Geoffrey_Arndt on 2016-08-08
OK, . . . I read a few of your other threads (psychcedelec).     Here is what I suggest, but clearly, do what you want:

>   Do a clean install of the 16.04.1 update iso
>   If this is the laptop you've had infinite wifi problems with, rather than getting on the compile/recompile merry-go-round, just get (for about $10.00), the Panda Ultra Wifi 150 nano dongle from Amazon.   Panda consistently provides excellent usb wifi adapters for various flavors of Linux including Ubuntu.   I assume your time is worth more than $10 usd.
>   Keep a change log of the major changes you make on your system.   Even better, create a test partition.

[http://www.pandawireless.com/](http://www.pandawireless.com/)

---

### Post by mastablasta on 2016-08-09
system specs? drivers used?

more here: [SIZE=2]https://ubuntuforums.org/showthread.php?t=1422475
[/SIZE]

---

### Post by psychedelicwonders2 on 2016-08-29
I'm not sure if I can get a terminal, there is nothing to click on.

What is the terminal keyboard shortcut to open it?

Is there some code I can run for you guys before I do a full re-install?

Specs are:

Intel 5820k
16gb ram
EVGA 970 video card
1000w PSU
dual boot 16.04 & win7

Thanks.

---

### Post by CantankRus on 2016-08-29
Do you get to the login greeter screen?

---

### Post by psychedelicwonders2 on 2016-08-29
Yes I get the login screen, after that the background image is there, but no dock or icons at all

---

### Post by CantankRus on 2016-08-29
At the greeter before you put in your password, does ctrl+alt+F1 take you to a terminal login?
ctrl+alt+F7 will take you back to the greeter.

---

### Post by psychedelicwonders2 on 2016-08-29
I just got back from trying that, yes I get the terminal, something fails to load, here is a screenshot:

[ATTACH=CONFIG]270929[/ATTACH]

---

### Post by CantankRus on 2016-08-29
At the bottom of all that do you get a "login:" line?

---

### Post by psychedelicwonders2 on 2016-08-29
yes I did, sorry I wanted to get a good close up of the loading error

---

### Post by CantankRus on 2016-08-29
Once logged in you can install another desktop environment for the moment which may give you
another graphical session you can work with.
Login to the tty1 terminal (ctrl+alt+F1) and run....
```
sudo apt install gnome-session-flashback
```
This will give you 2 more sessions at the greeter accessed from the small ubuntu icon.

ctrl+alt+F7 to get back to greeter.
Log into the Gnome Flashback(Metacity) session.
[ATTACH=CONFIG]270930[/ATTACH] [ATTACH=CONFIG]270931[/ATTACH]

If the new sessions are not showing may have to reboot.
If you can't reboot from the greeter, ctrl+alt+F1, login if not already and run....
```
sudo reboot
```

---

### Post by psychedelicwonders2 on 2016-08-29
Ok I'm in the middle of some website back end upgrading, so once I'm finished I'll try what you suggest and post back here with my results.

Thank you.

---

### Post by CantankRus on 2016-08-29
OK. I'm off to bed.
Some things to do.
Run an update and upgrade and check for errors.
```
sudo apt update && sudo apt upgrade
```

If you manage to get a graphical session, reset compiz (won't work from tty1)
```
dconf reset -f /org/compiz/
```

Were you running nvidia proprietary drivers before update?
Info from Inxi  (sysinfo script) will help.
```
sudo apt install inxi
```

To see what driver is being loaded run...
```
inxi -G
```

eg
```
**[COLOR="#006400"]glen@Xenial:~$[/COLOR] inxi -G**
Graphics:  Card: NVIDIA GF116 [GeForce GTX 550 Ti]
           Display Server: X.Org 1.18.3 drivers: nvidia (unloaded: fbdev,vesa,nouveau)
           Resolution: 1680x1050@59.88hz
           GLX Renderer: GeForce GTX 550 Ti/PCIe/SSE2 GLX Version: 4.5.0 NVIDIA 367.27

```

If using nvidia you can try purging, where the open source nouveau driver should be loaded upon reboot.
```
sudo apt purge nvidia*
```
Reboot.

---

### Post by psychedelicwonders2 on 2016-08-29
Hmm, didn't even past sudo update/upgrade:

[ATTACH=CONFIG]270932[/ATTACH]

Suggestions?

---

### Post by ian-weisser on 2016-08-30
Do it again while connected to the internet.

---

