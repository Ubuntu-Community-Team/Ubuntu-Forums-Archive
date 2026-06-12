---
title: "Screen won't stay powered off"
date: 2014-10-27
forum: General Help
---

### Post by Warlon on 2014-10-27
So my monitor's power button is broken and I can't power it off unless I unplug it. To make life easier I made a desktop shortcut to turn it off with this command

```
xset dpms force suspend
```

My problem is that it won't stay powered off, but keeps waking up every now and then even though nothing seems to be happening on screen. How can I find out what's causing the screen to power up randomly?

I'm running Cinnamon on Ubuntu 14.04.

---

### Post by Warlon on 2014-10-29
Do these power save events get logged somewhere?

---

### Post by tgalati4 on 2014-10-30
dpms is dynamic power management system (Energy Star) that is built into the monitor.  So any stray signal from the VGA cable can cause the monitor to wake up.  Log files are in /var/log.  Some wakeup events are logged.  I would set up a powerstrip with an on/off switch that is conveniently located and use that.

You could put your command in *crontab* and set it for hourly.  That way, every hour the monitor will be put to sleep.

```
crontab -e
```

Of course, that can cause the monitor to go to sleep when you are working, but an active video signal may keep it awake so that you don't notice.

---

