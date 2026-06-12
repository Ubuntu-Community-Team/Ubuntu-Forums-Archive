---
title: "Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)"
date: 2014-08-28
forum: General Help
---

### Post by ramosadams on 2014-08-28
Hello today afte installing my website its work fine but after some hour give this error , 
[COLOR=#000000][FONT=Times New Roman]Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
and when restart mysql work but give same error after e few hour 
any solution please
my my.cnf file 
[/FONT][/COLOR]
[client]
port=3306
socket=/var/run/mysqld/mysqld.sock


[mysqld_safe]
socket=/var/run/mysqld/mysqld.sock


[mysqld]
user=mysql
pid-file=/var/run/mysqld/mysqld.pid
socket=/var/run/mysqld/mysqld.sock
port=3306
basedir=/usr
datadir=/var/lib/mysql
tmpdir=/tmp
lc-messages-dir=/usr/share/mysql
log_error=/var/log/mysql/error.log
max_connections=200
max_user_connections=30
wait_timeout=30
interactive_timeout=50
long_query_time=5
innodb_file_per_table


!includedir /etc/mysql/conf.d/



and i cant find  [COLOR=#000000][FONT=Times New Roman]/var/run/mysqld/mysqld.sock 

i need fix it please i use [/FONT][/COLOR][CENTER][COLOR=#666666][FONT=helvetica neue]Ubuntu 14.04 x64[/FONT][/COLOR][/CENTER]
[COLOR=#000000][FONT=Times New Roman]
[/FONT][/COLOR][COLOR=#000000][FONT=Times New Roman]
when i type [/FONT][/COLOR] sudo find / -name mysqld.sock
/run/mysqld/mysqld.sock

[COLOR=#ff0000]**[FONT=Arial]and if there is no solution anyone tell me how ot make cron job command on ubuntu restart mysql evry 1 hour for exemple ?[/FONT]**[/COLOR]

---

