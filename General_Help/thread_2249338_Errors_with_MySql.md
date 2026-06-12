---
title: "Errors with MySql"
date: 2014-10-21
forum: General Help
---

### Post by Alberto_Giacalone on 2014-10-21
Hi. I have 2 errors on my mysql server.

When i try to enter to the server it gives me the error:
[FAIL] /etc/init.d/mysql: ERROR: The partition with /var/lib/mysql is too full! ... failed!

But i read a lot on internet and i tried to do a mysqldump, but when i try to restart the server:

mysqldump: Got error: 2002: Can't connect to local MySQL server through socket '/var/lib/mysql/mysql.sock' (2) when trying to connect

So i can't connect to the server to do a dump and services cannot too.
Thanks and sorry for my english i hope you understand what i wrote.

---

### Post by Alberto_Giacalone on 2014-10-21
Noone?

---

### Post by steeldriver on 2014-10-21
So have you tried deleting some files on /var to make enough space so that the mysql server can start? for example old log files

---

### Post by Alberto_Giacalone on 2014-10-21
I deleted only a database thinking it was the 16GB of the memory in the server, than i noticed the folder was ibdata1.

---

### Post by SeijiSensei on 2014-10-21
Is /var mounted on a separate partition, or is the entire filesystem on one partition?  What do you see if you run "df" from the command prompt?

Since MySQL cannot start because you are out of space, you cannot use mysqldump since it needs to connect to a running server.  Just delete some of the junk on your machine.  Beyond stuff in your home directory, I'd start with /var/log.

---

### Post by Alberto_Giacalone on 2014-10-21
> File system    1K-blocchi    Usati Disponib. Uso% Montato su
rootfs           20026236 19071496         0 100% /
/dev/root        20026236 19071496         0 100% /
devtmpfs         16419700        0  16419700   0% /dev
tmpfs             3284032      308   3283724   1% /run
tmpfs                5120        0      5120   0% /run/lock
tmpfs             6672700        4   6672696   1% /dev/shm
/dev/sda2        93576128 19450104  69349528  22% /home


But if i do "du":
> 612K	./BanManagement20K	./coins
144K	./wordpress
8,0K	./Auth**
176K	./phpmyadmin
1,1M	./mysql
20K	./warlock
15G	.

---

### Post by nerdtron on 2014-10-21
```
File system    1K-blocchi    Usati Disponib. Uso% Montato su
rootfs           20026236 19071496         0 100% /

```

Your / partition is full. You need to delete data. probably in /var/lib/ location
To see each folder usage on /var/lib
```

cd /var/lib/
du -sch *

```

---

### Post by SeijiSensei on 2014-10-21
I'd stay away from /var/lib myself.  There are too many ways that can go wrong.  As I said before, I'd start with /var/log.  

20 GB is pretty small for an entire root filesystem if you're running a server with a database.

---

### Post by Alberto_Giacalone on 2014-10-22
@nerdtron
> 85M    apt
6,9M    aptitude
8,0K    bind
8,0K    dbus
4,0K    dhcp
17M    dpkg
4,0K    initramfs-tools
4,0K    initscripts
4,0K    insserv
4,0K    libuuid
8,0K    logrotate
8,0K    mdadm
4,0K    misc
2,5M    mlocate
15G    mysql
4,0K    ntpdate
4,0K    os-prober
28K    pam
4,0K    php5
12K    phpmyadmin
12K    sgml-base
4,0K    smartmontools
4,0K    sudo
120K    ucf
4,0K    update-rc.d
8,0K    urandom
472K    usbutils
8,0K    vim
8,0K    xfonts
12K    xml-core
15G    total


@SenijiSensei 20GB is pretty small? So how can i expand the memory to dedicate to the mysql server?

---

### Post by nerdtron on 2014-10-22
15GB on MySQL plus the OS on the / partition. So I guess you really need to make space for mysql.

---

### Post by SeijiSensei on 2014-10-22
The answer to how big the server needs to be starts with how big is /var/lib/mysql? From the results above, that directory alone consumes 15GB of your 20GB machine.  

However the partition /dev/sda2 mounted as /home has nearly 70 GB free.  Do you expect that space to be used up over time, or did you set aside too much space for /home at installation?  That's easy to do; I've done it myself. Maybe you could split off 30-40 GB from /dev/sda2 into another partition and mount that as /var/lib/mysql.

