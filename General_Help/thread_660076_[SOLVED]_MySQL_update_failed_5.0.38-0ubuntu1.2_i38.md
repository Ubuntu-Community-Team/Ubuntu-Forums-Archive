---
title: "[SOLVED] MySQL update failed 5.0.38-0ubuntu1.2_i386.deb"
date: 2008-01-06
forum: General Help
---

### Post by Hopworks on 2008-01-06
I'm not seeing a lot in the forums on this, so I wonder if it has something to do with my installation specifically.

I'm trying to install updates to my Feisty 7.04 server, actually been trying for over a week now. The MySQL update fails and here is the output from apt-get upgrade
```
root@hopworks:~# apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be upgraded:
  mysql-server-5.0
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/25.7MB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 167096 files and directories currently installed.)
Preparing to replace mysql-server-5.0 5.0.38-0ubuntu1.1 (using .../mysql-server-5.0_5.0.38-0ubuntu1.2_i386.deb) ...
 * Stopping MySQL database server mysqld                                                                                                                                                        [fail]
invoke-rc.d: initscript mysql, action "stop" failed.
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
 * Stopping MySQL database server mysqld                                                                                                                                                        [fail]
invoke-rc.d: initscript mysql, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/mysql-server-5.0_5.0.38-0ubuntu1.2_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
 * Stopping MySQL database server mysqld                                                                                                                                                        [fail]
invoke-rc.d: initscript mysql, action "stop" failed.
 * Starting MySQL database server mysqld                                                                                                                                                        [ OK ]
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'debian-sys-maint'@'localhost' (using password: YES)'
Errors were encountered while processing:
 /var/cache/apt/archives/mysql-server-5.0_5.0.38-0ubuntu1.2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Somewhere in there it says 'Access denied for user 'debian-sys-maint'@'localhost' but not sure what that is all about. I can get into mysql just fine via
```
mysql -u debian-sys-maint -p
``` and using the usual password I have always used.
This is the first time I had a problem with an update, and I'm getting a little weary of seeing that icon on my desktop telling me I have updates I can't install. =\

Thanks for your time. =)

Hop

---

### Post by Hopworks on 2008-01-06
OK, as usual, once I post a cry for help, I figure it out. It's like magic! :)

What I did was, since I was able to get into MySQL using root (the password worked), manually shutdown mysql using root, using...
```
mysqladmin -u root -p shutdown
```
That worked, then I did an apt-get upgrade again, and the process finished without error.
I went into MySQL again, this time checking the status, and confirmed the version updated to 1.2. Now I'll see if the update icon goes away in my desktop.

thanks again everyone for your time. whew! :D

---

