---
title: "crontab job crashes in hardy"
date: 2008-06-20
forum: General Help
---

### Post by cottonmouth on 2008-06-20
After upgarding my slicehost to hardy my cronjobs are choking.

I have a cronjob that takes about 30 minutes, it downloads some .txt files from a web-site. 

When I log in and run them through a ssh terminal, everything's ok.

As a cron-job, they usually crash after about 5 minutes.
(They worked as a cron-job before 8.04)

Any suggestions would be really welcome, I've debugged this for 6 weeks without much to show for :confused:

---

### Post by cmnorton on 2008-06-21
What's in the first line of the shell script for the job, #!/bin/sh, #!/bin/bash, nothing, or something else? Our production systems are Red Hat. By default /bin/sh points to /bin/bash in Red Hat. By default, /bin/sh points to /bin/dash in Debian/Ubuntu. This was one of my first learning curves in seeing if we could put our home-grown tax collection system on Ubuntu. (We can.)

I've had a lot of things go wrong wjen #!/bin/sh was assumed. And, although it should not make a difference I have for good measure set /etc/crontab's SHELL environment variable  to /bin/bash as well. (It should not make a difference, because you are specifying the shell in the shell script itself.)

Other than this, try to come up with some dummy shell scripts that don't do as much and let them run at a smaller interval, using lots of debugging output. You should get email from cron, unless you redirect output on the cron line.

The bottom line is I have like you had a lot of manually executed scripts run just fine from the command line but not from cron.  

One last thing, who has permissions from the command line, and who has them from cron? That is in /etc/crontab who is the user, or if you are using crontab -e, which user is running the job?  When in doubt, run as root, and that's a topic for another post.

Edit:
------

I did not want to assume you would not have looked in /var/logs, but it cannot hurt to look in /var/log/messages, /var/log/syslog, and the cron logs.

---

