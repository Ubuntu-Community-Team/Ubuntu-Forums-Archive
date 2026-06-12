---
title: "Why does Python keep starting up."
date: 2007-02-07
forum: General Help
---

### Post by Edward The Bonobo on 2007-02-07
I keep noticing that Python is running in the background.  It shoes up in my System Monitor, hogging a lot of my processor.  It happens on startup, even though it's not in my startup script.  Also at other times - sometimes when I've been away from my machine.  If I kill it, it doesn't seem to cause any problems.

Any ideas what's happening?  How can I stop it?

---

### Post by raul_ on 2007-02-07
It's a process written in python :) Maybe Gnome Listen or another program...

---

### Post by Arisna on 2007-02-07
It sounds like a program of some sort that is implemented in Python is running on your system.  Try running the following command in a Terminal to see if you can determine what arguments are being passed to Python:

```
ps aux | grep python
```

You will see the above operation itself displayed, and hopefully your mystery process as well.

---

