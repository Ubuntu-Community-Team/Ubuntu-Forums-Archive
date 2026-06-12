---
title: "Disable Klogd and Syslogd"
date: 2008-05-10
forum: General Help
---

### Post by anotherdisciple on 2008-05-10
I disabled the services klogd and syslogd. It dramatically sped up ubuntu. Is it bad to do this? What do those services do?

---

### Post by pointone on 2008-05-11
They are logging daemons. It is not recommended to disable them since they provide valuable information if you need to troubleshoot problems or, in general, maintain your system.

```
man syslogd
man klogd
```

---

### Post by kerry_s on 2008-05-11
i always remove those from my install, if you don't need logs you don't need those. you can clear out /var/log from the folders down.

here's what mine looks like->

---

