---
title: "Screensaver"
date: 2005-10-21
forum: General Help
---

### Post by Ocxic on 2005-10-21
I would like to know if there is a way of turning off the screen saver thru a terminal, everytime my screen saver comes on my comp freezes cause of some bug, i wouldn't care but i can't leave my comp for more then ten min without it coming on and freezing.

---

### Post by ymmotrojam on 2005-10-21
Why do you need it through the Terminal? There's the screensaver configuration panel in System>Preferences>Screensaver (it's near the bottom)

Also, try going through the list and disabling any screensavers that may be more cpu intensive than others...

---

### Post by hobzu on 2005-10-24
Screensaver menu is crashing whole system. How to turn it off from the terminal?

---

### Post by vuknikolic on 2005-11-06
the same thing happens to me. 

the only way i do it is by killing xscreensaver in system monitor.

---

### Post by vuknikolic on 2005-11-06
me again, after killing the xscreensaver with system monitor, go to system>preferences>screensaver, you'll be asked to turn the xscreensaver deamon, just say cancel (or no) and than disable it from the menu.

works fine.

---

### Post by Arktis on 2005-11-06
```
killall xscreensaver
```

---

### Post by Yoda_Oz on 2005-11-07
you could try manually editing the .xscreensaver config file which is located somewhere in your home directory.

---

### Post by ceesa on 2005-11-23
I need to disable screensavers thru a terminal also. When a screen saver runs (not all, but have not figured out which ones) the mouse still moves, but does not function (clicks are not passed thru to the screen manager) and the keyboard is dead (no keys, no caps lock). If I use preferences to try and turn off the screen saver, as soon as the screen saver applet runs and starts displaying the screensaver that it is on (it is still set to Random), the screen and keyboard no longer work. no keys are passed thru, not even Ctrl-Alt-Del.

This is with **ubuntu-5.10-install-i386.iso** on a AMD Athlon XP 3000+ and a ATI Radeon 9000 video display adapter. I am not sure if it was detected, or matters, but I have a ATI TV Wonder PCI adapter installed.

I have'nt had time to muck the system up yet. I have installed XMMS because the default multimedia player does'nt support .MP3s, and was installing the development tools to install mplayer from source so I could view .MPG files.

I hope someone can provide a solution to the video problem, or tell me how to disable the screensaver. I really would like to be able to evaluate Ubuntu.

Best Regards, Ceesa.

---

### Post by ceesa on 2005-11-23
[QUOTE=vuknikolic]me again, after killing the xscreensaver with system monitor, go to system>preferences>screensaver, you'll be asked to turn the xscreensaver deamon, just say cancel (or no) and than disable it from the menu.

works fine.[/QUOTE]


When i do a killall xscreensaver and go into system->preferences->screensaver, the screensaver preview starts running and the system locks up. I also noticed that the system time on the taskbar is no longer being updated, yet the mouse pointer still moves and I can ping the system.

Setting Mode to blank in .xscreensaver works and does not lock up the screen/keyboard.

Any ideas what to try next ?

Regards, Ceesa

---

### Post by 23meg on 2005-11-23
It's possible with xscreensaver-command. To deactivate the screensaver, type ```
xscreensaver-command -deactivate
``` Take a look at the manpage for more options. This is a very flexible tool for use in scripts.

---

### Post by cisthebestuk on 2005-11-26
I too am having the same problems with a very fresh install. System is a AMD XP3400 512mb ram running Breezy i386. ATI graphics card, but no extra drivers installed for it.

The system locks as soon as screensaver cuts in and opening the screensaver preferences causes it too.  I get 99% CPU usage for Xorg.

This happens even after I kill xscreensaver using the system monitor. So how do I stop it running by default? Or better still, get a bugfix so we can use the screensavers.

---

### Post by a_little_insight on 2006-02-05
I have had a similar problem.  Every time the screensaver started I wouldn't get any response from the mouse or keyboard, and when I opened the screensaver configuration application everything would lock up.  I eventually found that if I commented out all of the OpenGL screensavers in the .xscreensaver file the problem went away.

---

### Post by fxleytens on 2006-02-08
Had the same problem too. I just de-installed xscreensaver-gl and then OK. Does anyone knows about a patch or update to make GL screensaver working ?

---

