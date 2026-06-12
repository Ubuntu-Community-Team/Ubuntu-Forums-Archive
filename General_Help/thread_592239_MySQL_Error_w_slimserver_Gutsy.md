---
title: "MySQL Error w/ slimserver Gutsy"
date: 2007-10-26
forum: General Help
---

### Post by Sceiron on 2007-10-26
I, beeing a new user of both Linux and Ubuntu forums, need help to get slimserver up and running on my Ubuntu 7.10 gutsy. Kernel 2.6.22-14-generic. Gnome 2.20.0.

Now i have tried to install from terminal and synaptic package manager, and i get the same error when trying to run slimserver:

odd@gutsy:~$ slimserver
2007-10-26 12:12:42.9355 ERROR: MySQLHelper: createSystemTables() Couldn't connect to database: [Can't connect to local MySQL server through socket '/home/odd/Cache/slimserver-mysql.sock' (2)]

The File "mysql-error-log.txt" says following:
071026 12:12:13  InnoDB: Started; log sequence number 0 43655
071026 12:12:13 [ERROR] Can't start server: Bind on TCP/IP port: Address already in use
071026 12:12:13 [ERROR] Do you already have another mysqld server running on port: 9092 ?
071026 12:12:13 [ERROR] Aborting

071026 12:12:13  InnoDB: Starting shutdown...
071026 12:12:15  InnoDB: Shutdown completed; log sequence number 0 43655
071026 12:12:15 [Note] /usr/sbin/mysqld: Shutdown complete

"my.cnf" for MySQL in Cache has following settings:
port = 9092
bind-adress = 127.0.0.1

When trying to find out what progrmas/services is using port 9092, i get this:
odd@gutsy:~$ sudo netstat -anp | grep -i list | grep :9092
tcp        0      0 127.0.0.1:9092          0.0.0.0:*               LISTEN     7237/mysqld  


Can someone please help me find out what i must do to fix this? And explain the problem in a common language. Remember i am a NEW user of linux, and dont have any experience.....
(This is the first time i have read a log file.....)

Sceiron

---

### Post by mannih2001 on 2007-10-26
Why did you tell mysql to listen on port 9092? Is slimserver aware of this non-standard port?

---

### Post by Sceiron on 2007-10-26
I did not tell MySQL to listen to port 9092, its default from installation....
During installation of slimserver i think it added a lokal MySQL database for slimserver.
How can i determine what port slimservers is listening to?
And in which file for slimserver can i change these settings?

---

### Post by mannih2001 on 2007-10-26
The default port for mysql is 3306 (have a look in /etc/services if you don't believe me). 

Since I don't know a single thing about slimvserver, I suggest you simply make mysql listen on its default port:

edit /etc/mysql/my.cnf and set the port to 3306
issue /etc/init.d/mysql restart
and see whether it works now.

---

### Post by Sceiron on 2007-10-26
Hello, i belive you ofc  :)

so i looked up /etc/mysql/my.cnf and here the port was set to 3306.

Ill try to explain what is happening:
When slimserver starts or is installed it creates a lokal MySQL database in /home/odd/Cache/
just for slimserver (this is what i think happens)
And here the port is set to 9092 by default. So i tried to change it to 3306, but still i get the same error about MySQL cant connect through "socket", when i try to run slimserver.

Thanks for the help btw.

---

### Post by mannih2001 on 2007-10-26
OK. I guess your best bet is on slimserver and its support. It seems more like a slimserver than a mysql problem to me.

---

