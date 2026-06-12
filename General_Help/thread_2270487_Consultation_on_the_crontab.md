---
title: "Consultation on the crontab"
date: 2015-03-23
forum: General Help
---

### Post by David_Vela on 2015-03-23
Hello , I have a question , is it possible to schedule a cron that Begin and end at a certain hour , and minute by minute run ?
That is, I have the following line in the cron :
* 9-18 * * 1-5 /usr/bin/mon.sh


But I do not want begins to 09:00, but at 09:30.
Is it possible ?
Greetings .

---

### Post by Lars Noodén on 2015-03-23
Wouldn't that be a matter of also setting the minutes field in the [crontab](http://manpages.ubuntu.com/manpages/trusty/en/man5/crontab.5.html)

```

30 9-18 * * 1-5 /usr/bin/mon.sh

```

---

### Post by David_Vela on 2015-03-23
[COLOR=#212121][FONT=arial]But I want you to run every minute , too.

[/FONT][/COLOR]

---

### Post by SeijiSensei on 2015-03-23
To run once each minute
```
* * * * * /path/to/some/script
```

To run once every five minutes:
```
*/5 * * * * /path/to/some/script
```

To run once every four hours:
```
* */4 * * * /path/to/some/script
```

---

### Post by ian-weisser on 2015-03-23
> **David_Vela said:**
> * 9-18 * * 1-5 /usr/bin/mon.sh
But I do not want begins to 09:00, but at 09:30.
Is it possible ?

Is it possible? Yes, but not that way.

Looks like you want to run that job when somebody is logged in, or some other event is happening.
If so, you can use that event or logon as a trigger to add/remove the job to /etc/cron.d/ as needed.

For example, if the trigger *really* is time, this set of cron jobs in a root-style crontab will create and remove the every-minute mon cronjob. Note the separate 'mon' user so the script isn't running as root:
30 9 * * 1-5 mon /usr/local/mon/add_mon_job
0 18 * * 1-5 mon /usr/local/mon/remove_mon_job

add_mon_job simply creates the mon cronjob from nothing once each weekday:
```
echo "* * * * * mon /usr/local/bin/mon" > /etc/cron.d/mon
```

remove_mon_job simply deletes the mon cronjob once each weekday
```
rm /etc/cron.d/mon
```

Or if the trigger is login/logout, use Upstart (systemd in 15.04 and newer) to add/remove the job from /etc/cron.d/ . This way also makes it easy to add the username instead of running the job as a different user or root.
It's up to you to figure out the best trigger (time, login, event, )

Petty stuff: Don't use '.' in root-style crontab filenames - they won't run (see man cron)
Petty stuff: I would put locally-created scripts in /usr/local/bin instead of /usr/bin

---

### Post by David_Vela on 2015-03-23
> **Lars Noodén said:**
> Wouldn't that be a matter of also setting the minutes field in the [crontab]("http://manpages.ubuntu.com/manpages/trusty/en/man5/crontab.5.html")

```

30 9-18 * * 1-5 /usr/bin/mon.sh

```

> **ian-weisser said:**
> Is it possible? Yes, but not that way.

Looks like you want to run that job when somebody is logged in, or some other event is happening.
If so, you can use that event or logon as a trigger to add/remove the job to /etc/cron.d/ as needed.

For example, if the trigger *really* is time, this set of cron jobs in a root-style crontab will create and remove the every-minute mon cronjob. Note the separate 'mon' user so the script isn't running as root:
30 9 * * 1-5 mon /usr/local/mon/add_mon_job
0 18 * * 1-5 mon /usr/local/mon/remove_mon_job

add_mon_job simply creates the mon cronjob from nothing once each weekday:
```
echo "* * * * * mon /usr/local/bin/mon" > /etc/cron.d/mon
```

remove_mon_job simply deletes the mon cronjob once each weekday
```
rm /etc/cron.d/mon
```

Or if the trigger is login/logout, use Upstart (systemd in 15.04 and newer) to add/remove the job from /etc/cron.d/ . This way also makes it easy to add the username instead of running the job as a different user or root.
It's up to you to figure out the best trigger (time, login, event, )

Petty stuff: Don't use '.' in root-style crontab filenames - they won't run (see man cron)
Petty stuff: I would put locally-created scripts in /usr/local/bin instead of /usr/bin

Thanks , the solution works!! .

---

