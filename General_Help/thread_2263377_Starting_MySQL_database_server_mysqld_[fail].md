---
title: "Starting MySQL database server mysqld [fail]"
date: 2015-01-31
forum: General Help
---

### Post by chris_g2 on 2015-01-31
I'm new to ubuntu.  Linux in general for that matter.  I'm learning how to utilize the command prompt and have a rough foundation, so expect my post to be very newbie like in nature.

I've installed mysql to ubuntu.  For some reason, while attempting to start mysql at system reboot, it fails.  It will attempt to start at startup, but it's unsuccessful.

Fortunately, I can simply type "sudo /etc/init.d/mysql start" and mysql will startup without a problem.  I can't for the life of me figure out why when at startup, it's unable to start.

I've done lots of searches, found a few similar questions, but have been unable to find a response which resolved my issue.

---

### Post by chris_g2 on 2015-02-02
Any thoughts?

---

### Post by steeldriver on 2015-02-02
Anything in the dmesg log or /var/log/mysql/error.logs?

---

