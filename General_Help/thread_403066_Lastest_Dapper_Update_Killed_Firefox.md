---
title: "Lastest Dapper Update Killed Firefox"
date: 2007-04-06
forum: General Help
---

### Post by moot on 2007-04-06
After I installed the latest update for Dapper, Firefox closes almost immediately after I run it, only staying open long enough to see my two homepage tabs start to render, forcing me to use Mozilla even after I rebooted.  What happened?

Edit: I ran Firefox using gksudo and it didn't close immediately, but it ran as a clean installation without any of my settings, bookmarks, extensions or cookies.

---

### Post by moot on 2007-04-06
I saw this thread about the latest Feisty update killing Opera and realized that I got a similar error:

```
moot@moot-desktop:/usr/bin$ firefox -profilemanager

(firefox-bin:7449): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.

(firefox-bin:7449): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
Segmentation fault
```

My one and only profile is moot, so I selected it and the exact same thing happened.  I tried running it again using sudo but it only showed a clean install profile called default, is there anyway I can use moot as root?

---

