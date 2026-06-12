---
title: "trying to update mysql starts carmen?"
date: 2008-03-29
forum: General Help
---

### Post by themoebius on 2008-03-29
I'm using Carmen as a robotics framework for a project, but I've no idea why when I try to upgrade mysql with apt it tries to start carmen and returns an error, preventing mysql from configuring. I don't know how the two are related at all. I don't think I have carmen installed by any kind of package - its compiled from source.

```

root@zac-desktop:/home/zac# dpkg --configure mysql-server-5.0
Setting up mysql-server-5.0 (5.0.45-1ubuntu3.3) ...
 * Stopping MySQL database server mysqld                                 [ OK ] 
CARMEN - Carnegie Mellon Robot Navigation Toolkit - Version 0.7.0

Could not connect to central.

Did you remember to start central?
Did you remember to set your CENTRALHOST variable? It is currently not set.
ATTENTION: An error has occured. More info is in the syslog!
CARMEN - Carnegie Mellon Robot Navigation Toolkit - Version 0.7.0

Could not connect to central.

Did you remember to start central?
Did you remember to set your CENTRALHOST variable? It is currently not set.
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 mysql-server-5.0


```

---

