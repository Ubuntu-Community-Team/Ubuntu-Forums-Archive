---
title: "Slows Down/Lags after a while"
date: 2007-11-04
forum: General Help
---

### Post by thetimekeeper on 2007-11-04
I'm really stumped on this one and it is rather irritating. In short my system starts lagging really badly after some innocuous task.

I usually have Compiz on Customized, Banshee, Firefox, Skype and Pidgin running.

After some random tasks, it could be opening a WINE app, trying to restore my Deluge window, or changing songs, the system starts lagging really badly, and top doesn't show any suspicious process taking up a lot of processing.

The system just lags, fading, launching apps, switching, etc. However, after relogging in, restart the X server, everything pretty much flies again.

Normally when this is not happening, everything works pretty fantastic, at full speed. One time this happened was also when I resumed the system after leaving it on standby for a while.

Does anyone have any ideas on what could be causing this or how to fix it? I'm getting might tired of rebooting my computer every now and then. :(

---

### Post by Pumalite on 2007-11-04
Maybe overheating. Check your fan. Maybe memory. Do memtest.

---

### Post by jksrecko on 2008-01-08
I've experienced such lags, especially when I was using high memory demanding applications. There was no high (not even medium) CPU activity.

That kind of problem happened regularly before, after upgrade to Feisty. It turned out swap partition label/uuid (or something) changed and it didn't get activated. So, slowdown was caused by applications inability to allocate memory (I guess). And system would almost halt, but without significant CPU usage.
There was no complaint about this (lack of memory), not from the app, nor from the system!?

Yesterday, something similar happened, after I resumed my system from standby. I had many applications opened, so I suspect before the suspend, swap was being utilized. After resuming more than 80% swap was used, and about 30% RAM!? System barely responded. I've restarted from prompt, just couldn't wait to close all the apps nicely. Again, there was no significant CPU usage.
I have 1GB swap partition and 1GB RAM (recently upgraded from 512MB).

Is swap needed for suspend? Could this be because I have equal sizes of RAM and swap, and at the time of suspend probably more than half available memory was used? Swappiness is default, so RAM was partially free.

---

### Post by galileon on 2008-05-20
just (re-)discovered swappiness today, and setting it to 20 instead of the default 60 solved the problem for me.

---

