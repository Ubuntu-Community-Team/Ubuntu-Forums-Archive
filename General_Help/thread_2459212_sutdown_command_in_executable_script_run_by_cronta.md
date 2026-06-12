---
title: "sutdown command in executable script run by crontab"
date: 2021-03-13
forum: General Help
---

### Post by Old Jimma on 2021-03-13
Hello Ubuntuers:

I wanto to run an executable script at 4am every day in the day using crontab.... and the only command I want in that script is the shutdown command.

My executable script to do this does not work. Here it is:


> 

## [https://linuxhandbook.com/linux-shutdown-command/](https://linuxhandbook.com/linux-shutdown-command/)

date

[COLOR="#FF0000"][B]shutdown -r 07:00
[/B][/COLOR]



Also, here is my crontab command:

> 
00 04 * * * /path/shutdown.sh > /path/shutdown.log 2>&1



I have checked and my script is executable: -rwxrwxrwx

This scheme does not work. The documentations says that shutdown can only be run by sudo.

How do I get it to run as sudo in an executable script run by crontab?

Thanks,
Old Jimma

---

### Post by yancek on 2021-03-13
You have your thread marked as solved, is it?  If not, one way to do this is to preface the shutdown command with sudo:

> 00 04 * * * sudo /path/shutdown.sh > /path/shutdown.log 2>&1 

You can then use visduo to give your user privilege to run that specific command as root (sudo).  Example at the link below.

[https://www.atrixnet.com/allow-an-unprivileged-user-to-run-a-certain-command-with-sudo/](https://www.atrixnet.com/allow-an-unprivileged-user-to-run-a-certain-command-with-sudo/)

---

### Post by Holger_Gehrke on 2021-03-13
Since shutdown is supposed to be run by root (or someone allowed to act as root through sudo), I see two ways - or three if we count yancek's idea of changing /etc/sudoers allowing your account to run 'sudo shutdown -r' without asking for a password - to do this. One would be to put the command into root's crontab ('sudo crontab -u root -e'). There should be no need for sudo then. The other would be to put the command into the system crontab (/etc/crontab or a file in /etc/cron.d) with the user account field set to 'root'. See the manual page for the crontab file format for details (man 5 crontab), especially the differences in format between a normal user-specific crontab and the system crontab.

Holger

---

### Post by Old Jimma on 2021-03-13
Dear Holger and Yancek:

THank you for your replies.

I'll start working on this. I've gotta gig and have to split. Be back tomorrow!

Old

---

