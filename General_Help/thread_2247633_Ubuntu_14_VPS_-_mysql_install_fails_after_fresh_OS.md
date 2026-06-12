---
title: "Ubuntu 14 VPS - mysql install fails after fresh OS install - Troubleshooting Help"
date: 2014-10-09
forum: General Help
---

### Post by weirdaljr on 2014-10-09
Hello all, I am hoping you can help me as my VPS is unmanaged and I am not getting any help there.  My issue is MySQL install fails after fresh OS image, even being the first thing installed.  I have reimaged the server 10+ times trying different things as well as using different images including Ubuntu 14.04 64-bit, 32-bit, & Debain 7.


Ubuntu 14.04 fresh vps load - 3gb ram - 2gb swap - 50gb hdd


After booting new VPS I run:
apt-get update
apt-get install mysql-server

Results:
```
...
...
...
Preparing to unpack .../libaio1_0.3.109-4_amd64.deb ...
Unpacking libaio1:amd64 (0.3.109-4) ...
Selecting previously unselected package mysql-common.
Preparing to unpack .../mysql-common_5.5.38-0ubuntu0.14.04.1_all.deb ...
Unpacking mysql-common (5.5.38-0ubuntu0.14.04.1) ...
Selecting previously unselected package libmysqlclient18:amd64.
Preparing to unpack .../libmysqlclient18_5.5.38-0ubuntu0.14.04.1_amd64.deb ...
Unpacking libmysqlclient18:amd64 (5.5.38-0ubuntu0.14.04.1) ...
Selecting previously unselected package libdbi-perl.
Preparing to unpack .../libdbi-perl_1.630-1_amd64.deb ...
Unpacking libdbi-perl (1.630-1) ...
Selecting previously unselected package libdbd-mysql-perl.
Preparing to unpack .../libdbd-mysql-perl_4.025-1_amd64.deb ...
Unpacking libdbd-mysql-perl (4.025-1) ...
Selecting previously unselected package libterm-readkey-perl.
Preparing to unpack .../libterm-readkey-perl_2.31-1_amd64.deb ...
Unpacking libterm-readkey-perl (2.31-1) ...
Selecting previously unselected package mysql-client-core-5.5.
Preparing to unpack .../mysql-client-core-5.5_5.5.38-0ubuntu0.14.04.1_amd64.deb
...
Unpacking mysql-client-core-5.5 (5.5.38-0ubuntu0.14.04.1) ...
Selecting previously unselected package mysql-client-5.5.
Preparing to unpack .../mysql-client-5.5_5.5.38-0ubuntu0.14.04.1_amd64.deb ...
Unpacking mysql-client-5.5 (5.5.38-0ubuntu0.14.04.1) ...
Selecting previously unselected package mysql-server-core-5.5.
Preparing to unpack .../mysql-server-core-5.5_5.5.38-0ubuntu0.14.04.1_amd64.deb
...
Unpacking mysql-server-core-5.5 (5.5.38-0ubuntu0.14.04.1) ...
Selecting previously unselected package psmisc.
Preparing to unpack .../psmisc_22.20-1ubuntu2_amd64.deb ...
Unpacking psmisc (22.20-1ubuntu2) ...
Setting up mysql-common (5.5.38-0ubuntu0.14.04.1) ...
Selecting previously unselected package mysql-server-5.5.
(Reading database ... 18109 files and directories currently installed.)
Preparing to unpack .../mysql-server-5.5_5.5.38-0ubuntu0.14.04.1_amd64.deb ...
Unpacking mysql-server-5.5 (5.5.38-0ubuntu0.14.04.1) ...
Selecting previously unselected package libhtml-template-perl.
Preparing to unpack .../libhtml-template-perl_2.95-1_all.deb ...
Unpacking libhtml-template-perl (2.95-1) ...
Selecting previously unselected package mysql-server.
Preparing to unpack .../mysql-server_5.5.38-0ubuntu0.14.04.1_all.deb ...
Unpacking mysql-server (5.5.38-0ubuntu0.14.04.1) ...
Processing triggers for ureadahead (0.100.0-16) ...
Setting up libaio1:amd64 (0.3.109-4) ...
Setting up libmysqlclient18:amd64 (5.5.38-0ubuntu0.14.04.1) ...
Setting up libdbi-perl (1.630-1) ...
Setting up libdbd-mysql-perl (4.025-1) ...
Setting up libterm-readkey-perl (2.31-1) ...
Setting up mysql-client-core-5.5 (5.5.38-0ubuntu0.14.04.1) ...
Setting up mysql-client-5.5 (5.5.38-0ubuntu0.14.04.1) ...
Setting up mysql-server-core-5.5 (5.5.38-0ubuntu0.14.04.1) ...
Setting up psmisc (22.20-1ubuntu2) ...
Setting up mysql-server-5.5 (5.5.38-0ubuntu0.14.04.1) ...
141009 2:37:51 [Warning] Using unique option prefix key_buffer instead of key_buffer_size is deprecated and will be removed in a future release. Please use the full name instead.

```

