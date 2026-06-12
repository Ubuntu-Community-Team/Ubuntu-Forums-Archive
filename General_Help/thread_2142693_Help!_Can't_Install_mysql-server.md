---
title: "Help! Can't Install mysql-server"
date: 2013-05-06
forum: General Help
---

### Post by Kissell on 2013-05-06
I cloned a system hard disk, and for some reason mysql wouldn't start when I put the drive in the other system.

It wouldn't uninstall either, not with apt-get.

I was able to use aptitude to remove mysql-server mysql-common and mysql-server

I also removed apparmor.

but when I go to re-install mysql, dpkg can't configure it.  WTH!

"apt-get -f install" and "dpkg-reconfigure -a" don't help.

So I removed everything in /var/lib and /etc that had "mysql" in the name, and tried to reinstall mysql-server, but still, it can't install.

```
Setting up mysql-server-5.5 (5.5.31-0ubuntu0.12.04.1) ...
start: Job failed to start
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.5 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.5; however:
  Package mysql-server-5.5 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
Processing triggers for libc-bin ...
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                         ldconfig deferred processing now taking place
Errors were encountered while processing:
 mysql-server-5.5
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Kissell on 2013-05-06
Wow...  figured it out myself...  it was NAGIOS!

The nag service was running, which uses an nconf mysql database.

I killed nagios "service nagios3 stop" and then mysql-server installed just fine.

---

### Post by Kissell on 2013-05-06
But thread tools no longer has the options to "mark this thread as solved"  ?

---

