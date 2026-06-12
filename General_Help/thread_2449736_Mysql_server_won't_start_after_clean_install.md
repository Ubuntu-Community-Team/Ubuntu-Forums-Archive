---
title: "Mysql server won't start after clean install"
date: 2020-09-01
forum: General Help
---

### Post by cscj01 on 2020-09-01
I just completed a clean install from a Live DVD of Ubuntu 18.04.5 x64.  I had a backup of my old system and restored my home directory to my new system.  I also moved my /var/lib/mysql folder from my backup to the new system after renaming the new /var/lib/mysql to mysql.old with the following commands:```
cd /var/lib
sudo mv mysql mysql.old
sudo rsync -av /media/butch/system/var/lib/mysql .
```I then issued the following command```
sudo service mysql start
```to start the MySQL server.  I received the following messages> &#9679; mysql.service - MySQL Community Server
   Loaded: loaded (/lib/systemd/system/mysql.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Tue 2020-09-01 13:44:43 EDT; 17min ago
  Process: 1452 ExecStartPre=/usr/share/mysql/mysql-systemd-start pre (code=exited, status=1/FAILURE)

Sep 01 13:44:43 cp1 systemd[1]: Starting MySQL Community Server...
Sep 01 13:44:43 cp1 systemd[1]: mysql.service: Control process exited, code=exited status=1
Sep 01 13:44:43 cp1 systemd[1]: mysql.service: Failed with result 'exit-code'.
Sep 01 13:44:43 cp1 systemd[1]: Failed to start MySQL Community Server.
Sep 01 13:44:43 cp1 systemd[1]: mysql.service: Service hold-off time over, scheduling restart.
Sep 01 13:44:43 cp1 systemd[1]: mysql.service: Scheduled restart job, restart counter is at 5.
Sep 01 13:44:43 cp1 systemd[1]: Stopped MySQL Community Server.
Sep 01 13:44:43 cp1 systemd[1]: mysql.service: Start request repeated too quickly.
Sep 01 13:44:43 cp1 systemd[1]: mysql.service: Failed with result 'exit-code'.
Sep 01 13:44:43 cp1 systemd[1]: Failed to start MySQL Community Server.I checked the Journal```
journalctl -xe
Sep 01 14:30:50 cp1 systemd[1]: Stopped MySQL Community Server.
-- Subject: Unit mysql.service has finished shutting down
-- Defined-By: systemd
-- Support: http://www.ubuntu.com/support
-- 
-- Unit mysql.service has finished shutting down.
Sep 01 14:30:50 cp1 systemd[1]: Starting MySQL Community Server...
-- Subject: Unit mysql.service has begun start-up
-- Defined-By: systemd
-- Support: http://www.ubuntu.com/support
-- 
-- Unit mysql.service has begun starting up.
Sep 01 14:30:50 cp1 mysql-systemd-start[4201]: ERROR: Unable to start MySQL server:
Sep 01 14:30:50 cp1 **mysql-systemd-start[4201]: mysqld: Can't change dir to '/var/lib/mysql/' (Errcode: 13 - Permission denied)**
Sep 01 14:30:50 cp1 mysql-systemd-start[4201]: 2020-09-01T18:30:50.994087Z 0 [ERROR] unknown variable 'key_buffer=16M'
Sep 01 14:30:50 cp1 mysql-systemd-start[4201]: 2020-09-01T18:30:50.996675Z 0 [ERROR] Aborting
Sep 01 14:30:50 cp1 mysql-systemd-start[4201]: Please take a look at https://wiki.debian.org/Teams/MySQL/FAQ for tips on fixing common upgrade issues.
Sep 01 14:30:50 cp1 mysql-systemd-start[4201]: Once the problem is resolved, restart the service.
Sep 01 14:30:50 cp1 systemd[1]: mysql.service: Control process exited, code=exited status=1
Sep 01 14:30:50 cp1 systemd[1]: mysql.service: Failed with result 'exit-code'.
Sep 01 14:30:50 cp1 systemd[1]: Failed to start MySQL Community Server.
-- Subject: Unit mysql.service has failed
-- Defined-By: systemd
-- Support: http://www.ubuntu.com/support
-- 
-- Unit mysql.service has failed.
-- 
-- The result is RESULT.
Sep 01 14:30:51 cp1 systemd[1]: mysql.service: Service hold-off time over, scheduling restart.
Sep 01 14:30:51 cp1 systemd[1]: mysql.service: Scheduled restart job, restart counter is at 5.
-- Subject: Automatic restarting of a unit has been scheduled
-- Defined-By: systemd
-- Support: http://www.ubuntu.com/support
-- 
-- Automatic restarting of the unit mysql.service has been scheduled, as the result for
-- the configured Restart= setting for the unit.
Sep 01 14:30:51 cp1 systemd[1]: Stopped MySQL Community Server.
-- Subject: Unit mysql.service has finished shutting down
-- Defined-By: systemd
-- Support: http://www.ubuntu.com/support
-- 
-- Unit mysql.service has finished shutting down.
Sep 01 14:30:51 cp1 systemd[1]: mysql.service: Start request repeated too quickly.
Sep 01 14:30:51 cp1 systemd[1]: mysql.service: Failed with result 'exit-code'.
Sep 01 14:30:51 cp1 systemd[1]: Failed to start MySQL Community Server.
-- Subject: Unit mysql.service has failed
-- Defined-By: systemd
-- Support: http://www.ubuntu.com/support
-- 
-- Unit mysql.service has failed.
-- 
-- The result is RESULT.

[2]+  Stopped                 journalctl -xe

``` and saw that permission was denied for mysql-server to change to /var/lib//mysql.  I then checked the permissions on the two folders, /var/lib/mysql and /var/lib/mysql.old and found that the user ID for the newly installed /var/lib/mysql (now mysql.old) is 'MySQL Server' and on the /var/lib/mysql (the one from my system backup) is root.  There is no user named 'MySQL Server' in my new system.  The default user for mysql-server is root according to the documentation.  So my question here is how to proceed?  What do I need to change and where?  Thanks for any help.

---

### Post by cscj01 on 2020-09-01
bump

---

### Post by cscj01 on 2020-09-02
I resolved the issue by removing and reinstalling mysql.

---

