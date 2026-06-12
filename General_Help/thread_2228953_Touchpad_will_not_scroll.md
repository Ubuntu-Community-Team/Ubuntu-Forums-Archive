---
title: "Touchpad will not scroll"
date: 2014-06-10
forum: General Help
---

### Post by Ski_HolmaNM on 2014-06-10
Ok, long story short, I had to delete .config and .cache because my system was screwed up. I am using a toshiba Satellite S870. After I relogged, the system ran perfectly, but now the scrolling on the side of the trackpad will not work. Can anyone tell me how to reinstall the drivers? Many thanks.

---

### Post by mc4man on 2014-06-10
Likely nothing to do with drivers. You are now using the default which is "two-finger-scrolling"
So try with 2 finger if supported
If not or desiring edge-scrolling (1 finger) then many ways - 2 examples
System Settings > Mouse & Touchpad > uncheck Two finger scroll box
or in terminal - 
```
gsettings set org.gnome.settings-daemon.peripherals.touchpad scroll-method "edge-scrolling"
```

---

