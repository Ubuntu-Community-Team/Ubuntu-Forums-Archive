---
title: "Trying to install MySQL on Ubuntu 18.04"
date: 2019-09-10
forum: General Help
---

### Post by cscj01 on 2019-09-10
I have Ubuntu 18.04 and am trying to install MySQL 5.7.  I started this yesterday, but something is wrong, and I have no idea.  After an initial install of mysql-server and mysql-workbench, I tried to start mysql-server.  It would not start although I tried several approaches based on some searches.  Then I decided to remove both.  I did with the commands```
sudo apt remove mysql-server and
sudo apt remove mysql-workbench
```I  thought things were okay, so I reinstalled mysql-server.  When I tried to start the server, I got the following:```
sudo systemctl start mysql
Job for mysql.service failed because the control process exited with error code.
See "systemctl status mysql.service" and "journalctl -xe" for details.
```So I ran the first command```
sudo systemctl status mysql.service
&#9679; mysql.service - MySQL Community Server
   Loaded: loaded (/lib/systemd/system/mysql.service; enabled; vendor preset: enabled)
   Active: activating (start) since Mon 2019-09-09 23:26:53 EDT; 57s ago
  Process: 15601 ExecStartPre=/usr/share/mysql/mysql-systemd-start pre (code=exited, status=0/SUCCESS)
 Main PID: 3070 (code=exited, status=0/SUCCESS); Control PID: 15610 (mysqld)
    Tasks: 14 (limit: 4915)
   CGroup: /system.slice/mysql.service
           &#9500;&#9472;15610 /usr/sbin/mysqld --daemonize --pid-file=/run/mysqld/mysqld.pid
           &#9492;&#9472;15612 /usr/sbin/mysqld --daemonize --pid-file=/run/mysqld/mysqld.pid
```Then I ran the second command```
sudo journalctl -xe
-- 
-- Unit mysql.service has finished shutting down.
Sep 09 23:26:53 cp1 systemd[1]: Starting MySQL Community Server...
-- Subject: Unit mysql.service has begun start-up
-- Defined-By: systemd
-- Support: http://www.ubuntu.com/support
-- 
-- Unit mysql.service has begun starting up.
Sep 09 23:26:53 cp1 audit[15608]: AVC apparmor="DENIED" operation="open" profile="/usr/sbin/mysqld" name="/sys/devices/system/node/" pid=15608 comm="mysqld" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Sep 09 23:26:53 cp1 kernel: audit: type=1400 audit(1568086013.571:502): apparmor="DENIED" operation="open" profile="/usr/sbin/mysqld" name="/sys/devices/system/node/" pid=15608 comm="mysqld" requested_mask="r" d
Sep 09 23:26:53 cp1 audit[15610]: AVC apparmor="DENIED" operation="open" profile="/usr/sbin/mysqld" name="/sys/devices/system/node/" pid=15610 comm="mysqld" requested_mask="r" denied_mask="r" fsuid=124 ouid=0
Sep 09 23:26:53 cp1 kernel: audit: type=1400 audit(1568086013.595:503): apparmor="DENIED" operation="open" profile="/usr/sbin/mysqld" name="/sys/devices/system/node/" pid=15610 comm="mysqld" requested_mask="r" d
Sep 09 23:27:51 cp1 sudo[15627]:    butch : TTY=pts/1 ; PWD=/usr/share/mysql-workbench/images ; USER=root ; COMMAND=/bin/systemctl status mysql.service
Sep 09 23:27:51 cp1 sudo[15627]: pam_unix(sudo:session): session opened for user root by (uid=0)
Sep 09 23:27:51 cp1 sudo[15627]: pam_unix(sudo:session): session closed for user root
Sep 09 23:28:34 cp1 mysqld[15610]: Initialization of mysqld failed: 0
Sep 09 23:28:34 cp1 systemd[1]: mysql.service: Control process exited, code=exited status=1
Sep 09 23:28:34 cp1 systemd[1]: mysql.service: Failed with result 'exit-code'.
Sep 09 23:28:34 cp1 systemd[1]: Failed to start MySQL Community Server.
-- Subject: Unit mysql.service has failed
-- Defined-By: systemd
-- Support: http://www.ubuntu.com/support
-- 
-- Unit mysql.service has failed.
-- 
-- The result is RESULT.
Sep 09 23:28:34 cp1 systemd[1]: mysql.service: Service hold-off time over, scheduling restart.
Sep 09 23:28:34 cp1 systemd[1]: mysql.service: Scheduled restart job, restart counter is at 5.
-- Subject: Automatic restarting of a unit has been scheduled
-- Defined-By: systemd
-- Support: http://www.ubuntu.com/support
-- 
-- Automatic restarting of the unit mysql.service has been scheduled, as the result for
-- the configured Restart= setting for the unit.
Sep 09 23:28:34 cp1 systemd[1]: Stopped MySQL Community Server.
-- Subject: Unit mysql.service has finished shutting down
-- Defined-By: systemd
-- Support: http://www.ubuntu.com/support
-- 
-- Unit mysql.service has finished shutting down.
Sep 09 23:28:34 cp1 systemd[1]: Starting MySQL Community Server...
-- Subject: Unit mysql.service has begun start-up
-- Defined-By: systemd
-- Support: http://www.ubuntu.com/support
-- 
-- Unit mysql.service has begun starting up.
Sep 09 23:28:34 cp1 audit[15639]: AVC apparmor="DENIED" operation="open" profile="/usr/sbin/mysqld" name="/sys/devices/system/node/" pid=15639 comm="mysqld" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Sep 09 23:28:34 cp1 kernel: audit: type=1400 audit(1568086114.571:504): apparmor="DENIED" operation="open" profile="/usr/sbin/mysqld" name="/sys/devices/system/node/" pid=15639 comm="mysqld" requested_mask="r" d
Sep 09 23:28:34 cp1 audit[15641]: AVC apparmor="DENIED" operation="open" profile="/usr/sbin/mysqld" name="/sys/devices/system/node/" pid=15641 comm="mysqld" requested_mask="r" denied_mask="r" fsuid=124 ouid=0
Sep 09 23:28:34 cp1 kernel: audit: type=1400 audit(1568086114.595:505): apparmor="DENIED" operation="open" profile="/usr/sbin/mysqld" name="/sys/devices/system/node/" pid=15641 comm="mysqld" requested_mask="r" d
Sep 09 23:29:11 cp1 sudo[15657]:    butch : TTY=pts/1 ; PWD=/usr/share/mysql-workbench/images ; USER=root ; COMMAND=/bin/journalctl -xe
Sep 09 23:29:11 cp1 sudo[15657]: pam_unix(sudo:session): session opened for user root by (uid=0)
```Then I tried to install mysqk-workbench and got the following```
sudo apt install mysql-workbench
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  gdal-data libarmadillo8 libarpack2 libctemplate3 libdap25 libdapclient6v5 libepsilon1 libfreexl1 libfyba0 libgdal20 libgeos-3.6.2 libgeos-c1v5 libgeotiff2 libhdf4-0-alt libkmlbase1 libkmldom1 libkmlengine1
  libnetcdf13 libodbc1 libogdi3.2 libpcrecpp0v5 libproj12 libqhull7 libspatialite7 libsuperlu5 libtinyxml2.6.2v5 liburiparser1 libvsqlitepp3v5 libxerces-c3.2 mysql-utilities mysql-workbench-data odbcinst
  odbcinst1debian2 proj-bin proj-data python-mysql.connector python-paramiko python-pexpect python-ptyprocess python-pyasn1 python-pyodbc python-pysqlite2
Suggested packages:
  geotiff-bin gdal-bin libgeotiff-epsg libhdf4-doc libhdf4-alt-dev hdf4-tools libmyodbc odbc-postgresql tdsodbc unixodbc-bin ogdi-bin python-gssapi python-pexpect-doc python-pysqlite2-doc python-pysqlite2-dbg
The following NEW packages will be installed:
  gdal-data libarmadillo8 libarpack2 libctemplate3 libdap25 libdapclient6v5 libepsilon1 libfreexl1 libfyba0 libgdal20 libgeos-3.6.2 libgeos-c1v5 libgeotiff2 libhdf4-0-alt libkmlbase1 libkmldom1 libkmlengine1
  libnetcdf13 libodbc1 libogdi3.2 libpcrecpp0v5 libproj12 libqhull7 libspatialite7 libsuperlu5 libtinyxml2.6.2v5 liburiparser1 libvsqlitepp3v5 libxerces-c3.2 mysql-utilities mysql-workbench
  mysql-workbench-data odbcinst odbcinst1debian2 proj-bin proj-data python-mysql.connector python-paramiko python-pexpect python-ptyprocess python-pyasn1 python-pyodbc python-pysqlite2
0 upgraded, 43 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0 B/25.9 MB of archives.
After this operation, 159 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
.
. lots of libraries
.
Setting up mysql-server-5.7 (5.7.27-0ubuntu0.18.04.1) ...
/var/lib/mysql/ibdata1:  3401
ERROR: Database files are locked. Daemon already running?
Warning: Unable to start the server. Please restart MySQL and run mysql_upgrade to ensure the database is ready for use.
/var/lib/mysql/ibdata1:  3401
ERROR: Database files are locked. Daemon already running?
Warning: Unable to start the server.
Job for mysql.service failed because the control process exited with error code.
See "systemctl status mysql.service" and "journalctl -xe" for details.
invoke-rc.d: initscript mysql, action "start" failed.
&#9679; mysql.service - MySQL Community Server
   Loaded: loaded (/lib/systemd/system/mysql.service; enabled; vendor preset: enabled)
   Active: activating (auto-restart) (Result: exit-code) since Mon 2019-09-09 23:38:41 EDT; 9ms ago
  Process: 16386 ExecStart=/usr/sbin/mysqld --daemonize --pid-file=/run/mysqld/mysqld.pid (code=exited, status=1/FAILURE)
  Process: 16377 ExecStartPre=/usr/share/mysql/mysql-systemd-start pre (code=exited, status=0/SUCCESS)
 Main PID: 3070 (code=exited, status=0/SUCCESS)
dpkg: error processing package mysql-server-5.7 (--configure):
 installed mysql-server-5.7 package post-installation script subprocess returned error exit status 1
Setting up libhdf4-0-alt (4.2.13-2) ...
Setting up python-mysql.connector (2.1.6-1) ...
Setting up mysql-workbench-data (6.3.8+dfsg-1build3) ...
Setting up libxerces-c3.2:amd64 (3.2.0+debian-2) ...
Setting up liburiparser1:amd64 (0.8.4-1) ...
Setting up proj-data (4.9.3-2) ...
Setting up python-pyodbc (4.0.17-1) ...
Setting up libproj12:amd64 (4.9.3-2) ...
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.7; however:
  Package mysql-server-5.7 is not configured yet.

dpkg: error processing package mysql-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Setting up python-pexpect (4.2.1-1) ...
Setting up libkmlbase1:amd64 (1.3.0-5) ...
Setting up libarmadillo8 (1:8.400.0+dfsg-2) ...
Setting up libogdi3.2 (3.2.0+ds-2) ...
Setting up mysql-utilities (1.6.4-1) ...
Setting up proj-bin (4.9.3-2) ...
Setting up libgeotiff2:amd64 (1.4.2-2build1) ...
Setting up libspatialite7:amd64 (4.3.0a-5build1) ...
Setting up libkmldom1:amd64 (1.3.0-5) ...
Setting up libkmlengine1:amd64 (1.3.0-5) ...
Setting up odbcinst1debian2:amd64 (2.3.4-1.1ubuntu3) ...
Setting up odbcinst (2.3.4-1.1ubuntu3) ...
Setting up libgdal20 (2.2.3+dfsg-2) ...
Setting up mysql-workbench (6.3.8+dfsg-1build3) ...
Processing triggers for man-db (2.8.3-2ubuntu0.1) ...
Processing triggers for shared-mime-info (1.9-2) ...
Processing triggers for gnome-menus (3.13.3-11ubuntu1.1) ...
Processing triggers for hicolor-icon-theme (0.17-2) ...
Processing triggers for mime-support (3.60ubuntu1) ...
Processing triggers for desktop-file-utils (0.23-1ubuntu3.18.04.2) ...
Processing triggers for libc-bin (2.27-3ubuntu1) ...
Errors were encountered while processing:
 mysql-server-5.7
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
```So something has gone badly wong, and I am lost as to how to proceed.

