---
title: "jffnms install"
date: 2007-07-17
forum: General Help
---

### Post by williemerwe on 2007-07-17
I have a problem with my jffnms install.  I followed these steps:
```
# mysql –u root –p
mysql> create database jffdb;
mysql> GRANT ALL ON jffdb.* TO jffuser@localhost IDENTIFIED BY ‘jffpw’;
mysql> flush privileges;
mysql> exit

# vim /etc/php5/apache2/php.ini
register_globals = On

# apt-get install jffnms
I decline when dbconfig-common want to configures the database as I've already done this.

# ln –s /usr/share/jffnms/htdocs /var/www/jffnms
# ln –s /var/lib/jffnms/tempimages /usr/share/jffnms/htdocs/images/temp

# chmod 775 /usr/share/jffnms/htdocs
# chmod 777 /usr/share/jffnms/conf
# chmod 777 /var/lib/jffnms/tempengine
# chmod 777 /var/lib/jffnms/tempimages

# vim /usr/share/jffnms/conf/jffnms.conf.defaults
jffnms_real_path:default = /usr/share/jffnms/
```

At this point I can open the URL [http://server/jffnms](http://server/jffnms) and it redirects me to [http://server/jffnms/admin/setup.php](http://server/jffnms/admin/setup.php) for the setup.  I amend the database settings and save.  Now, when I want to open the page [http://server/jffnms](http://server/jffnms), it gives me the following error(s):
```
14:00:02 db_ping(mysql) Connection to DB Restored... 14:00:03 db_ping(mysql) Connection to DB Restored... 14:00:04 db_ping(mysql) Connection to DB Restored... 14:00:05 db_ping(mysql) Connection to DB Restored... 14:00:06 db_ping(mysql) Connection to DB Restored... 
**Warning**: mysql_num_rows(): supplied argument is not a valid MySQL result resource in **/usr/share/jffnms/lib/api.db.inc.php** on line **306**
14:00:07 db_ping(mysql) Connection to DB Restored... 14:00:08 db_ping(mysql) Connection to DB Restored... 14:00:09 db_ping(mysql) Connection to DB Restored... 14:00:10 db_ping(mysql) Connection to DB Restored... 14:00:11 db_ping(mysql) Connection to DB Restored... 
**Warning**: mysql_num_rows(): supplied argument is not a valid MySQL result resource in **/usr/share/jffnms/lib/api.db.inc.php** on line **306**
14:00:12 db_ping(mysql) Connection to DB Restored... 14:00:13 db_ping(mysql) Connection to DB Restored... 14:00:14 db_ping(mysql) Connection to DB Restored... 14:00:15 db_ping(mysql) Connection to DB Restored... 14:00:16 db_ping(mysql) Connection to DB Restored... 14:00:16 Query Failed - table_insert(events) - insert into events (date,type,host,interface,state,username,info) VALUES ('2007-07-17 14:00:11','43','1','Login','failed','admin','from 192.168.0.176') - Table 'jffdb.events' doesn't exist14:00:17 db_ping(mysql) Connection to DB Restored... 14:00:18 db_ping(mysql) Connection to DB Restored... 14:00:19 db_ping(mysql) Connection to DB Restored... 14:00:20 db_ping(mysql) Connection to DB Restored... 14:00:21 db_ping(mysql) Connection to DB Restored... 
**Warning**: join() [[COLOR="Blue"]_function.join_[/COLOR]]: Bad arguments. in **/usr/share/jffnms/lib/api.events.inc.php** on line **246**
Query Failed - events_list() - Table 'jffdb.hosts' doesn't exist
```

Did I miss something somewhere in the isntall?

Please help  ](*,)

---

### Post by williemerwe on 2007-07-18
Something I forgot to ask.  I installed following , but don't quite understand the very first part.  Forgive me, but I'm kinda new to Linux.
It states:
sudo vi /etc/apt/sources.list (enable the other repos)
What exactly does "enable the other repos" mean?

Then, the install command is:
```
sudo aptitude install [COLOR="Blue"]openssh-server[/COLOR] clamav clamav-daemon [COLOR="blue"]apache2 php5 snmpd[/COLOR] snmp graphviz [COLOR="blue"]tftpd[/COLOR] ntp nmap fping [COLOR="blue"]mysql-server[/COLOR] dbconfig-common libapache2-mod-php5 php-pear [COLOR="blue"]php5-cli[/COLOR] php5-gd [COLOR="blue"]php5-mysql[/COLOR] php5-snmp [COLOR="blue"]rrdtool[/COLOR] ntp tac-plus ttf-bitstream-vera mtop htop
```
Those marked in blue are packages I already have installed - I have cacti running on the machine.  Do I really need all the other packages just for jffnms?

---

### Post by undecidable on 2007-07-18
Can't help with jffnms
but repos is "repositories".

Best explanation is in the Ubuntu documentation.
See either:

section 6.1 of the Dapper Manual
at  [https://help.ubuntu.com/6.06/](https://help.ubuntu.com/6.06/)

or in the specific section of the online documentation for Feisty 7.04 
at  [https://help.ubuntu.com/7.04/add-applications/C/index.html](https://help.ubuntu.com/7.04/add-applications/C/index.html)

(unfortunately the Feisty manual is no longer in downloadable format!)

hope this helps a bit.

---

### Post by williemerwe on 2007-07-18
Thanks!  Will read up on that.
If anyone can help with the jffnms, I'd appreciate it.

---

