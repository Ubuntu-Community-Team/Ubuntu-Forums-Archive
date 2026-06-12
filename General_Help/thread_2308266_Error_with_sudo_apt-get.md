---
title: "Error with sudo apt-get"
date: 2016-01-01
forum: General Help
---

### Post by cscj01 on 2016-01-01
I have Ubuntu 14.04.3 x64.  I recently got an error message (red symbol with white line through it in panel) telling me I had an error in Package Manager execution.  I presume this was from normal updates.  When I tried```
sudo apt-get update
```I received the following message:> E: Malformed line 4 in source list /etc/apt/sources.list.d/mysql.list (dist parse)
E: The list of sources could not be read.
The contents of /etc/apt/sources.list.s/mysql.list is```
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out entries below, but any other modifications may be lost.
# Use command 'dpkg-reconfigure mysql-apt-config' as root for modifications.
deb http://repo.mysql.com/apt//  mysql-apt-config
# deb http://repo.mysql.com/apt//  mysql-5.7

# deb-src http://repo.mysql.com/apt//  mysql-5.7
```

If I try to launch Synaptic, I get the following error message:```
: Malformed line 4 in source list /etc/apt/sources.list.d/mysql.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.
```Then only option then is to close Synaptic.

I have done nothing to my sources for a good while.  This message just appeared.  Any thoughts would be appreciated.

---

### Post by cscj01 on 2016-01-01
I believe I have repaired it with```
sudo dpkg-reconfigure mysql-apt-config
sudo apt-get update
```I'll wait a day or two to see if the error returns.  If not, I'll mark this solved.

---

### Post by Bashing-om on 2016-01-01
cscj01; Hello;

The error is in respect to the control file " /etc/apt/sources.list.d/mysql.list " in the 3rd party directory.

