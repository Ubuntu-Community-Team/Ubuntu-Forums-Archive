---
title: "[SOLVED] GDM appearance settings reset after restart and will not change back"
date: 2008-06-05
forum: General Help
---

### Post by Kimos on 2008-06-05
Barely know what I'm asking, but here goes...

I'm running 8.04 and it has been stable for some time. I restarted today and when it came back up my Gnome Appearance Settings were all messed up. Things like, the icons, window widgets, fonts and font sizes, etc were all reset to Gnome defaults. If I go into the Appearance Settings they all show that they are still set as they were before restart. Making any changes in here do not alter the default appearance of the desktop. I've attached a screenshot that shows all of this.

Oddly, Compiz-Fusion and Emerald are all working properly. The system seems to be running mostly normally otherwise. The only other real problem I've been able to find is an error about power management, which is odd because this is not a laptop. A Gnome notify message pops up saying power management did not start correctly and I should contact my computer. This is reflected in syslog:
```
Jun  5 06:54:36 sephiroth gnome-power-manager: (kevin) no gconf schema installed!
```

I did not notice anything else anomalous in dmesg/syslog. 

A number of updates have been applied since last restart so I couldn't even start to guess which one of them may have caused this problem.

Any direction or suggestions are appreciated.

---

### Post by rufus25 on 2008-06-05
It seems I got exactly the same problems (using Ubuntu 8.04 32bit).

After some automatic updates a couple of days ago I rebooted and got the error message about the gnome-power-manager (popup  in german: [http://img149.imageshack.us/img149/6600/bildschirmfotoag6.png](http://img149.imageshack.us/img149/6600/bildschirmfotoag6.png)). But purgin and re-installing gnome-power-manager seemed to solve it for me:

```
sudo apt-get purge gnome-power-manager gnome-applets
sudo apt-get install gnome-power-manager gnome-applets gnome-session ubuntu-desktop
```

Anyway, i still got the fancy pannels, icons, windowborders, etc. like you:
[http://img139.imageshack.us/img139/2025/bildschirmfoto1cx7.png](http://img139.imageshack.us/img139/2025/bildschirmfoto1cx7.png)

It *seems* to be GTK/Metacity related, if load emerald, i can use different window borders from themes. The pannels and the window contents remain unimpressed:

[http://img394.imageshack.us/img394/6580/bildschirmfoto2bk1.png](http://img394.imageshack.us/img394/6580/bildschirmfoto2bk1.png)

---

### Post by Kimos on 2008-06-05
Ok, got it fixed.

The power management error was key. Something caused the gconf schemas to become unregistered. I re-registered them and restarted X and everything came up as it was:
```
cd /usr/share/gconf/schemas/
sudo /usr/sbin/gconf-schemas --register *.schemas
```

Very strange problem. For reference, I found this in a couple other threads:
[http://ubuntuforums.org/showthread.php?p=5120870](http://ubuntuforums.org/showthread.php?p=5120870)
[http://ubuntuforums.org/showthread.php?t=127660](http://ubuntuforums.org/showthread.php?t=127660)

---

### Post by Kimos on 2008-06-05
> **rufus25 said:**
> It seems I got exactly the same problems (using Ubuntu 8.04 32bit).

It *seems* to be GTK/Metacity related, if load emerald, i can use different window borders from themes. The pannels and the window contents remain unimpressed

Yeah, I'm running the same version and it's definitely Gnome related. Reloading gconf cleaned it all up for me. Hopefully you'll be as fortunate. 

I'm very lucky to have stumbled onto that thread though.. I didn't even know the gconf *.schemas existed, let alone that the could be registered and unregistered!

---

### Post by rufus25 on 2008-06-05
Yeah! It worked. Thanks a lot :)

---

### Post by John.Gaythorpe on 2008-06-10
Gconf schema error messages were the key for me after the latest set of updates caused the same errors and hosed the schema.

Running these as above:


Code:
cd /usr/share/gconf/schemas/
sudo /usr/sbin/gconf-schemas --register *.schemas

Put everything back.

Obviously something in the update cycle unregisters the schema and it should be re-registered.

---

