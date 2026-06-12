---
title: "CRON - check is program working"
date: 2007-02-23
forum: General Help
---

### Post by artmajster on 2007-02-23
Hello

I have a problem.

I do not know how can I check is program working.

I want to check this by the sh file run by cron.

I want to chech is FireFox working.
If not, I will start FireFox.


I'll need some help with this.

p.s. As You see my english is not so good, but I'm trying. :)

---

### Post by cronholio on 2007-02-23
```
ps -C firefox-bin -o pid=
``` will return a PID if Firefox runs and nothing if it doesn't. If you want to check for the return code ($?), it will be 0 in the first and 1 in the second case.

---

### Post by artmajster on 2007-02-23
```
if [ ps -C firefox-bin -o pid= ] ; then
    DISPLAY=:0.0 usr/bin/firefox
```

That will be correct?

I'm not good in programing :/

---

### Post by cronholio on 2007-02-23
```
if [ ! `ps -C firefox-bin -o pid=` ] ; then DISPLAY=:0.0 /usr/bin/firefox ; fi
```

This will work.

---

### Post by artmajster on 2007-02-23
Thank you very much.

It works great !!!!

---

