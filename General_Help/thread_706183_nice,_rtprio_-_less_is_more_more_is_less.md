---
title: "nice, rtprio - less is more? more is less?"
date: 2008-02-24
forum: General Help
---

### Post by Mr.Johnny on 2008-02-24
I've read that a negative parameter for nice actually means a higher priority, but I still haven't understand what's the thing with rtprio.

"rtprio executes command with a real-time priority, or changes the real-time priority of currently executing process pid. Real-time priorities range from zero (highest) to 127 (lowest). Real-time processes are not subject to priority degradation, and are all of greater (scheduling) importance than non-real-time processes. See rtprio(2) for more details."

Not being a native english speaker, it seems to me that it's otherwise with rtprio, where a lower value means a higher priority.

If I am not missing something, shouldn't the line added to /etc/security/limits.conf in ubuntu studio ( @audio - rtprio <value> ) have the lowest possible value for <value> or am I missing something?

thanks

---

### Post by SeanTater on 2008-02-24
You can think of 'nice'ness as a suggestion. Lower numbers of niceness most likely mean higher priority, (think of a mean process taking all the resources).

Realtime processes are different. It's less of a suggestion because any realtime process would be would be the meanest of them all. (although there can be more than one, in which that would not be the case)

Think of it this way:
```

Lowest to highest priority:

nice                                rtprio
19 ... 10 ... 0 .. -10 .. -20 | 127 ... 100 ... 50 ... 0

```

---

### Post by Mr.Johnny on 2008-02-24
It makes sense now ;) tks

---

