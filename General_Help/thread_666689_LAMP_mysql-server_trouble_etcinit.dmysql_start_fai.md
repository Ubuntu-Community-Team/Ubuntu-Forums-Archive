---
title: "LAMP mysql-server trouble /etc/init.d/mysql start fails"
date: 2008-01-13
forum: General Help
---

### Post by LinuxNoob#1 on 2008-01-13
Hello, this is my first post I browsed the similar ones I couldn't find an exact answer so here goes.

Yesturday I struggled through the installation of my first LAMP server...(wow-I though just getting gutsy gibbon to work was hard)  I basically set everything up i though I started working on some stuff.  was able to run my cgi scripts access the mysql server database with the scripts and enter new rows into my tables....

Today I am trying to continue my work at WTF- 

Error
#2002 - The server is not responding (or the local MySQL server's socket is not correctly configured)

I am not quite sure why this could be since it was working perfectly yesturday.  I went to my console and typed in sudo /etc/init.d/mysql restart

the stop passed but the start failed....

any suggestions?

---

### Post by mccorkle on 2008-01-14
It depends.  I've seen all sorts of weirdness with mysql (though I use it in every case I can).  

First thing to check is file system.  Run a `df -h` and make sure you don't have any full disks.  Then check the files that mysql would need to read and write to and make sure they are set to the same permissions (do an `ls -al /var/lib/mysql` and look at the 3rd and 4th columns -- they should read mysql and mysql respectively).  I've spent hours reading through the mysql startup scripts and attempting to launch mysql in debug mode to only finally discover that mysql couldn't read/write to its own files because they got chmodded or were on a disk that was full.

If that doesn't fix your issue, let me know and I'll have you check some other things.

---

### Post by LinuxNoob#1 on 2008-01-14
[COLOR="Red"]`df -h` [/COLOR]

pbrack@ubuntulamp:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             5.8G  3.1G  2.5G  56% /
varrun                503M   92K  503M   1% /var/run
varlock               503M     0  503M   0% /var/lock
udev                  503M   72K  503M   1% /dev
devshm                503M     0  503M   0% /dev/shm
/dev/sda1             118G   64G   55G  54% /media/sda1
/dev/sda3             5.8G  2.6G  2.9G  48% /media/sda3
/dev/sda5              39G  699M   36G   2% /media/sda5
/dev/sda6              21G   65M   21G   1% /media/sda6


[COLOR="Red"] `ls -al /var/lib/mysql`[/COLOR]

pbrack@ubuntulamp:~$ ls -al /var/lib/mysql
total 20540
drwxr-xr-x  5 mysql mysql     4096 2008-01-14 07:30 .
drwxr-xr-x 49 root  root      4096 2008-01-13 15:00 ..
-rw-r--r--  1 root  root         0 2008-01-12 10:22 debian-5.0.flag
-rw-rw----  1 mysql mysql 10485760 2008-01-14 07:30 ibdata1
-rw-rw----  1 mysql mysql  5242880 2008-01-14 07:30 ib_logfile0
-rw-rw----  1 mysql mysql  5242880 2008-01-12 10:22 ib_logfile1
drwxr-xr-x  2 mysql root      4096 2008-01-12 10:22 mysql
drwx------  2 mysql mysql     4096 2008-01-12 10:46 rockets
drwx------  2 mysql mysql     4096 2008-01-12 16:00 test
pbrack@ubuntulamp:~$ 


these are the results of both of those commands.  It appears that I have sufficient disk space but there are couple in that second command which say are set to root.  

what should I try?

---

### Post by mccorkle on 2008-01-14
My first suggestion would be to make sure all of /var/lib/mysql is owned by mysql.mysql:

sudo chown -R mysql.mysql /var/lib/mysql/

