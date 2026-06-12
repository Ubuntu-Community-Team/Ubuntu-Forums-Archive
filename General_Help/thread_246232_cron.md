---
title: "cron"
date: 2006-08-29
forum: General Help
---

### Post by cssutto on 2006-08-29
How do I force cron.daily to run so I can determine whether it is doing what I want it to do?

CSSJR

---

### Post by maka on 2006-08-29
> **cssutto said:**
> How do I force cron.daily to run so I can determine whether it is doing what I want it to do?

CSSJR

why dont you just set up what you want it to do, and see if it works daily?

---

### Post by cssutto on 2006-08-29
Hey, even I am smart enough to know that if I wait 24 hours I will find out.

I want to find out NOW!!!!!!

---

### Post by Adler on 2006-08-29
cssutto,

What are you using for a *chron* job? Back-up? If so, let me know what you are using.

Adler

---

### Post by cssutto on 2006-08-29
Thanks for the offer, but that is not what I want.

I want to know how to force cron.daily to execute so I can determine what it is doing.

CSSJR

---

### Post by sgreszcz on 2006-09-07
Try this:

```
run-parts /etc/cron.daily
```

---

### Post by ayoli on 2006-09-07
check /var/log/syslog, you'll see commands ran by cron.

---

