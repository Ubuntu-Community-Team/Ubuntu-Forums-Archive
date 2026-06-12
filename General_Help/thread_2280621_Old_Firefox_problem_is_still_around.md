---
title: "Old Firefox problem is still around"
date: 2015-06-01
forum: General Help
---

### Post by Lloydb39 on 2015-06-01
I searched for this and found it happening as far back as 2008, which is a bit worrisome. No solution found. Occasionally, Firefox will fail to close a tab or do anything else. The window will gray out. I usually have to force quit and restart. Anyone know the cause or if there is a fix?

---

### Post by dino99 on 2015-06-01
i think you might have some borked config file(s), either: .local, .config, .gnome2 or .gconf
they are all 'hidden' files (ctrl+h to unhide) and are automatically cleanly recreated on the next boot if you either rename them or simply delete them (but your custom settings are gone then (can also be the cause trouble))

---

### Post by nerdtron on 2015-06-01
It does happen, especially when you have lots of tabs and computer is running out of memory, and most likely to happen when firefox is open for extended periods of time.

I dunno, I just close and re-open firefox, my tabs will be restored anyway when it re-launches.

---

### Post by Lloydb39 on 2015-06-01
I rarely have more than three tabs open and I have 8 gigs of memory. I'm a little hesitant to wipe the config files so I guess I'll live with it. Seems like Mozilla could have fixed it by now, though.

---

### Post by philinux on 2015-06-01
Some website's scripts are to blame. Natwest in UK Grey's out on the login screen for ages. Using no script solved that site.

---

### Post by leunam12 on 2015-06-01
Corrupt extension? have you tried safe mode?

```
firefox -safe-mode
```

---

