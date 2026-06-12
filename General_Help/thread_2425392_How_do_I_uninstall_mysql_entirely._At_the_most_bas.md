---
title: "How do I uninstall mysql *entirely*. At the most basic level."
date: 2019-08-25
forum: General Help
---

### Post by david503 on 2019-08-25
18.04.2 

I kept having this problem:

```

bog@bog-Lenovo-Product:~/Downloads$ sudo systemctl status mysql
&#9679; mysql.service - MySQL Community Server
   Loaded: loaded (/lib/systemd/system/mysql.service; disabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Sun 2019-08-25 13:02:48 EDT; 32min ago
     Docs: man:mysqld(8)
           http://dev.mysql.com/doc/refman/en/using-systemd.html
 Main PID: 17132 (code=exited, status=1/FAILURE)
   Status: "Data Dictionary upgrade from MySQL 5.7 in progress"


Aug 25 13:02:43 bog-Lenovo-Product systemd[1]: Starting MySQL Community Server...
Aug 25 13:02:48 bog-Lenovo-Product systemd[1]: mysql.service: Main process exited, code=exited, status=1/FAILURE
Aug 25 13:02:48 bog-Lenovo-Product systemd[1]: mysql.service: Failed with result 'exit-code'.
Aug 25 13:02:48 bog-Lenovo-Product systemd[1]: Failed to start MySQL Community Server.

``` 

So after hours of frustration, I took advice from a stackoverflow and removed the packages, deleted everything in /var/lib/mysql, and deleted the mysql user.

