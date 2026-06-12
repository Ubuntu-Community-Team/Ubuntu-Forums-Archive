---
title: "Multiple PHP Processes Locking Up System"
date: 2008-04-30
forum: General Help
---

### Post by DaRabman on 2008-04-30
Hi,
I set an entry in **crontab** to automate the execution of a php file in the shell every three mins. I felt my system start to drag after about half an hour, and **ps** showed a list of **sh** and **php** processes about 40 lines long. 

System monitor had jammed up so I had to kill each individual process in bash before the system started to ease up. The system monitor showed the remaining **php** processes were expanding their CPU usage to fill the space (the last four using 25% each).

I suspect what's happening is that each time the **crontab** entry is executed, another screen or something is opened up and doesn't close. I thought about trying to knock together a (basic, still learning) script that would contain the execution in a screen and then close it shortly afterwards, but I don't exactly know the syntax.

Here's the crontab entry:
```
*/3 * * * * cd /var/www/soldat/ && php update.php
```

Any help would be really, really appreciated.
Cheers,
Sam.

---

### Post by Monicker on 2008-05-01
> **DaRabman said:**
> Hi,
I set an entry in **crontab** to automate the execution of a php file in the shell every three mins. I felt my system start to drag after about half an hour, and **ps** showed a list of **sh** and **php** processes about 40 lines long. 

System monitor had jammed up so I had to kill each individual process in bash before the system started to ease up. The system monitor showed the remaining **php** processes were expanding their CPU usage to fill the space (the last four using 25% each).

I suspect what's happening is that each time the **crontab** entry is executed, another screen or something is opened up and doesn't close. I thought about trying to knock together a (basic, still learning) script that would contain the execution in a screen and then close it shortly afterwards, but I don't exactly know the syntax.

Here's the crontab entry:
```
*/3 * * * * cd /var/www/soldat/ && php update.php
```

Any help would be really, really appreciated.
Cheers,
Sam.

Every 3 minutes is kinda frequent, but then I have no idea what it is doing.  Is this script not exiting normally?  I would consider putting some logic in the script that checks to see if its already running before proceeding.

---

### Post by DaRabman on 2008-05-01
> Is this script not exiting normally? I would consider putting some logic in the script that checks to see if its already running before proceeding.
The confusing thing is that I'm not executing a script as such, literally just a php command, but I reckon it's multiple instances of the shell being called by the **cd /var/www/..etc..**. But what's important is that this command does execute every 3 minutes, update.php is used for populating a MySQL database with logs from a dedicated game server.

I figured that if I could contain the command in a screen, then I could just kill it after three minutes, or similarly, a bit of logic to close the previous instance before opening a new one. I'd just need some help with the exact syntax to use.

Sam.

---

### Post by Monicker on 2008-05-01
Did you check to make sure that no errors are occuring the during the loading of the information into mysql?  You should be receiving emails to your local machine account with any output from the cron job.  I would also look at that, and see if it shows a problem.  I would not just kill the php process each time; you need to find out why its hanging and not exiting normally.

---

### Post by DaRabman on 2008-05-01
The server machine is local (that is to say, I'm using it right now). When I change directory and **php update.php** manually in bash there are no problems or residual processes so I'm sure it's not a problem with the actual file being executed. Is there any way of turning on an error log for crontab?

---

### Post by rickh57 on 2008-05-01
You should be able to direct the output of the crontab entry to a log file. (e.g. "*/3 * * * * cd /var/www/soldat/ && php update.php> /tmp/updates.log 2>&1")

Then look at the file.

---

### Post by DaRabman on 2008-05-01
The action of sending the output to a log seems to have solved the problem itself! Although the log only showed what I saw on executing the php file manually, I think the system just needed somewhere to put the shell output. I don't know if that's what it actually means, but at least the problem is solved in one way or another.

---

