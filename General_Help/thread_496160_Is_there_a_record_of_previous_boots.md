---
title: "Is there a record of previous boots?"
date: 2007-07-08
forum: General Help
---

### Post by fearpi on 2007-07-08
I suppose I could just write a little startup script, but is there already a log (that is persistent between sessions) that is written to when the system starts or shuts down?

---

### Post by dasunst3r on 2007-07-08
Try looking at /var/log for the log files you are looking for.

---

### Post by fearpi on 2007-07-08
I already have. Nothing seems to fit the description. Everything I found in there was gathered from the current session.

---

### Post by fredj on 2007-07-09
Go to System - Administration - System Log

---

### Post by Mr. C. on 2007-07-09
```
last | grep reboot
```

MrC

---

### Post by fearpi on 2007-07-09
Great. Thanks, guys.

---