And then followed this: (even though I'm on 18.04):

[https://linuxscriptshub.com/uninstall-completely-remove-mysql-ubuntu-16-04/](https://linuxscriptshub.com/uninstall-completely-remove-mysql-ubuntu-16-04/)

That's enough to nuke it right?

And did [COLOR=inherit][FONT=Monaco]sudo apt-get install mysql-server[/FONT][/COLOR]

Now I get this:

```

bog@bog-Lenovo-Product:~/Downloads$ sudo systemctl status mysql
&#9679; mysql.service - MySQL Community Server
   Loaded: loaded (/lib/systemd/system/mysql.service; disabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Sun 2019-08-25 14:55:26 EDT; 17s ago
     Docs: man:mysqld(8)
           http://dev.mysql.com/doc/refman/en/using-systemd.html
  Process: 26926 ExecStartPre=/usr/share/mysql-8.0/mysql-systemd-start pre (code=exited, status=217/USER)
 Main PID: 17132 (code=exited, status=1/FAILURE)


Aug 25 14:55:25 bog-Lenovo-Product systemd[1]: Starting MySQL Community Server...
Aug 25 14:55:26 bog-Lenovo-Product systemd[1]: mysql.service: Control process exited, code=exited status=217
Aug 25 14:55:26 bog-Lenovo-Product systemd[1]: mysql.service: Failed with result 'exit-code'.
Aug 25 14:55:26 bog-Lenovo-Product systemd[1]: Failed to start MySQL Community Server.


bog@bog-Lenovo-Product:~/Downloads$ sudo systemctl start mysql
Job for mysql.service failed because the control process exited with error code.
See "systemctl status mysql.service" and "journalctl -xe" for details.
 


```

output of sudo journalctl -xe:


```


bog@bog-Lenovo-Product:~/Downloads$ sudo journalctl -xe
-- Defined-By: systemd
-- Support: http://www.ubuntu.com/support
-- 
-- Unit systemd-tmpfiles-clean.service has finished starting up.
-- 
-- The start-up result is RESULT.
Aug 25 14:48:49 bog-Lenovo-Product sudo[26656]:      bog : TTY=pts/0 ; PWD=/home/bog/Downloads ; USER=root ; COMMAND=/bin/systemctl start mysql
Aug 25 14:48:49 bog-Lenovo-Product sudo[26656]: pam_unix(sudo:session): session opened for user root by (uid=0)
Aug 25 14:48:49 bog-Lenovo-Product systemd[1]: Starting MySQL Community Server...
-- Subject: Unit mysql.service has begun start-up
-- Defined-By: systemd
-- Support: http://www.ubuntu.com/support
-- 
-- Unit mysql.service has begun starting up.
Aug 25 14:48:49 bog-Lenovo-Product systemd[26659]: mysql.service: Failed to determine user credentials: No such process
Aug 25 14:48:49 bog-Lenovo-Product systemd[26659]: mysql.service: Failed at step USER spawning /usr/share/mysql-8.0/mysql-systemd-start: No such process
-- Subject: Process /usr/share/mysql-8.0/mysql-systemd-start could not be executed
-- Defined-By: systemd
-- Support: http://www.ubuntu.com/support
-- 
-- The process /usr/share/mysql-8.0/mysql-systemd-start could not be executed and failed.
-- 
-- The error number returned by this process is 3.
Aug 25 14:48:49 bog-Lenovo-Product sudo[26656]: pam_unix(sudo:session): session closed for user root
Aug 25 14:48:49 bog-Lenovo-Product systemd[1]: mysql.service: Control process exited, code=exited status=217
Aug 25 14:48:49 bog-Lenovo-Product systemd[1]: mysql.service: Failed with result 'exit-code'.
Aug 25 14:48:49 bog-Lenovo-Product systemd[1]: Failed to start MySQL Community Server.
-- Subject: Unit mysql.service has failed
-- Defined-By: systemd
-- Support: http://www.ubuntu.com/support
-- 
-- Unit mysql.service has failed.
-- 
-- The result is RESULT.
Aug 25 14:48:52 bog-Lenovo-Product sudo[26660]:      bog : TTY=pts/0 ; PWD=/home/bog/Downloads ; USER=root ; COMMAND=/bin/journalctl -xe
Aug 25 14:48:52 bog-Lenovo-Product sudo[26660]: pam_unix(sudo:session): session opened for user root by (uid=0)
lines 1496-1531/1531 (END)
-- Defined-By: systemd
-- Support: http://www.ubuntu.com/support
-- 
-- Unit systemd-tmpfiles-clean.service has finished starting up.
-- 
-- The start-up result is RESULT.
Aug 25 14:48:49 bog-Lenovo-Product sudo[26656]:      bog : TTY=pts/0 ; PWD=/home/bog/Downloads ; USER=root ; COMMAND=/bin/systemctl start mysql
Aug 25 14:48:49 bog-Lenovo-Product sudo[26656]: pam_unix(sudo:session): session opened for user root by (uid=0)
Aug 25 14:48:49 bog-Lenovo-Product systemd[1]: Starting MySQL Community Server...
-- Subject: Unit mysql.service has begun start-up
-- Defined-By: systemd
-- Support: http://www.ubuntu.com/support
-- 
-- Unit mysql.service has begun starting up.
Aug 25 14:48:49 bog-Lenovo-Product systemd[26659]: mysql.service: Failed to determine user credentials: No such process
Aug 25 14:48:49 bog-Lenovo-Product systemd[26659]: mysql.service: Failed at step USER spawning /usr/share/mysql-8.0/mysql-systemd-start: No such process
-- Subject: Process /usr/share/mysql-8.0/mysql-systemd-start could not be executed
-- Defined-By: systemd
-- Support: http://www.ubuntu.com/support
-- 
-- The process /usr/share/mysql-8.0/mysql-systemd-start could not be executed and failed.
-- 
-- The error number returned by this process is 3.
Aug 25 14:48:49 bog-Lenovo-Product sudo[26656]: pam_unix(sudo:session): session closed for user root
Aug 25 14:48:49 bog-Lenovo-Product systemd[1]: mysql.service: Control process exited, code=exited status=217
Aug 25 14:48:49 bog-Lenovo-Product systemd[1]: mysql.service: Failed with result 'exit-code'.
Aug 25 14:48:49 bog-Lenovo-Product systemd[1]: Failed to start MySQL Community Server.
-- Subject: Unit mysql.service has failed
-- Defined-By: systemd
-- Support: http://www.ubuntu.com/support
-- 
-- Unit mysql.service has failed.
-- 
-- The result is RESULT.
Aug 25 14:48:52 bog-Lenovo-Product sudo[26660]:      bog : TTY=pts/0 ; PWD=/home/bog/Downloads ; USER=root ; COMMAND=/bin/journalctl -xe
Aug 25 14:48:52 bog-Lenovo-Product sudo[26660]: pam_unix(sudo:session): session opened for user root by (uid=0)
~
~
~
~
~
~
lines 1496-1531/1531 (END)



```

I checked if the user mysql exists and the group mysql exists.  They don't.  Why wouldn't the be recreated?  And do you think that's the problem?

---

