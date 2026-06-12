---
title: "Bacula Connection to Remote Storage Daemon issue"
date: 2015-11-15
forum: General Help
---

### Post by ishotbambi on 2015-11-15
I have 2 raspberry pi's running Ubuntu 15.10. 

1 is backup server and client which backs itself up to /mnt/backup which is a cifs share //x.x.x.x/backup without any problems or issues.

I could see the remote client from the Bacula Server and execute a job. 

However, the job hangs as the remote client or server has an issue with writing to the share I'm assuming.

Since the Pi's have a network 100mbps limitation I was wondering if it's possible to have a client run its own storage daemon to write to the CIFS share directly but can't connect to it from webmin on the Bacula server.

Anyone help or advice is greatly appreciated.  If I'm going about this all wrong please let me know and I'll be perfect with a step in the proper direction.

Thank you

---

