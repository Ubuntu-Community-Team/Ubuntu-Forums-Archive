---
title: "[SOLVED] Why anacron won't run"
date: 2008-03-04
forum: General Help
---

### Post by wayfarer51 on 2008-03-04
Does anyone have any idea why nothing in this /etc/anacron file works at all? 

Anacron is checked as an active service in System > Administration > Services > Services Settings, but there is nothing recognizable to me as anacron in System Monitor > Processes.  Looking at some search results, perhaps there should be an entry when I crontab -e?  The very bottom text is the content of /etc/cron.d/anacron.  Shouldn't that run anacron? 

I posted with a [similar problem in December]("http://ubuntuforums.org/showthread.php?t=647050"), but as my computer is only on intermittently, I want to use anacron instead of cron.

Though not a long trip, I'm at my wit's end.  Can anyone help me out?

Thanks!

Neill

```
# /etc/anacrontab: configuration file for anacron

# See anacron(8) and anacrontab(5) for details.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# These replace cron's entries
7	5	run.xmltv	/usr/bin/tv_grab_na_dd | tv_sort > /home/neill/listings.xml
7	5	run.f-prot	/usr/local/f-prot/f-prot -ARCHIVE -PACKED -COLLECT -REPORT=/home/neill/.xfprot/xfprot.log -AI -SAFEREMOVE -AUTO -DISINF 
```

```
# /etc/cron.d/anacron: crontab entries for the anacron package

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

30 7    * * *   root	test -x /etc/init.d/anacron && /usr/sbin/invoke-rc.d anacron start >/dev/null
```

---

### Post by bmt on 2008-03-09
Executive summary: put anacrontab back to default and set cron jobs.

I'd suggest leaving the anacrontab file at default, which is:
```
SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# These replace cron's entries
1	5	cron.daily	 nice run-parts --report /etc/cron.daily
7	10	cron.weekly	 nice run-parts --report /etc/cron.weekly
@monthly	15	cron.monthly nice run-parts --report /etc/cron.monthly

```
And putting whatever tasks you want to run in crontab.  The default settings have anacron run the cron jobs set for daily, weekly and monthly.

Did you read the wiki article, referenced in your thread from December 2007? It's [here](https://help.ubuntu.com/community/CronHowto) and has some useful stuff.  Bottom line: don't just add jobs to crontab directly, rather run: ```
sudo crontab -e
```

You can also set cron jobs from within Webmin, including the possibility of one-shot trial runs and an easy periodicity setting gui.

---

### Post by wayfarer51 on 2008-03-09
I've done as you suggested and my jobs are now running as scheduled.  As per usual, I attributed far too much complexity to a problem that had a simple answer.

Thanks bmt...I really appreciate your help.

Neill

---

