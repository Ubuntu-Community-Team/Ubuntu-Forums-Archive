---
title: "How to have system email me if no data is written to a specific dir in x-time frame?"
date: 2015-01-20
forum: General Help
---

### Post by Roasted on 2015-01-20
I have an odd-ball question... I have two network based surveillance cameras recording 24/7 to an always-on system. The cameras themselves do not have any sort of email feature, so I don't have a fallback in case the camera's network drive fills up on the end system. I got to wondering, is there a way I could rig up a script to email me if a specific directory has no new files (video feeds in this case) written after a certain time?

Something like "If no new files recorded in 10 minutes within /media/surveillance drive, mailto: [email]roasted@email.com[/email]"

Eh?

p.s. - the only time the cameras seem to drop recording is if the target drive gets full. They'll re-try a few times, but if all fails, they shut off recording. I have a script to auto clean the drive with feeds older than a week that runs at midnight, so this largely takes care of the issue, but more than anything I just want to KNOW the recording dropped if it should ever happen again.

---

### Post by Roasted on 2015-01-20
edit - accidental double post when forums didn't respond. Feel free to delete.

---

### Post by kevdog on 2015-01-21
I'd set up a cron job that references a particular script.  With cron you could make the script run on whatever time interval you wanted -- every ten minutes, not a problem.  

Within the script itself -- I'm not sure what exactly you want, but you could check if a particular file existed, if the file was greater than x bytes in size, the last creation date, etc.  I usually do this in bash however any programming language could be used.  If whatever condition you were testing for was true you would then email yourself.  For the email to work however, you have to have a MTU or mail transfer agent setup.  This can be kind of tricky but there are plenty of posts in the forums to help you.

---

