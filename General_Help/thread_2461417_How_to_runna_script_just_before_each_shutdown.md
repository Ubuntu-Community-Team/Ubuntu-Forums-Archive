---
title: "How to runna script just before each shutdown"
date: 2021-04-30
forum: General Help
---

### Post by Paloseco on 2021-04-30
Hi people. Need to automate the execution os certain command (s), as soon as I choose to power off or re-boot my Kubuntu. What would be the approach, for either running as limited user or as root?

---

### Post by dragonfly41 on 2021-04-30
Why not write a shutdown.py script which

runs your custom script(s) in sequence
shutdown Ubuntu thereafter,

shutdown via command line. 

[https://vitux.com/ubuntu/](https://vitux.com/ubuntu/)

In python use subprocess (which runs commands)

[https://docs.python.org/3/library/subprocess.html](https://docs.python.org/3/library/subprocess.html)

---

### Post by TheFu on 2021-04-30
On a laptop, I have it suspend nightly about 5 minutes after backups finish. The delay is so the backup completion report gets emailed.
It could just as easily shutdown rather than suspend.  The backup script can be run prematurely manually or it will be run automatically via cron.
My script:```
#!/bin/bash
/root/bin/backup-to-rom.sh 
sleep 5m
/usr/sbin/pm-suspend
```

"rom" is my backup server.  This script is run from the root crontab normally, but it can be run via sudo as well.

---

