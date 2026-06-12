---
title: "Cannot update Ubunntu 12.04.1 (sysvutils)"
date: 2012-12-18
forum: General Help
---

### Post by jomoyomo on 2012-12-18
Updateing systutils causes error..

Here is log:

```


installArchives() failed: (Reading database ...  (Reading database ... 5%% (Reading database ... 10%% (Reading database ... 15%% (Reading database ... 20%% (Reading database ... 25%% (Reading database ... 30%% (Reading database ... 35%% (Reading database ... 40%% (Reading database ... 45%% (Reading database ... 50%% (Reading database ... 55%% (Reading database ... 60%% (Reading database ... 65%% (Reading database ... 70%% (Reading database ... 75%% (Reading database ... 80%% (Reading database ... 85%% (Reading database ... 90%% (Reading database ... 95%% (Reading database ... 100%% (Reading database ... 223012 files and directories currently installed.) 
Unpacking sysvutils (from .../sysvutils_2.86.ds1-14.1ubuntu45.1_amd64.deb) ... 
dpkg: error processing /var/cache/apt/archives/sysvutils_2.86.ds1-14.1ubuntu45.1_amd64.deb (--unpack): 
 trying to overwrite '/usr/share/man/man1/mesg.1.gz', which is also in package sysvinit-utils 2.88dsf-13.10ubuntu11.1 
No apport report written because MaxReports is reached already
Processing triggers for man-db ... 
Errors were encountered while processing: 
 /var/cache/apt/archives/sysvutils_2.86.ds1-14.1ubuntu45.1_amd64.deb 
Error in function:  

```


Thanks

---

