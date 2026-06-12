---
title: "previously unseen crontab errors?"
date: 2007-03-26
forum: General Help
---

### Post by datakid on 2007-03-26
hola,

I've got this strange crontab errors that I'm having problems with. 

I set up a crontab for my updates to happen over night:

musicman@boxen:~$ less /etc/cron.daily/crontab 

m h  dom mon dow   command
0 0 * * * aptitude -y update && aptitude -y upgrade && aptitude -y autoclean

as I discovered online at this howto: [URL="http://ubuntu-tutorials.com/2006/10/07/automatic-updates-ubuntu-all-versions/"]

I saved it in /usr/local/bin/crontab

When I wake up in the morning - no updates have happened!

Now, when I run 
musicman@boxen:~$ sudo crontab -e /usr/local/bin/crontab 
or 
musicman@boxen:~$ sudo crontab -e crontab


I get this error:

/usr/local/bin/crontab: 2: 00: not found
/usr/local/bin/crontab: 3: 00: not found

anyone?

cheers
L.

---

### Post by dcstar on 2007-03-26
> **datakid said:**
> hola,

I've got this strange crontab errors that I'm having problems with. 

I set up a crontab for my updates to happen over night:

musicman@boxen:~$ less /etc/cron.daily/crontab 

m h  dom mon dow   command
0 0 * * * aptitude -y update && aptitude -y upgrade && aptitude -y autoclean

as I discovered online at this howto: [URL="http://ubuntu-tutorials.com/2006/10/07/automatic-updates-ubuntu-all-versions/"]

I saved it in /usr/local/bin/crontab

When I wake up in the morning - no updates have happened!

Now, when I run 
musicman@boxen:~$ sudo crontab -e /usr/local/bin/crontab 
or 
musicman@boxen:~$ sudo crontab -e crontab


I get this error:

/usr/local/bin/crontab: 2: 00: not found
/usr/local/bin/crontab: 3: 00: not found

anyone?

cheers
L.

I'm not surprised that the crontab command didn't work.

Scheduled jobs do not run in a shell environment (like when you are in a terminal), therefore there are no **path**s set to where binary commands may reside.

Without a full path to all commands, how does **cron** know where to find them?

In a terminal, do:
```
whereis aptitude
```
and then put the full command path into your cron line, then it will have some chance of functioning.

Even better is to have all of those commands in a script somewhere, and then have cron run that script.

---

