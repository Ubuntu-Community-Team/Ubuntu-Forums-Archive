---
title: "MYSQL server after upgrade to 16.04"
date: 2016-08-28
forum: General Help
---

### Post by jmcgee on 2016-08-28
I did upgrade to 16.04 from 14.04.

This is a MythTV Backend, but the problem is MYSQL.

MYSQL is not running.

I ran:
mythuser@amethi:~$ sudo apt-get install -f 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libterm-readkey-perl mariadb-common
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  mysql-server-5.7
Suggested packages:
  mailx tinyca
The following NEW packages will be installed:
  mysql-server-5.7
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
5 not fully installed or removed.
Need to get 0 B/2,722 kB of archives.
After this operation, 48.4 MB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Preconfiguring packages ...
(Reading database ... 656713 files and directories currently installed.)
Preparing to unpack .../mysql-server-5.7_5.7.13-0ubuntu0.16.04.2_amd64.deb ...
Aborting downgrade from (at least) 10.0 to 5.7.
If are sure you want to downgrade to 5.7, remove the file
/var/lib/mysql/debian-*.flag and try installing again.
dpkg: error processing archive /var/cache/apt/archives/mysql-server-5.7_5.7.13-0ubuntu0.16.04.2_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/mysql-server-5.7_5.7.13-0ubuntu0.16.04.2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


What to try next?
thanks.

---

### Post by SeijiSensei on 2016-08-28
Are there any files that match "/var/lib/mysql/debian-*.flag"?  If so, try deleting them with "sudo rm /var/lib/mysql/debian-*.flag", then run "sudo apt-get install -f" and see if you get any further.

You can also remove the server entirely with
```
sudo apt-get remove --purge mysql-server
```
but make a dump of all the databases first with
```
sudo mysqldump --all-databases > /path/to/some/backup/mysql.dump
```
just to be sure.

---

### Post by jmcgee on 2016-08-28
mythuser@amethi:~$ sudo ls /var/lib/mysql/debian-*.flag
[sudo] password for mythuser: 
ls: cannot access '/var/lib/mysql/debian-*.flag': No such file or directory
mythuser@amethi:~$ sudo apt-get remove --purge mysql-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  mysql-server*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 164 kB disk space will be freed.
Do you want to continue? [Y/n] Y
dpkg: mysql-server: dependency problems, but removing anyway as you requested:
 mythtv-backend-master depends on mysql-server | virtual-mysql-server | mysql-server-5.7 | mysql-server-5.6 | mariadb-server; however:
  Package mysql-server is to be removed.
  Package virtual-mysql-server is not installed.
  Package mysql-server-5.7 which provides virtual-mysql-server is not configured yet.
  Package mysql-server-5.5 which provides virtual-mysql-server is not installed.
  Package mariadb-server-10.0 which provides virtual-mysql-server is not installed.
  Package mysql-server-5.7 is not configured yet.
  Package mysql-server-5.6 is not installed.
  Package mariadb-server is not installed.

(Reading database ... 656778 files and directories currently installed.)
Removing mysql-server (5.7.13-0ubuntu0.16.04.2) ...
Setting up mysql-server-5.7 (5.7.13-0ubuntu0.16.04.2) ...
Renaming removed key_buffer and myisam-recover options (if present)
ERROR: Unable to start MySQL server:
2016-08-28T21:15:54.056414Z 0 [ERROR] unknown variable 'table_cache=128'
2016-08-28T21:15:54.058636Z 0 [ERROR] Aborting
Please take a look at [https://wiki.debian.org/Teams/MySQL/FAQ](https://wiki.debian.org/Teams/MySQL/FAQ) for tips on fixing common upgrade issues.
Once the problem is resolved, run apt-get --fix-broken install to retry.
dpkg: error processing package mysql-server-5.7 (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 mysql-server-5.7
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by SeijiSensei on 2016-08-28
> 
2016-08-28T21:15:54.056414Z 0 [ERROR] unknown variable 'table_cache=128'
2016-08-28T21:15:54.058636Z 0 [ERROR] Aborting
Please take a look at [https://wiki.debian.org/Teams/MySQL/FAQ](https://wiki.debian.org/Teams/MySQL/FAQ) for tips on fixing common upgrade issues.
Once the problem is resolved, run apt-get --fix-broken install to retry.

Did you do that?

Also it could be a bug based on [this change](http://dba.stackexchange.com/questions/104025/mysql-unknown-variable-table-cache-64)
> Version 5.1.3 "Renamed the table_cache system variable to table_open_cache. Any scripts that refer to table_cache should be updated to use the new name." However, it did not become an error until years later, in 5.7.6. Change to table_open_cache.
In my version running on 14.04, the "table_cache" directive is disabled entirely.  See what your my.cnf has.  If there is a "table_cache" directive, try changing it to "table_open_cache", then try to start mysqld.

---

### Post by jmcgee on 2016-08-28
That did get me further, but is now stopping at the 1524 error.

mythuser@amethi:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up mysql-server-5.7 (5.7.13-0ubuntu0.16.04.2) ...
Renaming removed key_buffer and myisam-recover options (if present)
insserv: warning: script 'K02vncserver' missing LSB tags and overrides
insserv: warning: script 'vncserver.nogood' missing LSB tags and overrides
insserv: warning: script 'vncserver' missing LSB tags and overrides
mysql_upgrade: Got error: 1524: Plugin 'unix_socket' is not loaded while connecting to the MySQL server
Upgrade process encountered error and will not continue.
mysql_upgrade failed with exit status 11
dpkg: error processing package mysql-server-5.7 (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 mysql-server-5.7
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by SeijiSensei on 2016-08-31
As always, my first step is to search for the error text on Google.  That led me to this: [http://askubuntu.com/questions/705458/ubuntu-15-10-mysql-error-1524-unix-socket](http://askubuntu.com/questions/705458/ubuntu-15-10-mysql-error-1524-unix-socket).

Since 15.10 was the predecessor to 16.04, I'd bet the solution is the same.

---

