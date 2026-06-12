---
title: "XAMPP/mysqld problem"
date: 2007-03-23
forum: General Help
---

### Post by ktm5124 on 2007-03-23
I have root ssh access, but no desktop acccess, to my web hosting. My web hosting runs Clean Slate Linux something or other. Yes, I know, it's not Ubuntu. I run Ubuntu at home, and I like these forums, so I'm posting this here.

I installed MediaWiki yesterday and I don't know how but in the process of installing it and adding users to mysql, mysqld simply died. 

Before I go on, I think it's important to note that I set up my server components using XAMPP. XAMPP packages together The Stuff, i.e. apache, php5, mysql, perl, etc., and installs it all for you. So all of these programs are found in lampp/bin.  

Here's the output when I run /opt/lampp/bin/mysql:

```

[andrew@vps]$ sudo mysql
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/opt/lampp/var/mysql/mysql.sock' (2)

```

So at first I thought I was having problems with the client program and the file mysql.sock. Later I came to the conclusion that it's not the client program I'm having problems with, but the server program, mysqld. 

Here's the output when I run /opt/lampp/bin/mysqld_safe:

```

[andrew@vps bin]$ sudo ./mysqld_safe
Starting mysqld daemon with databases from /opt/lampp/var
./mysqld_safe: line 1:  8193 Killed                  nohup /opt/lampp/sbin/mysqld --basedir=/opt/lampp --datadir=/opt/lampp/var --user=nobody --pid-file=/opt/lampp/var/vps.pid --skip-external-locking --port=3306 --socket=/opt/lampp/var/mysql/mysql.sock >>/opt/lampp/var/vps.err 2>&1
STOPPING server from pid file /opt/lampp/var/vps.pid
070323 18:59:31  mysqld ended

[andrew@vps bin]$

```

The log file /opt/lampp/vars/vps.err is useless, it just contains the following:

[timestamp] mysqld started
[timestamp] mysqld ended

It's interesting to note that every time I run mysqld_safe the mysql.sock file dies. The file is in the appropriate place, i.e. the path specified by my.cnf.

Here's my my.cnf file:

