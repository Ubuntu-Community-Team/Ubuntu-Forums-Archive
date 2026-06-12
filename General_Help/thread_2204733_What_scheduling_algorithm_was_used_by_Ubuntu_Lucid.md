---
title: "What scheduling algorithm was used by Ubuntu Lucid Lynx?"
date: 2014-02-10
forum: General Help
---

### Post by SkyLinePH on 2014-02-10
I'm not sure if this is the correct section to post my query. Mods can delete my thread anytime if its not related to the section.

I just want to ask, what scheduling algorithm was used by Ubuntu Lucid Lynx?

Thanks and God bless. :)

---

### Post by sandyd on 2014-02-10
What do you mean by 'scheduling algorithm"
kernel scheduling?

---

### Post by SkyLinePH on 2014-02-10
cpu scheduling such as **First Come First Serve, Round-Robin etc.**

---

### Post by tgalati4 on 2014-02-10
I believe it is different between desktop and server kernels back then.  Now it is unified.

tgalati4@Mint14-Extensa ~ $ apropos schedule
cron (8)             - daemon to execute scheduled commands (Vixie Cron)
cupsd (8)            - cups scheduler
pthread_attr_getinheritsched (3) - set/get inherit scheduler attribute in thread attributes object
pthread_attr_setinheritsched (3) - set/get inherit scheduler attribute in thread attributes object
[B]sched_getscheduler (2) - set and get scheduling policy/parameters
sched_setscheduler (2) - set and get scheduling policy/parameters[/B]
tc-choke (8)         - choose and keep scheduler
tc-drr (8)           - deficit round robin scheduler
ualarm (3)           - schedule signal after given number of microsecond

```
man sched_getscheduler
```

There is also:

schedtool - Queries/alters process' scheduling policy and CPU affinity 

which I believe is available in Lucid according to:  [http://manpages.ubuntu.com/manpages/lucid/man8/schedtool.8.html](http://manpages.ubuntu.com/manpages/lucid/man8/schedtool.8.html)

---

