---
title: "rsync overwriting each other in crontab"
date: 2007-08-18
forum: General Help
---

### Post by dibblego on 2007-08-18
I have a crontab job to rsync a directory, but if the time interval is too short and the rsync process has not completed, the two rsyncs overwrite each other indefinitely, until the machine finally falls over and stops responding with too many rsync processes.

How can I only have one rsync process running?

---

### Post by HermanAB on 2007-08-18
You need a semaphore:
Check for the presence of a lock file in /var/lock.  If it exists, exit.
Touch the lock file in /var/lock when you start rsync and remove it when done.  

Hope that helps!

Herman

---

