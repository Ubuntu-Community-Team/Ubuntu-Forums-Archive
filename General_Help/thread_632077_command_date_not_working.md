---
title: "command date not working ?"
date: 2007-12-05
forum: General Help
---

### Post by GoldWing on 2007-12-05
holmes:/var/log/ntpstats# date
Wed Dec  5 11:55:42 CET 2007
holmes:/var/log/ntpstats# date 12051110
Wed Dec  5 11:10:00 CET 2007
holmes:/var/log/ntpstats# date
Wed Dec  5 11:55:55 CET 2007

What is happening ?
Is this also the reason why my ntp keeps failing ?

---

### Post by pointone on 2007-12-05
Try date -s 12051110.

---

### Post by GoldWing on 2007-12-06
> **pointone said:**
> Try date -s 12051110.

uh ?
holmes:~# date -s 12051110
date: invalid date `12051110'

Can you please explain what you are suggesting ?

Can it be that I can't change the time/hour because this is a 'VM' machine ?



Thanks

---

### Post by pointone on 2007-12-06
The -s switch is used to set the date according to the supplied string, but I just noticed something else: you need to run date as root to make permanent changes. Try:

```
sudo date 12051110
```

---

