---
title: "GT 630M: Bumblebee killed the GUI"
date: 2013-03-11
forum: General Help
---

### Post by Archie Moses on 2013-03-11
I'll be clear that I haven't spent as much time reading as I should, only reason I'm posting this now is that every answer seems to be different and I fear I'll do more damage with ready fire aim.

I was playing around with cairo dock, trying to get openGL up.  Laptop is a Dell XPS 14 with GT630m, installed bumblebee.  Didn't like it at all,
 
```
sudo apt-get --purge remove bumblebee
```

Reboot, and poof login screen is gone.  Console still works fine.  Played around a little bit with apt-get reinstall & dpkg-reconfigure lightdm and such, but really don't know what I'm doing so don't want to get serious on it.

---

### Post by Archie Moses on 2013-03-11
```
sudo lightdm start
```

> Failed to use bus name org.freedesktop.DisplayManager, do you have appropriate permissions?

---

