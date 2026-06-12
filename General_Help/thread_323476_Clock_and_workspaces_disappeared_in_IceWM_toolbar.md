---
title: "Clock and workspaces disappeared in IceWM toolbar"
date: 2006-12-22
forum: General Help
---

### Post by finferflu on 2006-12-22
Hi all,

I've been playing around with themes on IceWM, and suddenly my clock disappeared from the toolbar, I've looked into ~/.icewm/preferences, and it appears that it should be there:
```

# Show clock on task bar
TaskBarShowClock=1 # 0 / 1
```

but it's not! How can I put it back? I can't use this Windows Manager without a clock, and it's a real pity.

Also my workspaces have disappeared as well, so I have only one available, which is ugly!
Any tip will be greatly appreciated!

Thanks!

---

### Post by finferflu on 2006-12-22
Sorted!

I've just noticed a mistake in the preferences file, there was a line like 

IconPat"

in the way, so I deleted it and restarted IceWM, and everything is in its proper place now :cool:

---

### Post by clarezoe on 2008-07-17
Sorry to post get this post up, but I have the same problem now with no luck, delete the "IconPath" doesn't help me.

> # Show clock on task bar
TaskBarShowClock=1 # 0 / 1

# Task bar clock uses nice pixmapped LCD display
TaskBarClockLeds=1 # 0 / 1
This is my relavent settings in the preference file.

Any help? Thanks!

---

