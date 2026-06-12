---
title: "mod-python version mismatch"
date: 2007-10-15
forum: General Help
---

### Post by paulhide on 2007-10-15
On restarting Apache after installing mod-python I get the following entry in the Apache error.log.
Ubuntu server version is 7.04. All other software is the default version

[Mon Oct 15 08:49:13 2007] [notice] caught SIGTERM, shutting down
[Mon Oct 15 08:49:23 2007] [error] python_init: Python version mismatch, expected '2.5', found '2.5.1'.
[Mon Oct 15 08:49:23 2007] [error] python_init: Python executable found '/usr/bin/python'.
[Mon Oct 15 08:49:23 2007] [error] python_init: Python path being used '/usr/lib/python25.zip:/usr/lib/python2.5/:/usr/lib/python2.5/plat-linux2:/usr/lib/py$
[Mon Oct 15 08:49:23 2007] [notice] mod_python: Creating 8 session mutexes based on 150 max processes and 0 max threads.
[Mon Oct 15 08:49:23 2007] [notice] mod_python: using mutex_directory /tmp
[Mon Oct 15 08:49:23 2007] [notice] Apache/2.2.3 (Ubuntu) mod_python/3.2.10 Python/2.5.1 PHP/5.2.1 configured -- resuming normal operations

This is just on the restart, no request has been made, so I don't think the two previous posts on this topic back in July are relevant.

Paul Hide

---