After that, restart mysql and look at syslog (I guess 7.10 spits all of mysql's errors/output into the main syslog) and let me know what the last 10 or so mysql lines in there are if this doesn't fix it for you.

---

### Post by LinuxNoob#1 on 2008-01-14
[COLOR="Red"]sudo chown -R mysql.mysql /var/lib/mysql/[/COLOR]

ran this, then ran

sudo /etc/init.d/mysql restart    it failed


[COLOR="Red"]gedit /var/log/syslog[/COLOR]

Jan 14 07:57:31 ubuntulamp mysqld[6126]: 080114  7:57:31  InnoDB: Starting shutdown...
Jan 14 07:57:34 ubuntulamp mysqld[6126]: 080114  7:57:34  InnoDB: Shutdown completed; log sequence number 0 43655
Jan 14 07:57:34 ubuntulamp mysqld[6126]: 080114  7:57:34 [Note] /usr/sbin/mysqld: Shutdown complete
Jan 14 07:57:34 ubuntulamp mysqld[6126]: 
Jan 14 07:57:34 ubuntulamp mysqld_safe[6153]: ended
Jan 14 07:57:46 ubuntulamp /etc/init.d/mysql[6270]: 0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' resulted in
Jan 14 07:57:46 ubuntulamp /etc/init.d/mysql[6270]: ^G/usr/bin/mysqladmin: connect to server at 'localhost' failed
Jan 14 07:57:46 ubuntulamp /etc/init.d/mysql[6270]: error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Jan 14 07:57:46 ubuntulamp /etc/init.d/mysql[6270]: Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
Jan 14 07:57:46 ubuntulamp /etc/init.d/mysql[6270]: 

are the results

I guess the obvious question is how one does  "Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!"

I ran a  'cd /var/run/mysqld/ and there appeared to be nothing in there 
ls-a gave .... 

I don't know how to check if that thing is running

suggestions?

---

### Post by mccorkle on 2008-01-14
the following will show you where your mysql.pid and mysql.sock should be: 
`ls -al /var/run/mysqld/` 

They will only be in there if mysql is running though.  Let me know the output of the ls.  

Also, can you post your /etc/mysql/my.cnf?

---

### Post by LinuxNoob#1 on 2008-01-14
Cheers mate,
    I really think we are making progress here. Really nice of you to help out a guy who is trying to learn.  After this is done would you mind giving my advice on learning all of these commands and such, because I only know a little.   :(

[SIZE="5"]ls -al /var/run/mysqld/[/SIZE]
pbrack@ubuntulamp:/var/run/mysqld$ ls -al /var/run/mysqld/
total 0
drwxr-xr-x  2 mysql root  40 2008-01-14 07:30 .
drwxr-xr-x 15 root  root 620 2008-01-14 07:57 ..
pbrack@ubuntulamp:/var/run/mysqld$ 


[SIZE="5"]/etc/mysql/my.cnf[/SIZE]
[SIZE="1"]#
# The MySQL database server configuration file.
#
# You can copy this to one of:
# - "/etc/mysql/my.cnf" to set global options,
# - "~/.my.cnf" to set user-specific options.
# 
# One can use all long options that the program supports.
# Run program with --help to get a list of available options and with
# --print-defaults to see which it would actually understand and use.
#
# For explanations see
# [http://dev.mysql.com/doc/mysql/en/server-system-variables.html](http://dev.mysql.com/doc/mysql/en/server-system-variables.html)

# This will be passed to all mysql clients
# It has been reported that passwords should be enclosed with ticks/quotes
# escpecially if they contain "#" chars...
# Remember to edit /etc/mysql/debian.cnf when changing the socket location.
[client]
port		= 3306
socket		= /var/run/mysqld/mysqld.sock

# Here is entries for some specific programs
# The following values assume you have at least 32M ram

# This was formally known as [safe_mysqld]. Both versions are currently parsed.
[mysqld_safe]
socket		= /var/run/mysqld/mysqld.sock
nice		= 0

[mysqld]
#
# * Basic Settings
#
user		= mysql
pid-file	= /var/run/mysqld/mysqld.pid
socket		= /var/run/mysqld/mysqld.sock
port		= 3306
basedir		= /usr
datadir		= /var/lib/mysql
tmpdir		= /tmp
language	= /usr/share/mysql/english
skip-external-locking
#
# Instead of skip-networking the default is now to listen only on
# localhost which is more compatible and is not less secure.
bind-address		= 24.24.240.43
#
# * Fine Tuning
#
key_buffer		= 16M
max_allowed_packet	= 16M
thread_stack		= 128K
thread_cache_size	= 8
#max_connections        = 100
#table_cache            = 64
#thread_concurrency     = 10
#
# * Query Cache Configuration
#
query_cache_limit       = 1M
query_cache_size        = 16M
#
# * Logging and Replication
#
# Both location gets rotated by the cronjob.
# Be aware that this log type is a performance killer.
#log		= /var/log/mysql/mysql.log
#
# Error logging goes to syslog. This is a Debian improvement :)
#
# Here you can see queries with especially long duration
#log_slow_queries	= /var/log/mysql/mysql-slow.log
#long_query_time = 2
#log-queries-not-using-indexes
#
# The following can be used as easy to replay backup logs or for replication.
# note: if you are setting up a replication slave, see README.Debian about
#       other settings you may need to change.
#server-id		= 1
log_bin			= /var/log/mysql/mysql-bin.log
# WARNING: Using expire_logs_days without bin_log crashes the server! See README.Debian!
expire_logs_days	= 10
max_binlog_size         = 100M
#binlog_do_db		= include_database_name
#binlog_ignore_db	= include_database_name
#
# * BerkeleyDB
#
# Using BerkeleyDB is now discouraged as its support will cease in 5.1.12.
skip-bdb
#
# * InnoDB
#
# InnoDB is enabled by default with a 10MB datafile in /var/lib/mysql/.
# Read the manual for more InnoDB related options. There are many!
# You might want to disable InnoDB to shrink the mysqld process by circa 100MB.
#skip-innodb
#
# * Security Features
#
# Read the manual, too, if you want chroot!
# chroot = /var/lib/mysql/
#
# For generating SSL certificates I recommend the OpenSSL GUI "tinyca".
#
# ssl-ca=/etc/mysql/cacert.pem
# ssl-cert=/etc/mysql/server-cert.pem
# ssl-key=/etc/mysql/server-key.pem



[mysqldump]
quick
quote-names
max_allowed_packet	= 16M

[mysql]
#no-auto-rehash	# faster start of mysql but no tab completition

[isamchk]
key_buffer		= 16M

#
# * NDB Cluster
#
# See /usr/share/doc/mysql-server-*/README.Debian for more information.
#
# The following configuration is read by the NDB Data Nodes (ndbd processes)
# not from the NDB Management Nodes (ndb_mgmd processes).
#
# [MYSQL_CLUSTER]
# ndb-connectstring=127.0.0.1


#
# * IMPORTANT: Additional settings that can override those from this file!
#
!includedir /etc/mysql/conf.d/
[/SIZE]

---

### Post by mccorkle on 2008-01-14
hmmm, does your box still have the ip of 24.24.240.43?  

run `ifconfig` and check the output.

::Mark

---

### Post by LinuxNoob#1 on 2008-01-14
[COLOR="Red"]ifconfig[/COLOR]


pbrack@ubuntulamp:/var/run/mysqld$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:F2:06:B1:33  
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::215:f2ff:fe06:b133/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8800 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6428 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5084878 (4.8 MB)  TX bytes:1222131 (1.1 MB)
          Interrupt:23 Base address:0xe000 

eth1      Link encap:Ethernet  HWaddr 00:15:F2:06:C7:5D  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

pbrack@ubuntulamp:/var/run/mysqld$ 
pbrack@ubuntulamp:/var/run/mysqld$

---

### Post by LinuxNoob#1 on 2008-01-14
I believe when i initially set up the LAMP I used eth0.

---

### Post by mccorkle on 2008-01-14
Ok, I had this long beautiful explanation as to why it was broken, then I lost network connectivity and never posted it.  Here's the short version.

You've got your my.cnf attempting to bind your mysql to that 24.24.240.43 IP.  Your linux box doesn't have that IP right now.  So you can do one of two things:
1) change the IP in my.cnf to 127.0.0.1 (the best option, security wise)
2) get your linux box set up with the static IP of 24.24.240.43.