Terminal stalls there every time - multiple reimages of the vps including ubuntu 14.04 and debian 7 - same result.


The terminal output stops there right before a warning message box is shown due stating "Unable to set mysql root password...".  This is after setting and confirming the password during the install process via the prompts.

Here are some logs I gathered so far - Again these logs are all after a fresh image with only command issued being "apt-get install mysql-server"



_**Apt\History.log:**_


```
Start-Date: 2014-10-09 01:56:43
Commandline: apt-get install mysql-server
Install: mysql-server-core-5.5:amd64 (5.5.38-0ubuntu0.14.04.1, automatic), mysql-server-5.5:amd64 (5.5.38-0ubuntu0.14.04.1, automatic), libaio1:amd64 (0.3.109-4, automatic), mysql-client-core-5.5:amd64 (5.5.38-0ubuntu0.14.04.1, automatic), psmisc:amd64 (22.20-1ubuntu2, automatic), mysql-client-5.5:amd64 (5.5.38-0ubuntu0.14.04.1, automatic), libhtml-template-perl:amd64 (2.95-1, automatic), libterm-readkey-perl:amd64 (2.31-1, automatic), mysql-common:amd64 (5.5.38-0ubuntu0.14.04.1, automatic), libmysqlclient18:amd64 (5.5.38-0ubuntu0.14.04.1, automatic), mysql-server:amd64 (5.5.38-0ubuntu0.14.04.1), libdbd-mysql-perl:amd64 (4.025-1, automatic), libdbi-perl:amd64 (1.630-1, automatic)

```
_**Apt\Term.log:**_




