---
title: "MySQL - error #1045 cannot connect..."
date: 2008-05-02
forum: General Help
---

### Post by GCoffee on 2008-05-02
Hello all,

I am running apache2 and php under ubuntu 8.04 DESKTOP edition, anyway,

I'm trying to setup mysql, yet everytime I try to connect to it using mysql admin it says this:

'Unable to connect to server at localhost using root@localhost, check for connection errors.'

I'm using the mysql default root user, in the install I left the password field empty.

Its mySQL 5
I have reinstalled it 3 times (complete remove) first time i put a password in the dialog, second time i did and third time I didn't.

All yeilding the same result :(

Please Help Someone!

Yours sincerely,
GCoffee.

---

### Post by GCoffee on 2008-05-02
Anyone? Please?

I am trying to run a phpbb installstion but need mysql to do so. Please help!

---

### Post by Monicker on 2008-05-02
> **GCoffee said:**
> Anyone? Please?

I am trying to run a phpbb installstion but need mysql to do so. Please help!

What is the exact error you receive if you go to a terminal session and do the following?

```
mysql -u root
```

---

### Post by GCoffee on 2008-05-02
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

Error I get when i run mysql -u root

---

### Post by Monicker on 2008-05-02
> **GCoffee said:**
> ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

Error I get when i run mysql -u root


Sounds like mysqld may not even be running.

Do this:

```
sudo netstat -anltp | grep 3306
```


You should see similar the following:

```
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      4985/mysqld
```

If you don't see mysqld at all when you run that command:

```
sudo /etc/init.d/mysql start
```

---

### Post by GCoffee on 2008-05-02
df: `/var/lib/mysql/.': No such file or directory
df: no file systems processed
 * /etc/init.d/mysql: ERROR: The partition with /var/lib/mysql is too full!

Thats what I get when running the last command you suggested,

Strange because ubuntu is on a 80GB partition, and only 10gb been used..

---

### Post by Monicker on 2008-05-02
When there are problems, the mysql logs can contain quite a bit of info and consume a lot of space.


What are the results of the following commands?

```
df -h
sudo du -ch --max-depth=1 /
sudo du -ch --max-depth=1 /var/lib
```

---

### Post by GCoffee on 2008-05-02
df -h:

Filesystem            Size  Used Avail Use% Mounted on
dev/sda3              74G  3.3G   67G   5% /
varrun                251M  108K  251M   1% /var/run
varlock               251M     0  251M   0% /var/lock
udev                  251M   56K  251M   1% /dev
devshm                251M   12K  251M   1% /dev/shm
lrm                   251M   38M  214M  15% /lib/modules/2.6.24-16-generic/volatile
/dev/sda1              81G  7.6G   73G  10% /media/sda1
/dev/sda4             7.5G  3.5G  3.7G  49% /media/sda4
gvfs-fuse-daemon       74G  3.3G   67G   5% /home/joe/.gvfs
/dev/sdb1             984M  109M  875M  12% /media/joes DATA 2


sudo du -ch --max-depth=1 /:

joe@localhost:~$ sudo du -ch --max-depth=1 /
[sudo] password for joe: 
14M	/etc
280M	/lib
du: cannot access `/home/joe/.gvfs': Permission denied
171M	/home
7.4M	/root
4.0K	/opt
80K	/dev
5.2M	/bin
11G	/media
0	/sys
2.0G	/usr
4.0K	/mnt
du: cannot access `/proc/6629/task/6629/fd/4': No such file or directory
du: cannot access `/proc/6629/task/6629/fdinfo/4': No such file or directory
du: cannot access `/proc/6629/fd/4': No such file or directory
du: cannot access `/proc/6629/fdinfo/4': No such file or directory
0	/proc
6.4M	/sbin
104K	/tmp
730M	/var
16K	/lost+found
36M	/boot
4.0K	/srv
4.0K	/initrd
14G	/
14G	total

sudo du -ch --max-depth=1 /var/lib:

[sudo] password for joe: 
4.0K	/var/lib/gnome-session
12K	/var/lib/mozilla-firefox
4.0K	/var/lib/aptitude
176K	/var/lib/misc
4.0K	/var/lib/guidance-backends
8.0K	/var/lib/dovecot
8.0K	/var/lib/urandom
4.0K	/var/lib/avahi-autoipd
16K	/var/lib/locales
4.0K	/var/lib/update-manager
29M	/var/lib/apt
12K	/var/lib/ufw
8.0K	/var/lib/vim
4.0K	/var/lib/sgml-base
8.0K	/var/lib/hal
36K	/var/lib/dictionaries-common
28K	/var/lib/gdm
39M	/var/lib/dpkg
2.5M	/var/lib/mlocate
8.0K	/var/lib/logrotate
4.0K	/var/lib/apparmor
4.0K	/var/lib/PolicyKit-public
4.0K	/var/lib/initscripts
5.1M	/var/lib/python-support
16K	/var/lib/alsa
8.0K	/var/lib/PolicyKit
4.0K	/var/lib/snmp
24K	/var/lib/php5
4.0K	/var/lib/NetworkManager
3.5M	/var/lib/aspell
172K	/var/lib/ucf
52K	/var/lib/belocs
380K	/var/lib/doc-base
12K	/var/lib/initramfs-tools
8.0K	/var/lib/phpmyadmin
8.0K	/var/lib/dbus
4.0K	/var/lib/mod_bt
8.0K	/var/lib/update-notifier
24K	/var/lib/acpi-support
32K	/var/lib/xml-core
1.7M	/var/lib/defoma
4.0K	/var/lib/libuuid
24K	/var/lib/x11
4.0K	/var/lib/mysql-cluster
62M	/var/lib/gconf
12K	/var/lib/thunderbird
4.0K	/var/lib/xkb
21M	/var/lib/scrollkeeper
8.0K	/var/lib/displayconfig-gtk
8.0K	/var/lib/dhcp3
4.0K	/var/lib/synaptic
164M	/var/lib
164M	total

NOTE: joe is not my actual user name..

---

### Post by Monicker on 2008-05-02
Weird. That one error message was right, you do not have a /var/lib/mysql directory.  That is the default directory where all the database and log files are kept.  By any chance did you manually remove the mysql directory before reinstalling?


Do this:

```
sudo mkdir /var/lib/mysql
sudo chown mysql.mysql /var/lib/mysql
sudo /etc/init.d/mysql start
```


Then try to connect again from the terminal.

---

### Post by GCoffee on 2008-05-02
All went well, then this occured:  * Starting MySQL database server mysqld                                [fail]

---

### Post by Monicker on 2008-05-02
> **GCoffee said:**
> All went well, then this occured:  * Starting MySQL database server mysqld                                [fail]

Check /var/log/mysql.log for the cause of the error.  I'm not sure what you did previously, but you may be better off starting completing over, and making sure that all the config files are purged. It looks like you reinstalled after deleting the /var/lib/mysql folder manually.  If the config files were still in place the install may have assumed it did not need to create that directory.  I don't know what else that may have borked.

---

### Post by GCoffee on 2008-05-02
When you say starting over what do you mean?

---

### Post by Monicker on 2008-05-02
> **GCoffee said:**
> When you say starting over what do you mean?

A fresh install, without leaving crud from an improper removal of mysql.


```
sudo apt-get --purge remove mysql-server
sudo rm -rf /etc/mysql
sudo rm -rf /var/lib/mysql
```


Then reinstall it.

---

### Post by GCoffee on 2008-05-02
I will do so tommorow, I have completely removed it,

I will reinstall tommorow. 

I'm shattered.. ;)

---

### Post by jimv on 2008-05-02
Try

sudo apt-get remove --purge mysql*
sudo apt-get install mysql-server

---

### Post by Monicker on 2008-05-02
> **jimv said:**
> Try

sudo apt-get remove --purge mysql*
sudo apt-get install mysql-server


The down side to using msyql* is that it will also remove the mysql client and admin tools, which are separate from the mysql-server package.

---

### Post by GCoffee on 2008-05-03
bump

---

### Post by davehimself on 2008-05-09
I'm having the exact same issue with mysql on 8.04. I don't think there's any sort of permission issue. Mysql starts just fine with: /etc/init.d/mysql start. The run level symlinks (/etc/rc.d) *seem* to be correct, however I'm no guru in this area.

Anyone else know what's going on here?

---

### Post by Monicker on 2008-05-09
> **davehimself said:**
> I'm having the exact same issue with mysql on 8.04. I don't think there's any sort of permission issue. Mysql starts just fine with: /etc/init.d/mysql start. The run level symlinks (/etc/rc.d) *seem* to be correct, however I'm no guru in this area.

Anyone else know what's going on here?

Did you follow the troubleshooting steps mentioned previously in this thread???

If so, what were the results?

---

