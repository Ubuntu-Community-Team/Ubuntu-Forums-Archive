---
title: "Use cron to execute script as root"
date: 2014-07-02
forum: General Help
---

### Post by Tristan_Williams on 2014-07-02
I have a script, let's call it example.sh

In crontab, I have the following line:
0 24 * * * example.sh

How would I configure it so that the script gets run automatically as root?
I need to do this because most of the commands require root permissions, and I will not be around the computer most days.

---

### Post by sisco311 on 2014-07-02
Add the command to the root user's crontab. [uhelp]community/CronHowto[/uhelp]

---