I'd recommend you look into the security of mysql listening on a public IP before you take the second option though.  

::Mark McCorkle

---

### Post by LinuxNoob#1 on 2008-01-14
You are LEGEND mccorkle,  
That did the trick.
Now I am off to continue the cause.  

Thanks a load I hope this thread will help others.

:)

---

### Post by cong06 on 2008-05-10
apparently I just got the same problem (up to the my.cnf problem) as LinuxNoob#1.

1) */etc/init.d/mysql start* fails
2) permissions are set properly on */var/lib/mysql/*
```
me@comp:/var/lib/mysql$ ls -al
total 20532
drwxr-xr-x  2 mysql mysql     4096 2008-05-10 01:21 .
drwxr-xr-x 55 root  root      4096 2008-05-08 20:00 ..
-rw-r--r--  1 mysql mysql        0 2008-05-08 20:00 debian-5.0.flag
-rw-rw----  1 mysql mysql 10485760 2008-05-08 22:11 ibdata1
-rw-rw----  1 mysql mysql  5242880 2008-05-10 01:21 ib_logfile0
-rw-rw----  1 mysql mysql  5242880 2008-05-08 19:34 ib_logfile1
-rw-------  1 mysql mysql        7 2008-05-08 19:34 mysql_upgrade_info
```

3) I unmounted drives (just to be sure that all drives were less then 85%)
And here are my */var/log/syslog* right after running *sudo /etc/init.d/mysql*
```
May 10 01:21:11 comp mysqld_safe[19713]: started
May 10 01:21:11 comp mysqld[19717]: 080510  1:21:11  InnoDB: Started; log sequence number 0 43665
May 10 01:21:11 comp mysqld[19717]: 080510  1:21:11 [ERROR] Fatal error: Can't open and lock privilege tables: Table 'mysql.host' doesn't exist
May 10 01:21:11 comp mysqld_safe[19729]: ended
May 10 01:21:26 comp /etc/init.d/mysql[19888]: 0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' resulted in
May 10 01:21:26 comp /etc/init.d/mysql[19888]: ^G/usr/bin/mysqladmin: connect to server at 'localhost' failed
May 10 01:21:26 comp /etc/init.d/mysql[19888]: error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
May 10 01:21:26 comp /etc/init.d/mysql[19888]: Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
May 10 01:21:26 comp /etc/init.d/mysql[19888]: 
```

