---
title: "Problems with running a cronjob"
date: 2023-04-04
forum: General Help
---

### Post by johndid on 2023-04-04
Hi,
I'm practicing with **rsnaphot. **It works great, but I am having some problems at scheduling it with a cronjob.
if I run: 

```
sudo rsnapshot alpha
```
The folder I set up gets backupped as expected each time I just run the command in the terminal

[[IMG]https://images2.imgbox.com/f9/08/wpWh6eri_o.jpg[/IMG]]("https://imgbox.com/wpWh6eri")

but the cronjob seems not to be working at the time I set up. I mean, nothing happens:

```
#Daily backup
35 15 * * * /usr/bin/rsnapshot alpha
```


what did I get wrong?
Thanks

---

### Post by ian-weisser on 2023-04-04
Check your /var/log/syslog for logged messages around that time.

---

### Post by johndid on 2023-04-04
> **ian-weisser said:**
> Check your /var/log/syslog for logged messages around that time.

this could be meaningful:


```

Apr  4 15:35:01 tom-vm CRON[3501]: (tom) CMD (/usr/bin/rsnapshot alpha)
Apr  4 15:35:01 tom-vm rsnapshot[3502]: /usr/bin/rsnapshot alpha: ERROR: Could not write lockfile /var/run/rsnapshot.pid
Apr  4 15:35:01 tom-vm CRON[3500]: (CRON) info (No MTA installed, discarding output)
Apr  4 15:35:21 tom-vm rsnapshot[3514]: /usr/bin/rsnapshot alpha: ERROR: Could not write lockfile /var/run/rsnapshot.pid
Apr  4 15:35:30 tom-vm rsnapshot[3518]: /usr/bin/rsnapshot alpha: completed successfully


```

Thanks

UPDATE:

I fixed it!
You first need to create a new cronjob file:

```
sudo nano /etc/cron.d/rsnapshot
```

then I wrote this command inside with root permission:

```
12 20           * * *           root    /usr/bin/rsnapshot alpha
```


and it worked as espected.

---

### Post by johndid on 2023-04-04
Another question:

I set the cronjob to be run at 8:20 PM. What happened if I start, for any reason, the pc after that time? Does the cronjob run just after I start my machine, or what?

---

### Post by TheFu on 2023-04-04
If you specify a specific time in the crontab, then it must be booted at that time to run.  Perhaps you'd rather use anacron?  There are hourly, daily, weekly, monthly and yearly anacron tasks.  They will run, at most, once during those periods.

Just dropping a script into /etc/cron.daily/ is sufficient.  Every script in there will run as root, once a day.  Anacron, regardless of the period, only works on a daily basis.  The /etc/cron.hourly/ is a best effort.

If you use regular cron, then you've accepted those capabilities/limitations.  Maybe the better answer would be to use @daily in root's crontab file or to make backups part of your shutdown/sleep process for the system?  I do the 2nd on a laptop here.  When I'm done for the evening, I run a script that performs the network backup, then puts the machine to sleep.  Sadly, there is no @shutdown keyword for crontabs.  
Section 5 of the manpages for crontab have a list of all these "special strings" and how they are expanded.  Section 5 of manpages contains the explanation for most config files, allowed commands, settings, and any special formatting requirements.

---

### Post by johndid on 2023-04-05
Got it, thanks

---

### Post by HermanAB on 2023-04-05
For future reference: Put backup scripts in the root crontab, so that it has permission to access everything.  Also use the full pathname of any utility, since the cron environment variables are limited for security reasons.

---

### Post by TheFu on 2023-04-05
There are multiple places for crontabs.  /etc/crontab calls the anacron scripts in /etc/
 cron.daily/   cron.hourly/  cron.monthly/ cron.weekly/ directories.

Each userid has a crontab that has a slightly different format, accessed by the 'crontab' program.
```
crontab -e # edit the current user's crontab.
sudo crontab -e # edit root's crontab
```
I add this header to all my personal crontabs, as a reminder for what each field means:
```
# .---------------- minute (0 - 59) 
# |  .------------- hour (0 - 23)
# |  |  .---------- day of month (1 - 31)
# |  |  |  .------- month (1 - 12) OR jan,feb,mar,apr ... 
# |  |  |  |  .---- day of week (0 - 6) (Sunday=0 or 7)
# |  |  |  |  |
# *  *  *  *  *  /path/to/command --arg1 --arg2 file1 file2  > /tmp/log.file  2>&1
# m h  dom mon dow   command

```

It is handy to redirect stdout to /dev/null, but allow stderr to be emailed.  That means errors are reported, but normal processing isn't. Here's how:
```
# *  *  *  *  *  /path/to/command --arg1 --arg2 file1 file2  > /dev/null
```

The issue with using the 'crontab' command is that those end up stored under /var/spool/cron/ .... somewhere.  So customized parts of the system aren't likely included in your backup areas. On some servers, crontabs ARE VERY IMPORTANT.  I specifically dump the crontabs for users that have them using **crontab -l** as part of my nightly backups.  I don't like the default time that daily anacron tasks run and running too many things all at once is bad form. Don't want to slam a machine with 50 jobs at the same instant.  I never start any cron job on any 15 minute time either. I always pick an odd time to prevent overloading a system accidentally.

---

### Post by johndid on 2023-04-06
> **HermanAB said:**
> For future reference: Put backup scripts in the root crontab, so that it has permission to access everything.  Also use the full pathname of any utility, since the cron environment variables are limited for security reasons.

I'm not sure if I get what you mean.

is this not correctt?

sudo nano /etc/cron.d/rsnapshot

then 

12 20           * * *           root    /usr/bin/rsnapshot alpha


thanks

---

