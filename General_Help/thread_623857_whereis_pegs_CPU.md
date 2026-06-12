---
title: "whereis pegs CPU"
date: 2007-11-26
forum: General Help
---

### Post by brianwarner on 2007-11-26
Hi all,

Anybody else seeing whereis take their CPU to 100%?  It seems to be due to a cron job or some daemon, because it happens on a repeating basis.

'ps aux | grep whereis' reveals:

```
  9932 46.0  0.0   1704   492 ?        R    10:37   0:00 /usr/bin/whereis -b -B /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /usr/ucb /sbin /usr/sbin /bin /usr/bin /us
```

Any thoughts?  This is really killing my performance (and my battery)...

Thanks all,
Brian

---

