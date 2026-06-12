---
title: "crontab Not Executing Entry"
date: 2015-09-06
forum: General Help
---

### Post by eklikeroomys on 2015-09-06
Hi,

I added the entry below to cron using sudo crontab -e:

```
# Edit this file to introduce tasks to be run by cron.#
# Each task to run has to be defined through a single line
# indicating with different fields when the task will be run
# and what command to run for the task
#
# To define the time you can provide concrete values for
# minute (m), hour (h), day of month (dom), month (mon),
# and day of week (dow) or use '*' in these fields (for 'any').#
# Notice that tasks will be started based on the cron's system
# daemon's notion of time and timezones.
#
# Output of the crontab jobs (including errors) is sent through
# email to the user the crontab file belongs to (unless redirected).
#
# For example, you can run a backup of all your user accounts
# at 5 a.m every week with:
# 0 5 * * 1 tar -zcf /var/backups/home.tgz /home/
#
# For more information see the manual pages of crontab(5) and cron(8)
#
# m h  dom mon dow   command
0 1  * * *   apt-get -y update && apt-get -y upgrade



```

I want my system to be updated every night at 1 am. The format of the entry seems correct in my inexperienced view. Can someone please help explaining what I am doing wrong?

Thanks, 
Chris

---

### Post by ian-weisser on 2015-09-06
Try using the complete path: /usr/bin/apt-get
That crontab entry won't actually install all updates. Kernel updates won't be included.

Discover the complete path using the 'which' command: 'which apt-get'

A different way to accomplish the same thing is to install the 'unattended-upgrades' package, and edit the settings to match your desires.

I'm not a big fan of 'sudo crontab.' It's not included in the normal root crontabs in /etc/cron.d/ , nor searchable among them when you want to change a setting. If you browse /etc/cron.daily , you will discover that apt already has a daily cron trigger - that's what 'unattended-upgrades' uses.

---

### Post by eklikeroomys on 2015-09-07
Thanks, I will have a look at unnattended-upgrades. I got it to work by adding sudo to each of the apt-get commands. How can I get it to include Kernel updates? 

Thanks,
Chris

---

