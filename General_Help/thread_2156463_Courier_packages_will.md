---
title: "Courier packages will"
date: 2013-06-21
forum: General Help
---

### Post by mbrown2441 on 2013-06-21
I get the following error when courier packages are attempted to be installed in Ubuntu 13.04

mbrown@mikeabrown:~$ sudo apt-get install courier-imap-ssl courier-pop-ssl
Reading package lists... Done
Building dependency tree
Reading state information... Done
Suggested packages:
  courier-doc imap-client
The following NEW packages will be installed:
  courier-imap-ssl courier-pop-ssl
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 21.1 kB of archives.
After this operation, 249 kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring/universe courier-pop-ssl i386 0.68.2-1ubuntu1 [10.5 kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring/universe courier-imap-ssl i386 4.10.0-20120615-1ubuntu1 [10.6 kB]
Fetched 21.1 kB in 0s (118 kB/s)
Selecting previously unselected package courier-pop-ssl.
(Reading database ... 217525 files and directories currently installed.)
Unpacking courier-pop-ssl (from .../courier-pop-ssl_0.68.2-1ubuntu1_i386.deb) ...
Selecting previously unselected package courier-imap-ssl.
Unpacking courier-imap-ssl (from .../courier-imap-ssl_4.10.0-20120615-1ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Setting up courier-pop-ssl (0.68.2-1ubuntu1) ...
cp: not writing through dangling symlink â/usr/lib/courier/pop3d.pemâ
chmod: cannot operate on dangling symlink â/usr/lib/courier/pop3d.pemâ
chown: cannot dereference â/usr/lib/courier/pop3d.pemâ: No such file or directory
error on line -1 of /etc/courier/pop3d.cnf
3074255048:error:02001002:system library:fopen:No such file or directory:bss_file.c:169:fopen('/etc/courier/pop3d.cnf','rb')
3074255048:error:2006D080:BIO routines:BIO_new_file:no such file:bss_file.c:172:
3074255048:error:0E078072:configuration file routines:DEF_LOAD:no such file:conf_def.c:197:
dpkg: error processing courier-pop-ssl (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up courier-imap-ssl (4.10.0-20120615-1ubuntu1) ...
cp: not writing through dangling symlink â/usr/lib/courier/imapd.pemâ
chmod: cannot operate on dangling symlink â/usr/lib/courier/imapd.pemâ
chown: cannot dereference â/usr/lib/courier/imapd.pemâ: No such file or directory
error on line -1 of /etc/courier/imapd.cnf
3073599688:error:02001002:system library:fopen:No such file or directory:bss_file.c:169:fopen('/etc/courier/imapd.cnf','rb')
3073599688:error:2006D080:BIO routines:BIO_new_file:no such file:bss_file.c:172:
3073599688:error:0E078072:configuration file routines:DEF_LOAD:no such file:conf_def.c:197:
dpkg: error processing courier-imap-ssl (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 courier-pop-ssl
 courier-imap-ssl
E: Sub-process /usr/bin/dpkg returned an error code (1)

mbrown@mikeabrown:~$ sudo apt-get remove courier-imap-ssl courier-pop-ssl
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  courier-imap-ssl courier-pop-ssl
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 249 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 217538 files and directories currently installed.)
Removing courier-imap-ssl ...
 * Stopping Courier IMAP-SSL server imapd-ssl                                                                                                         [ OK ]
Removing courier-pop-ssl ...
 * Stopping Courier POP3-SSL server...                                                                                                                [ OK ]
Processing triggers for ureadahead ...
Processing triggers for man-db ...

---

