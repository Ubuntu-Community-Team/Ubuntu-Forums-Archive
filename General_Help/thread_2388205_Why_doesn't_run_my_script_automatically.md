---
title: "Why doesn't run my script automatically"
date: 2018-03-30
forum: General Help
---

### Post by stylus3530 on 2018-03-30
Hello

Have a script made as follows:

sudo -i
cd /usr/sbin/
nano test.sh
chmod +x test.sh

nano /etc/crontab

SHELL=/bin/sh PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user command 
17 * * * * root cd / && run-parts --report /etc/cron.hourly 
25 6 * * * root test -x /usr/sbin/anacron || ( cd / && run-parts --repo$ 
47 6 * * 7 root test -x /usr/sbin/anacron || ( cd / && run-parts --repo$ 
52 6 1 * * root test -x /usr/sbin/anacron || ( cd / && run-parts --repo$ 
20 08 * * * root /usr/sbin/test.sh #

What am I doing wrong? So it should be run at 8.20

Thanks in advance

STYLUS

---

### Post by ajgreeny on 2018-03-30
I am confused; are those four lines in your post, ie,
```
sudo -i
cd /usr/sbin/
nano test.sh
chmod +x test.sh
```
exactly what is in the script?  If not show us the script content.
Are you trying to run this script in your own user crontab or root's crontab?

---

### Post by TheFu on 2018-03-30
**sudo -i **creates a new shell.
You cannot run interactive programs in cron.  So sudo -i won't work.  nano won't work. Definitely don't bother trying to run any GUI/TUI programs either.

If  a program doesn't run, then end, without human interaction, don't use it in a cron job.

Please use *code tags* when posting commands/scripts.  I can't tell what you intended to be part of the script and what is just random, added, commands and what is a different file.

---

### Post by yancek on 2018-03-30
What exactly do you expect your script to do?  You haven't posted it and from the information you have posted, all we can see is that you have created an empty file named test.sh in /usr/sbin and made it executable.  There is nothing wrong with the crontab entry, it will work with a functioning shell script.

---

