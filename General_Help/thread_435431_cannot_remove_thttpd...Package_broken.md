---
title: "cannot remove thttpd...Package broken?"
date: 2007-05-06
forum: General Help
---

### Post by doyenguy on 2007-05-06
Fresh install of Edgy.

Done an apt-get upgrade.

Happened to install thttpd to play with.

I'm done with it now, but can't remove it.  Whether I manually start it or it's not running, apt-get still can't remove it.

# apt-get remove thttpd
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  thttpd
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  thttpd
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
Need to get 0B of archives.
After unpacking 221kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 110759 files and directories currently installed.)
[B]Removing thttpd ...
Stopping web server: kill: 60: No such process

dpkg: error processing thttpd (--remove):
 subprocess pre-removal script returned error exit status 1
Errors were encountered while processing:
 thttpd
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/B]

---

### Post by n2j3 on 2007-12-19
yeah, for some reason if the thttpd daemon is not running it cannot be removed.

run thttpd and then proceed in removing it

---

