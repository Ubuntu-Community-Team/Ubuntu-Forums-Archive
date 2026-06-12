---
title: "Have to resume two times from suspend in 12.10"
date: 2013-03-14
forum: General Help
---

### Post by Arjunanda on 2013-03-14
I have one slightly annoying issue: Every time when I try to resume my laptop from suspend, it awakes nicely, but immediately suspends again. Only on the 2nd resume it remains up & running.

Is this a known bug? Any fixes?

I am running Ubuntu 12.10 on Asus Avibook S200 (F202E / X202E).

---

### Post by tgalati4 on 2013-03-14
Any useful messages in:

tgalati4@Mint14-Extensa /var/log $ ls -la pm*
-rw-r--r-- 1 root root 273080 Mar 14 12:00 pm-powersave.log
-rw-r--r-- 1 root root 427067 Mar  1 08:30 pm-powersave.log.1
-rw-r--r-- 1 root root    904 Feb  6 10:20 pm-powersave.log.2.gz
-rw-r--r-- 1 root root 489454 Mar 14 12:00 pm-suspend.log
-rw-r--r-- 1 root root 513098 Mar  1 08:30 pm-suspend.log.1

```
cat /var/log/pm-powersave.log
cat /var/log/pm-suspend.log
```

---

