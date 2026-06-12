---
title: "tracker.log"
date: 2008-06-24
forum: General Help
---

### Post by Nipopolis on 2008-06-24
Hello all,

I have no tracker.log at all.  I looked in .local/shared/tracker but it is not there.  I even touched tracker.log to create one.  When I rebooted it was gone.  Does tracker not use a log now?  If it does, where is mine?  I'm running Ubuntu 8.04 with kernel 2.6.24-19-generic.

Nip

---

### Post by Nipopolis on 2008-06-25
I found an answer to this.  In $HOME/.config/tracker/tracker.cfg I changed the log verbosity from 0 to 2.  I now have a tracker.log file.


This is how tracker.cfg looked before:
```
 # Log Verbosity - Valid values are 0 (displays/logs only errors), 1 (minimal    ), 2 (detailed), and 3 (debug)
  4 Verbosity=0

```

Now it looks like this:
```
 # Log Verbosity - Valid values are 0 (displays/logs only errors), 1 (minimal    ), 2 (detailed), and 3 (debug)
  4 Verbosity=2

```

I will switch it from 2 to 1 when I am finished debugging my problem.  Hope this helps out.

Nip

---

