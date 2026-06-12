---
title: "slow mysqlcheck"
date: 2008-04-18
forum: General Help
---

### Post by idoerg on 2008-04-18
Hi,

I recently upgraded from 7.04 to 7.10 (yeah, yeah, I know 8,04 is coming out in a week). mysqld recognized a few old tables and decided to run mysql_upgrade on them, using mysqlcheck. Trouble is, it's taking a long time, and it is practically disabled my computer, hogging CPU and memory. The database contains some very large tables, and large indexes. But even with relatively small ones,  it took 8 hours to check this one:

```
-rw-rw---- 1 mysql mysql 8.4K 2008-04-18 19:19 prot_hmm.frm
-rw-rw---- 1 mysql mysql  33M 2008-04-18 19:21 prot_hmm.MYI
-rw-rw---- 1 mysql mysql  99M 2008-04-18 19:21 prot_hmm.MYD

```
my mysql processes (I distorted the password):
```
% ps -elf | grep mysql
0 S root      7411     1  0  85   0 -   438 wait   Apr17 ?        00:00:00 /bin/sh /usr/bin/mysqld_safe
4 S mysql     7448  7411  4  75   0 - 32022 -      Apr17 ?        01:02:45 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --pid-file=/var/run/mysqld/mysqld.pid --skip-external-locking --port=3306 --socket=/var/run/mysqld/mysqld.sock
0 S root      7449  7411  0  85   0 -   724 pipe_w Apr17 ?        00:00:00 logger -p daemon.err -t mysqld_safe -i -t mysqld
1 S root      7484     1  0  85   0 -   960 wait   Apr17 ?        00:00:00 /bin/bash /etc/mysql/debian-start
4 S root      7490  7484  0  85   0 -  1074 pipe_w Apr17 ?        00:00:00 /usr/bin/mysql_upgrade --defaults-extra-file=/etc/mysql/debian.cnf
0 S root      7493  7484  0  85   0 -   723 pipe_w Apr17 ?        00:00:00 logger -p daemon.warn -i -t/etc/mysql/debian-start
0 S root      7499  7490  0  85   0 -   439 wait   Apr17 ?        00:00:00 sh -c '/usr/bin/mysqlcheck' '--port=3306' '--socket=/var/run/mysqld/mysqld.sock' '--host=localhost' '--user=debian-sys-maint' '--password=HaXSgobbledygookmWC' '--socket=/var/run/mysqld/mysqld.sock' '--user=debian-sys-maint' '--password=zHablavlablan2mWC' '--socket=/var/run/mysqld/mysqld.sock' '--user=debian-sys-maint'  '--check-upgrade' '--all-databases' '--auto-repair'
0 S root      7500  7499  0  75   0 -  1105 -      Apr17 ?        00:00:00 /usr/bin/mysqlcheck --port=3306 --socket=/var/run/mysqld/mysqld.sock --host=localhost --user=debian-sys-maint --password=x xxxxxxxxxxxxxx --socket=/var/run/mysqld/mysqld.sock --user=debian-sys-maint --password=x xxxxxxxxxxxxxx --socket=/var/run/mysqld/mysqld.sock --user=debian-sys-maint --check-upgrade --all-databases --auto-repair
0 R idoerg   13110 13093  0  78   0 -   743 -      19:34 pts/1    00:00:00 grep mysql
```


Is this normal? I have an 11G table, I'm not sure what will happen when mysqlcheck reaches that one. I guess I need to upgrade the tables, but does it have to take so long and hog my resources so badly?

---

