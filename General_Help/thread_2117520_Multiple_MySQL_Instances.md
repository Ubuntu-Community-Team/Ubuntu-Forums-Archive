---
title: "Multiple MySQL Instances"
date: 2013-02-18
forum: General Help
---

### Post by Kissell on 2013-02-18
I want to run two versions of mysql on the same Ubuntu machine.

I've never tried this before.

I was trying to follow a tutorial, and it didn't work for me.

First, I edited apparmor to allow the new database locations:
vi /etc/apparmor.d/usr.sbin.mysqld
>   /var/lib/mysql1/ r,
  /var/lib/mysql1/** rwk,
  /var/log/mysql1/ r,
  /var/log/mysql1/* rw,
  /var/run/mysqld/mysqld1.pid w,
  /var/run/mysqld/mysqld1.sock w,

  /var/lib/mysql2/ r,
  /var/lib/mysql2/** rwk,
  /var/log/mysql2/ r,
  /var/log/mysql2/* rw,
  /var/run/mysqld/mysqld2.pid w,
  /var/run/mysqld/mysqld2.sock w,


Then restarted apparmor "service apparmor restart"

Then I edited /etc/mysql/my.cnf to add the following above the [mysqld] section:
> # mysqld_multi test, instance 1
[mysqld1]
server-id=10001
socket=/var/run/mysqld/mysqld1.sock
port=23306
pid-file=/var/run/mysqld/mysqld1.pid
datadir=/var/lib/mysql1
log_bin=/var/log/mysql1/mysql1-bin.log

# mysqld_multi test, instance 2
[mysqld2]
server-id=10002
socket=/var/run/mysqld/mysqld2.sock
port=33306
pid-file=/var/run/mysqld/mysqld2.pid
datadir=/var/lib/mysql2
log_bin=/var/log/mysql2/mysql2-bin.log


Then I ran DB install commands for the two new databases:
> 
sudo mysql_install_db --user=mysql --datadir=/var/lib/mysql1
sudo mysql_install_db --user=mysql --datadir=/var/lib/mysql2


But "sudo mysqld_multi report" shows:
> 
Reporting MySQL servers
MySQL server from group: mysqld1 is not running
MySQL server from group: mysqld2 is not running


I try to start mysqld1 with: "sudo mysqld_multi start 1" but it continues to report as "not running"

---

