---
title: "evolution-data- using all cpu?"
date: 2008-04-29
forum: General Help
---

### Post by rekster on 2008-04-29
What exactly is this evolution-data- process?

Occasionally i notice the system becoming slow and after running top I can see 'evolution-data-' using up to 99% of cpu and then wavering from 80%+

If I kill the process it stops and the system is fine again.

I googled the process and I see two different things, one says something about a telecommunications standard, the other mentions the evolution mail/calendar software.  However I have never used evolution.  If its something to do with the mail/calendar software how can I disable this process from returning.

Using latest Ubuntu 8.04

Thanks!

---

### Post by Enfenion on 2008-04-30
I also got this problem after updating to hardy.

Since I do not use evolution this worked perfectly:

```
sudo apt-get remove evolution-data-server evolution
```

---

### Post by rekster on 2008-05-01
Thanks enfenion good idea I'll do the same :)

Surprised nobody else has mentioned the same issue though.

---

### Post by ipguru99 on 2008-05-02
Same thing here.  It happened about 5 minutes ago and I went to the trusty forums and saw this.. Thanks!  Just killed the process and everything seems fine.  I also don't use evolution, so I just removed.

But I would assume we have stumbled on something bigger here..

---

### Post by Enfenion on 2008-05-02
More information:

[https://bugs.launchpad.net/ubuntu/+source/evolution-data-server/+bug/151536](https://bugs.launchpad.net/ubuntu/+source/evolution-data-server/+bug/151536)

Looks like they're working on it...

---

