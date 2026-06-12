---
title: "kernel panic"
date: 2013-12-12
forum: General Help
---

### Post by kurrent93 on 2013-12-12
Hi

Yesterday my ubuntu 13.10 froze. I did a hard reboot. Then it crashed to a kernel panic screen.

Today I cannot start.

I have tried running live cd, but I get as far as a screen that says:
Mount Failed
An error occurred while mounting the device you entered for your root file system (/dev/sbd1) on /target.

Please check the syslog for more information.

I have no idea where the syslog is or how I view it.

What might the problem be? How can I fix this?

---

### Post by kurrent93 on 2013-12-12
I managed to fix this problem using these:
[http://askubuntu.com/questions/8566/...-recovery-mode](http://askubuntu.com/questions/8566/...-recovery-mode)
[http://pissedoffadmins.com/os/mount-...m2_member.html](http://pissedoffadmins.com/os/mount-...m2_member.html)

---

### Post by claracc on 2013-12-12
Glad you have got fixed your problem.

Syslog file containing the events of the system is in /var/log/ directory and you can see the file executing the following command in a xterm:```
less /var/log/syslog
```

Please, mark the thread as solved with "thread tools" in order to get more quickly the information. Thanks

---

