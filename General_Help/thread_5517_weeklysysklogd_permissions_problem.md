---
title: "weekly/sysklogd permissions problem"
date: 2004-11-19
forum: General Help
---

### Post by ubuntu_demon on 2004-11-19
Hi,

I was trying to secure my log files. 

chmod 751 /var/log /etc/logrotate.d
chmod 640 /etc/syslog.conf /etc/logrotate.conf
chmod 640 /var/log/*.log

But now I get :

/etc/cron.weekly/sysklogd:
ln: creating hard link `/var/log//messages.0' to `/var/log/messages': Operation
+not permitted
Error hardlinking /var/log/messages to /var/log//messages.0
run-parts: /etc/cron.weekly/sysklogd exited with return code 8

I obviously want sysklogd to work :)

Thnx

---

### Post by ubuntu_demon on 2004-11-29
But now the problem is irritating me some more because apt-get can't upgrade sysklogd :

chown: changing ownership of `/var/log/messages': Operation not permitted

chattr -i didn't help

chmod and chown give the same error

thnx

---

### Post by ubuntu_demon on 2004-11-29
I chmodded /var/log :
chmod 755 /var/log

messages has the following permissions :
-rw-r--r--   1 root     root     1080425 2004-11-29 17:41 messages

I still can't chmod messages.

---

### Post by ubuntu_demon on 2004-12-02
lsattr gives :

-----a----------- messages

I can't remove or chmod or chown the file.

anyone ?

---

### Post by ubuntu_demon on 2004-12-02
I thought the "a" attribute couldn't be it (append only) but it was :). 

solved!

---

