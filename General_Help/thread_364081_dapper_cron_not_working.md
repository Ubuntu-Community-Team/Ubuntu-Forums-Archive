---
title: "dapper cron not working"
date: 2007-02-17
forum: General Help
---

### Post by eng69 on 2007-02-17
I am having a problem with cron.  I have a simple script that is not working.  I am fairly new to linux in general, but have a good grasp of some basics.  Here is the situation.

Here is the content of my script.

echo "cron test" >> /home/jeng4/az511/crontest.txt

my crontab file has the following:
*/5 * * * * /home/az511/test.sh

Nothing happens.  I dont get any output files, nothing happens.  

when i type in  ps -e | grep cron
i get
4622 ? 00:00:00 cron

so i think its running, but nothing is happening.  I cannot find anything in the log files relating to cron, either.  

I tried setting it up as root and nothing happens either.  I also have tried restarting the daemon, stopping it, then starting it, rebooting the computer.  Nothing seems to help.

I am stumped on this one.  Any suggestions would be great.

Thanks,

---

### Post by yabbadabbadont on 2007-02-17
Just to ask an obvious question, what does "crontab -l" show when you run it as your user?

---

### Post by llamakc on 2007-02-17
Worked for me when I made the script executable, and added a shebang.

---

### Post by WW on 2007-02-17
Don't forget to make the script executable:
>  $ chmod u+x test.sh

---

### Post by eng69 on 2007-02-17
Those were amazingly fast responses.

crontab -l shows 
*/5 * * * * /home/az511/test.sh


ow yeah i did a chmod 777 on the script.

i still got nuthin.

---

### Post by llamakc on 2007-02-17
Add a shebang to your script at the top. Add:

#!/bin/sh

as the first line. Save the file. Wait 5 minutes.

---

### Post by WW on 2007-02-17
You script writes to **/home/jeng4/az511/crontest.txt**, but your command in the crontab is **/home/az511/test.sh**.  Should that be **/home/jeng4/az511/test.sh**?

Edit:  My test worked without the 'shebang'.

---

### Post by eng69 on 2007-02-17
I have added the shebang to the script.

excuse me for the lagged response, i was banging my head against the desk.

boy do i feel like a complete retard... amazing... it was the path that was the problem.  I cant believe how stupid i feel right now.  two days trying to figure out whats wrong...


thanks a bunch... that was uber fast.  At least i found a new forum.

just out of curiosity, where can i find the logs for cron?

---

### Post by llamakc on 2007-02-17
I've a follow-up question: if one's cron script does not have the shebang, **will errors get logged somewhere?** Before I chmod'd the test script I received this via email:

```

From: Cron Daemon <root@ll>
Date: Sat, 17 Feb 2007 19:25:01 -0600 (CST)
To: ken@ll
Subject: Cron <ken@ll> /home/ken/bin/crontest.sh

/bin/sh: /home/ken/bin/crontest.sh: Permission denied

```

Which told me what was wrong.

I'm familiar with redirecting stderr, but in this test case I didn't do that in my cron line.

---

### Post by WW on 2007-02-17
cron writes log messages to /var/log/syslog. Try this:
> $ grep "CRON" /var/log/syslog | less

According to **man cron**, "When executing commands, any output is mailed to the owner of the crontab (or to the user named in the MAILTO environment variable in  the  crontab, if  such  exists)."  If you don't want that to happen, you can redirect stdout and stderr to /dev/null.

---

### Post by llamakc on 2007-02-17
> **WW said:**
> cron writes log messages to /var/log/syslog. Try this:


According to **man cron**, "When executing commands, any output is mailed to the owner of the crontab (or to the user named in the MAILTO environment variable in  the  crontab, if  such  exists)."  If you don't want that to happen, you can redirect stdout and stderr to /dev/null.

Thanks. I should have read the man page.

---