---

### Post by Alberto_Giacalone on 2014-10-22
I'ts the [COLOR=#000000]ibdata1 folder that occupies 15GB, there isn't a way to purge it? Until a few days ago it wasn't more than 1G

So Senji how can i do that? And it would solve both 2 problems? I don't need so much space in the /home[/COLOR]

---

### Post by nerdtron on 2014-10-22
You can technically changed the save folder of mysql and save for example to /home/mysql. 
here: [http://ubuntuforums.org/showthread.php?t=2202446](http://ubuntuforums.org/showthread.php?t=2202446)
and here too: [http://sharadchhetri.com/2013/05/18/how-to-change-mysql-default-data-directory-in-ubuntu/](http://sharadchhetri.com/2013/05/18/how-to-change-mysql-default-data-directory-in-ubuntu/)
Don't forget to apply the same permission of the original mysql folder to the new mysql folder.

---

### Post by SeijiSensei on 2014-10-22
> **Alberto_Giacalone said:**
> I'ts the ibdata1 folder that occupies 15GB, there isn't a way to purge it? Until a few days ago it wasn't more than 1G

Do you have any idea why the database should have become so large so fast?  That sounds like there's a problem with whatever application is storing data there.  Perhaps if you told us a bit about what you're storing we'd be better able to help.  

In the meantime, I'd try this, following nerdtron's suggestion:

1)  Create a directory as root called /home/mysql, and give it the same ownership and permissions as /var/lib/mysql.

2)  Edit my.cnf and change datadir and socket to point to /home/mysql instead of /var/lib/mysql.

3)  Copy the contents of /var/lib/mysql to /home/mysql.

Now see if you can start the server.

---

### Post by Alberto_Giacalone on 2014-10-22
The same error: ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/home/mysql/mysql.sock' (2) (when connecting to the server), the file mysql.sock don't exist in the folder /home/mysql so i can't regenerate it.

---

### Post by nerdtron on 2014-10-22
> **Alberto_Giacalone said:**
> The same error: ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/home/mysql/mysql.sock' (2) (when connecting to the server), the file mysql.sock don't exist in the folder /home/mysql so i can't regenerate it.

What steps did you already taken exactly?

---

### Post by steeldriver on 2014-10-22
^^^ +1 (in particular any errors when you try to restart the mysql service) - I suspect that if you change the location of the mysql datadir you may need to modify the apparmor configuration as well

---

### Post by Alberto_Giacalone on 2014-10-22
I don't use AppArmor, i'm going to install it
Edit: Is necessary to install it?
root@ns3000557:/etc/apparmor.d# service mysql restart
[ ok ] Stopping MySQL database server: mysqld.
df: `/home/mysql/data/.': No such file or directory
df: no file systems processed
[FAIL] /etc/init.d/mysql: ERROR: The partition with /home/mysql/data is too full! ... failed!

I've done all steps (without apparmor ones)
It isn't more simple if i reinstall mysql and i restore datas from .frm and .opt files?

---

### Post by steeldriver on 2014-10-22
I advise NOT attempting to install anything if your root disk is already full. Just please post any error messages that occur when you attempt to start the mysql service.

---

### Post by Alberto_Giacalone on 2014-10-22
The only error messages i get are:

When i try to restart the server:
[COLOR=#000000][FAIL] /etc/init.d/mysql: ERROR: The partition with /home/mysql/data is too full! ... failed!

When i try to connect to the server:
[/COLOR]ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/home/mysql/mysql.sock' (2)

That's all.
Edit: I'm trying to free up some space, have you got some tips?

---

### Post by nerdtron on 2014-10-22
> **Alberto_Giacalone said:**
> I don't use AppArmor, i'm going to install it
Edit: Is necessary to install it?
root@ns3000557:/etc/apparmor.d# service mysql restart
[ ok ] Stopping MySQL database server: mysqld.
**df: `/home/mysql/data/.': No such file or directory**
df: no file systems processed
[FAIL] /etc/init.d/mysql: ERROR: The partition with /home/mysql/data is too full! ... failed!

** I've done all steps (without apparmor ones)**
It isn't more simple if i reinstall mysql and i restore datas from .frm and .opt files?

Did you set the permissions of the /home/mysql/ folder? Does the data folder even exists?

