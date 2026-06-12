---
title: "rsyslog error after update"
date: 2014-01-25
forum: General Help
---

### Post by clearski on 2014-01-25
Hi, everyone!

I've updated one of my systems last night (Ubuntu 12.04.4 LTS (GNU/Linux 3.8.0-35-generic i686)), but the installer returned an error at the end. The system was working fine and is still working fine, except this:

```
user@host:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Setting up rsyslog (5.8.6-1ubuntu8.6) ...
start: Job failed to start
invoke-rc.d: initscript rsyslog, action "start" failed.
dpkg: error processing rsyslog (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 rsyslog
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Tried to follow some online hints:

```
user@host:~$ sudo dpkg --configure -a
Setting up rsyslog (5.8.6-1ubuntu8.6) ...
start: Job failed to start
invoke-rc.d: initscript rsyslog, action "start" failed.
dpkg: error processing rsyslog (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 rsyslog
```

```
user@host:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up rsyslog (5.8.6-1ubuntu8.6) ...
start: Job failed to start
invoke-rc.d: initscript rsyslog, action "start" failed.
dpkg: error processing rsyslog (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 rsyslog
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I can't figure out a solution. I would have tried to _purge_ rsyslog and reinstall the package, but *ubuntu-minimal* is going to be removed too, I'm not sure it's a good idea? Is it safe to purge them both and then reinstall without rebooting? Or is there any other solution?

Thank you!

---

