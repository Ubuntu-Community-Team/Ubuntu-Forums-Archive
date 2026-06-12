---
title: "Debugging a &quot;failsafe&quot; message during init"
date: 2014-01-06
forum: General Help
---

### Post by uone2 on 2014-01-06
My server (Ubuntu Server 13.10) has been hanging on boot since sometime shortly after I upgraded from 13.04. I still haven't been able to pinpoint a cause.

The server does eventually finish booting, but not until these errors are logged:
```
[   28.391645] init: failsafe main process (849) killed by TERM signal
```
```
Jan  6 23:35:56 localhost failsafe: Failsafe of 120 seconds reached.
```
Is there any way to force extra logging during init, so that I can see which process had PID 849 at the time? This message is extremely unhelpful on its own.

Thanks!

---

