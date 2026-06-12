---
title: "undisplayablescreen resolution"
date: 2008-04-18
forum: General Help
---

### Post by johnthomson on 2008-04-18
Yesterday my computer booted into 1024*768 resolution instead of the usual 1280*960.
When I corrected the resolution nothing changed, in fact any resolution I set was displayed as
1024. Today when I boot up my screen will not sync, I get an over-range message, and can't boot
into the normal graphical environment. Obviously something has gone badly wrong.I can boot
into a terminal window (looks like 1024*768) and the xorg.conf is OK no strange frequencies,
all resolutions are in the range of my display. Is there some other file also affecting screen resolution,
or a way of getting into a low resolution graphical environment to try to fix the problem.

Many thanks for any help, john

---

### Post by confused57 on 2008-04-18
If you mean you can boot to Recovery Mode, then try reconfiguring your xorg.conf:
```
dpkg-reconfigure xserver-xorg
```
if you're able to get to a console, using "Ctrl+Alt+F2", then you would need to log in, then:
```
sudo dpkg-reconfigure xserver-xorg
```

You might want to have your refresh rates for your monitor to ensure they're correctly entered.

---