```
Log started: 2014-10-09 01:56:43
Selecting previously unselected package libaio1:amd64.
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 17633 files and directories currently installed.)
Preparing to unpack .../libaio1_0.3.109-4_amd64.deb ...
Unpacking libaio1:amd64 (0.3.109-4) ...
Selecting previously unselected package mysql-common.
Preparing to unpack .../mysql-common_5.5.38-0ubuntu0.14.04.1_all.deb ...
Unpacking mysql-common (5.5.38-0ubuntu0.14.04.1) ...
Selecting previously unselected package libmysqlclient18:amd64.
Preparing to unpack .../libmysqlclient18_5.5.38-0ubuntu0.14.04.1_amd64.deb ...
Unpacking libmysqlclient18:amd64 (5.5.38-0ubuntu0.14.04.1) ...
Selecting previously unselected package libdbi-perl.
Preparing to unpack .../libdbi-perl_1.630-1_amd64.deb ...
Unpacking libdbi-perl (1.630-1) ...
Selecting previously unselected package libdbd-mysql-perl.
Preparing to unpack .../libdbd-mysql-perl_4.025-1_amd64.deb ...
Unpacking libdbd-mysql-perl (4.025-1) ...
Selecting previously unselected package libterm-readkey-perl.
Preparing to unpack .../libterm-readkey-perl_2.31-1_amd64.deb ...
Unpacking libterm-readkey-perl (2.31-1) ...
Selecting previously unselected package mysql-client-core-5.5.
Preparing to unpack .../mysql-client-core-5.5_5.5.38-0ubuntu0.14.04.1_amd64.deb ...
Unpacking mysql-client-core-5.5 (5.5.38-0ubuntu0.14.04.1) ...
Selecting previously unselected package mysql-client-5.5.
Preparing to unpack .../mysql-client-5.5_5.5.38-0ubuntu0.14.04.1_amd64.deb ...
Unpacking mysql-client-5.5 (5.5.38-0ubuntu0.14.04.1) ...
Selecting previously unselected package mysql-server-core-5.5.
Preparing to unpack .../mysql-server-core-5.5_5.5.38-0ubuntu0.14.04.1_amd64.deb ...
Unpacking mysql-server-core-5.5 (5.5.38-0ubuntu0.14.04.1) ...
Selecting previously unselected package psmisc.
Preparing to unpack .../psmisc_22.20-1ubuntu2_amd64.deb ...
Unpacking psmisc (22.20-1ubuntu2) ...
Setting up mysql-common (5.5.38-0ubuntu0.14.04.1) ...
Selecting previously unselected package mysql-server-5.5.
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 18016 files and directories currently installed.)
Preparing to unpack .../mysql-server-5.5_5.5.38-0ubuntu0.14.04.1_amd64.deb ...
Unpacking mysql-server-5.5 (5.5.38-0ubuntu0.14.04.1) ...
Selecting previously unselected package libhtml-template-perl.
Preparing to unpack .../libhtml-template-perl_2.95-1_all.deb ...
Unpacking libhtml-template-perl (2.95-1) ...
Selecting previously unselected package mysql-server.
Preparing to unpack .../mysql-server_5.5.38-0ubuntu0.14.04.1_all.deb ...
Unpacking mysql-server (5.5.38-0ubuntu0.14.04.1) ...
Processing triggers for ureadahead (0.100.0-16) ...
Setting up libaio1:amd64 (0.3.109-4) ...
Setting up libmysqlclient18:amd64 (5.5.38-0ubuntu0.14.04.1) ...
Setting up libdbi-perl (1.630-1) ...
Setting up libdbd-mysql-perl (4.025-1) ...
Setting up libterm-readkey-perl (2.31-1) ...
Setting up mysql-client-core-5.5 (5.5.38-0ubuntu0.14.04.1) ...
Setting up mysql-client-5.5 (5.5.38-0ubuntu0.14.04.1) ...
Setting up mysql-server-core-5.5 (5.5.38-0ubuntu0.14.04.1) ...
Setting up psmisc (22.20-1ubuntu2) ...
Setting up mysql-server-5.5 (5.5.38-0ubuntu0.14.04.1) ...
141009 1:56:54 [Warning] Using unique option prefix key_buffer instead of key_buffer_size is deprecated and will be removed in a future release. Please use the full name instead.
[?1049h[1;25r[4l[?25l(B[m[37m[40m[1;25r[H[2J[1;1H[1m[37m[45m [2;1H [3;1H [4;1H [5;1H [6;1H [7;1H [8;1H [9;1H [10;1H [11;1H [12;1H [13;1H [14;1H [15;1H [16;1H [17;1H [18;1H [19;1H [20;1H [21;1H [22;1H [23;1H [24;1H [25;1H [25;79H [4h [4l[1;1H(B[m[37m[45mPackage configuration[5;2H(0[30m[47mlqqqqqqqqqqqqqqqqqqqqqu(B[m(B[30m[47m [31mConfiguring mysql-server-5.5[30m (0[30m[47mtqqqqqqqqqqqqqqqqqqqqqqk[6;2Hx(B[m(B[30m[47m (0[30m[47mx(B[m(B[1m[37m[40m [7;2H(B[m(0[30m[47mx(B[m(B[30m[47m Unable to set password for the MySQL "root" user (0[30m[47mx(B[m(B[1m[37m[40m [8;2H(B[m(0[30m[47mx(B[m(B[30m[47m (0[30m[47mx(B[m(B[1m[37m[40m [9;2H(B[m(0[30m[47mx(B[m(B[30m[47m An error occurred while setting the password for the MySQL (0[30m[47mx(B[m(B[1m[37m[40m [10;2H(B[m(0[30m[47mx(B[m(B[30m[47m administrative user. This may have happened because the account already (0[30m[47mx(B[m(B[1m[37m[40m [11;2H(B[m(0[30m[47mx(B[m(B[30m[47m has a password, or because of a communication problem with the MySQL (0[30m[47mx(B[m(B[1m[37m[40m [12;2H(B[m(0[30m[47mx(B[m(B[30m[47m server. (0[30m[47mx(B[m(B[1m[37m[40m [13;2H(B[m(0[30m[47mx(B[m(B[30m[47m (0[30m[47mx(B[m(B[1m[37m[40m [14;2H(B[m(0[30m[47mx(B[m(B[30m[47m You should check the account's password after the package installation. (0[30m[47mx(B[m(B[1m[37m[40m [15;2H(B[m(0[30m[47mx(B[m(B[30m[47m (0[30m[47mx(B[m(B[1m[37m[40m [16;2H(B[m(0[30m[47mx(B[m(B[30m[47m Please read the /usr/share/doc/mysql-server-5.5/README.Debian file for (0[30m[47mx(B[m(B[1m[37m[40m [17;2H(B[m(0[30m[47mx(B[m(B[30m[47m more information. (0[30m[47mx(B[m(B[1m[37m[40m [18;2H(B[m(0[30m[47mx(B[m(B[30m[47m (0[30m[47mx(B[m(B[1m[37m[40m [19;2H(B[m(0[30m[47mx(B[m(B[30m[47m [37m[41m<Ok>[30m[47m (0[30m[47mx(B[m(B[1m[37m[40m [20;2H(B[m(0[30m[47mx(B[m(B[30m[47m (0[30m[47mx(B[m(B[1m[37m[40m [21;2H(B[m(0[30m[47mmqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqj(B[m(B[1m[37m[40m [22;3H [19;38H[?12l[?25h[25;1H(B[m[37m[40m(B[m[39;49m
[K
[?1049l



```_**Mysql\error.log:**_


