---
title: "How do I show/restore the default indicators in the top panel ?"
date: 2012-11-24
forum: General Help
---

### Post by lemwt on 2012-11-24
I'm using Ubuntu 12.04 (Precice) with Gnome classic with no special effects.

I held the Windows + Alt keys and then right clicked on the mail icon and selected "Remove From Panel" thinking it would remove only that; but it removed everything. 

How do I show/restore the default indicators in the top panel (messages, networking, power, sound, user accounts, time display)? (And please note that I'm not trying to customize it, I've given up on that, I just want to restore it the way it was originally).

---

### Post by llamabr on 2012-11-24
[https://www.google.com/search?q=gnome+restore+panel&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a](https://www.google.com/search?q=gnome+restore+panel&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a)

---

### Post by zombifier25 on 2012-11-24
As a bonus tip, if you want to remove the mail icon from the indicators, remove the indicator-messages package.

---

### Post by stinkeye on 2012-11-24
To restore gnome-panel to default in 12.04 and 12.10 use this terminal command...
```
dconf reset -f /org/gnome/gnome-panel/layout/
```

---

