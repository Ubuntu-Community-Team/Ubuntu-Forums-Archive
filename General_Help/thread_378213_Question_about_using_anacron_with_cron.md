---
title: "Question about using anacron with cron"
date: 2007-03-07
forum: General Help
---

### Post by richbl on 2007-03-07
Hello all,

I have a question about cron and anancron.

After reading the man page for both cron/crontab and anacron/anacrontab, it's not clear to me how to configure for the following:

--jobs to run currently live in /etc/crontab
--jobs need to run serially (hence the staggered start times in crontab)

As I understand it, anacron will only run those jobs created as scripts in the **ly folders (e.g. /etc/cron.weekly).

So, my question is this: if I have periodic jobs to run in /etc/crontab, how do I have anacron run those jobs when cron fails to do so (e.g. machine turned off)?

It seems to me that the only way anacron will do what I expect it to do is to move my jobs in /etc/crontab into /etc/cron.daily. Yet, if I do that, I lose the ability to have jobs run serially (or at least run the risk of having jobs overlap each other).

Please advise.

Thanks.

---

### Post by richbl on 2007-04-30
For completeness, here is the solution to my original question:

It turns out that cron jobs in /etc/cron.xxly will run serially, or rather, lexicographically (alphabetically). So, the solution for me was to migrate my cron jobs into the /etc/cron.xxly folders.

---

