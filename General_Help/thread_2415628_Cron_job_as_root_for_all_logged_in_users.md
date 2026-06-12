---
title: "Cron job as root for all logged in users"
date: 2019-03-29
forum: General Help
---

### Post by manjeet.singh on 2019-03-29
Hi, I am trying to create a simple script for scrot to take screenshot of any gui logged in user on system. I need to run this script / commands with root user so that it will save screenshots in any of root permission folder and then rsync to remote directory with auto ssh from root only so that any other user will not edit it. Issue is, i am not able to run cron job as root. I have logged in with terminal with root. created required folder and script. Given executable permission to script. Edited cron job with crontab -e as well as editing the /etc/crontab file. Everytime, no matter what i do, script do not run with cron or may be do not work. If i simply run the script it does what it suppose to do but not with cron.

This is my script:
#!/bin/bash
DISPLAY=:0 scrot /screenshots/data/$(hostname)-%Y-%m-%d-%H_%M_%S.jpg -q 80
rsync /screenshots/data/* -e ssh root@IP:/Screenshots/

Please help me with this cron job, i urgently need it..
I run both Ubuntu and Lubuntu in my environment if it matters.

Thanks.

---

### Post by SeijiSensei on 2019-03-29
Without showing us the crontab entry it's hard to know where the problem lies.

My first guess is that you are not using /full/path/to/the/script in the cron entry. Cron has a more limited environment than ordinary users so using full paths is often required.

---

