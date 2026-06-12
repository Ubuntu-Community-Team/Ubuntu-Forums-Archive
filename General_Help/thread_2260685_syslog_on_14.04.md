---
title: "syslog on 14.04"
date: 2015-01-13
forum: General Help
---

### Post by myron2 on 2015-01-13
Hi all

i have a quit problem my syslog via tail -f it stop every 12 hours does anybody experience this problem?

thanks

---

### Post by bashiergui on 2015-01-13
Try using ```
less --follow-name
``` The processes updating the log file may cause the file's inode to change. From the OS point of view, it's a new file after the updates, so if you're using tail -f there won't be new entries written to the old file.

---

### Post by myron2 on 2015-01-15
Hi bash

thanks your response the problem cause of this.
 
anacron [20562] job ' cron daily ' started
craklib no update neccessary

---

