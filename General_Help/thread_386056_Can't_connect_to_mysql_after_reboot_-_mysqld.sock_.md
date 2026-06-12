---
title: "Can't connect to mysql after reboot - mysqld.sock doesn't exist"
date: 2007-03-16
forum: General Help
---

### Post by frankadelic on 2007-03-16
I started my Ubuntu machine this morning to work on my LAMP project, which was working yesterday. Today I get the error:

> Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2).

If I try to connect through command line, like I did successfully yesterday, I get this:
> mysql -uroot -p
Enter password:
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
Normally, my mysql instance starts up automatically. Today it did not and I cannot get it started! I tried the following to manually start mysql (BTW, is this the correct method?? I'm new at this.):
> sudo /etc/init.d/mysql start
and got the errors:
> Starting MySQL database server: mysqld...failed.
        Please take a look at the syslog.
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
The mysqld.sock file really **does not** exist. I ran the following and got zero results:
> find / -name mysqld.sock
find / -name mysql.sock
I grep'd the syslog for "mysql", which shows the following:
> Mar 16 13:04:18 localhost mysqld_safe[6168]: started
Mar 16 13:04:18 localhost mysqld[6171]: 070316 13:04:18 [ERROR] Can't start server: Bind on TCP/IP port: Address already in use
Mar 16 13:04:18 localhost mysqld[6171]: 070316 13:04:18 [ERROR] Do you already have another mysqld server running on port: 3306 ?
Mar 16 13:04:18 localhost mysqld[6171]: 070316 13:04:18 [ERROR] Aborting
Mar 16 13:04:18 localhost mysqld[6171]:
Mar 16 13:04:18 localhost mysqld[6171]: 070316 13:04:18 [Note] /usr/sbin/mysqld: Shutdown complete
Mar 16 13:04:18 localhost mysqld[6171]:
Mar 16 13:04:18 localhost mysqld_safe[6173]: ended
Mar 16 13:04:24 localhost /etc/init.d/mysql[6236]: 0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' resulted in
Mar 16 13:04:24 localhost /etc/init.d/mysql[6236]: ^G/usr/bin/mysqladmin: connect to server at 'localhost' failed
Mar 16 13:04:24 localhost /etc/init.d/mysql[6236]: error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Mar 16 13:04:24 localhost /etc/init.d/mysql[6236]: Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
Mar 16 13:04:24 localhost /etc/init.d/mysql[6236]:

A few things I've tried that DID NOT work:
- Renaming my /etc/mysql/my.cnf file.
- Manually creating a blank file at /var/run/mysqld/mysqld.sock

Here's what I have installed:
> 
dpkg -l | grep mysql
ii  libapache2-mod-auth-mysql              4.3.9-2ubuntu3                             Apache 2 module for MySQL authentication
ii  libdbd-mysql-perl                      3.0002-2build1                             A Perl5 database interface to the MySQL data
ii  libmysqlclient12                       4.0.24-10ubuntu2                           mysql database client library
ii  libmysqlclient14                       4.1.15-1ubuntu5                            mysql database client library
ii  libmysqlclient15off                    5.0.22-0ubuntu6.06.2                       mysql database client library
ii  mysql-client-4.1                       4.1.15-1ubuntu5                            mysql database client binaries
ii  mysql-common                           5.0.22-0ubuntu6.06.2                       mysql database common files (e.g. /etc/mysql
rc  mysql-common-4.1                       4.1.12-1ubuntu3.2                          mysql database common files (e.g. /etc/mysql
ii  mysql-server-4.1                       4.1.15-1ubuntu5                            mysql database server binaries
rc  php4-mysql                             4.4.0-3ubuntu2                             MySQL module for php4
ii  php5-mysql                             5.1.2-1ubuntu3.6                           MySQL module for php5
ii  php5-mysqli                            5.1.2-1ubuntu3.6                           MySQL Improved module for php5


I ran apt-get update and upgrade a few days ago but I've restarted twice since then and it was working before today.

If anyone has suggestions, please let me know. I've been working on a LAMP project and suddenly I can't do anything.

edit: I did install gd yesterday as it was needed for the lamp cms I'm using.
> sudo apt-get install php5-gd
...besides that I've changed nothing since it was last working.

---

### Post by dannyboy79 on 2007-03-16
these are ALL the solutions I found using gogle. pick one

updated /etc/my.cnf and explicitly defined the location of mysql.sock on line 3. 

OR

first check the permissions of /var/run/mysqld/ 
try to chown to "mysql.mysql" if owned by root, and give it a 755. 

OR

cd /var/lib 
chown mysql.root mysql 
chmod 755 mysql 

Create a my.cnf in /etc 
------------------------------------------------------------- 
[mysqld] 
datadir=/var/lib/mysql 
socket=/var/lib/mysql/mysql.sock 
#set-variable = interactive_timeout=240 
#set-variable = wait_timeout=240 
#set-variable = max_connections=150 
bind-address = 127.0.0.1 
skip-name-resolve 
safe-show-database 

[mysql.server] 
user=mysql 
basedir=/var/lib 

[safe_mysqld] 
err-log=/var/log/mysqld.log 
pid-file=/var/run/mysqld/mysqld.pid 
log-slow-queries = /var/log/mysql-slow.log 
---------------------------------------------------------- 

Try to start it.

OR

I too have been bashing my head against the keyboard on this and found a tip that solved it for me. SELinux was my problem and needed to disable it for mysqld (run system_config_securitylevel and select SELinux and the bottom twistie will expose the deamons). Once done rerun "mysql_install_db --user=mysql" followed by "/usr/bin/mysqld_safe &". At least this is what done it for me on FC3.

OR

WOOT.....found a solution 

SE linux makes it very hard for anything to work in Fedora Core 3.....(generalization) 

When i was shutting the computer down i noticed that there was and error in removing the mysql.sock.....no permissions. I had monkeyed arround trying to find out what i need to give permissions too.....the i revisited my installation proceedure. I had origionally installed Fedora Core using Stanton-Finley notes. During the install it made a reference to turn off the protection for the httpd daemon. SO CLICK, the light bulb came on. 

What you need to do is to go to terminal in root 

/usr/sbin/setenforce 0 
/etc/init.d/mysql start 

This will force selinux off and start msql to get a mysql.sock started. 

Go to Applications > System Settings > Security Level and type in your root pass word 

Open the SELinux tab and under Modify SE linux policy 
open SElinux service protection and click on Disable SELinux protection for mysqld daemon. 

reboot your computer 

Everything should work..... For some reason if the you dont disable the daemon the shut down proceedure WILL NOT be granted removal priveleges for the mysql.sock.......It will be there at start up and Mysql gets all confused at this and promptly shuts down........thats why i was getting the subject errors.....LOL


OR

SOLVED: 

My problem (Ubuntu) was a permission issue on /var/run/mysqld and the clue was that logging into mysql worked when I was root, but not as any other use (did not work with '-u root' on the command line either). Here is an 'ls -l' for me: 

(login failed) 
drwxrwx--- 2 mysql root 80 2006-02-19 16:51 mysqld 

(login succeeded) 
drwxrwxr-x 2 mysql root 80 2006-02-19 16:51 mysqld 

Hope this helps someone. 

Regards, 
-Darryl


OR


Please read carefull, because its solved. 

i spend 5 weeks as newbie and got no help for solaris10, and have a to z configure listed for futer newbies so that you can save your time now.., thanks me if you want. 

1. download mysql (i am in solaris10) to 
/sbin direcotry 
ht t p:/ /dev.mysql.com/get/Downloads/MySQL-5.0/mysql-standard-5.0.27-solaris10-i386.pkg.gz/from/[mysql.belnet.be] 

2. unzip the file which you downloaded in /sbin directory 
#gunzip mysql-standard-5.0.27-solaris10-i386.pkg.gz 

3. install the package from /sbin direcotry 
#pkgadd -d mysql-standard-5.0.27-solaris10-i386.pkg 

4. it will be installed in /usr/local/mysql or /opt/mysql/mysql 

5. copy the mysql configuration file to one global place, which you can define easyly. 
#cp /usr/local/mysql/support-bin/my-small.cnf /etc/my.cnf 

6. edit the my.cnf file 
#vi /etc/my.cnf 

7. add 3 lines under /etc/my.cnf 
[mysqld] 
user=mysql 
basedir=/usr/local/mysql 
datadir=/var/lib/mysql/mysql 

save this configurations it 

8. mysqld startup method, (like starting services) 
#/usr/local/mysql/scripts/mysql_install_db --defaults-file=/etc/my.cnf --user=mysql 
#/usr/local/mysql/bin/mysqld_safe --defaults-file=/etc/my.cnf --user=mysql 

9. congratulation, you saved your 5 weeks time in 5 minutes. 

10. check its running or not!. 
#ps -ef | grep mysql 

11. login to mysql promt. and startup your database and table and query. 
#/usr/local/mysql/bin/mysql 
Welcome to the MySQL monitor. Commands end with ; or \g. 
Your MySQL connection id is 2 to server version: 5.0.27-standard 

Type 'help;' or '\h' for help. Type '\c' to clear the buffer. 

mysql> 


note: if you force to start use /etc/init.d/mysql start, make one thing clear that mysqld.sock is created by mysqld startup. its not related with mysql package.



Hello, 

For Debian users i found the problem to be wrong permissions on the tmp folder 

# sudo chmod 777 /tmp

---

### Post by frankadelic on 2007-03-16
Thanks Danny,
I got it working! I tried a bunch of stuff which didn't help initially but it worked after I rebooted the server.

I think this might have fixed it:
> sudo chown mysql:mysql /var/run/mysqld

After rebooting, the /var/run/mysqld directory was no longer empty, so maybe the permissions changes enabled the .sock and .pid files to be created.
> ls /var/run/mysqld/
mysqld.pid  mysqld.sock


Thanks and Happy St. Patrick's Day weekend!
-Frank

---

### Post by silurius on 2007-03-16
I went through all the proposed fixes and am still at square one.  This problem started while I was troubleshooting a different issue (whereby I could not connect to mysql from an external machine):

mysqladmin -u root -p flush-hosts

As soon as I did this -- bam, this issue began.  I was able to restore the mysqld.pid & mysqld.sock files using the fix in the previous post (permissions) but that's as far as I've gotten.

At this point I'm out of ideas and am considering starting over with a fresh installation.

---

### Post by dannyboy79 on 2007-03-16
have you at least restsarted your machine? you don't need a fresh install! just recreate your databases? i don't know cause I don't use it yet.

---

### Post by silurius on 2007-03-17
Yes, tried several reboots after various troubleshooting steps.  Did not try to recreate databases (or create a new one); not a bad idea.  Won't be able to try until I have access to the machine again on Monday.

Noting that Drupal and phpMyAdmin would not come up at all over http (even on localhost) I wonder if the flush host command could have impacted another layer of my site than just MySQL?

---

