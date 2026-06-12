---
title: "Wierd error"
date: 2013-08-09
forum: General Help
---

### Post by dasaint80 on 2013-08-09
Every time I tried to setup mysql i get this error.

I'm running Ubuntu 13.04, I'm about to re install and start from fresh.



```
start: Job failed to start
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.5 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.5; however:
  Package mysql-server-5.5 is not configured yet.


dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                     Errors were encountered while processing:
 mysql-server-5.5
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by bsamim on 2013-08-11
Try running the following to fix any broken packages with dependency issues

  sudo apt-get -f install

if that doesn't work then run the following and see the errors you might be getting

 sudo apt-get update && sudo apt-get upgrade

---