Looking at :
[https://dev.mysql.com/downloads/repo/apt/](https://dev.mysql.com/downloads/repo/apt/)
The download PPA site, one is directed to:
[http://dev.mysql.com/doc/mysql-apt-repo-quick-guide/en/#repo-qg-apt-repo-manual-setup](http://dev.mysql.com/doc/mysql-apt-repo-quick-guide/en/#repo-qg-apt-repo-manual-setup)
to properly set up the fetch line for apt's /etc/apt/sources.list.d/mysql.list control file.
```

deb http://repo.mysql.com/apt/{debian|ubuntu}/ {jessie|wheezy|precise|trusty|utopic|vivid} {mysql-5.6|mysql-5.7|workbench-6.2|utilities-1.4|connector-python-2.0}

```

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by cscj01 on 2016-01-02
> **Bashing-om said:**
> cscj01; Hello;

The error is in respect to the control file " /etc/apt/sources.list.d/mysql.list " in the 3rd party directory.

Looking at :
[https://dev.mysql.com/downloads/repo/apt/](https://dev.mysql.com/downloads/repo/apt/)
The download PPA site, one is directed to:
[http://dev.mysql.com/doc/mysql-apt-repo-quick-guide/en/#repo-qg-apt-repo-manual-setup](http://dev.mysql.com/doc/mysql-apt-repo-quick-guide/en/#repo-qg-apt-repo-manual-setup)
to properly set up the fetch line for apt's /etc/apt/sources.list.d/mysql.list control file.
```

deb http://repo.mysql.com/apt/{debian|ubuntu}/ {jessie|wheezy|precise|trusty|utopic|vivid} {mysql-5.6|mysql-5.7|workbench-6.2|utilities-1.4|connector-python-2.0}

```

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

Thanks for the references.  Here's what I got for mysql.list using ```
sudo dpkg-reconfigure mysql-apt-config
``` > ### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out entries below, but any other modifications may be lost.
# Use command 'dpkg-reconfigure mysql-apt-config' as root for modifications.
deb [http://repo.mysql.com/apt/ubuntu/](http://repo.mysql.com/apt/ubuntu/) trusty mysql-apt-config
deb [http://repo.mysql.com/apt/ubuntu/](http://repo.mysql.com/apt/ubuntu/) trusty mysql-5.6

deb-src [http://repo.mysql.com/apt/ubuntu/](http://repo.mysql.com/apt/ubuntu/) trusty mysql-5.6The others (Tools and Utilities) were disabled.

---

### Post by cscj01 on 2016-01-22
I thought I had fixed this, but today I ran into some problems.  I launched MySQL Workbench and did not have a connection to MySQL Server.  When I tried to start one, I got the following:> 2016-01-22 15:44:05 - Starting server...
2016-01-22 15:44:05 - Executing '/etc/init.d/mysql start'
2016-01-22 15:44:41 - Checking server status...
2016-01-22 15:44:41 - Trying to connect to MySQL...
2016-01-22 15:44:41 - Can't connect to MySQL server on '127.0.0.1' (111) (2003)
2016-01-22 15:44:41 - Assuming server is not running
2016-01-22 15:44:41 - Starting server...
2016-01-22 15:44:41 - Executing '/etc/init.d/mysql start'
2016-01-22 15:44:41 - Start server:  * Starting MySQL database server mysqld x64 is  5.5
2016-01-22 15:44:41 - Start server: 

2016-01-22 15:44:41 - Start server:    ...fail!

2016-01-22 15:44:41 - Server start done.

FROM /var/log/mysql/error.log:
    2016-01-22 15:44:10    mysqld_safe  Starting mysqld daemon with databases from /var/lib/mysql
    2016-01-22 15:44:10    [Note]  /usr/sbin/mysqld (mysqld 5.5.46-0ubuntu0.14.04.2) starting as process 14790 ...
    2016-01-22 15:44:10    [ERROR]  Can't read from messagefile '/usr/share/mysql/english/errmsg.sys'
    2016-01-22 15:44:10    [Note]  Plugin 'FEDERATED' is disabled.
    2016-01-22 15:44:10    InnoDB:  The InnoDB memory heap is disabled
    2016-01-22 15:44:10    InnoDB:  Mutexes and rw_locks use GCC atomic builtins
    2016-01-22 15:44:10    InnoDB:  Compressed tables use zlib 1.2.8
    2016-01-22 15:44:10    InnoDB:  Using Linux native AIO
    2016-01-22 15:44:10    InnoDB:  Initializing buffer pool, size = 128.0M
    2016-01-22 15:44:10    InnoDB:  Completed initialization of buffer pool
    2016-01-22 15:44:10    InnoDB:  highest supported file format is Barracuda.
    2016-01-22 15:44:11    InnoDB:  Waiting for the background threads to start
    2016-01-22 15:44:12    InnoDB:  5.5.46 started; log sequence number 367546895
    2016-01-22 15:44:12    [ERROR]  /usr/sbin/mysqld: unknown option '--explicit_defaults_for_timestamp'
    2016-01-22 15:44:12    [ERROR]  Aborting
    2016-01-22 15:44:12    InnoDB:  Starting shutdown...
    2016-01-22 15:44:13    InnoDB:  Shutdown completed; log sequence number 367546895
    2016-01-22 15:44:13    [Note]  
    2016-01-22 15:44:13    mysqld_safe  mysqld from pid file /var/run/mysqld/mysqld.pid ended
2016-01-22 15:44:41 - Checking server status...
2016-01-22 15:44:41 - Trying to connect to MySQL...
2016-01-22 15:44:41 - Can't connect to MySQL server on '127.0.0.1' (111) (2003)
2016-01-22 15:44:41 - Assuming server is not runningAs noted earlier in the first post of this thread, I had encountered an error in /etc/apt/sources.list.d/mysql.list.  Upon doing some research, I came upon a suggestion that I run```
sudo dpkg-reconfigure mysql-apt-config
```I now believe this caused me to have some of MySQL 5.5 installed```
mysql-client
mysql-server
mysql-client-core
mysql-server-core
``` and some of MySQL 5.6 installed```
mysql-common
libmysqlclient18I am not sure which version I should have.  
libmysqlclient18:i386
```It seems that I also had the following entries in my Other Software list:```
http://repo.mysql.com/apt/ubuntu/trusty mysql-apt-config
http://repo.mysql.com/apt/ubuntu/trusty mysql-5.6
http://repo.mysql.com/apt/ubuntu/trusty mysql-5.6 (Source Code)
```I do not know what I did to get these items in my Sources list.  I am not sure which version I should have, but I believe the current version for Ubuntu 14.04.3 x64 is MySQL 5.5.

I have always run the version of MySQL that is in the current release.  So my question is, how do I get things back to where they should be?  Can I just remove the 5.6 components?  Is there a way to check that I have all that I need for 5.5?  I'm a little (well, mabe a lot) lost here.

---

### Post by Bashing-om on 2016-01-22
cscj01; Welp;

Not in my experience range;
But:
```

apt-cache show mysql-client
apt-cache show mysql-server

```
says " Version: 5.5.35+dfsg-1ubuntu1 ' for release 14.04.

[INDENT][INDENT]hope this helps just a bit
[/INDENT][/INDENT]

---

### Post by cscj01 on 2016-01-22
At this stage, I have determined if I attempt to uninstall the 5.6 components,```
sudo apt-get remove mysql-common
``` the system wants to uninstall the 5.5 components as well.  I looked at downgrading mysql-common to 5.5,```
sudo apt-get install mysql-common=5.5.46-0ubuntu0.14.04.2
``` but the same happens there; the system wants to uninstall all my 5.5 components.  I suppose I'll need to completely uninstall MySQL and re-install.  Can anyone tell me which items (databases, config files, log files, etc.) I should keep so I can have the same environment I had before things got fouled up?

---

### Post by cscj01 on 2016-01-23
Okay, I have done the following, and my MySQL is now correct with the 14.04.3 x64 distribution:[LIST=1]
[*]Backup databases, config files;
[*]Removed mysql with ```
sudo apt-get remove --purge mysql-server mysql-common mysql-client
```
[*]Removed the Oracle repositories from my sources;
[*]Reinstalled mysql with ```
sudo apt-get install mysql-server mysql-client mysql-common
```
[*]Renstalled mysql-workbench with ```
sudo apt-get install mysql-workbench
```
[*]
[/LIST]I then checked /etc/mysql/my.cnf to make sure things were set up properly.  Using MySQL Workbench, I checked my connections to my databases and ran queries against them to confirm that they were ok.  I did not have to restore the backups, because everything was up to date and correct.

I have an idea, though I cannot be 100% sure, that I must have added the Oracle repos when I upgraded MySQL Workbench.  I had been doing that by downloading .deb files and installing the new releases.  I seem to recall the last time I did that, there was something about getting the new releases of Workbench by adding a source, but I do not recall anything about MySQL.  Oh well, I will just use the Workbench that is in the release repositories from now on.  Not paying attention can be a real pain.  So I will close this issue once again.

---

### Post by Bashing-om on 2016-01-23
cscj01; Outstanding !

You do good work. Glad it all worked out.

mark it up to
[INDENT][INDENT][INDENT]lessons learned
[/INDENT][/INDENT][/INDENT]

---

