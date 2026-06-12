---
title: "Package manager broken"
date: 2014-02-07
forum: General Help
---

### Post by Carol_Milner on 2014-02-07
I have a message - top right 'No entry' sign and text that there is an error that BrokenCount>0.
I've done apt-get -f install to fix it, but that ends with
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)

This came about trying to install MySQL server, and the result is that the installation is incomplete and I can't start the server (but installation works fine on another Ubuntu 12.04 machine)

How can I clean up the package manager?

---

### Post by jeanjd63 on 2014-02-07
Hello

You can try :

[SIZE=3][FONT=arial black][SIZE=2]**[COLOR=#333333]sudo rm /var/lib/[/COLOR][COLOR=#333333]apt/lists/[/COLOR][COLOR=#333333]lock[/COLOR]**
[/SIZE][COLOR=#333333][SIZE=2]sudo rm /var/lib/dpkg/lock
[/SIZE][/COLOR][/FONT][/SIZE][COLOR=#333333][FONT=arial black]sudo apt-get  install  -f[/FONT][/COLOR][SIZE=3][FONT=arial black][COLOR=#333333][SIZE=2][/SIZE][/COLOR][/FONT][/SIZE]

---

### Post by Carol_Milner on 2014-02-08
Thanks but didn't work
The Ubuntu Software Centre tells me teh server is installed, but it won't start. Neither can I remove it - the package manager is broken.
It tells me the package catalogue must be repaired, aoffers to do so, but then goes into an endless loop.

---

### Post by jeanjd63 on 2014-02-08
Could you give the returns (complete) for :
**sudo  apt-get  install  -f**

---

### Post by Carol_Milner on 2014-02-08
I've had the problem with samba for some time - I think its a know issue:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gir1.2-ubuntuoneui-3.0 libcommons-net2-java eclipse-cdt-jni
  language-pack-kde-en kde-l10n-engb libubuntuoneui-3.0-1
  thunderbird-globalmenu libcmis-0.2-0 libreoffice-emailmerge
  language-pack-kde-en-base
Use 'apt-get autoremove' to remove them.
0 to upgrade, 0 to newly install, 0 to remove and 79 not to upgrade.
4 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up mysql-common (5.5.35-0ubuntu0.12.04.2) ...
Setting up libmysqlclient18 (5.5.35-0ubuntu0.12.04.2) ...
Setting up libdbd-mysql-perl (4.020-1build2) ...
Setting up samba4 (4.0.0~alpha18.dfsg1-4ubuntu2) ...
Unknown parameter encountered: "max log size"
Ignoring unknown parameter "max log size"
Unknown parameter encountered: "syslog"
Ignoring unknown parameter "syslog"
Unknown parameter encountered: "unix password sync"
Ignoring unknown parameter "unix password sync"
Unknown parameter encountered: "passwd program"
Ignoring unknown parameter "passwd program"
Unknown parameter encountered: "pam password change"
Ignoring unknown parameter "pam password change"
Unknown parameter encountered: "map to guest"
Ignoring unknown parameter "map to guest"
Unknown parameter encountered: "usershare allow guests"
Ignoring unknown parameter "usershare allow guests"
Unknown parameter encountered: "username map"
Ignoring unknown parameter "username map"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
ERROR: Invalid smb.conf
Unknown parameter encountered: "max log size"
Ignoring unknown parameter "max log size"
Unknown parameter encountered: "syslog"
Ignoring unknown parameter "syslog"
Unknown parameter encountered: "unix password sync"
Ignoring unknown parameter "unix password sync"
Unknown parameter encountered: "passwd program"
Ignoring unknown parameter "passwd program"
Unknown parameter encountered: "pam password change"
Ignoring unknown parameter "pam password change"
Unknown parameter encountered: "map to guest"
Ignoring unknown parameter "map to guest"
Unknown parameter encountered: "usershare allow guests"
Ignoring unknown parameter "usershare allow guests"
Unknown parameter encountered: "username map"
Ignoring unknown parameter "username map"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
ERROR: Invalid smb.conf
/var/lib/dpkg/info/samba4.postinst: 14: /var/lib/dpkg/info/samba4.postinst: /usr/share/samba/setoption.pl: not found
dpkg: error processing samba4 (--configure):
 subprocess installed post-installation script returned error exit status 127
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 samba4
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by jeanjd63 on 2014-02-08
You have a pb with you file /etc/samba/smb.conf
could you post it (between balises Code please : the symbol # in top of  this window "Go Advanced" )?
[B]cat /etc/samba/smb.conf
[/B]and do a :[B]
testparm 
[/B]to test the validity of this file

---

### Post by Elfy on 2014-02-08
Try to remove samba4 

```
sudo apt-get purge samba4
```

If that fails which I think it will

```
sudo dpkg --remove --force-remove-reinstreq samba4
```

There's possibly a failed smb.conf file - move that, if it says there is no file to move, then ignore.

```
sudo mv /etc/samba/smb.conf /etc/samba/smb.conf.bak
```

Reinstall samba - but not samba4

```
sudo apt-get install samba
```

Also, please use code tags in future

If you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end of the code.

---

### Post by Carol_Milner on 2014-02-08
Removing samba4 and installing samba completed with no error messages. However installing MySQL server form the software centre again failed.
 
```

 sudo apt-get -f install
```
now produces:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
yThe following extra packages will be installed:
  mysql-client-5.5 mysql-server-5.5
Suggested packages:
  tinyca
The following NEW packages will be installed
  mysql-client-5.5 mysql-server-5.5
0 to upgrade, 2 to newly install, 0 to remove and 78 not to upgrade.
1 not fully installed or removed.
Need to get 0 B/17.1 MB of archives.
After this operation, 63.2 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 321444 files and directories currently installed.)
Unpacking mysql-client-5.5 (from .../mysql-client-5.5_5.5.35-0ubuntu0.12.04.2_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/mysql-client-5.5_5.5.35-0ubuntu0.12.04.2_amd64.deb (--unpack):
 trying to overwrite '/usr/share/man/man1/mysql_client_test.1.gz', which is also in package mysql-test 5.6.16-2
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Unpacking mysql-server-5.5 (from .../mysql-server-5.5_5.5.35-0ubuntu0.12.04.2_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/mysql-server-5.5_5.5.35-0ubuntu0.12.04.2_amd64.deb (--unpack):
 trying to overwrite '/usr/share/man/man1/mysqltest_embedded.1.gz', which is also in package mysql-test 5.6.16-2
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/mysql-client-5.5_5.5.35-0ubuntu0.12.04.2_amd64.deb
 /var/cache/apt/archives/mysql-server-5.5_5.5.35-0ubuntu0.12.04.2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by fdrake on 2014-02-08
remove the package mysql-test (do a " sudo apt-get -f install && sudo apt-get update ") and try agan the prev installation

---

### Post by jeanjd63 on 2014-02-08
Hello

You can do :
[B]sudo  dpkg  -i  --force-all  [COLOR=#000000][FONT=Ubuntu Mono]/var/cache/apt/archives/mysql-client-5.5_5.5.35-0ubuntu0.12.04.2_amd64.deb
[/FONT][/COLOR]sudo  dpkg  -i  --force-all  [/B][COLOR=#000000][FONT=Ubuntu Mono]**/var/cache/apt/archives/mysql-server-5.5_5.5.35-0ubuntu0.12.04.2_amd64.deb**
and
**sudo apt-get  install -f**[/FONT][/COLOR]

---

### Post by Carol_Milner on 2014-02-08
MySQL server and client working!
Many thanks jeanjd63 :P

---

### Post by jeanjd63 on 2014-02-08
May be Solved ?

---

### Post by Carol_Milner on 2014-02-08
Yes, done

---

