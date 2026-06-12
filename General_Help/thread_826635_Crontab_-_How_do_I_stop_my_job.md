---
title: "Crontab - How do I stop my job?"
date: 2008-06-12
forum: General Help
---

### Post by ngms27 on 2008-06-12
Hi,

A year ago I set up a cron job that I now want to stop.
I cannot remember how I set it up.

It doesn't show using either crontab -l or sudo crontab -l

I think I may have directly edited a file but cannot remember which one.

Any ideas how i might have done this?

PS I haven't changed user or anything like that

Thanks

JonnyT

---

### Post by iaculallad on 2008-06-12
What about crontab -e, w/c lets you edit your crontab file.

```
crontab -e
```

---

### Post by ngms27 on 2008-06-12
It doesn't show for either my user name or with sudo

I'm pretty sure this is running under the system rather than a user but cannot remember.

---

