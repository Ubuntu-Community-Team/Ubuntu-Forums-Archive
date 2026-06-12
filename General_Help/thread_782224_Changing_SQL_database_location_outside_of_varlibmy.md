---
title: "Changing SQL database location outside of /var/lib/mysql results in permission error"
date: 2008-05-04
forum: General Help
---

### Post by mobodo on 2008-05-04
I'm trying to change the datadir for MySQL, but always end up with permission errors no matter that directory I use, if it is different than /var/lib/mysql.  The most simple case of the problem is the following:

rm -rf /var/lib/mysql
mysql_install_db --no-defaults --datadir=/var/lib/mysql
 -> works

rm -rf /var/lib/mysql-abc
mysql_install_db --no-defaults --datadir=/var/lib/mysql-abc
 -> fails with 
    080504 19:59:52 [Warning] Can't create test file /var/lib/mysql-abc/maya.lower-test
    ERROR: 1005  Can't create table 'db' (errno: 13)

rm -rf /var/lib/mysql/subdir
mysql_install_db --no-defaults --datadir=/var/lib/mysql/subdir
 -> works

The fact that I can change the datadir to a subdir but not to another directory suggests that mysql performs a chroot /var/lib/mysql at some point - but I don't know where/why

For these cases, I have removed the /etc/mysql/my.conf

I am root when doing all this, and I have just installed mysql with "apt-get install mysql-client mysql-server"

Anyone has an idea?

---

### Post by JacobSteelsmith on 2008-05-04
Looks like /var/lib/mysql is owned by the mysql user and the group is set to mysql as well. 

$ sudo chown -R mysql /var/lib/mysql-abc
$ sudo chgrp -R mysql /var/lib/mysql-abc
$ sudo chmod 755 /var/lib/mysql-abc

---

### Post by mobodo on 2008-05-04
If you look in the commands I gave above, you'll notice that I rm -rf the directory before I create the database, /var/lib/mysql-abc and /var/lib/mysql do not exist prior to the mysql_install_db command - so permissions can't be an issue here.

---

### Post by vik4 on 2008-05-07
I have much the same issue. I have /var/lib symlinked to a different disk, and it creates the same issues:

```
$ ls -ld /var/lib/mysql
drwxr-xr-x 3 mysql mysql 4096 2008-05-07 16:09 /var/lib/mysql

```

The errors from syslog are:
```
May  7 16:01:29 vcke-gl-linux mysqld_safe[5927]: started
May  7 16:01:29 vcke-gl-linux kernel: [   77.275620] audit(1210140089.689:2): type=1503 operation="inode_create" requested_mask="w::" denied_mask="w::" name="/mnt/fastdata/var/lib/mysql/vcke-gl-linux.lower-test" pid=5929 profile="/usr/sbin/mysqld" namespace="default"
May  7 16:01:29 vcke-gl-linux mysqld[5931]: 080507 16:01:29 [Warning] Can't create test file /var/lib/mysql/vcke-gl-linux.lower-test
May  7 16:01:29 vcke-gl-linux kernel: [   77.277266] audit(1210140089.689:3): type=1503 operation="inode_create" requested_mask="w::" denied_mask="w::" name="/mnt/fastdata/var/lib/mysql/vcke-gl-linux.lower-test" pid=5929 profile="/usr/sbin/mysqld" namespace="default"
May  7 16:01:29 vcke-gl-linux mysqld[5931]: 080507 16:01:29 [Warning] Can't create test file /var/lib/mysql/vcke-gl-linux.lower-test
May  7 16:01:29 vcke-gl-linux kernel: [   77.398269] audit(1210140089.809:4): type=1503 operation="inode_permission" requested_mask="rw::" denied_mask="rw::" name="/mnt/fastdata/var/lib/mysql/ibdata1" pid=5929 profile="/usr/sbin/mysqld" namespace="default"
May  7 16:01:29 vcke-gl-linux mysqld[5931]: 080507 16:01:29  InnoDB: Operating system error number 13 in a file operation.
May  7 16:01:29 vcke-gl-linux mysqld[5931]: InnoDB: The error means mysqld does not have the access rights to
May  7 16:01:29 vcke-gl-linux mysqld[5931]: InnoDB: the directory.
May  7 16:01:29 vcke-gl-linux mysqld[5931]: InnoDB: File name ./ibdata1
May  7 16:01:29 vcke-gl-linux mysqld[5931]: InnoDB: File operation call: 'open'.
May  7 16:01:29 vcke-gl-linux mysqld[5931]: InnoDB: Cannot continue operation.
May  7 16:01:29 vcke-gl-linux mysqld_safe[5937]: ended
```

