---
title: "Command to connect to wired network at startup?"
date: 2007-08-28
forum: General Help
---

### Post by macdim on 2007-08-28
Hi everyone,
I was wondering if there is a command that allows me to enable my wired network connection instead of using the connections manager beside the clock.  Ubuntu does not connect to it by default, but when I click the icon and click on "wired network" from the list that appears, it proceeds to connect without trouble.  Also, how would I be able to run this command automatically at boot time?
Thanks

---

### Post by 505 on 2007-08-28
Take a look at the file /etc/networking/interfaces and the man page 'man interfaces' There might be something wrong there. This file is automatically parsed at boot, so you don't have to change anything there.

---

