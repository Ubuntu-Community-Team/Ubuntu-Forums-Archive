---
title: "Problem connecting to mysql"
date: 2008-05-13
forum: General Help
---

### Post by spark01 on 2008-05-13
I am having trouble connecting to mysql data base. When I try to access the MYSQL shell, add a database or change the password for root, it gives me this error. 

root@ns2:/usr/sbin# mysql -u root -p
Enter password: 
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/tmp/mysql.sock' (2)

I did some research about this error in google but could not find a solution. In the file my.cnf the socket part points to /tmp/mysqld.sock but I do not have this file at all on my machine. Also, mysqld appears to be running... If anyone has a suggestions it would be greatly appreciated! Thank you in advance.

---

### Post by spark01 on 2008-05-14
Does anybody at all have any suggestions?

---

### Post by Monicker on 2008-05-14
Are you sure mysql is running?

What does this command show?
```

sudo ps -ef |grep mysql
```

Also check for information in /var/log/mysql.log and /var/log/mysql.err

---

### Post by spark01 on 2008-05-14
When i type ps -ef |grep mysql this is the output:

root     30550     1  0 09:17 ?        00:00:00 /bin/sh /usr/bin/mysqld_safe
mysql    30676 30550  0 09:18 ?        00:00:00 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --pid-file=/var/run/mysqld/mysqld.pid --skip-external-locking --port=3306 --socket=/var/run/mysqld/mysqld.sock
root     30677 30550  0 09:18 ?        00:00:00 logger -p daemon.err -t mysqld_safe -i -t mysqld
root     30726 24647  0 09:20 pts/1    00:00:00 grep mysql

And there does not seem to be anything in those 2 error log files.

---

### Post by Monicker on 2008-05-14
Did you change the defaults for mysql?  Normally mysql.sock will be in /var/run/mysqld/.  Who has ownership of /tmp/mysql.sock?  It should be the mysql account.

---

### Post by spark01 on 2008-05-14
I did not change any of the defaults for MYSQL. I don't have mysqld.sock in the tmp folder, but I did find it in /var/run/mysqld/

Does it have to be in the tmp folder?

---

### Post by Monicker on 2008-05-14
No, it should not be in /tmp, but your error messages references /tmp/mysql.sock.

Give the output for this command:

```
sudo grep socket /etc/mysql/my.cnf
```

---

### Post by spark01 on 2008-05-14
When I run "grep socket /etc/mysql/my.cnf" this is the output:

# Remember to edit /etc/mysql/debian.cnf when changing the socket location.
socket          = /var/run/mysqld/mysqld.sock
socket          = /var/run/mysqld/mysqld.sock
socket          = /var/run/mysqld/mysqld.sock
[1]+  Done                    gedit my.cnf  (wd: /etc)
(wd now: /var/run/mysqld)

---

### Post by spark01 on 2008-05-14
When I run "grep socket /etc/mysql/my.cnf" this is the output:

# Remember to edit /etc/mysql/debian.cnf when changing the socket location.
socket          = /var/run/mysqld/mysqld.sock
socket          = /var/run/mysqld/mysqld.sock
socket          = /var/run/mysqld/mysqld.sock
[1]+  Done                    gedit my.cnf  (wd: /etc)
(wd now: /var/run/mysqld)

---

### Post by Monicker on 2008-05-14
Strange.  Which version of Ubuntu is this?  How was mysql installed?

---

### Post by spark01 on 2008-05-14
I think I figured out what was wrong, I had my.cnf in 2 places, one in /etc and one in /etc/mysq/ and the one in /etc had the socket pointing to the /tmp folder. I changed that path to /var/run/mysqld/mysqld.sock and I no longer get that error. Will having 2 my.cnf files mess anything up?

---

### Post by Monicker on 2008-05-14
Well, as long as you know which one to use, it should be alright; personally I would only keep the one which I am actually using.  Did you install from source or non Ubuntu package?  The Ubuntu packages use /etc/mysql/my.cnf.

---

### Post by spark01 on 2008-05-14
Originaly, I installed MYSQL not from the package's that come with Ubuntu but I was having problems with configuring and making everything so I downloaded it from the package manager instead. 

Thanks for all your help!

---

### Post by wagb278 on 2008-05-17
I also need help getting MySQL to start, please.

I am running Ubuntu HH 8.04 (64-bit).  
I changed the location of the MySQL Databases in my.cnf.  I have another computer (GG 7.10 server) on which I performed the same steps to move the MySQL data and that works.  The configuration and directory permissions for the new data location are the same on both setups.  I moved the databases to a different partition "/data" which is mounted and functioning.

On the computer that MySQL is not starting I do not have any files (socket & pid) in /var/run/mysqld - I assume those get created when MySQL starts running.  Apache2 is running. 

Running command: "/etc/init.d/mysql restart" returns a [COLOR="Red"][fail][/COLOR].

The only clue I know to give is errors in dmesg.
The output of dmesg | grep 'mysql' is: 
```
[  924.753408] audit(1211033973.187:6): type=1503 operation="inode_create" requested_mask="w::" denied_mask="w::" name="/data/databases/green.lower-test" pid=7204 profile="/usr/sbin/mysqld" namespace="default"
[  924.754093] audit(1211033973.187:7): type=1503 operation="inode_create" requested_mask="w::" denied_mask="w::" name="/data/databases/green.lower-test" pid=7204 profile="/usr/sbin/mysqld" namespace="default"
[  924.768970] audit(1211033973.203:8): type=1503 operation="inode_permission" requested_mask="rw::" denied_mask="rw::" name="/data/databases/ibdata1" pid=7204 profile="/usr/sbin/mysqld" namespace="default"
```

The "ibdata1" file is in /data/databases and has 664 permissions with mysql:mysql as owner:group.  The "mysql" directory in /data/databases is owned by user mysql and has the same permissions as where that file was copied from (/var/lib/mysql). I don't know what the first two messages refer to.  However, "green" is the name of this node

I noticed a comment in my.cnf about might have to change appamor, but I didn't have to do that on the GG 7.10 installation. Is there a difference in the two Ubuntu versions I need to know about with respect to this?

Any suggestions as to where and what to look for will be most welcome.

---

### Post by wagb278 on 2008-05-20
**SOLVED** :)
In case others are having difficulty with MySQL databases that are relocated in Ubuntu 8.04 this is how I resolved my problem.

My problem was resolved by changing the MySQL settings for AppArmor as suggested in the comment contained in the the my.cnf file.  I duplicated the the two lines in file: usr.sbin.mysqld that have to due with the data directory and changed the paths to where my databases are located.

Had to restart the computer - apparmor's restart or reload commands were of no use for me.

It appears that AppArmor is built-in starting with Ubuntu 8.04 and MySQL does have a profile - different from Ubuntu 7.10.

Hope this helps someone.

---

