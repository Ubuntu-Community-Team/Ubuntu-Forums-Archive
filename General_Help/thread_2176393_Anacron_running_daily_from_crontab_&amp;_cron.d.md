---
title: "Anacron running daily from crontab &amp; cron.d"
date: 2013-09-24
forum: General Help
---

### Post by Rich_Stanton on 2013-09-24
I've recently upgraded a LTS box to 12.04, after the old LTS release became end of life'd. Since then I've been getting the following message every morning:

start: Job is already running: anacron

In the logs I see anacron running twice each day:

```

Sep 24 06:25:01 rich CRON[18033]: (root) CMD (test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily ))
Sep 24 07:30:01 rich CRON[18492]: (root) CMD (start -q anacron || :)

```
The first entry is being run from /etc/cron.d & the second from /etc/crontab.

Is this normal? If not, which should I delete?

This is my crontab:
```
17 *    * * *   root    cd / && run-parts --report /etc/cron.hourly
25 6    * * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6    * * 7   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6    1 * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )

```
& this is /etc/cron.d/anacron:

```
[FONT=Verdana]SHELL=/bin/sh[/FONT]
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin


#30 7    * * *   root   test -x /etc/init.d/anacron && /usr/sbin/invoke-rc.d anacron start >/dev/null
30 7    * * *   root    start -q anacron || :

```

---

### Post by ian-weisser on 2013-09-24
It's normal.

Are you worried that a job will run twice? It won't...anacron keeps track.

---

### Post by Rich_Stanton on 2013-09-25
No, I was worried because some jobs weren't running. But it turns out that was because  prior job in cron.daily was hanging, so it's all fixed now. Thanks anyway!

---

