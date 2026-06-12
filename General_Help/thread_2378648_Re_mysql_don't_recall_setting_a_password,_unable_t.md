---
title: "Re: mysql: don't recall setting a password, unable to reset password or reinstall"
date: 2017-11-25
forum: General Help
---

### Post by freeflyjohn on 2017-11-25
I am getting into a right mess with mysql... I am trying to install Nextcloud (using this guide [https://www.youtube.com/watch?v=nXr_muYB6xI](https://www.youtube.com/watch?v=nXr_muYB6xI)) but when I run "mysql_secure_installation" it asks me for a password.

I don't even remember installing mysql before, yet alone setting a password for it.  I have tried my root password but mysql didn't accept it.

```

root@HomeServer:~# mysql_secure_installation

Securing the MySQL server deployment.

Enter password for user root: 
[COLOR=#ff0000]Error: Access denied for user 'root'@'localhost' (using password: YES)[/COLOR]
root@HomeServer:~# 

```

I have tried resetting my password using this guide [https://help.ubuntu.com/community/MysqlPasswordReset](https://help.ubuntu.com/community/MysqlPasswordReset) but it fails when I run "mysql -u root":

```

root@HomeServer:~# sudo /etc/init.d/mysql stop
[ ok ] Stopping mysql (via systemctl): mysql.service.
root@HomeServer:~#  sudo /usr/sbin/mysqld --skip-grant-tables --skip-networking &
[1] 4628
root@HomeServer:~# mysql -u root
[COLOR=#ff0000]ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)[/COLOR]
[1]+  Exit 1                  sudo /usr/sbin/mysqld --skip-grant-tables --skip-networking
root@HomeServer:~# 

```

I have tried to remove and reinstall mysql but this fails at "mysqladmin -u root password your-new-password":

```
root@HomeServer:~# sudo apt-get --purge remove mysql-server mysql-common mysql-client
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  mysql-client-core-5.7 mysql-server-core-5.7
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED
  mysql-client* mysql-client-5.7* mysql-common* mysql-server* mysql-server-5.7*
0 to upgrade, 0 to newly install, 5 to remove and 0 not to upgrade.
After this operation, 82.8 MB disk space will be freed.
Do you want to continue? [Y/n] y
dpkg: warning: files list file for package 'oracle-java7-installer' missing; assuming package has no files currently installed
(Reading database ... 226261 files and directories currently installed.)
Removing mysql-client (5.7.20-0ubuntu0.16.04.1) ...
Removing mysql-server (5.7.20-0ubuntu0.16.04.1) ...
Removing mysql-server-5.7 (5.7.20-0ubuntu0.16.04.1) ...
update-alternatives: using /etc/mysql/my.cnf.fallback to provide /etc/mysql/my.cnf (my.cnf) in auto mode
Purging configuration files for mysql-server-5.7 (5.7.20-0ubuntu0.16.04.1) ...
insserv: warning: script 'K01psad' missing LSB tags and overrides
insserv: warning: script 'psad' missing LSB tags and overrides
Removing mysql-client-5.7 (5.7.20-0ubuntu0.16.04.1) ...
Removing mysql-common (5.7.20-0ubuntu0.16.04.1) ...
Purging configuration files for mysql-common (5.7.20-0ubuntu0.16.04.1) ...
dpkg: warning: while removing mysql-common, directory '/etc/mysql' not empty so not removed
Processing triggers for man-db (2.7.5-1) ...

root@HomeServer:~# sudo apt-get install mysql-server mysql-common mysql-client
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  mysql-client-5.7 mysql-server-5.7
Suggested packages:
  mailx tinyca
The following NEW packages will be installed
  mysql-client mysql-client-5.7 mysql-common mysql-server mysql-server-5.7
0 to upgrade, 5 to newly install, 0 to remove and 0 not to upgrade.
Need to get 0 B/4,418 kB of archives.
After this operation, 82.8 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Preconfiguring packages ...
Selecting previously unselected package mysql-common.
dpkg: warning: files list file for package 'oracle-java7-installer' missing; assuming package has no files currently installed
(Reading database ... 226121 files and directories currently installed.)
Preparing to unpack .../mysql-common_5.7.20-0ubuntu0.16.04.1_all.deb ...
Unpacking mysql-common (5.7.20-0ubuntu0.16.04.1) ...
Selecting previously unselected package mysql-client-5.7.
Preparing to unpack .../mysql-client-5.7_5.7.20-0ubuntu0.16.04.1_amd64.deb ...
Unpacking mysql-client-5.7 (5.7.20-0ubuntu0.16.04.1) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up mysql-common (5.7.20-0ubuntu0.16.04.1) ...
update-alternatives: using /etc/mysql/my.cnf.fallback to provide /etc/mysql/my.cnf (my.cnf) in auto mode
Selecting previously unselected package mysql-server-5.7.
dpkg: warning: files list file for package 'oracle-java7-installer' missing; assuming package has no files currently installed
(Reading database ... 226169 files and directories currently installed.)
Preparing to unpack .../mysql-server-5.7_5.7.20-0ubuntu0.16.04.1_amd64.deb ...
Unpacking mysql-server-5.7 (5.7.20-0ubuntu0.16.04.1) ...
Selecting previously unselected package mysql-client.
Preparing to unpack .../mysql-client_5.7.20-0ubuntu0.16.04.1_all.deb ...
Unpacking mysql-client (5.7.20-0ubuntu0.16.04.1) ...
Selecting previously unselected package mysql-server.
Preparing to unpack .../mysql-server_5.7.20-0ubuntu0.16.04.1_all.deb ...
Unpacking mysql-server (5.7.20-0ubuntu0.16.04.1) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for systemd (229-4ubuntu21) ...
Processing triggers for ureadahead (0.100.0-19) ...
ureadahead will be reprofiled on next reboot
Setting up mysql-client-5.7 (5.7.20-0ubuntu0.16.04.1) ...
Setting up mysql-server-5.7 (5.7.20-0ubuntu0.16.04.1) ...
update-alternatives: using /etc/mysql/mysql.cnf to provide /etc/mysql/my.cnf (my.cnf) in auto mode
Renaming removed key_buffer and myisam-recover options (if present)
insserv: warning: script 'K01psad' missing LSB tags and overrides
insserv: warning: script 'psad' missing LSB tags and overrides
Checking if update is needed.
This installation of MySQL is already upgraded to 5.7.20, use --force if you still need to run mysql_upgrade
Setting up mysql-client (5.7.20-0ubuntu0.16.04.1) ...
Setting up mysql-server (5.7.20-0ubuntu0.16.04.1) ...
Processing triggers for systemd (229-4ubuntu21) ...
Processing triggers for ureadahead (0.100.0-19) ...

root@HomeServer:~# mysqladmin -u root password dummy
[COLOR=#ff0000]mysqladmin: connect to server at 'localhost' failed[/COLOR]
[COLOR=#ff0000]error: 'Access denied for user 'root'@'localhost' (using password: NO)'[/COLOR]
root@HomeServer:~# 

```

I have tried to reconfigure but when I run "mysql_secure_installation" it still asks for a password:

```
root@HomeServer:~# sudo dpkg-reconfigure mysql-server-5.7
insserv: warning: script 'K01psad' missing LSB tags and overrides
insserv: warning: script 'psad' missing LSB tags and overrides
Checking if update is needed.
This installation of MySQL is already upgraded to 5.7.20, use --force if you still need to run mysql_upgrade
root@HomeServer:~# 

```

I have also tried the following to remove and reinstall mysql but when I run "mysql_secure_installation" it still asks for a password:

```

root@HomeServer:~# sudo apt-get purge mysql*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'mysqltcl' for glob 'mysql*'
Note, selecting 'mysql-mmm-agent' for glob 'mysql*'
Note, selecting 'mysql-workbench' for glob 'mysql*'
Note, selecting 'mysql-client-5.5' for glob 'mysql*'
Note, selecting 'mysql-client-5.6' for glob 'mysql*'
Note, selecting 'mysql-client-5.7' for glob 'mysql*'
Note, selecting 'mysql-mmm-tools' for glob 'mysql*'
Note, selecting 'mysql-common-5.6' for glob 'mysql*'
Note, selecting 'mysql-server-5.0' for glob 'mysql*'
Note, selecting 'mysql-server-5.1' for glob 'mysql*'
Note, selecting 'mysql-server-5.5' for glob 'mysql*'
Note, selecting 'mysql-server-5.6' for glob 'mysql*'
Note, selecting 'mysql-server-5.7' for glob 'mysql*'
Note, selecting 'mysql-utilities' for glob 'mysql*'
Note, selecting 'mysql-testsuite' for glob 'mysql*'
Note, selecting 'mysql-mmm-common' for glob 'mysql*'
Note, selecting 'mysql-server' for glob 'mysql*'
Note, selecting 'mysql-client' for glob 'mysql*'
Note, selecting 'mysql-sandbox' for glob 'mysql*'
Note, selecting 'mysql-client-core-5.5' for glob 'mysql*'
Note, selecting 'mysql-client-core-5.6' for glob 'mysql*'
Note, selecting 'mysql-client-core-5.7' for glob 'mysql*'
Note, selecting 'mysql-testsuite-5.5' for glob 'mysql*'
Note, selecting 'mysql-testsuite-5.6' for glob 'mysql*'
Note, selecting 'mysql-testsuite-5.7' for glob 'mysql*'
Note, selecting 'mysql-common' for glob 'mysql*'
Note, selecting 'mysql-mmm-monitor' for glob 'mysql*'
Note, selecting 'mysqltuner' for glob 'mysql*'
Note, selecting 'mysql-workbench-data' for glob 'mysql*'
Note, selecting 'mysql-server-core-5.1' for glob 'mysql*'
Note, selecting 'mysql-server-core-5.5' for glob 'mysql*'
Note, selecting 'mysql-server-core-5.6' for glob 'mysql*'
Note, selecting 'mysql-server-core-5.7' for glob 'mysql*'
Note, selecting 'mysql-source-5.7' for glob 'mysql*'
Package 'mysql-client-5.5' is not installed, so not removed
Package 'mysql-client-5.6' is not installed, so not removed
Package 'mysql-server-core-5.6' is not installed, so not removed
Package 'mysql-client-core-5.5' is not installed, so not removed
Package 'mysql-client-core-5.6' is not installed, so not removed
Note, selecting 'mysql-common' instead of 'mysql-common-5.6'
Package 'mysql-server-5.5' is not installed, so not removed
Package 'mysql-server-5.6' is not installed, so not removed
Package 'mysql-server-core-5.5' is not installed, so not removed
Package 'mysql-testsuite-5.5' is not installed, so not removed
Package 'mysql-testsuite-5.6' is not installed, so not removed
Package 'mysql-server-5.0' is not installed, so not removed
Package 'mysql-server-5.1' is not installed, so not removed
Package 'mysql-server-core-5.1' is not installed, so not removed
Package 'mysql-mmm-agent' is not installed, so not removed
Package 'mysql-mmm-common' is not installed, so not removed
Package 'mysql-mmm-monitor' is not installed, so not removed
Package 'mysql-mmm-tools' is not installed, so not removed
Package 'mysql-sandbox' is not installed, so not removed
Package 'mysql-utilities' is not installed, so not removed
Package 'mysql-workbench' is not installed, so not removed
Package 'mysql-workbench-data' is not installed, so not removed
Package 'mysqltcl' is not installed, so not removed
Package 'mysqltuner' is not installed, so not removed
Package 'mysql-source-5.7' is not installed, so not removed
Package 'mysql-testsuite' is not installed, so not removed
Package 'mysql-testsuite-5.7' is not installed, so not removed
The following packages will be REMOVED
  mysql-client* mysql-client-5.7* mysql-client-core-5.7* mysql-common* mysql-server* mysql-server-5.7*
  mysql-server-core-5.7*
0 to upgrade, 0 to newly install, 7 to remove and 0 not to upgrade.
After this operation, 160 MB disk space will be freed.
Do you want to continue? [Y/n] y
dpkg: warning: files list file for package 'oracle-java7-installer' missing; assuming package has no files currently installed
(Reading database ... 226261 files and directories currently installed.)
Removing mysql-client (5.7.20-0ubuntu0.16.04.1) ...
Removing mysql-server (5.7.20-0ubuntu0.16.04.1) ...
Removing mysql-server-5.7 (5.7.20-0ubuntu0.16.04.1) ...
update-alternatives: using /etc/mysql/my.cnf.fallback to provide /etc/mysql/my.cnf (my.cnf) in auto mode
Purging configuration files for mysql-server-5.7 (5.7.20-0ubuntu0.16.04.1) ...
insserv: warning: script 'K01psad' missing LSB tags and overrides
insserv: warning: script 'psad' missing LSB tags and overrides
Removing mysql-client-5.7 (5.7.20-0ubuntu0.16.04.1) ...
Removing mysql-client-core-5.7 (5.7.20-0ubuntu0.16.04.1) ...
Removing mysql-common (5.7.20-0ubuntu0.16.04.1) ...
Purging configuration files for mysql-common (5.7.20-0ubuntu0.16.04.1) ...
dpkg: warning: while removing mysql-common, directory '/etc/mysql' not empty so not removed
Removing mysql-server-core-5.7 (5.7.20-0ubuntu0.16.04.1) ...
Processing triggers for man-db (2.7.5-1) ...

root@HomeServer:~# sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
root@HomeServer:~# 
root@HomeServer:~# sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
root@HomeServer:~# sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.

root@HomeServer:~# sudo apt-get install mysql-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  mysql-client-5.7 mysql-client-core-5.7 mysql-common mysql-server-5.7 mysql-server-core-5.7
Suggested packages:
  mailx tinyca
The following NEW packages will be installed
  mysql-client-5.7 mysql-client-core-5.7 mysql-common mysql-server mysql-server-5.7 mysql-server-core-5.7
0 to upgrade, 6 to newly install, 0 to remove and 0 not to upgrade.
Need to get 0 B/18.4 MB of archives.
After this operation, 160 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Preconfiguring packages ...
Selecting previously unselected package mysql-common.
dpkg: warning: files list file for package 'oracle-java7-installer' missing; assuming package has no files currently installed
(Reading database ... 226013 files and directories currently installed.)
Preparing to unpack .../mysql-common_5.7.20-0ubuntu0.16.04.1_all.deb ...
Unpacking mysql-common (5.7.20-0ubuntu0.16.04.1) ...
Selecting previously unselected package mysql-client-core-5.7.
Preparing to unpack .../mysql-client-core-5.7_5.7.20-0ubuntu0.16.04.1_amd64.deb ...
Unpacking mysql-client-core-5.7 (5.7.20-0ubuntu0.16.04.1) ...
Selecting previously unselected package mysql-client-5.7.
Preparing to unpack .../mysql-client-5.7_5.7.20-0ubuntu0.16.04.1_amd64.deb ...
Unpacking mysql-client-5.7 (5.7.20-0ubuntu0.16.04.1) ...
Selecting previously unselected package mysql-server-core-5.7.
Preparing to unpack .../mysql-server-core-5.7_5.7.20-0ubuntu0.16.04.1_amd64.deb ...
Unpacking mysql-server-core-5.7 (5.7.20-0ubuntu0.16.04.1) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up mysql-common (5.7.20-0ubuntu0.16.04.1) ...
update-alternatives: using /etc/mysql/my.cnf.fallback to provide /etc/mysql/my.cnf (my.cnf) in auto mode
Selecting previously unselected package mysql-server-5.7.
dpkg: warning: files list file for package 'oracle-java7-installer' missing; assuming package has no files currently installed
(Reading database ... 226169 files and directories currently installed.)
Preparing to unpack .../mysql-server-5.7_5.7.20-0ubuntu0.16.04.1_amd64.deb ...
Unpacking mysql-server-5.7 (5.7.20-0ubuntu0.16.04.1) ...
Selecting previously unselected package mysql-server.
Preparing to unpack .../mysql-server_5.7.20-0ubuntu0.16.04.1_all.deb ...
Unpacking mysql-server (5.7.20-0ubuntu0.16.04.1) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for systemd (229-4ubuntu21) ...
Processing triggers for ureadahead (0.100.0-19) ...
Setting up mysql-client-core-5.7 (5.7.20-0ubuntu0.16.04.1) ...
Setting up mysql-client-5.7 (5.7.20-0ubuntu0.16.04.1) ...
Setting up mysql-server-core-5.7 (5.7.20-0ubuntu0.16.04.1) ...
Setting up mysql-server-5.7 (5.7.20-0ubuntu0.16.04.1) ...
update-alternatives: using /etc/mysql/mysql.cnf to provide /etc/mysql/my.cnf (my.cnf) in auto mode
Renaming removed key_buffer and myisam-recover options (if present)
insserv: warning: script 'K01psad' missing LSB tags and overrides
insserv: warning: script 'psad' missing LSB tags and overrides
Checking if update is needed.
This installation of MySQL is already upgraded to 5.7.20, use --force if you still need to run mysql_upgrade
Setting up mysql-server (5.7.20-0ubuntu0.16.04.1) ...
Processing triggers for systemd (229-4ubuntu21) ...
Processing triggers for ureadahead (0.100.0-19) ...

```

I don't even know what mysql is used for (is it a database?) so I don't know if it was being used by other programs prior to installing Nextcloud. 

I hope I haven’t broken other programs by trying to reconfigure and reinstall mysql ?

When I installed Ubuntu onto my server, I think I selected LAMP so would mysql have been installed as part of the LAMP installation ?

Other things I have installed are:


[LIST]
[*]SSH
[*]Netatalk (AFP?) & Samba (SMB?) so that I can access my server from my Mac and use Time Machine and Screen Sharing
[*]Plex Media Server
[*]fail2ban
[*]gufw
[*]ddclient (for use with Dynu free dynamic DNS service provider)
[*]dconf-tools
[*]sendmail (didn't get working so left it)
[*]Minecraft server (which doesnt seem to work and Java caused all sorts of headaches)
[/LIST]

(error log attached in case that helps)

---

### Post by freeflyjohn on 2017-11-25
Looking back at this, its asking for the password for root@local host (not the password for mysql).

I googled for root password and it says:

"By default root account is locked under Ubuntu Linux. Therefore, you cannot login as root or use 'su -' command to become a superuser. To run all administrative command use sudo command. sudo allows a permitted user to execute a command as the superuser or another user"
[COLOR=#111111][FONT=Roboto]
[/FONT][/COLOR]The Nextcloud installation instructions are below and the first step is to login as root (which works), but root is suppose to be locked and you are not suppose to be able to login as root or use 'su -' ??
[COLOR=#111111][FONT=Roboto]
[/FONT][/COLOR]Its step 6 I am having the problems with (mysql_secure_installation).


[FONT=courier new]Step 1: Login in Root
#su -
password:


Step 2: Update the System
#apt-get update


Step 3: Install LAMP Server + PHP Extension
#apt-get install lamp-server^
#apt-get install libapache2-mod-php7.0 php7.0-mbstring php7.0-curl php7.0-zip php7.0-gd php7.0-mysql php7.0-mcrypt
#apt-get install php-xml


Step 4: Download NextCloud
#wget [https://download.nextcloud.com/server/releases/nextcloud-12.0.3.zip]("https://download.nextcloud.com/server/releases/nextcloud-9.0.52.zip")


Step 5: Unzip + Permissions
#unzip nextcloud-12.0.3.zip
#mv nextcloud /var/www/html
#chown -R www-data:www-data /var/www/html/nextcloud


Step 6: Configuring MariaDB for NextCloud
#mysql_secure_installation
Type Y for all except root password


CREATE DATABASE nextcloud;
GRANT ALL PRIVILEGES ON nextcloud.* TO 'nextcloud'@'localhost' IDENTIFIED BY 'anand';
FLUSH PRIVILEGES;
exit;


Step 7: Disable MariaDB binary logging


#nano /etc/mysql/my.cnf


Add the following three lines at the end:


log-bin        = /var/log/mysql/mariadb-bin
log-bin-index  = /var/log/mysql/mariadb-bin.index
binlog_format  = mixed


Step 8: Configuring Apache Web Server
#sudo a2enmod rewrite
#touch /etc/apache2/sites-available/nextcloud.conf
#ln -s /etc/apache2/sites-available/nextcloud.conf /etc/apache2/sites-enabled/nextcloud.conf
#nano /etc/apache2/sites-available/nextcloud.conf


Add the following:


<VirtualHost *:80>
ServerAdmin admin@ubuntu
DocumentRoot "/var/www/html/nextcloud/"
ServerName ipaddress
ServerAlias ubuntu
<Directory "/var/www/html/nextcloud/">
Options FollowSymLinks
AllowOverride All
Order allow,deny
allow from all
</Directory>
ErrorLog /var/log/apache2/your-domain.com-error_log
CustomLog /var/log/apache2/your-domain.com-access_log common
</VirtualHost>


Restart the Apache web server
#systemctl restart apache2.service&#65279;[/FONT]


I went to the Nextcloud website and read the installation instructions...  [https://docs.nextcloud.com/server/12/admin_manual/installation/source_installation.html#snaps-label](https://docs.nextcloud.com/server/12/admin_manual/installation/source_installation.html#snaps-label)

I ran the following command:

```

sudo snap install nextcloud

```

But then what do I do, the instructions after that are for manual installation ?  I am SO CONFUSED !

---

