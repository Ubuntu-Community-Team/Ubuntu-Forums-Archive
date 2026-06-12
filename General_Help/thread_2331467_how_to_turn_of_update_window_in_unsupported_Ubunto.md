---
title: "how to turn of update window in unsupported Ubunto"
date: 2016-07-22
forum: General Help
---

### Post by fredrikbergquist on 2016-07-22
Hi
I am a newbee in Ubunto as well as Linux. I am running LinuxCNC on an older kernel supporting realtime control. The Ubuntu is checking for updates all the time an give the message that the support for the version is closed. But it works perfectly for my needs so I want to continue to use it as it is. The problem is that the window hangs when I try to close it. Is there any way to stop Ubuntu to check for updates?
Kind regards
Fredrik

---

### Post by howefield on 2016-07-22
What version of Ubuntu are you using ? The terminal command 

```
cat /etc/lsb-release
```

will give you some idea. You could probably go into Startup Applications and disable Update Notifier, and/or from the Update tab in Software and Updates, set "Automatically check for Updates" to Never.

---

