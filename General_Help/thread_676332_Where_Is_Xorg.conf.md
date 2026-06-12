---
title: "Where Is Xorg.conf"
date: 2008-01-23
forum: General Help
---

### Post by luckyhalo on 2008-01-23
Sorry noob question, but where us xorg.conf?

---

### Post by lloyd_b on 2008-01-23
> **luckyhalo said:**
> Sorry noob question, but where us xorg.conf?

Try in "/etc/X11"

Lloyd B.

---

### Post by Zill on 2008-01-23
luckyhalo:

FYI if you want to find *anything* on your system use the locate command eg.
```
locate xorg.conf
```
Be aware that this command will only work *after* the slocate database has been updated.  This is normally updated daily by the cron daemon.
```
man slocate
man updatedb
```

---

