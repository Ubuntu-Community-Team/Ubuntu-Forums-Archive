---
title: "Sudo and other things not working"
date: 2007-03-17
forum: General Help
---

### Post by jamesstl on 2007-03-17
Was trying to add to repositories.  Today, when I click on the Synaptic icon, nothing happens.  Same with a few others in the system/administration menu.

Tried to edit /etc/apt/sources.list and when I used the terminal and typed sudo, etc, I got the following return:

sudo: /etc/sudoers is mode 0740, should be 0440
sendmail: fatal: open /etc/postfix/main.cf: No such file or directory

Doesn't matter if I type just sudo or sudo plus a command, the answer is always the same.

How do I correct this.  I'm VERY new to Ubuntu and am stumped at correcting this.

---

### Post by johnc4510 on 2007-03-17
It looks like the file /etc/sudoers needs to be change from 0740 permissions to 0440 permissions. Here is the wiki page that will tell you how to do this:
[http://en.wikipedia.org/wiki/Chmod](http://en.wikipedia.org/wiki/Chmod)

---

### Post by aysiu on 2007-03-17
Reboot into recovery mode and type ```
chmod 0440 /etc/sudoers
reboot
``` For more details on recovery mode, check this out:
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

