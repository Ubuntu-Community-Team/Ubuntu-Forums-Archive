---
title: "System randomly freezes."
date: 2018-11-19
forum: General Help
---

### Post by olehz on 2018-11-19
My system used to freeze once per week. Now it happens several times per day. When it's frozen, it gets completely unresponsive. Commands like
```
Ctrl + Alt + F2
```
```
Alt + SysRq + __
```
seem to do nothing.
I thought that this happens permanently, and the only way to solve this was a reboot. But recently I discovered that it unfreeze in ~5minutes.
My swap is configured, and `swapon -s` gives me this
```

Filename                Type        Size    Used    Priority
/dev/dm-3                                  partition    16596476    3066356    -1

```

Most of the time these freezes happen when I open several email accounts simultaneously in Chrome. But recently this may happen randomly on any occasion.
Is there any way I could possibly debug this to find out the reason? Maybe look for some log files?

Additional info:
I work on the system, where I ran tomcat, nginx and several java microservices.
And not sure, if this is related, but after system unfreeze, ssh connection for the DB I use, gets lost.

---