And it won't work if you did not follow the apparmor steps.

What is the output of the following commands:
```

ls -lah /home/mysql
cat /etc/mysql/my.cnf
tail -n 50 /var/log/mysql/error.log 
```

---

### Post by nerdtron on 2014-10-22
> 
That's all.
Edit: I'm trying to free up some space, have you got some tips?


Your data is already big unless you want to lose data go ahead and delete those in /var/lib/mysql, you'll surely free up data and you'll lose your databases.
That's why we want to help you move the datadir of mysql, fo you to use the 90 GB of your /home partition.

---

### Post by Alberto_Giacalone on 2014-10-23
How i configure apparmor for MySql?

Output:
> root@ns3000557:/# ls -lah /home/mysqltotale 15G [these are for a game server]
drwxr-xr-x 15 mysql root  4,0K ott 23 13:30 .
drwxr-xr-x 19 Omega root  4,0K ott 22 20:38 ..
drwxr-xr-x  2 root  root  4,0K ott 22 19:26 AuthMe
-rwxr-xr-x  1 root  root     0 ott 22 19:26 backup.sql
drwxr-xr-x  2 root  root  4,0K ott 22 19:26 BanManagement
drwxr-xr-x  2 root  root  4,0K ott 22 19:26 coins
drwxr-xr-x  2 root  root  4,0K ott 22 19:26 CoreProtect
drwxr-xr-x  2 root  root  4,0K ott 23 13:30 data
-rwxr-xr-x  1 root  root     0 ott 22 19:26 debian-5.5.flag
**-rwxr-xr-x  1 root  root   _15G_ ott 22 19:29 ibdata1**
-rwxr-xr-x  1 root  root  5,0M ott 22 19:29 ib_logfile0
-rwxr-xr-x  1 root  root  5,0M ott 22 19:29 ib_logfile1
drwxr-xr-x  2 root  root  4,0K ott 22 19:29 kitpvp
drwxr-xr-x  2 root  root  4,0K ott 22 19:29 MoneySQL
drw-rw----  2 mysql mysql 4,0K ott 22 19:29 mysql
-rw-r--r--  1 root  root     0 ott 22 20:10 mysqld.sock
-rwxr-xr-x  1 root  root     6 ott 22 19:29 mysql_upgrade_info
drwxr-xr-x  2 root  root  4,0K ott 22 19:29 phpmyadmin
drwxr-xr-x  2 root  root  4,0K ott 22 19:29 spleef
drwxr-xr-x  2 root  root  4,0K ott 22 19:29 trapdoor
drwxr-xr-x  2 root  root  4,0K ott 22 19:29 warlock
drwxr-xr-x  2 root  root  4,0K ott 22 19:29 wordpress
root@ns3000557:/# cat /etc/mysql/my.cnf
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
# [http://dev.mysql.com/doc/mysql/en/server-system-variables.html](http://dev.mysql.com/doc/mysql/en/server-system-variables.html)


# This will be passed to all mysql clients
# It has been reported that passwords should be enclosed with ticks/quotes
# escpecially if they contain "#" chars...
# Remember to edit /etc/mysql/debian.cnf when changing the socket location.
[client]
port		= 3306
socket		= /home/mysql/mysql.sock


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
socket		= /home/mysql/mysql.sock
port		= 3306
basedir		= /usr/local/mysql
datadir		= /home/mysql/data
tmpdir		= /tmp
lc-messages-dir	= /usr/share/mysql
skip-external-locking
#
# Instead of skip-networking the default is now to listen only on
# localhost which is more compatible and is not less secure.
bind-address		= localhost
#
# * Fine Tuning
#
key_buffer		= 16M
max_allowed_packet	= 16M
thread_stack		= 192K
thread_cache_size       = 8
# This replaces the startup script and checks MyISAM tables if needed
# the first time they are touched
myisam-recover         = BACKUP
#max_connections        = 100
#table_cache            = 64
#thread_concurrency     = 10
#
# * Query Cache Configuration
#
query_cache_limit	= 1M
query_cache_size        = 16M
#
# * Logging and Replication
#
# Both location gets rotated by the cronjob.
# Be aware that this log type is a performance killer.
# As of 5.1 you can enable the log at runtime!
#general_log_file        = /var/log/mysql/mysql.log
#general_log             = 1
#
# Error logging goes to syslog due to /etc/mysql/conf.d/mysqld_safe_syslog.cnf.
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
# * InnoDB
#
# InnoDB is enabled by default with a 10MB datafile in /var/lib/mysql/.
# Read the manual for more InnoDB related options. There are many!
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
# * IMPORTANT: Additional settings that can override those from this file!
#   The files must end with '.cnf', otherwise they'll be ignored.
#
!includedir /etc/mysql/conf.d/
root@ns3000557:/# tail -n 50 /var/log/mysql/error.log
tail: impossible open "/var/log/mysql/error.log" to read: [file does not exist]

