---
title: "Zabbix Daemon User Permissions"
date: 2007-05-04
forum: General Help
---

### Post by artesvida on 2007-05-04
I have a daemon process (zabbix_server) that is running as a local user named 'zabbix.'  When I su to the zabbix user, I can use the modem that I have installed at /dev/ttyS1.  However, the daemon process, which I swear is running as the zabbix user, cannot open /dev/ttyS1 unless I chmod 666 the device.  WHY?!  It works fine interactively, but running in background it does not.  It's clearly a permissions issue, because opening the device up to everyone makes it work.

I don't really want to change the security on the device.  Any thoughts on what I might be doing wrong?

I might have to post this to the Zabbix forums, but I thought I would try here first.

Just fyi:
ls -l /dev/ttyS1
crw-rw---- 1 root dialout 4, 65 2007-05-04 09:43 /dev/ttyS1

groups zabbix
zabbix : zabbix dialout

ps -ef | grep zabbix_server
zabbix    3341     1  0 09:43 ?        00:00:00 /usr/local/bin/zabbix_server
zabbix    3422  3341  0 09:43 ?        00:00:00 /usr/local/bin/zabbix_server
zabbix    3423  3341  0 09:43 ?        00:00:00 /usr/local/bin/zabbix_server
zabbix    3424  3341  0 09:43 ?        00:00:04 /usr/local/bin/zabbix_server
zabbix    3425  3341  0 09:43 ?        00:00:03 /usr/local/bin/zabbix_server
zabbix    3426  3341  0 09:43 ?        00:02:03 /usr/local/bin/zabbix_server
zabbix    3427  3341  0 09:43 ?        00:00:00 /usr/local/bin/zabbix_server
zabbix    3428  3341  0 09:43 ?        00:00:00 /usr/local/bin/zabbix_server
zabbix    3429  3341  0 09:43 ?        00:00:00 /usr/local/bin/zabbix_server
zabbix    3430  3341  0 09:43 ?        00:00:00 /usr/local/bin/zabbix_server
zabbix    3431  3341  0 09:43 ?        00:00:00 /usr/local/bin/zabbix_server
franka   10391  3517  0 15:37 pts/0    00:00:00 grep zabbix_server

Those processes are running as the 'zabbix' user, and therefore have the same rights as the 'zabbix' user, right?

---

### Post by artesvida on 2007-05-09
In case anyone else is having this problem...  I posted a few messages on the Zabbix forum, and the developer tells me that if the zabbix_server daemon logs on with the "zabbix" user, then it inherits the rights of the primary group (gid) of that user (in this case, the "zabbix" group) ONLY, and it doesn't inherit any of the rights of the user's additional groups.

Is this a Zabbix thing?  Or is this common to all init.d daemons?

---

