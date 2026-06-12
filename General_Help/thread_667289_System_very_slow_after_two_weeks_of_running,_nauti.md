---
title: "System very slow after two weeks of running, nautilus particularly"
date: 2008-01-14
forum: General Help
---

### Post by jnoreiko on 2008-01-14
I have a system that's got to be on all the time to stream radio to the internet & store an archive of our station's output.

It's been running for about two weeks now, and it's really slow, nautilus in particular. Opening a new nautilus window takes something like a minute. At the weekend I had to copy some audio files to a flashdrive and it was painfull slow.

All the system runs apart from the basic Ubuntu 7.10 stuff is darkice, a streaming app which I recompiled to have mp3 support. There's a perl script run by cron every hour.
The system is brand new, it's a Sempron of some sort with 1gig of ram. I would have thought it could easily handle what's being run on it.

I tried logging out, in case nautilus doesn't like running continously for so long, but just been on the phone to the manager who logged in and couldn't open a nautilus window from the panel.
I got him to launch terminal from the Applications menu and that wasn't too bad apparently.

Any ideas of what's causing this and what can be done?

---

### Post by p_quarles on 2008-01-14
Since this machine is for all intents and purposes a production server, I would recommend ditching the default desktop environment (Gnome) and using a light window manager (e.g., Fluxbox) along with a lighter file manager (e.g., Thunar, Rox-filer, Midnight-Commander). 

A box running Linux can stay up indefinitely. A box running a complicated GUI environment is another story altogether.

---

### Post by jnoreiko on 2008-01-14
If it's the GUI in general that's slowing it down...
is there a way to quit the GNOME gui completely when I log out, and launch it up again when I log in?

People only need to log in to the machine every few days. And since that's usually only to take a copy of archived files, that could be done through the network instead.

---

### Post by pieisgood4589 on 2008-01-14
Yes, switching to Ubuntu server might also be a nice idea, although you can install fluxbox in a breeze- [http://ubuntuforums.org/showthread.php?t=116759](http://ubuntuforums.org/showthread.php?t=116759)

Or, just switch completely to Geubuntu (E-17) which also looks VERY nice and is EXTREMELY fast, or to Fluxbuntu (Fluxbox) which is even faster. :guitar:

---

### Post by p_quarles on 2008-01-14
> **jnoreiko said:**
> If it's the GUI in general that's slowing it down...
is there a way to quit the GNOME gui completely when I log out, and launch it up again when I log in?

People only need to log in to the machine every few days. And since that's usually only to take a copy of archived files, that could be done through the network instead.
Sure:
```
sudo /etc/init.d/gdm stop
```
will log you out. Replace "stop" with "start" to bring it back up.

---

### Post by jnoreiko on 2008-01-17
> **p_quarles said:**
> Sure:
```
sudo /etc/init.d/gdm stop
```
will log you out. Replace "stop" with "start" to bring it back up.

Thanks!

I've done that, and 'top' is still showing two instances of Nautilus being run by the regular user, using up 50% of CPU between them.
Is it safe to kill them?

Also, when I CTRL+ALT+F7, I see a lot of 'Reloading system log daemon'. Is that normal?

---