---

### Post by nerdtron on 2014-10-23
> How i configure apparmor for MySql?
On the links that I provided, they edited the apparmor for mysql.

```
root@ns3000557:/# ls -lah /home/mysqltotale 15G [these are for a game server]
drwxr-xr-x 15 mysql root  4,0K ott 23 13:30 .
drwxr-xr-x 19 Omega root  4,0K ott 22 20:38 ..
drwxr-xr-x  2 root  root  4,0K ott 22 19:26 AuthMe
-rwxr-xr-x  1 root  root     0 ott 22 19:26 backup.sql
drwxr-xr-x  2 root  root  4,0K ott 22 19:26 BanManagement
drwxr-xr-x  2 root  root  4,0K ott 22 19:26 coins
drwxr-xr-x  2 root  root  4,0K ott 22 19:26 CoreProtect
drwxr-xr-x  2 root  root  4,0K ott 23 13:30 data
-rwxr-xr-x  1 root  root     0 ott 22 19:26 debian-5.5.flag
**-rwxr-xr-x  1 root  root   _15G_ ott 22 19:29 ibdata1**
-rwxr-xr-x  1 root  root  5,0M ott 22 19:29 ib_logfile0
-rwxr-xr-x  1 root  root  5,0M ott 22 19:29 ib_logfile1
drwxr-xr-x  2 root  root  4,0K ott 22 19:29 kitpvp
```

You said you followed everything except the apparmor part, why is the permissions still owned by root?
Run the following:
```
sudo chown -R mysql:mysql /home/mysql 
```

---

### Post by Alberto_Giacalone on 2014-10-23
Ok... We've made some progress (i think)

When restarting MySql server:

root@ns3000557:~# service mysql restart
[ ok ] Stopping MySQL database server: mysqld.
[FAIL] Starting MySQL database server: mysqld . . . . . . . . . . . . . . failed!

---

### Post by nerdtron on 2014-10-23
How far did you go? What steps did you take?

Post the output of the mysql error logs here.

---

### Post by Alberto_Giacalone on 2014-10-23
I followed all the steps.
Here is one error string i taken from my website:

> Warning: mysqli_connect(): (HY000/2002): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2) in /var/www/money.php on line 35
Failed to connect to MySQL: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

Line 35 of "money.php":
> $con=mysqli_connect($database_adress,$database_user,$database_password,$database_name);


---

### Post by nerdtron on 2014-10-23
Not the error on the website but the error on mysql.
See the mysql logs in /var/log/mysql

---

