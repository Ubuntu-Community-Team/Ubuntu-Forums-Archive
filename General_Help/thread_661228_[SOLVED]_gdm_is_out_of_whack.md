---
title: "[SOLVED] gdm is out of whack"
date: 2008-01-07
forum: General Help
---

### Post by bwgolling on 2008-01-07
I was reading some quotes by L Torvalds and one of them mentioned the fact that he uses KDE for his desktop, and I got to thinking that maybe I should do that too.
So I installed the whole KDE stuff and shortly realized that I prefer GNOME anyway. So I removed KDE and tried to put my ubuntu 7.10 back to its original state.  Well, most everything worked fine except I can't get gdm to start automatically.
I can only boot into console mode.  I can manually start gdm, but I cannot find the script that should be starting gdm automatically. 
And by the way where is /etc/inittab?

---

### Post by PeterJS on 2008-01-07
Ubuntu uses upstart so there is no /ete/inittab. To get gdm to start up at boot try:
```

sudo dkpg-reconfigure gdm

```

---

### Post by bwgolling on 2008-01-07
Thanks for the try, but alas no good.  I found out that I did have upstart ( altho I didn't know it replaced inittab) and tried to reinstall it earlier.
Any other suggestions?

---

### Post by PeterJS on 2008-01-07
Ok, plan B:
```

sudo update-rc.d gdm defaults 13 01

```
update-rc.d controls when things load and unload when you start and stop your system. So we're telling it that we want to work with gdm and add it to the default boot up and shutdown process, that it's supposed to be the 13th start up position, and the first thing to close on shutdown.

---

### Post by bwgolling on 2008-01-07
That doesn't work.  It reports that the system startup links already exist.

---

### Post by PeterJS on 2008-01-07
Don't know it it's any help but the script that launches gdm is in /etc/init.d/

This is a real puzzler. GDM and X can be started manually so it's not a config issue, of X at least.

---

### Post by bwgolling on 2008-01-08
I found the answer.  The problem was in /etc/X11/default-display-manager.  Originally I just changed kdm to gdm.  The problem resulted from the path being different for gdm.  kdm is /usr/bin/kdm but gdm is /usr/**sbin**/gdm, and it was very easy to overlook.
Thanks for all your help.

---

