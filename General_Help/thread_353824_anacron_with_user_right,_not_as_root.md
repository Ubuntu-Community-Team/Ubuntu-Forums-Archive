---
title: "anacron with user right, not as root"
date: 2007-02-05
forum: General Help
---

### Post by RikoW on 2007-02-05
Dear all,

I have the suspicion, the answer to this question is no, but I'll ask it anyway. :)

I have a few jobs, which is would run periodically, on a machine, which is not always on. The solution to this would be using *anacron*. However, I don't want to execute those jobs as root, but as my 'regular' user. Is there a way to do this?

Thanks,

                 Riko

---

### Post by schilcha on 2007-02-05
Never used anacron, but if jobs are by default executed as root, rewrite your anacrontab to execute job as su-job.

e.g.: instead of launching 
```

touch /tmp/qaqa

```
schedule
```

su -l -c "touch /tmp/qaqa" schilcha

```

"su" will not require a password, if it is executed as root
-l will create the user's login-environment
-c "command" will execute the command "command"
and finally substitue "schilcha" with your username.

HTH and good luck!

---

### Post by RikoW on 2007-02-06
Great! Works as expected ... I was thinking about something like that, actually! :)

Thanks,
               Riko

---

### Post by Nallep on 2008-01-21
Probably a little late for you, but for anyone else that wants to run anacron as a user, it's pretty easy, it can be done without having to su your commands.
A quick look at **man anacron** will show the way...

**anacron -t** *${HOME}/etc/anacrontab* **-S** *${HOME}/var/spool/anacron*

-t *anacrontab*  (eg.  ${HOME}/etc/anacrontab )
-S *spooldir*      (eg.  ${HOME}/var/spool/anacron

put the command in your *~/.profile* to execute when you login, or put it in a hourly cronjob. to run on it's own.  You don't need to worry about anacron running all it's scripts every hour if you put it in cron, as it keeps it's own timestamps of it's last run in the spool directoy.

See **man anacrontab** for more info on making your own anacrontab file.

Cheers.

---

