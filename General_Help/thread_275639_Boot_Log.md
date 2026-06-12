---
title: "Boot Log ?"
date: 2006-10-11
forum: General Help
---

### Post by Fedcer on 2006-10-11
Hi, one of the steps during boot is failing, so I tried to boot into the recovery mode to see what was the error but the text scrolls too fast and I can't read what is says.
So is there any kind of boot-log where I can read what is failing ?

Thanks,

Fedcer

---

### Post by ayoli on 2006-10-11
try in a terminal:```

dmesg
```
other logs (syslog and messages) are in /var/log

---

