---
title: "I can't get .profile to run"
date: 2015-03-22
forum: General Help
---

### Post by jeff-p-hanson on 2015-03-22
Ubuntu 14.04 desktop

I am running a python script from cron. It does not read my ~/.bashrc so it does not get my PYTHONPATH variable. I've tried creating a ~/.profile and editing the /etc/profile, but nobody, interactive or batch, seems to read these files. I have also edited my .bashrc so it sets PYTHONPATH before it checks if it's being run in interactive mode. How can I set PYTHONPATH in an initialization script (like .profile) when running a cron job?

Thanks.

---

### Post by bab1 on 2015-03-22
There are limited shell environment variables when using cron.  You must declare ***ALL*** the variables explicitly in the script you are running.  This most likely include the path to the executable you are using.

---

### Post by Holger_Gehrke on 2015-03-22
You can just define the variables you need in the crontab. For more details see 'man 5 crontab'.

---

