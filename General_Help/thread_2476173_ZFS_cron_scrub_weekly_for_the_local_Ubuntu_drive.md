---
title: "ZFS cron scrub weekly: for the local Ubuntu drive"
date: 2022-06-18
forum: General Help
---

### Post by david509 on 2022-06-18
Hi, how do you setup a **weekly** cron job to scrub **all** local ZFS pools? 

If the cron job is missed, will it run on the next login or at the same day/time *next* week?

Thanks for reading.

---

### Post by #&amp;thj^% on 2022-06-18
Dose this file exist? "/etc/cron.d/zfsutils-linux"
```
cat /etc/cron.d/zfsutils-linux
```
Whoops forgot to add your second question, >> if your system is turned off when a crontab entry should run then it will be missed.

---

### Post by david509 on 2022-06-18
> **1fallen said:**
> Whoops forgot to add your second question, >> if your system is turned off when a crontab entry should run then it will be missed. Good to know and thanks for answering my question. :)

I'm setting up a new Ubuntu 22.04 install during the week on a laptop with an SSD, so just need to know how to setup the weekly scrub. I think, by default, the ZFS scrub runs about once a month on a Sunday??? I would prefer weekly tbh, but maybe that default scrub mode should find and fix any checksum errors - making Ubuntu on ZFS maintenance-free?

---

### Post by #&amp;thj^% on 2022-06-18
you never showed me 
```
cat /etc/cron.d/zfsutils-linux
```

---

### Post by david509 on 2022-06-18
> **1fallen said:**
> you never showed me 
```
cat /etc/cron.d/zfsutils-linux
```

On my own Ubuntu (20.04) setup, the cron file shows this: ```
# Scrub the second Sunday of every month.24 0 8-14 * * root if [ $(date +\%w) -eq 0 ] && [ -x /usr/lib/zfs-linux/scrub ]; then /usr/lib/zfs-linux/scrub; fi
```

I'm assuming Ubuntu 22.04 has the same file and cron setup as 20.04? If so, I will apply the steps (to setup a weekly cron job) to the new Ubuntu 22.04 when I install it during next week. :)

---

### Post by #&amp;thj^% on 2022-06-18
> **david509 said:**
> 
I'm assuming Ubuntu 22.04 has the same file and cron setup as 20.04? If so, I will apply the steps (to setup a weekly cron job) to the new Ubuntu 22.04 when I install it during next week. :)
Yes Sir! and happy scrubbing. ;)

---

### Post by david509 on 2022-06-18
Thanks for your help. :)

I take it I just need to make a simple(?) adjustment to that file? I can do it on both my existing Ubuntu setup - and the new setup too (adjust the file on both to weekly)?

---

### Post by david509 on 2022-06-19
How to change the cron file from monthly to weekly?

---

