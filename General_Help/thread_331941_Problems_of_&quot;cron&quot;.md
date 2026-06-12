---
title: "Problems of &quot;cron&quot;"
date: 2007-01-05
forum: General Help
---

### Post by yuliang on 2007-01-05
Could anybody tell me how to use *cron*, step by step? I created a *crontab* file and added a task, but nothing ever happened. Do I need to run the command *cron* in the first place? But here is what I got:

[I]yuliang@thinkpad:/$ cron
cron: can't open or create /var/run/crond.pid: Permission denied
yuliang@thinkpad:/$ sudo cron
cron: can't lock /var/run/crond.pid, otherpid may be 4690: Resource temporarily unavailable
[/I]

](*,)

---

### Post by kingmonkey on 2007-01-05
Here are some guides:

[http://www.crontabrocks.org/](http://www.crontabrocks.org/)

[http://www.adminschoice.com/docs/crontab.htm](http://www.adminschoice.com/docs/crontab.htm)

---

### Post by AusIV4 on 2007-01-05
//Manage crontabs executed by your user
$ crontab -e
//Manage crontabs executed by root
$ sudo crontab -e
//Manage crontabs executed by other users (I've used this for mythtv)
$ sudo -u <username> crontab -e

---

### Post by SyvanX on 2007-01-05
Your first command, "cron" didn't work because you needed root priviliges, which you correctly identified.

When you ran "sudo cron" it didn't like that, since cron was already running.  The commands cron run won't be invoked until the times that are specified in the /etc/crontab file.  

Here is a site that will give you a pretty good overview of the usage of cron.  [Intro to Cron]("http://www.unixgeeks.org/security/newbie/unix/cron-1.html")

If you still have questions post your crontab file, so we can see where the problem is happening.

---

### Post by i-Buntu-2 on 2007-03-24
I set-up a cron job to copy files from one drive to another using rsync and output a log to /var/log/rsync.log

Initially I was getting the error below:

cron: can't open or create /var/run/crond.pid: Permission denied

As I'm running cron as root (sudo crontab -e)  I checked the permissions on /var/run/crond.pid and they were set to -rw-r--r-- (0644)

Using chmod I changed this to -rwxr--r-- (0744) and this appears to of resolved the problem.

Being somewhat of a *nix newbie I'm not sure if this is the correct way to resolve the cron error (security considerations etc.) but my cron job has run successfully.

All feedback welcome

---

