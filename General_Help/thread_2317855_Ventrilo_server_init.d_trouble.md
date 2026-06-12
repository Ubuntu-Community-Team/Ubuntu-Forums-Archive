---
title: "Ventrilo server init.d trouble"
date: 2016-03-20
forum: General Help
---

### Post by stephen58 on 2016-03-20
I'm trying to follow the guide here: [http://corlewsolutions.com/articles/article-2-setup-ventrilo-server-3-0-3-on-32bit-or-64bit-ubuntu-any-version](http://corlewsolutions.com/articles/article-2-setup-ventrilo-server-3-0-3-on-32bit-or-64bit-ubuntu-any-version)

It is working out pretty well and I can get a Ventrilo server running directly from the command line manually - in terminal or as a daemon. However, the init script isn't working (it doesn't actually start the Ventrilo server; no .pid file is created). If I check the status after trying to start the service, it says "active (exited)" which searching Google suggests implies that something ran and finished rather than continuing to be run as a daemon. The files all appear to be in the correct directories/folders and with the correct owner and permissions. The /srv/ventsrv/ventrilo_srv.log doesn't show any errors and I don't know where else to look for a log file which might identify a problem.

What *should* the "/etc/init.d/ventrilo status" be if it was running (in addition to creating the /srv/ventsrv/ventrilo_srv.pid file which it is not currently creating)?
Is there some log I can check that would list errors if an init.d script encountered any, or are those always printed to the terminal window calling e.g. "/etc/init.d/ventrilo start"?
Can someone please hazard a guess as to what might be wrong?

Thanks.

---

