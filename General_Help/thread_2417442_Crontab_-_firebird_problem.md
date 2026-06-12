---
title: "Crontab - firebird problem"
date: 2019-04-23
forum: General Help
---

### Post by fenyxiakk on 2019-04-23
Hey,

I have bash script to make copy file's. But it must stop firebird before copy and start firebird after copy.

Manually script work fine but when i use crontab to auto run script firebird can stopped but after copy files don't start.

To run firebird i use
/etc/init.d/firebird start

---

### Post by TheFu on 2019-04-23
cron tasks don't have many environment variables set when compared to an interactive login.  It is a common error in crontab scripts.  Set the missing, important, environment variables in your copy script.  Also, be certain that tasks run using the expected userid.

---

