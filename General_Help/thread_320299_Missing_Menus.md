---
title: "Missing Menus"
date: 2006-12-17
forum: General Help
---

### Post by TombstoneX on 2006-12-17
i enabled automatic login from:

[http://ubuntuguide.org/wiki/Dapper#How_to_automatic_login_into_GNOME_.28not_secure.29]("http://ubuntuguide.org/wiki/Dapper#How_to_automatic_login_into_GNOME_.28not_secure.29")

Now i have no control for disabling it, adding users, configuring the network.. here are the menus

System >> Administration >> 

i only have the following options:
Device Manager
Network Tools
Printing
System Log
System Monitor

------------------------------------------
Is there anyway to reset it back to manual login.. or better yet.. is there a way to keep it with automatic login, but still have all the menus?

---

### Post by aysiu on 2006-12-17
Have you tried this?

Alt-F2 ```
gksudo gdmsetup
```

---

