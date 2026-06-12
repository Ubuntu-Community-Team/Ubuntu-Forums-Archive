---
title: "@reboot in crontab doesn't work"
date: 2006-11-08
forum: General Help
---

### Post by mcpish on 2006-11-08
Help, I'm trying to add a command to my crontab with the @reboot command so that the task will start as a particular user but the @reboot command does not seem to work in Crontab, am I doing something wrong or does Ubuntu not support it?

---

### Post by dcstar on 2006-11-08
> **mcpish said:**
> Help, I'm trying to add a command to my crontab with the @reboot command so that the task will start as a particular user but the @reboot command does not seem to work in Crontab, am I doing something wrong or does Ubuntu not support it?

And I assume you are using the full path of /sbin/reboot so it will actually work?

---

### Post by dev-h on 2006-11-08
yep, u have to include the complete path

---

### Post by mcpish on 2006-11-08
I don't quite understand how this works, I thought simply the @reboot was a command for crontab to do something when the system boots up.

To be clear, I'm not trying to set a time for the SYSTEM to reboot, rather I want to run a command specifically as a particular user when the system starts but before X loads. (So I won't be putting any particular time for this crontab entry just simply the @reboot command).

Basically what I'm trying to do is I want to run "rtorrent" in a detached screen session as a particular user on my machine whenever the system starts up, but before X even loads.  I know I can make a startup script in init.d but that always runs it as root which I don't want to do.  I want this task to run as a certain user regardless if he/she is logged in or not, then when he/she logs in they can simply reattach that screen session of rtorrent whenever they load up a terminal to check the status.

I am following the advice of this article but it doesn't work 
[http://www.debian-administration.org/articles/372](http://www.debian-administration.org/articles/372)

---

