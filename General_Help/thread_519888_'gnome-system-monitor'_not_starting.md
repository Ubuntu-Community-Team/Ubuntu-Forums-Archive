---
title: "'gnome-system-monitor' not starting"
date: 2007-08-07
forum: General Help
---

### Post by gav616 on 2007-08-07
i noticed it wasn't starting from gui soo tryed through term, and getting;
```

$ gnome-system-monitor

** (gnome-system-monitor:8809): WARNING **: SELinux was found but is not enabled.

Floating point exception
```

if i start more then three simultaneously i.e. 4, it finally opens but seems slow to react to active processes.. and memory usage says '0'.

System info;

Feisty up-to-date with gutsy latest kernel

---

### Post by gav616 on 2007-08-08
bump

---

### Post by Delvien on 2007-12-20
I get the same error.

---

### Post by legend2440 on 2007-12-23
I had the exact same problem.
I fixed it by removing old launcher from panel where I had it and then went to System>>Administration>>System Monitor and right click>> add to panel and for some reason it worked again
Forgot to mention I reinstalled it from Synaptic before doing anything else.

---

