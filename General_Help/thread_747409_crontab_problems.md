---
title: "crontab problems"
date: 2008-04-06
forum: General Help
---

### Post by linuxonbute on 2008-04-06
i am running ubuntu 7.10  and I am having real problems with cron.

crontab is :


# m h  dom mon dow   command
11 20 * * * -f /home/norman/Documents/Kingdom-Hall/Skype/startup

and startup is :

date>>/home/norman/Documents/Kingdom-Hall/Skype/skt
skype &
echo Sleeping
sleep 12
echo Continueing
/home/norman/Documents/Kingdom-Hall/Skype/skypeconfsunday.py


running this manually works fine  but nothing does from the crontab.

i have tried the same in root's crontab but although the date gets appended 
to the skt file the rest of it doesn't work.

Has anyone any idea why?

thanks

---