Could it be that mysqld is running as another user?

I couldn't successfully su to mysql to try it from the shell.

vik

---

### Post by nijaba on 2008-05-07
Hello,

There is now an apparmor profile enabled by default for mysql that will prevent mysql to access non standard area of the file system.  Putting the mysql profile in complain mode using "sudo aa-complain" as described in the [server guide]("https://help.ubuntu.com/8.04/serverguide/C/apparmor.html") should show you this in the logs.

To fix this, you will need to add /mnt/fastdata/var/lib/mysql (or whatever non standard path you are using) to the list of authorized paths in the apparmor mysql profile you will find in /etc/apparmor.d/.

Hope this helps,
Nick

---

### Post by excalq on 2010-06-03
I'm running Ubuntu 10.04, MySQL 5.0.83.
I was following this great tutorial for installing multiple instances of mysql on the same server, and ran into this issue.

I was able to resolve it by running:
```
vim /etc/apparmor.d/usr.sbin.mysqld
```

And then edited the block of mysql paths to appear as follows:
```

  /etc/mysql/*.pem r,
  /etc/mysql/conf.d/ r,
  /etc/mysql/conf.d/* r,
  /etc/mysql/my.cnf r,
  /etc/mysql2/*.pem r,
  /etc/mysql2/conf.d/ r,
  /etc/mysql2/conf.d/* r,
  /etc/mysql2/my.cnf r,
  /usr/sbin/mysqld mr,
  /usr/share/mysql/** r,
  /usr/share/mysql2/** r,
  /var/log/mysql.log rw,
  /var/log/mysql.err rw,
  /var/lib/mysql/ r,
  /var/lib/mysql/** rwk,
  /var/log/mysql/ r,
  /var/log/mysql/* rw,
  /var/log/mysql2.log rw,
  /var/log/mysql2.err rw,
  /var/lib/mysql2/ r,
  /var/lib/mysql2/** rwk,
  /var/log/mysql2/ r,
  /var/log/mysql2/* rw,
  /var/run/mysqld/mysqld*.pid w,
  /var/run/mysqld/mysqld*.sock w,

```

---

### Post by ddoxey on 2010-11-06
Same problem here. I needed to get my mysql datadir on a different partition to avoid using up all the drive space there.

I moved the **mysql** directory from **/var/lib** to **/home**. 

I was beating my head against the wall until I updated **/etc/apparmor.d/usr.sbin.mysqld**.

Thanks excalq!

---

### Post by dpranker on 2011-04-29
Hey, I just found this thread and it sounds like exactly what is happening in my situation, but in my case changing the apparmor profile at /etc/apparmor.d/usr.sbin.mysqld did not fix the error. 

Here is the error it is giving me

In addition to this error, no log files are created even though it says to check the logs

```
demo@ubuntu:/media/FreeAgentDisk$ mysql_install_db --ldata=data
Installing MySQL system tables...
110429 14:34:42 [Warning] Can't create test file /usr/data/ubuntu.lower-test
110429 14:34:42 [Warning] Can't create test file /usr/data/ubuntu.lower-test
/usr/sbin/mysqld: Can't change dir to '/usr/data/' (Errcode: 2)
110429 14:34:42 [ERROR] Aborting

110429 14:34:42 [Note] /usr/sbin/mysqld: Shutdown complete

```

---

### Post by jrssystemsnet on 2012-06-30
A year and some change later, for anybody else with this problem...

Just editing the profile in /etc/apparmor.d alone won't do the trick.  You must then **reload** the profile you've edited.

```
you@box:~$ sudo apt-get install apparmor-utils
you@box:~$ sudo apparmor_parser -a < /etc/apparmor.d/usr.sbin.mysqld
```

THEN you can try restarting mysql again, and you should have joy.  (Alternately, of course, you could have gone into Windows Mode[tm] and rebooted the machine.)

---

### Post by oldos2er on 2012-06-30
Old thread closed.

---

