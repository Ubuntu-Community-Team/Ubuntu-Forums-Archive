---
title: "error log help"
date: 2015-12-05
forum: General Help
---

### Post by michael277 on 2015-12-05
Where can i find a log of all error messages that have appeared on my computer?

---

### Post by steeldriver on 2015-12-05
I don't think there's a single log file that records "all error messages that have appeared" on your computer - at least, not by default.

Can you be more specific about what you are looking for?

---

### Post by tgalati4 on 2015-12-05
Most error logs are stored in /var/log.  Some are stored in your home directory, such as:

```
more ~/.xsession-errors
```

Spacebar to page forward.  "q" to quit.

There is a log viewer program.  In MATE, it is called *mate-system-log*.  In Gnome, *gnome-system-log*.

```
mate-system-log
```

or

```
gnome-system-log
```

90% of the time, you will want to look at *dmesg* or *syslog*:

```
dmesg | tail -50
```

or 

```
less /var/log/syslog
```

---

### Post by michael277 on 2015-12-07
i'm looking for internal errors, i think. i got some after my hover click stopped working.

---

