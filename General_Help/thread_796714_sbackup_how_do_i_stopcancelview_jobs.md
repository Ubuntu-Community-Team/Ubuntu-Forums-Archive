---
title: "sbackup how do i stop/cancel/view jobs?"
date: 2008-05-16
forum: General Help
---

### Post by clockworkmcd on 2008-05-16
hi all, not sure if the would be the right place to post but..
i've used sbackup to create a backup job, i beleive it makes a cron job or a crontab job, but it doesn't seem to have an area to cancel a job or show/edit current jobs. i've uninstalled sbackup but the backups still seem to be going on. HOW DO I MAKE IT STOP!!! :P

thanks in advance.

---

### Post by clockworkmcd on 2008-05-20
anybody know?

---

### Post by wportre on 2008-06-01
In a console, (Applications/Accessories/Terminal) "ps -e" lists all processes (equivalent of "jobs" in other distros. Then "kill -term [chosen job number]". Careful!

---

### Post by sdennie on 2008-06-01
sbackup uses tar at it's core so, removing the package without --purge (or even removing it with that) may not cancel the cron job.  I'm not sure how it sets up its cronjobs but, you should be able to find them with something like this:

```

grep sbackup `find /etc -name "cron*"`

```

Or maybe:

```

grep tar `find /etc -name "cron*"`

```

Find the files where it looks like sbackup is running and comment out the sbackup commands by putting a # in front of the command.

---