and my /etc/mysql/my.cnf```

#
# The MySQL database server configuration file.
#
# You can copy this to one of:
# - "/etc/mysql/my.cnf" to set global options,
# - "~/.my.cnf" to set user-specific options.
# 
# One can use all long options that the program supports.
# Run program with --help to get a list of available options and with
# --print-defaults to see which it would actually understand and use.
#
# For explanations see
# http://dev.mysql.com/doc/mysql/en/server-system-variables.html

# This will be passed to all mysql clients
# It has been reported that passwords should be enclosed with ticks/quotes
# escpecially if they contain "#" chars...
# Remember to edit /etc/mysql/debian.cnf when changing the socket location.
[client]
port		= 3306
socket		= /var/run/mysqld/mysqld.sock

# Here is entries for some specific programs
# The following values assume you have at least 32M ram

# This was formally known as [safe_mysqld]. Both versions are currently parsed.
[mysqld_safe]
socket		= /var/run/mysqld/mysqld.sock
nice		= 0

[mysqld]
#
# * Basic Settings
#

#
# * IMPORTANT
#   If you make changes to these settings and your system uses apparmor, you may
#   also need to also adjust /etc/apparmor.d/usr.sbin.mysqld.
#

user		= mysql
pid-file	= /var/run/mysqld/mysqld.pid
socket		= /var/run/mysqld/mysqld.sock
port		= 3306
basedir		= /usr
datadir		= /var/lib/mysql
tmpdir		= /tmp
language	= /usr/share/mysql/english
skip-external-locking
#
# Instead of skip-networking the default is now to listen only on
# localhost which is more compatible and is not less secure.
bind-address		= 127.0.0.1
#
# * Fine Tuning
#
key_buffer		= 16M
max_allowed_packet	= 16M
thread_stack		= 128K
thread_cache_size	= 8
#max_connections        = 100
#table_cache            = 64
#thread_concurrency     = 10
#
# * Query Cache Configuration
#
query_cache_limit       = 1M
query_cache_size        = 16M
#
# * Logging and Replication
#
# Both location gets rotated by the cronjob.
# Be aware that this log type is a performance killer.
#log		= /var/log/mysql/mysql.log
#
# Error logging goes to syslog. This is a Debian improvement :)
#
# Here you can see queries with especially long duration
#log_slow_queries	= /var/log/mysql/mysql-slow.log
#long_query_time = 2
#log-queries-not-using-indexes
#
# The following can be used as easy to replay backup logs or for replication.
# note: if you are setting up a replication slave, see README.Debian about
#       other settings you may need to change.
#server-id		= 1
#log_bin			= /var/log/mysql/mysql-bin.log
expire_logs_days	= 10
max_binlog_size         = 100M
#binlog_do_db		= include_database_name
#binlog_ignore_db	= include_database_name
#
# * BerkeleyDB
#
# Using BerkeleyDB is now discouraged as its support will cease in 5.1.12.
skip-bdb
#
# * InnoDB
#
# InnoDB is enabled by default with a 10MB datafile in /var/lib/mysql/.
# Read the manual for more InnoDB related options. There are many!
# You might want to disable InnoDB to shrink the mysqld process by circa 100MB.
#skip-innodb
#
# * Security Features
#
# Read the manual, too, if you want chroot!
# chroot = /var/lib/mysql/
#
# For generating SSL certificates I recommend the OpenSSL GUI "tinyca".
#
# ssl-ca=/etc/mysql/cacert.pem
# ssl-cert=/etc/mysql/server-cert.pem
# ssl-key=/etc/mysql/server-key.pem



[mysqldump]
quick
quote-names
max_allowed_packet	= 16M

[mysql]
#no-auto-rehash	# faster start of mysql but no tab completition

[isamchk]
key_buffer		= 16M

#
# * NDB Cluster
#
# See /usr/share/doc/mysql-server-*/README.Debian for more information.
#
# The following configuration is read by the NDB Data Nodes (ndbd processes)
# not from the NDB Management Nodes (ndb_mgmd processes).
#
# [MYSQL_CLUSTER]
# ndb-connectstring=127.0.0.1


#
# * IMPORTANT: Additional settings that can override those from this file!
# The files must end with '.cnf', otherwise they'll be ignored.
#
!includedir /etc/mysql/conf.d/
```

LinuxNoob#1 had a problem cause he had bind-on-address at the wrong address...mine is from 127.0.0.1 though...

---

### Post by cong06 on 2008-05-11
reinstall....

:oops:

---

