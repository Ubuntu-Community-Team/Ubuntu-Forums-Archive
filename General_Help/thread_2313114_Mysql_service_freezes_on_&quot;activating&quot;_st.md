---
title: "Mysql service freezes on &quot;activating&quot; status"
date: 2016-02-09
forum: General Help
---

### Post by mariuscasado on 2016-02-09
Hi, it's my first time here. Have to say that you all (ubuntu modds, developers, support team) are doing a great work.

To the point: I Cannot start my mysql server, it freezes when activating. The service mysql status shows this:

&#9679; mysql.service - MySQL Community Server
   Loaded: loaded (/lib/systemd/system/mysql.service; enabled; vendor preset: enabled)
   Active:** activating** (start-post) since dt 2016-02-09 21:31:30 CET; 2min 24s ago
  Process: 28969 ExecStart=/usr/bin/mysqld_safe (code=exited, status=0/SUCCESS)
  Process: 28967 ExecStartPre=/usr/share/mysql/mysql-systemd-start pre (code=exited, status=0/SUCCESS)
 Main PID: 28969 (code=exited, status=0/SUCCESS);         : 28970 (mysql-systemd-s)
   CGroup: /system.slice/mysql.service
           &#9492;&#9472;control
             &#9500;&#9472;28970 /bin/bash /usr/share/mysql/mysql-systemd-start post
             &#9492;&#9472;29764 sleep 1

And keeps showing this even if I restart my computer.

I've fully uninstalled mysql (following the steps of this post [http://stackoverflow.com/questions/10853004/removing-mysql-5-5-completely/16178696#16178696](http://stackoverflow.com/questions/10853004/removing-mysql-5-5-completely/16178696#16178696)).
Then installed it again and the problem still exists.

I was wondering if any of you have experienced a problem like this before. I've been searching for half an hour on the internet and I've found nothing...

Thanks in advance.


EDIT: Now I've remembered I was changing some users permissions before the last reboot (when it started to fail). May this have any connection to the problem?

---

### Post by sandyd on 2016-02-10
Any errors in /var/log/mysql?

Does
```
ps ax | grep mysql
```
return any mysql processes?

If there are no mysql processes, does
```

sudo mysqld
```
return any errors?

---

### Post by mariuscasado on 2016-02-10
tailing the error.log shows this:

2016-02-10 11:31:53 10241 [ERROR] InnoDB: Attempted to open a previously opened tablespace. Previous tablespace *database*/*table* uses space ID: 5 at filepath: ./*database*/*table*.ibd. Cannot open tablespace mysql/slave_worker_info which uses space ID: 5 at filepath: ./mysql/slave_worker_info.ibd

Seems this came because a bad starting from hibernation, ubuntu crashed and mysql was forced to close.


Thanks a lot for your help. Guess I have to get used to the error logs.


EDIT: Deleting the .ibd file and installing mysql again solved my problem. Thanks again for your help.

---