```

[andrew@vps etc]$ cat my.cnf
# Example MySQL config file for medium systems.
#
# This is for a system with little memory (32M - 64M) where MySQL plays
# an important part, or systems up to 128M where MySQL is used together with
# other programs (such as a web server)
#
# You can copy this file to
# /etc/my.cnf to set global options,
# mysql-data-dir/my.cnf to set server-specific options (in this
# installation this directory is /opt/lampp/var/mysql) or
# ~/.my.cnf to set user-specific options.
#
# In this file, you can use all long options that a program supports.
# If you want to know which options a program supports, run the program
# with the "--help" option.

# The following options will be passed to all MySQL clients
[client]
#password       = your_password
port            = 3306
socket          = /opt/lampp/var/mysql/mysql.sock

# Here follows entries for some specific programs

# The MySQL server
[mysqld]
# commented out by lampp security
port            = 3306
#port = 0
socket          = /opt/lampp/var/mysql/mysql.sock
skip-locking
key_buffer = 16M
max_allowed_packet = 1M
table_cache = 64
sort_buffer_size = 512K
net_buffer_length = 8K
read_buffer_size = 256K
read_rnd_buffer_size = 512K
myisam_sort_buffer_size = 8M

# Don't listen on a TCP/IP port at all. This can be a security enhancement,
# if all processes that need to connect to mysqld run on the same host.
# All interaction with mysqld must be made via Unix sockets or named pipes.
# Note that using this option without enabling named pipes on Windows
# (via the "enable-named-pipe" option) will render mysqld useless!
#
#skip-networking

# Replication Master Server (default)
# binary logging is required for replication
# log-bin deactivated by default since XAMPP 1.4.11
#log-bin=mysql-bin

# required unique id between 1 and 2^32 - 1
# defaults to 1 if master-host is not set
# but will not function as a master if omitted
server-id       = 1

# Replication Slave (comment out master section to use this)
#
# To configure this host as a replication slave, you can choose between
# two methods :
#
# 1) Use the CHANGE MASTER TO command (fully described in our manual) -
#    the syntax is:
#
#    CHANGE MASTER TO MASTER_HOST=<host>, MASTER_PORT=<port>,
#    MASTER_USER=<user>, MASTER_PASSWORD=<password> ;
#
#    where you replace <host>, <user>, <password> by quoted strings and
#    <port> by the master's port number (3306 by default).
#
#    Example:
#
#    CHANGE MASTER TO MASTER_HOST='125.564.12.1', MASTER_PORT=3306,
#    MASTER_USER='joe', MASTER_PASSWORD='secret';
#
# OR
#
# 2) Set the variables below. However, in case you choose this method, then
#    start replication for the first time (even unsuccessfully, for example
#    if you mistyped the password in master-password and the slave fails to
#    connect), the slave will create a master.info file, and any later
#    change in this file to the variables' values below will be ignored and
#    overridden by the content of the master.info file, unless you shutdown
#    the slave server, delete master.info and restart the slaver server.
#    For that reason, you may want to leave the lines below untouched
#    (commented) and instead use CHANGE MASTER TO (see above)
#
# required unique id between 2 and 2^32 - 1
# (and different from the master)
# defaults to 2 if master-host is set
# but will not function as a slave if omitted
#server-id       = 2
#
# The replication master for this slave - required
#master-host     =   <hostname>
#
# The username the slave will use for authentication when connecting
# to the master - required
#master-user     =   <username>
#
# The password the slave will authenticate with when connecting to
# the master - required
#master-password =   <password>
#
# The port the master is listening on.
# optional - defaults to 3306
#master-port     =  <port>
#
# binary logging - not required for slaves, but recommended
#log-bin=mysql-bin


# Point the following paths to different dedicated disks
#tmpdir         = /tmp/
#log-update     = /path-to-dedicated-directory/hostname

# Uncomment the following if you are using BDB tables
#bdb_cache_size = 4M
#bdb_max_lock = 10000

# Comment the following if you are using InnoDB tables
skip-innodb
innodb_data_home_dir = /opt/lampp/var/mysql/
innodb_data_file_path = ibdata1:10M:autoextend
innodb_log_group_home_dir = /opt/lampp/var/mysql/
innodb_log_arch_dir = /opt/lampp/var/mysql/
# You can set .._buffer_pool_size up to 50 - 80 %
# of RAM but beware of setting memory usage too high
innodb_buffer_pool_size = 16M
innodb_additional_mem_pool_size = 2M
# Set .._log_file_size to 25 % of buffer pool size
innodb_log_file_size = 5M
innodb_log_buffer_size = 8M
innodb_flush_log_at_trx_commit = 1
innodb_lock_wait_timeout = 50

[mysqldump]
quick
max_allowed_packet = 16M

[mysql]
no-auto-rehash
# Remove the next comment character if you are not familiar with SQL
#safe-updates

[isamchk]
key_buffer = 20M
sort_buffer_size = 20M
read_buffer = 2M
write_buffer = 2M

[myisamchk]
key_buffer = 20M
sort_buffer_size = 20M
read_buffer = 2M
write_buffer = 2M

[mysqlhotcopy]
interactive-timeout
[andrew@vps etc]$

```

Thanks in advance to all who give away some of their time to help me.

---

### Post by darkos on 2007-03-28
I had the same problem some days ago. Personally i removed xampp and used apache2, php4-5 and mysql seperately.
You can try stopping the mysql daemon from xampp, and put in the php.ini the path of your normal mysql db.Then stop xampp and start your normal mysql and then start xampp again. This time it wont load its mysql daemon, because the other one is already running. Hope this will work! ;)

---

