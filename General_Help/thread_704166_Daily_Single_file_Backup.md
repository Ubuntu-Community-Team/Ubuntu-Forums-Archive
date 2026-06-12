---
title: "Daily Single file Backup?"
date: 2008-02-22
forum: General Help
---

### Post by Abaddon on 2008-02-22
Hey all,

I'm currently warring with my ISP about some usage that is supposed to be counting as free download, but isn't, so I've installed squid, and modified the access.log to provide date, time, IP and URL of every file I access with my computer.

Is there a straightforward way (cron, script etc) to backup my access.log to access_ddmmyy.log (eg as part of my startup) so everyday, I get a fresh file without overwriting the old ones?

Thanks in advance,

---

### Post by SpaceTeddy on 2008-02-22
have  a look at /etc/logrotate.d (configuration of logrotate)
it should let you define files and intervalls, and how many "old" files you want to keep
should be pretty straight forwards :)

---

### Post by Abaddon on 2008-02-23
do I have to change a startup setting so that logrotate actually runs each time I turn the computer on?

---

### Post by SpaceTeddy on 2008-02-24
logrotate runs automatically on every system unless you specificially turn it off... no need to restart or change anything, it will pick up the changes by default... (i think)

---

