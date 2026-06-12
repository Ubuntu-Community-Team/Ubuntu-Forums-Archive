---
title: "still cannot change Mysql datadir in Ubuntu 18.04"
date: 2018-09-10
forum: General Help
---

### Post by mike4ubuntu on 2018-09-10
This has been an issue for a long time now.  For several years of Mysql on Ubuntu, we have not been able to change the datadir from /var/lib/mysql to something else on another drive.  This recent article for Ubuntu 18.04 and Mysql seemed to suggest that they found the solotuion, but it doesn't work:

[https://www.digitalocean.com/community/tutorials/how-to-move-a-mysql-data-directory-to-a-new-location-on-ubuntu-18-04]("https://www.digitalocean.com/community/tutorials/how-to-move-a-mysql-data-directory-to-a-new-location-on-ubuntu-18-04")

when the "datadir" property is changed in my.cnf for the daemon, mysqld will still not start up even if you follow all of the steps in the referenced article.  Has anybody found a way to make this work?

---

### Post by SeijiSensei on 2018-09-11
Installing mysql-server creates these files on my system:

```

drwx------  5 mysql         mysql         4096 Sep 11 16:11 mysql
drwx------  2 mysql         mysql         4096 Sep 11 16:11 mysql-files
drwx------  2 mysql         mysql         4096 Sep 11 16:11 mysql-keyring
drwxr-xr-x  2 root          root          4096 Jul 27 10:28 mysql-upgrade

```

Make sure your alternative location has identical permissions.

---