### Post by Alberto_Giacalone on 2014-10-23
[COLOR=#000000]I opened mysql.err and mysql.log with the nano command. Both of these files are empty though.[/COLOR]

---

### Post by Alberto_Giacalone on 2014-10-24
Edit:
> root@ns3000557:/# /var/log/mysql.err/var/log/mysql.err: line 1: 141024: command not found
/var/log/mysql.err: line 2: 141024: command not found
/var/log/mysql.err: line 3: 141024: command not found
/var/log/mysql.err: line 4: 141024: command not found
/var/log/mysql.err: line 5: 141024: command not found
/var/log/mysql.err: line 6: /usr/sbin/mysqld:: File o directory non esistente
/var/log/mysql.err: line 8: 141024: command not found
/var/log/mysql.err: line 9: 141024: command not found
/var/log/mysql.err: line 10: 141024: command not found
/var/log/mysql.err: line 11: 141024: command not found
/var/log/mysql.err: line 12: 141024: command not found
/var/log/mysql.err: line 13: 141024: command not found
/var/log/mysql.err: line 14: 141024: command not found
/var/log/mysql.err: line 15: InnoDB:: command not found
/var/log/mysql.err: line 16: 141024: command not found
/var/log/mysql.err: line 17: InnoDB:: command not found
/var/log/mysql.err: line 18: InnoDB:: command not found
/var/log/mysql.err: line 19: InnoDB:: command not found
/var/log/mysql.err: line 20: InnoDB:: command not found
/var/log/mysql.err: line 21: InnoDB:: command not found
/var/log/mysql.err: line 22: 141024: command not found
/var/log/mysql.err: line 23: InnoDB:: command not found
/var/log/mysql.err: line 24: InnoDB:: command not found
/var/log/mysql.err: line 25: 141024: command not found
/var/log/mysql.err: line 26: 141024: command not found
/var/log/mysql.err: line 26: log: command not found
/var/log/mysql.err: line 27: syntax error near unexpected token `('
/var/log/mysql.err: line 27: `141024 14:14:01 [Note] Server hostname (bind-address): 'localhost'; port: 3306'

---

### Post by Alberto_Giacalone on 2014-10-24
Ok, i've did some more search on internet, so i got the following results:
> root@ns3000557:~# mysqld141024 16:22:31 [Warning] The syntax '--log' is deprecated and will be removed in a future release. Please use '--general-log'/'--general-log-file' instead.
141024 16:22:31 [Warning] Using unique option prefix key_buffer instead of key_buffer_size is deprecated and will be removed in a future release. Please use the full name instead.
141024 16:22:31 [Warning] Using unique option prefix myisam-recover instead of myisam-recover-options is deprecated and will be removed in a future release. Please use the full name instead.
141024 16:22:31 [Note] Plugin 'FEDERATED' is disabled.
mysqld: Table 'mysql.plugin' doesn't exist
141024 16:22:31 [ERROR] Can't open the mysql.plugin table. Please run mysql_upgrade to create it.
141024 16:22:31 InnoDB: The InnoDB memory heap is disabled
141024 16:22:31 InnoDB: Mutexes and rw_locks use GCC atomic builtins
141024 16:22:31 InnoDB: Compressed tables use zlib 1.2.7
141024 16:22:31 InnoDB: Using Linux native AIO
141024 16:22:31 InnoDB: Initializing buffer pool, size = 128.0M
141024 16:22:31 InnoDB: Completed initialization of buffer pool
141024 16:22:31 InnoDB: highest supported file format is Barracuda.
InnoDB: Log scan progressed past the checkpoint lsn 49439
141024 16:22:31  InnoDB: Database was not shut down normally!
InnoDB: Starting crash recovery.
InnoDB: Reading tablespace information from the .ibd files...
InnoDB: Restoring possible half-written data pages from the doublewrite
InnoDB: buffer...
InnoDB: Doing recovery: scanned up to log sequence number 1595675
141024 16:22:31  InnoDB: Starting an apply batch of log records to the database...
InnoDB: Progress in percents: 28 29 30 31 32 33 34 35 36 37 38 39 40 41 42 43 44 45 46 47 48 49 50 51 52 53 54 55 56 57 58 59 60 61 62 63 64 65 66 67 68 69 70 71 72 73 74 75 76 77 78 79 80 81 82 83 84 85 86 87 88 89 90 91 92 93 94 95 96 97 98 99 
InnoDB: Apply batch completed
141024 16:22:31  InnoDB: Waiting for the background threads to start
141024 16:22:32 InnoDB: 5.5.38 started; log sequence number 1595675
141024 16:22:32 [Note] Server hostname (bind-address): '37.59.3.150'; port: 3306
141024 16:22:32 [Note]   - '37.59.3.150' resolves to '37.59.3.150';
141024 16:22:32 [Note] Server socket created on IP: '37.59.3.150'.
141024 16:22:32 [ERROR] Fatal error: Can't open and lock privilege tables: Table 'mysql.host' doesn't exist

---

### Post by Alberto_Giacalone on 2014-10-26
Solved. Thanks to everyone

[http://askubuntu.com/questions/125686/failed-to-spawn-mysql-main-process-unable-to-execute-no-such-file-or-director](http://askubuntu.com/questions/125686/failed-to-spawn-mysql-main-process-unable-to-execute-no-such-file-or-director)

---

### Post by nerdtron on 2014-10-26
sorry wrong post.....please delete comment.

---

