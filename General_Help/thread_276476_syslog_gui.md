---
title: "syslog gui"
date: 2006-10-12
forum: General Help
---

### Post by dguido on 2006-10-12
Is there a tool out there that will let me look through my syslog in a GUI, I hate to say it but something like Event Viewer?  Even better, is there something that will sit in my tasktray and pop up a little alert when certain things are detected in syslog?

---

### Post by ansi on 2006-10-13
> **dguido said:**
> Is there a tool out there that will let me look through my syslog in a GUI, I hate to say it but something like Event Viewer?  Even better, is there something that will sit in my tasktray and pop up a little alert when certain things are detected in syslog?
```

[~] apt-cache show root-tail | grep "^ "
 Root-tail, is a program that displays one or more log files, on the X root window, through the use of transparent windows.

```

---

