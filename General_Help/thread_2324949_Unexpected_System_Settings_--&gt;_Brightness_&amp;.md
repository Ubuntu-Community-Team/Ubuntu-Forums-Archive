---
title: "Unexpected System Settings --&gt; Brightness &amp; Lock behavior"
date: 2016-05-17
forum: General Help
---

### Post by jamesisin on 2016-05-17
If I set "Turn screen off when inactive for:" to "Never" and "Lock screen after:" to "5 minutes" (or any amount), the screen never locks.  I want it to lock after five minutes without turning off the screen.  What gives?

---

### Post by QDR06VV9 on 2016-05-17
[s]In Gnome 3., gnome-screensaver doesn't exist, and[/s] screen locking is part of Gnome Shell.

They have re implemented some functions, but not all. On Ubuntu you can access all power-related settings with dconf-editor from org.gnome.settings-daemon.plugins.power.

OR

You can use x-screensaver as described here:
[http://askubuntu.com/questions/64086/how-can-i-change-or-install-screensavers](http://askubuntu.com/questions/64086/how-can-i-change-or-install-screensavers)
Hope this is useful

---

### Post by jamesisin on 2016-05-17
Thanks, runrickus.  All of what you say seems accurate enough.  I'm not clear how it helps me though.

I did fine the function "lock-delay" under org --> gnome --> screensaver and it is set to 300.  This says that the delay represents the time after the screen is dowsed before it is locked.  I really don't care about the screen getting turned off (I want it to stay on in fact), but I want the screen to lock anyway.

Also, if I manually lock the screen it still dowses the screen (which I don't want).

---

### Post by QDR06VV9 on 2016-05-17
> Also, if I manually lock the screen it still dowses the screen (which I don't want).

Well maybe have look here: [http://askubuntu.com/questions/216783/ubuntu-12-10-turn-screen-off-when-inactive-for-never-still-turns-off](http://askubuntu.com/questions/216783/ubuntu-12-10-turn-screen-off-when-inactive-for-never-still-turns-off)

---

