---
title: "how to get the exact time of system lock"
date: 2015-03-05
forum: General Help
---

### Post by mer23 on 2015-03-05
Hello,

I would like to know the exact time my system locks after I leave it for a while. Is there any way I could find this?

Thank you
Anupama

---

### Post by tgalati4 on 2015-03-06
```
tail -50 /var/log/syslog
```

---

### Post by gordintoronto on 2015-03-07
Use conky, and include the time in the conky display.

Syslog might be unchanged for a substantial amount of time.

---

