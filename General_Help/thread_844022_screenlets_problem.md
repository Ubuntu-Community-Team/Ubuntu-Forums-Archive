---
title: "screenlets problem"
date: 2008-06-29
forum: General Help
---

### Post by savsav on 2008-06-29
I just completely  uninstalled screenlets.

I restart my kubuntu 8.04 and get this message:



Sorry - KDesktop

KDEInit could not
launch '/usr/share/screenlets-manager/screenlets-daemon.py'.





Kubuntu loads up normally and everything works perfectly. I just get
that annoying message.

How do I get rid of the message? The message comes up every time I restart.

---

### Post by dentaku65 on 2008-06-29
See if there is a file called something like screenlets.desktop here:

```
ls ~/.kde/Autostart
```

If so delete or edit it

---

