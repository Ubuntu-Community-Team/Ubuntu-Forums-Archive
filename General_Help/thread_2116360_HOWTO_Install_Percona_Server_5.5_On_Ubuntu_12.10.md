---
title: "HOWTO: Install Percona Server 5.5 On Ubuntu 12.10"
date: 2013-02-15
forum: General Help
---

### Post by linuxsyst on 2013-02-15
**1. Prepare**
[[COLOR="RoyalBlue"]_Percona Server_[/COLOR]]("http://www.percona.com/software/percona-server")
Because we will run all the steps from this tutorial with root privileges, we can either prepend all commands in this tutorial with the string sudo, or we become root right now by typing ```
sudo -s
```

**2. Configure apt**
 Percona provides an apt repository for Debian and Ubuntu, which makes Percona Server very easy to install. First, import Percona's key: ```
gpg --keyserver hkp://keys.gnupg.net --recv-keys 1C4CBDCDCD2EFD2A
```
```
gpg -a --export CD2EFD2A | apt-key add -
```
Next open _/etc/apt/sources.list..._
```
vi /etc/apt/sources.list
```
And add the following lines in it:
```
deb http://repo.percona.com/apt quantal main
deb-src http://repo.percona.com/apt quantal main
```
Next we need to pin Percona's package so that they don't get overwritten by upgrades from the Ubuntu repositories:
```
vi /etc/apt/preferences.d/00percona.pref
```
```
Package: *
Pin: release o=Percona Development Team
Pin-Priority: 1001
```
Then update the package database:
```
apt-get update
```
**3. Install Percona Server**
Percona Server can now be installed as follows:
```
apt-get install percona-server-server-5.5 percona-server-client-5.5
```
New password for the Percona Server "root" user: <-- yourrootsqlpassword
Repeat password for the Percona Server "root" user: <-- yourrootsqlpassword
_________________________________________________

That's it already. To check your MySQL version, log into the MySQL shell:
```
mysql -u root -p
```
> root@blackhat:~# mysql -u root -p
Enter password:
Welcome to the MySQL monitor. Commands end with ; or \g.
Your MySQL connection id is 38
Server version: 5.5.28-29.2 Percona Server (GPL), Release 29.2

Copyright (c) 2000, 2012, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> quit
Bye
root@blackhat:~# 

---

