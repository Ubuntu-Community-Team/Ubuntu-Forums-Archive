---
title: "log of system changes"
date: 2014-12-15
forum: General Help
---

### Post by bigrockcrasher on 2014-12-15
Does anyone know what log file tells you who and when netowrk setting were changes.

---

### Post by slickymaster on 2014-12-15
You can find the Network Manager logs in **/var/log/syslog**, which acts as a catch-all for log messages.

In a terminal window, run the following:```
grep -i networkmanager /var/log/syslog
```

---

