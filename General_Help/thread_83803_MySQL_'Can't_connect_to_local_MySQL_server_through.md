---
title: "MySQL: 'Can't connect to local MySQL server through socket /tmp/mysql.sock'"
date: 2005-10-29
forum: General Help
---

### Post by kerinin on 2005-10-29
i am unable to access my mysql server.  any time i attempt to connect to it i get the error in the thread title.

i've tried reinstalling mysql-client and mysql-server, to no avail.  there are some suggestions [here,]("http://www.tech-recipes.com/mysql_tips762.html") however they don't seem to apply (the lines they suggest adding to /etc/mysql/my.conf already exist).

the [MySQL development reference manual]("http://dev.mysql.com/doc/refman/5.0/en/can-not-connect-to-server.html") says
>  The error (2002) Can't connect to ...  normally means that there is no MySQL server running on the system or that you are using an incorrect Unix socket filename or TCP/IP port number when trying to connect to the server.

i'm not sure how to fix this, and i'm a little confused as to why the default install would be causing a problem related to a simple configuration file.

any suggestions?

thanks!

---

### Post by kerinin on 2005-10-29
ok, nevermind - problem fixed

i was using mysqlcc to connect, and didn't notice the area where it says 'socket file'...  just put '/var/run/mysqld/mysqld.sock' in there and it connected perfectly

---

### Post by DouglasAWh on 2007-12-30
Where is said file?  I am getting the same error in Gutsy.  Thanks!

EDIT: I found some more posts.  Here's my /etc/mysql/my.cnf

```

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


```

It appears as though I have the line this thread says I should have.  Hmm.

ANOTHER EDIT:
It's probably worth noting I got the process started doing
sudo apt-get install mysql-client-5.0.  

I don't know if that is everything I need to have installed.


ANOTHER EDIT:
I installed the server and now I get:

ERROR 1045 (28000): Access denied for user 'whitdoug'@'localhost' (using password: NO)
whitdoug@linux-laptop:/usr$ sudo mysql
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)

Figured it out.  I needed to use the -p to get the password prompt.

---

### Post by xkorakidis on 2008-01-03
hi guys!
I have some similar problems using mysql I installed with jasperserver package. when trying to mysql i get an error msg for mysql.sock. I used mysqld.sock : ./mysql --socket=/var/run/mysqld/mysqld.sock --user=admin -p=admin
using various user and pwd (including that i entered for mysql server when installing jasperserver) but i get always the same error message:  Access denied for user 'admin'@'localhost' (using password: YES). what may there be wrong?
p.s. the only .sock file in my pc is the mysqld.sock, there isn't any mysql.sock

---

### Post by DouglasAWh on 2008-01-03
```

$ sudo apt-get install mysql-server

```

The above is what did it for me.  Did you do that?

---

### Post by xkorakidis on 2008-01-04
jasperserver already has installed mysql server. how can i find it out if the mysql server is already running?

---

### Post by DouglasAWh on 2008-01-04
I haven't used the = in my syntax, so you could try 

```

./mysql -user admin -p

```

It should then prompt you for the password.  It sounds like you know at least as much as I do though...

Have you tried sending to the MySQL list?  [http://lists.mysql.com/mysql](http://lists.mysql.com/mysql)

---

### Post by xkorakidis on 2008-01-04
I used the following 
./mysql -u jasperadmin -p
and get 
ERROR 1045 (28000): Access denied for user 'jasperadmin'@'localhost' (using password: YES)

---

### Post by DouglasAWh on 2008-01-04
have you tried being logged in as root when you connect to mysql?

---

### Post by xkorakidis on 2008-01-04
yes :(
both as root and as sudo ./mysql -u jasperadmin -p
the same error message

---

### Post by DouglasAWh on 2008-01-04
Perhaps a bit more time this should getting moved to programming and development.  I mean, it's more of a sysadmin thing, but the DBAs are going to be the ones that need MySQL.  I still think the MySQL list is the way to go.  Perhaps there's a Jasper list too.  I know nothing about Jasper.

---

### Post by sdowney717 on 2008-01-04
scott@scott-desktop:~$ mysql -u root -p

mysql will prompt for password you set up when you installed mysql

And if you want to login somewhere other than localhost you have to do the grant all priveleges for the user.

my.cnf is also important for connections

to unbind mysql only listeneing to localhost put a '#'' in front of the line
#bind-address		= 127.0.0.1

```

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
#bind-address		= 127.0.0.1
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

#to ignore case in table names
#set lower_case_table_names=1


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


```

---