```
141009 1:56:52 [Warning] Using unique option prefix myisam-recover instead of myisam-recover-options is deprecated and will be removed in a future release. Please use the full name instead.
141009 1:56:52 [Note] Plugin 'FEDERATED' is disabled.
141009 1:56:52 InnoDB: The InnoDB memory heap is disabled
141009 1:56:52 InnoDB: Mutexes and rw_locks use GCC atomic builtins
141009 1:56:52 InnoDB: Compressed tables use zlib 1.2.8
141009 1:56:52 InnoDB: Using Linux native AIO
141009 1:56:52 InnoDB: Warning: io_setup() failed with EAGAIN. Will make 5 attempts before giving up.
InnoDB: Warning: io_setup() attempt 1 failed.
InnoDB: Warning: io_setup() attempt 2 failed.
InnoDB: Warning: io_setup() attempt 3 failed.
InnoDB: Warning: io_setup() attempt 4 failed.
InnoDB: Warning: io_setup() attempt 5 failed.
141009 1:56:54 InnoDB: Error: io_setup() failed with EAGAIN after 5 attempts.
InnoDB: You can disable Linux Native AIO by setting innodb_use_native_aio = 0 in my.cnf
141009 1:56:54 InnoDB: Fatal error: cannot initialize AIO sub-system
141009 1:56:54 [ERROR] Plugin 'InnoDB' init function returned error.
141009 1:56:54 [ERROR] Plugin 'InnoDB' registration as a STORAGE ENGINE failed.
141009 1:56:54 [ERROR] Unknown/unsupported storage engine: InnoDB
141009 1:56:54 [ERROR] Aborting


141009 1:56:54 [Note] /usr/sbin/mysqld: Shutdown complete



[SIZE=4][COLOR=#ff0000]_**...**_[/COLOR]
[COLOR=#ff0000]_*****2500 lines of this repeating in the 8 minutes the server has been up *****_[/COLOR]
[/SIZE][COLOR=#ff0000][U][B][SIZE=4]...[/SIZE]
[/B][/U][/COLOR]


141009 2:03:53 [Warning] Using unique option prefix myisam-recover instead of myisam-recover-options is deprecated and will be removed in a future release. Please use the full name instead.
141009 2:03:53 [Note] Plugin 'FEDERATED' is disabled.
141009 2:03:53 InnoDB: The InnoDB memory heap is disabled
141009 2:03:53 InnoDB: Mutexes and rw_locks use GCC atomic builtins
141009 2:03:53 InnoDB: Compressed tables use zlib 1.2.8
141009 2:03:53 InnoDB: Using Linux native AIO
141009 2:03:53 InnoDB: Warning: io_setup() failed with EAGAIN. Will make 5 attempts before giving up.
InnoDB: Warning: io_setup() attempt 1 failed.
InnoDB: Warning: io_setup() attempt 2 failed.
InnoDB: Warning: io_setup() attempt 3 failed.
InnoDB: Warning: io_setup() attempt 4 failed.
InnoDB: Warning: io_setup() attempt 5 failed.
141009 2:03:55 InnoDB: Error: io_setup() failed with EAGAIN after 5 attempts.
InnoDB: You can disable Linux Native AIO by setting innodb_use_native_aio = 0 in my.cnf
141009 2:03:55 InnoDB: Fatal error: cannot initialize AIO sub-system
141009 2:03:55 [ERROR] Plugin 'InnoDB' init function returned error.
141009 2:03:55 [ERROR] Plugin 'InnoDB' registration as a STORAGE ENGINE failed.
141009 2:03:55 [ERROR] Unknown/unsupported storage engine: InnoDB
141009 2:03:55 [ERROR] Aborting


141009 2:03:55 [Note] /usr/sbin/mysqld: Shutdown complete

```




Any suggestions or help would be greatly appreciated.  I have been googling it for hours and re-imaging the vps for days trying different things to make a simple "apt-get install mysql-server" complete on a clean os image.


Thanks!

---

### Post by weirdaljr on 2014-10-09
Well I got it fixed after a few more hours of googling errors.  

The problem seems to be a issue with OpenVZ VPSes.   

It was fixed by creating a /etc/my.cnf file prior to installing mysql containing:

[mysqld]
innodb_use_native_aio = 0

Hopefully it saves some people time figuring this out.

---

### Post by chebs2 on 2014-12-07
> **weirdaljr said:**
> Hopefully it saves some people time figuring this out.

Thanks a lot certainly does!

---

### Post by cfernanrodri on 2014-12-25
works fine, you saved my life

---

