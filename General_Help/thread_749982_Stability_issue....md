---
title: "Stability issue..."
date: 2008-04-09
forum: General Help
---

### Post by road_rage on 2008-04-09
I have noticed that every now and then, and of course at the worse times, my x session will just completely freeze and the system becomes completely unresponsive and need to be hard reset to work again. I have not found any special sequence of events and have looked into /var/log/syslog to see if there are any common entries with previous lock-up's and the only entry that looks as though is in all is...
```
Updated timestamp for job `cron.daily'
```

I did some googles and forum search and the only hits I get with that or the other error I am seeing...
```
<WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
```
which appears as though is a bug, but want to be sure I am in the right neighborhood or see if there are other things I should look at to better determine the cause ?

TYIA,

--RR

---

### Post by road_rage on 2008-04-11
-bump-

Anyone ?

---

