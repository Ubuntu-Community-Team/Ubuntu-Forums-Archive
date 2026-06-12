---
title: "Oracle-xe"
date: 2007-04-10
forum: General Help
---

### Post by javaholic on 2007-04-10
I have installed oracle-xe for the first time and i like it alot.  All connected and ready to rumble but i can't say i have evere liked sqlplus.  I used to use Toad when i was running a windows based system but don,'t know what can be used besides sqlplus on my ubuntu system.

Any Idea Lads?

---

### Post by marianom on 2007-04-10
Two options:
1- download sql developer, free as a beer from [oracle's site]("http://www.oracle.com/technology/software/products/sql/index.html") (it runs on java).

2- tora (a kde app that runs on gnome). You can downloaded it from [their site]("http://tora.sourceforge.net/").
You should know that you can get it from the repos directly but as discussed [here]("http://ubuntuforums.org/showthread.php?t=189381"), that's not a good idea.

Have fun!

---

### Post by IcemanV9 on 2007-04-10
@ javaholic - Amen! Oracle-XE is fantastic on Ubuntu. :)

SQL Developer is very good (compared to Toad). Hint: do NOT use RPM package. Use "Multiple Platforms". :)

---

### Post by MickSulley on 2007-11-25
Hi,

I have installed Oracle XE, I can log in and see the tables from sqlplus but cannot open the home page and also cannot access via SQLDEVELOPER.
From the investigation I have done it seems that the listener will not start.  If I run manually I get -

mick@mick-laptop:~$ lsnrctl start listener

LSNRCTL for Linux: Version 10.2.0.1.0 - Production on 25-NOV-2007 22:32:12

Copyright (c) 1991, 2005, Oracle.  All rights reserved.

Starting /usr/lib/oracle/xe/app/oracle/product/10.2.0/server/bin/tnslsnr: please wait...

TNSLSNR for Linux: Version 10.2.0.1.0 - Production
NL-00280: error creating log stream /usr/lib/oracle/xe/app/oracle/product/10.2.0/server/network/log/listener.log
 NL-00278: cannot open log file
  SNL-00016: snlfohd: error opening file
   Linux Error: 13: Permission denied

Listener failed to start. See the error message(s) above...

mick@mick-laptop:~$ 

I have checked the permissionsmick@mick-laptop:/usr/lib/oracle/xe/app/oracle/product/10.2.0/server/network$ ls -lrt
total 24
drwxr-xr-x 2 oracle dba 4096 2006-02-24 05:18 trace
drwxr-xr-x 2 oracle dba 4096 2006-02-24 05:18 log
drwxr-xr-x 2 oracle dba 4096 2007-11-25 21:53 mesg
drwxr-xr-x 2 oracle dba 4096 2007-11-25 21:53 lib
drwxr-xr-x 3 oracle dba 4096 2007-11-25 21:53 install
drwxr-xr-x 3 oracle dba 4096 2007-11-25 22:06 admin
mick@mick-laptop:/usr/lib/oracle/xe/app/oracle/product/10.2.0/server/network$ id

so they are owned by oracle, I have logged on to Linux as oracle ans still get similar messages

Any ideas where I have gone wrong?

Thanks

Mick

---