---

### Post by dragonfly41 on 2019-09-10
I would pick out some clues (strings) from your logs and search around ..

[for example]("https://askubuntu.com/questions/909059/cant-reinstall-mysql-mysql-server-depends-on-mysql-server-5-7-however-packag")

---

### Post by SeijiSensei on 2019-09-10
```
Sep 09 23:26:53 cp1 audit[15608]: AVC apparmor="DENIED" operation="open" profile="/usr/sbin/mysqld" name="/sys/devices/system/node/" pid=15608 comm="mysqld" requested_mask="r" denied_mask="r" fsuid=0 ouid=0

```
The version you installed seems incompatible with AppArmor.  Did you run "sudo apt update" before installing?  I'd do that, then run "sudo apt upgrade" before trying to install MySQL.

---

### Post by cscj01 on 2019-09-10
> **dragonfly41 said:**
> I would pick out some clues (strings) from your logs and search around ..

[for example]("https://askubuntu.com/questions/909059/cant-reinstall-mysql-mysql-server-depends-on-mysql-server-5-7-however-packag")

In my latest log, I get this message over and over```
2019-09-10T15:08:45.295044Z 0 [ERROR] InnoDB: Unable to lock ./ibdata1 error: 11
2019-09-10T15:08:45.295094Z 0 [Note] InnoDB: Check that you do not already have another mysqld process using the same InnoDB data or log files.
```I used System monitor to see if there were any mysql processes, and I never found any that I could identify.  At the end I have these:```
2019-09-10T04:08:58.804749Z 0 [ERROR] InnoDB: Operating system error number 11 in a file operation.
2019-09-10T04:08:58.804765Z 0 [ERROR] InnoDB: Error number 11 means 'Resource temporarily unavailable'
2019-09-10T04:08:58.804775Z 0 [Note] InnoDB: Some operating system error numbers are described at http://dev.mysql.com/doc/refman/5.7/en/operating-system-error-codes.html
2019-09-10T04:08:58.804785Z 0 [ERROR] InnoDB: Cannot open datafile './ibdata1'
2019-09-10T04:08:58.804813Z 0 [ERROR] InnoDB: Could not open or create the system tablespace. If you tried to add new data files to the system tablespace, and it failed here, you should now edit innodb_data_file_path in my.cnf back to what it was, and remove the new ibdata files InnoDB created in this failed attempt. InnoDB only wrote those files full of zeros, but did not yet use them in any way. But be careful: do not remove old data files which contain your precious data!
2019-09-10T04:08:58.804825Z 0 [ERROR] InnoDB: Plugin initialization aborted with error Cannot open a file
2019-09-10T04:08:59.405286Z 0 [ERROR] Plugin 'InnoDB' init function returned error.
2019-09-10T04:08:59.405329Z 0 [ERROR] Plugin 'InnoDB' registration as a STORAGE ENGINE failed.
2019-09-10T04:08:59.405342Z 0 [ERROR] Failed to initialize builtin plugins.
2019-09-10T04:08:59.405349Z 0 [ERROR] Aborting

2019-09-10T04:08:59.405376Z 0 [Note] Binlog end
2019-09-10T04:08:59.405432Z 0 [Note] Shutting down plugin 'CSV'
2019-09-10T04:08:59.405924Z 0 [Note] /usr/sbin/mysqld: Shutdown complete
``` I have no idea why /ibdata1 is unavailable.  The my.cnf is what came with the system.  I have not gotten to the point that I could modify it.  From the system log I have this:```
Sep 10 11:15:43 cp1 systemd[1]: Starting MySQL Community Server...
Sep 10 11:15:43 cp1 kernel: [65430.041413] audit: type=1400 audit(1568128543.571:1347): apparmor="DENIED" operation="open" profile="/usr/sbin/mysqld" name="/sys/devices/system/node/" pid=29388 comm="mysqld" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Sep 10 11:15:43 cp1 kernel: [65430.063902] audit: type=1400 audit(1568128543.591:1348): apparmor="DENIED" operation="open" profile="/usr/sbin/mysqld" name="/sys/devices/system/node/" pid=29390 comm="mysqld" requested_mask="r" denied_mask="r" fsuid=124 ouid=0
Sep 10 11:17:01 cp1 CRON[29408]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep 10 11:17:24 cp1 mysqld[29390]: Initialization of mysqld failed: 0
Sep 10 11:17:24 cp1 systemd[1]: mysql.service: Control process exited, code=exited status=1
Sep 10 11:17:24 cp1 systemd[1]: mysql.service: Failed with result 'exit-code'.
Sep 10 11:17:24 cp1 systemd[1]: Failed to start MySQL Community Server.
Sep 10 11:17:24 cp1 systemd[1]: mysql.service: Service hold-off time over, scheduling restart.
Sep 10 11:17:24 cp1 systemd[1]: mysql.service: Scheduled restart job, restart counter is at 416.
Sep 10 11:17:24 cp1 systemd[1]: Stopped MySQL Community Server.
Sep 10 11:17:24 cp1 systemd[1]: Starting MySQL Community Server...
Sep 10 11:17:24 cp1 kernel: [65531.040576] audit: type=1400 audit(1568128644.572:1349): apparmor="DENIED" operation="open" profile="/usr/sbin/mysqld" name="/sys/devices/system/node/" pid=29421 comm="mysqld" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Sep 10 11:17:24 cp1 kernel: [65531.066129] audit: type=1400 audit(1568128644.596:1350): apparmor="DENIED" operation="open" profile="/usr/sbin/mysqld" name="/sys/devices/system/node/" pid=29423 comm="mysqld" requested_mask="r" denied_mask="r" fsuid=124 ouid=0
```So I am still lost.

---

### Post by dragonfly41 on 2019-09-10
I can only suggest continuing with the google search approach .. 

I ran this google search using the clues gleaned so far ,,

```
Ubuntu NEAR MySql NEAR apparmor
```

and here is just one hit ..

[https://serverfault.com/questions/896653/how-do-i-get-the-right-apparmor-profile-for-mysql-on-ubuntu](https://serverfault.com/questions/896653/how-do-i-get-the-right-apparmor-profile-for-mysql-on-ubuntu)

---

### Post by cscj01 on 2019-09-10
Okay, it seems I had somehow gotten some parts of mysql that were not getting removed whenever I tried to remove it.  I finally found two commands that cleaned everything out and was able to reinstall successfully.  here are the two commands:```
sudo apt-get purge mysql-common mysql-server-core-5.7 mysql-client-core-5.7
sudo rm -rf /etc/mysql (all config files)
```So, I'll mark this thread as solved.

---

