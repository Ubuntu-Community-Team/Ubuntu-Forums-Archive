---
title: "mysql problem"
date: 2008-06-01
forum: General Help
---

### Post by suxxor on 2008-06-01
1.
      i`ve made some stupid thing i`ve typed "whereis mysql" and than looking the output of command i`ve delete all directories containing "mysql" , i want to install mysql server 5.0 but i can`t install it now i got problems installing DNS server and other, i`ve made this because i`ve installed lampp and the default mysql server in ubuntu always running i want those in lampp but things get worst :<
   2.
       
   3.
      here is output of some comand  :
   4.
       
   5.
      dpkg --configure -a
   6.
      Setting up mysql-server-5.0 (5.0.51a-3ubuntu5.1) ...
   7.
       * Stopping MySQL database server mysqld                                 [ OK ]
   8.
      Reloading AppArmor profiles /sbin/apparmor_parser: Unable to replace "/usr/lib/cups/backend/cups-pdf".  Profile doesn't conform to protocol
   9.
       Profile /etc/apparmor.d/usr.sbin.cupsd failed to load
  10.
      Warning: found /etc/apparmor.d/force-complain/usr.sbin.mysqld, forcing complain mode
  11.
      /sbin/apparmor_parser: Unable to replace "/usr/sbin/mysqld".  Profile doesn't conform to protocol
  12.
       Profile /etc/apparmor.d/usr.sbin.mysqld failed to load
  13.
      : Failed.
  14.
      invoke-rc.d: initscript apparmor, action "force-reload" failed.
  15.
       * Starting MySQL database server mysqld                                 [ OK ]
  16.
      /etc/init.d/mysql: line 115: /etc/mysql/debian-start: No such file or directory
  17.
      invoke-rc.d: initscript mysql, action "start" failed.
  18.
       
  19.
       
  20.
      what to do now ?

---

### Post by quelx on 2008-06-01
Try reinstalling **mysql-server** to repair the installation so you can remove it.

```
sudo killall -9 mysqld
sudo apt-get --reinstall install mysql-server
sudo apt-get --purge remove mysql-server
```

*Always* use **apt*** to remove packages installed with **apt***.

***apt** = *aptitude*/*apt-get*/*dpkg*/*synaptic* and the rest

---

### Post by suxxor on 2008-06-01
kaloqn@kaloqn-desktop:~/Desktop/assembly$ sudo killall -9 mysqld
[sudo] password for kaloqn: 
kaloqn@kaloqn-desktop:~/Desktop/assembly$ sudo apt-get --reinstall install mysql-server
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

when i execute 

kaloqn@kaloqn-desktop:~/Desktop/assembly$ sudo dpkg --configure -a
Setting up mysql-server-5.0 (5.0.51a-3ubuntu5.1) ...
 * Stopping MySQL database server mysqld                                 [ OK ] 
Reloading AppArmor profiles /sbin/apparmor_parser: Unable to replace "/usr/lib/cups/backend/cups-pdf".  Profile doesn't conform to protocol
 Profile /etc/apparmor.d/usr.sbin.cupsd failed to load
Warning: found /etc/apparmor.d/force-complain/usr.sbin.mysqld, forcing complain mode
/sbin/apparmor_parser: Unable to replace "/usr/sbin/mysqld".  Profile doesn't conform to protocol
 Profile /etc/apparmor.d/usr.sbin.mysqld failed to load
: Failed.
invoke-rc.d: initscript apparmor, action "force-reload" failed.
 * Starting MySQL database server mysqld                                 [ OK ] 
/etc/init.d/mysql: line 115: /etc/mysql/debian-start: No such file or directory
invoke-rc.d: initscript mysql, action "start" failed.

it stops here

---

### Post by snakdoc on 2008-11-13
sudo apt-get autoremove --purge mysql-server mysql-server-5.0
sudo apt-get install mysql-server

---

### Post by brightwings on 2008-11-23
Hi!

I've searched a lot of forums and these post, but sitll have a problem.
I'm using 8.04 64bit, and had different errors during install Mysql server.

Last version is something like this:

/var/lib/dpkg/info/mysql-server-5.0.postinst: line 143: /etc/mysql/conf.d/old_passwords.cnf:
mysql-server-5.0 (--configure):
 
post-installation script failed code 1 
Sub-process /usr/bin/dpkg returned an error code (1)

This was the "best" result.

#Update: with 8.10 everything works fine.

brightwings

---

### Post by ravenpi on 2008-12-03
I had the same problem -- turns out that I was, and you may have been, bitten by what's usually a good thing: not having to reboot.  For some reason, it appears that when you start having problems, various mysql processes don't die; I actually had a mysqld running by user "107" -- yup, running as a deleted user.  A bit of "kill -9" action, and a re-install worked like a charm.

---

### Post by Hypnoz on 2009-05-11
I had this same issue and this is how I solved it. The key is the part of the error that says 
/etc/init.d/mysql: line 115: /etc/mysql/debian-start: No such file or directory

If you check /etc/mysql/ you will notice there is no file named debian-start but this file is necessary. I'm not sure how it gets removed, but you need to recreate it.

In /etc/mysql/ create a new file named debian-start, give it chmod 755 permissions (rwxr-xr-x), and paste this text into it.

#!/bin/bash
#
# This script is executed by "/etc/init.d/mysql" on every (re)start.
#
# Changes to this file will be preserved when updating the Debian package.
#

source /usr/share/mysql/debian-start.inc.sh

MYSQL="/usr/bin/mysql --defaults-file=/etc/mysql/debian.cnf"
MYADMIN="/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf"
MYUPGRADE="/usr/bin/mysql_upgrade --defaults-extra-file=/etc/mysql/debian.cnf"
MYCHECK="/usr/bin/mysqlcheck --defaults-file=/etc/mysql/debian.cnf"
MYCHECK_SUBJECT="WARNING: mysqlcheck has found corrupt tables"
MYCHECK_PARAMS="--all-databases --fast --silent"
MYCHECK_RCPT="root"

# The following commands should be run when the server is up but in background
# where they do not block the server start and in one shell instance so that
# they run sequentially. They are supposed not to echo anything to stdout.
# If you want to disable the check for crashed tables comment
# "check_for_crashed_tables" out.
# (There may be no output to stdout inside the background process!)
echo "Checking for corrupt, not cleanly closed and upgrade needing tables."
(
  upgrade_system_tables_if_necessary;
  check_root_accounts;
  check_for_crashed_tables;
) >&2 &

exit 0

---

