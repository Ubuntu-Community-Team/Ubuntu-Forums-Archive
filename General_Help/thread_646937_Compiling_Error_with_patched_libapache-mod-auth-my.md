---
title: "Compiling Error with patched libapache-mod-auth-mysql"
date: 2007-12-21
forum: General Help
---

### Post by Russianspi on 2007-12-21
Hi.  First, some background.  I have an Ubuntu Feisty server running Apache2.  I am using mod-auth-mysql to authenticate users against a mysql database on another server.  I set it up, and it works well.  The trouble is, every once in a while, I get errors ("mysql server has gone away" in my Apache2 log) and "Server Error 500" in users' browsers.    After digging around, I believe that this is caused by [Debian Bug 420010]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=420010") libapache-mod-auth-mysql.  I found a patch, and downloaded the source, and applied the patch but when I try and compile the package, I get trouble. (For reference, I get the same errors if I try to compile without applying the patch.) I ran:

```
./configure --disable-apache13 --enable-apache2
```

No problems so far.

When I ran ```
make
```, I ran into trouble.  I got:

```
/usr/bin/apxs2  -o apache2_mod_auth_mysql.la -I/usr/include/mysql -L/usr/lib -lmysqlclient -DAPACHE2 -c mod_auth_mysql.c
/usr/share/apr-1.0/build/libtool --silent --mode=compile --tag=disable-static i486-linux-gnu-gcc -prefer-pic -DLINUX=2 -D_GNU_SOURCE -D_LARGEFILE64_SOURCE -D_REENTRANT -I/usr/include/apr-1.0 -I/usr/include/openssl -I/usr/include/postgresql -I/usr/include/xmltok -pthread     -I/usr/include/apache2  -I/usr/include/apr-1.0   -I/usr/include/apr-1.0 -I/usr/include/postgresql -I/usr/include/mysql -DAPACHE2  -c -o mod_auth_mysql.lo mod_auth_mysql.c && touch mod_auth_mysql.slo
mod_auth_mysql.c:686: error: expected expression before 'mysql_auth_config_rec'
mod_auth_mysql.c:686: error: initializer element is not constant
mod_auth_mysql.c:686: error: (near initialization for 'mysql_auth_cmds[8].cmd_data')
mod_auth_mysql.c:690: error: expected expression before 'mysql_auth_config_rec'
mod_auth_mysql.c:690: error: initializer element is not constant
mod_auth_mysql.c:690: error: (near initialization for 'mysql_auth_cmds[9].cmd_data')
mod_auth_mysql.c:694: error: expected expression before 'mysql_auth_config_rec'
mod_auth_mysql.c:694: error: initializer element is not constant
mod_auth_mysql.c:694: error: (near initialization for 'mysql_auth_cmds[10].cmd_data')
mod_auth_mysql.c:698: error: expected expression before 'mysql_auth_config_rec'
mod_auth_mysql.c:698: error: initializer element is not constant
mod_auth_mysql.c:698: error: (near initialization for 'mysql_auth_cmds[11].cmd_data')
mod_auth_mysql.c:702: error: expected expression before 'mysql_auth_config_rec'
mod_auth_mysql.c:702: error: initializer element is not constant
mod_auth_mysql.c:702: error: (near initialization for 'mysql_auth_cmds[12].cmd_data')
mod_auth_mysql.c:706: error: expected expression before 'mysql_auth_config_rec'
mod_auth_mysql.c:706: error: initializer element is not constant
mod_auth_mysql.c:706: error: (near initialization for 'mysql_auth_cmds[13].cmd_data')
mod_auth_mysql.c:710: error: expected expression before 'mysql_auth_config_rec'
mod_auth_mysql.c:710: error: initializer element is not constant
mod_auth_mysql.c:710: error: (near initialization for 'mysql_auth_cmds[14].cmd_data')
mod_auth_mysql.c:714: error: expected expression before 'mysql_auth_config_rec'
mod_auth_mysql.c:714: error: initializer element is not constant
mod_auth_mysql.c:714: error: (near initialization for 'mysql_auth_cmds[15].cmd_data')
mod_auth_mysql.c:718: error: expected expression before 'mysql_auth_config_rec'
mod_auth_mysql.c:718: error: initializer element is not constant
mod_auth_mysql.c:718: error: (near initialization for 'mysql_auth_cmds[16].cmd_data')
mod_auth_mysql.c:722: error: expected expression before 'mysql_auth_config_rec'
mod_auth_mysql.c:722: error: initializer element is not constant
mod_auth_mysql.c:722: error: (near initialization for 'mysql_auth_cmds[17].cmd_data')
mod_auth_mysql.c:726: error: expected expression before 'mysql_auth_config_rec'
mod_auth_mysql.c:726: error: initializer element is not constant
mod_auth_mysql.c:726: error: (near initialization for 'mysql_auth_cmds[18].cmd_data')
mod_auth_mysql.c:730: error: expected expression before 'mysql_auth_config_rec'
mod_auth_mysql.c:730: error: initializer element is not constant
mod_auth_mysql.c:730: error: (near initialization for 'mysql_auth_cmds[19].cmd_data')
mod_auth_mysql.c:734: error: expected expression before 'mysql_auth_config_rec'
mod_auth_mysql.c:734: error: initializer element is not constant
mod_auth_mysql.c:734: error: (near initialization for 'mysql_auth_cmds[20].cmd_data')
mod_auth_mysql.c:738: error: expected expression before 'mysql_auth_config_rec'
mod_auth_mysql.c:738: error: initializer element is not constant
mod_auth_mysql.c:738: error: (near initialization for 'mysql_auth_cmds[21].cmd_data')
mod_auth_mysql.c:742: error: expected expression before 'mysql_auth_config_rec'
mod_auth_mysql.c:742: error: initializer element is not constant
mod_auth_mysql.c:742: error: (near initialization for 'mysql_auth_cmds[22].cmd_data')
mod_auth_mysql.c:746: error: expected expression before 'mysql_auth_config_rec'
mod_auth_mysql.c:746: error: initializer element is not constant
mod_auth_mysql.c:746: error: (near initialization for 'mysql_auth_cmds[23].cmd_data')
mod_auth_mysql.c:750: error: expected expression before 'mysql_auth_config_rec'
mod_auth_mysql.c:750: error: initializer element is not constant
mod_auth_mysql.c:750: error: (near initialization for 'mysql_auth_cmds[24].cmd_data')
mod_auth_mysql.c:754: error: expected expression before 'mysql_auth_config_rec'
mod_auth_mysql.c:754: error: initializer element is not constant
mod_auth_mysql.c:754: error: (near initialization for 'mysql_auth_cmds[25].cmd_data')
mod_auth_mysql.c:758: error: expected expression before 'mysql_auth_config_rec'
mod_auth_mysql.c:758: error: initializer element is not constant
mod_auth_mysql.c:758: error: (near initialization for 'mysql_auth_cmds[26].cmd_data')
mod_auth_mysql.c:762: error: expected expression before 'mysql_auth_config_rec'
mod_auth_mysql.c:762: error: initializer element is not constant
mod_auth_mysql.c:762: error: (near initialization for 'mysql_auth_cmds[27].cmd_data')
mod_auth_mysql.c:766: error: expected expression before 'mysql_auth_config_rec'
mod_auth_mysql.c:766: error: initializer element is not constant
mod_auth_mysql.c:766: error: (near initialization for 'mysql_auth_cmds[28].cmd_data')
mod_auth_mysql.c:770: error: expected expression before 'mysql_auth_config_rec'
mod_auth_mysql.c:770: error: initializer element is not constant
mod_auth_mysql.c:770: error: (near initialization for 'mysql_auth_cmds[29].cmd_data')
mod_auth_mysql.c:774: error: expected expression before 'mysql_auth_config_rec'
mod_auth_mysql.c:774: error: initializer element is not constant
mod_auth_mysql.c:774: error: (near initialization for 'mysql_auth_cmds[30].cmd_data')
mod_auth_mysql.c:778: error: expected expression before 'mysql_auth_config_rec'
mod_auth_mysql.c:778: error: initializer element is not constant
mod_auth_mysql.c:778: error: (near initialization for 'mysql_auth_cmds[31].cmd_data')
mod_auth_mysql.c:782: error: expected expression before 'mysql_auth_config_rec'
mod_auth_mysql.c:782: error: initializer element is not constant
mod_auth_mysql.c:782: error: (near initialization for 'mysql_auth_cmds[32].cmd_data')
mod_auth_mysql.c:786: error: expected expression before 'mysql_auth_config_rec'
mod_auth_mysql.c:786: error: initializer element is not constant
mod_auth_mysql.c:786: error: (near initialization for 'mysql_auth_cmds[33].cmd_data')
mod_auth_mysql.c:790: error: expected expression before 'mysql_auth_config_rec'
mod_auth_mysql.c:790: error: initializer element is not constant
mod_auth_mysql.c:790: error: (near initialization for 'mysql_auth_cmds[34].cmd_data')
mod_auth_mysql.c:794: error: expected expression before 'mysql_auth_config_rec'
mod_auth_mysql.c:794: error: initializer element is not constant
mod_auth_mysql.c:794: error: (near initialization for 'mysql_auth_cmds[35].cmd_data')
mod_auth_mysql.c:798: error: expected expression before 'mysql_auth_config_rec'
mod_auth_mysql.c:798: error: initializer element is not constant
mod_auth_mysql.c:798: error: (near initialization for 'mysql_auth_cmds[36].cmd_data')
mod_auth_mysql.c:802: error: expected expression before 'mysql_auth_config_rec'
mod_auth_mysql.c:802: error: initializer element is not constant
mod_auth_mysql.c:802: error: (near initialization for 'mysql_auth_cmds[37].cmd_data')
mod_auth_mysql.c:850: error: expected expression before 'mysql_auth_config_rec'
mod_auth_mysql.c:850: error: initializer element is not constant
mod_auth_mysql.c:850: error: (near initialization for 'mysql_auth_cmds[49].cmd_data')
apxs:Error: Command failed with rc=65536
.
make: *** [apache2_mod_auth_mysql.la] Error 1
```

I have tried this on several different machines, running either Feisty or Gutsy, but I continue to get the same results.  Can anyone help me, please?  Thanks!

---

### Post by Russianspi on 2007-12-28
Is there more information that people need?  I am happy to answer any questions about my predicament, but I'd love for someone to point me in the right direction.  Just let me know how I can help you help me!  Thanks!

---

### Post by Russianspi on 2008-01-25
Well, it seems that my difficulty is at an end.  I found a package that includes the patch I was looking for [here]("http://giantrobot.co.nz/node/89"), but the kind owner of that site had a bit of advice for me as well.  He told me that mod-auth-mysql is quite rough on a mysql server (resource intensive) and that if my setup allowed it that I might try having a script update a .htaccess file once in a while.  For my (internal) server, which rarely sees new members, this worked perfectly.  I highly recommend it if you need less-than-instantly-updated access from a mysql server database.

Update: the site has changed, and all of the comments from the post are now gone (including the .deb files that the site's owner posted for me).  I really would like to take this opportunity to discourage you from using mod-auth-mysql with a remote mysql server, but if you insist on doing so, I'll post the deb file that he gave me.

---

