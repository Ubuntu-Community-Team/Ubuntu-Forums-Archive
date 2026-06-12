---
title: "My first cron job"
date: 2006-11-16
forum: General Help
---

### Post by luken8r on 2006-11-16
Im attempting my first cron job and its not quite working.

I wrote a shell small script to start a daemon if it is not detected. The script works if I just call it by its self so I doubt that is the problem

Script: 
#!/bin/sh
pidof l2tpd
if [ $? -eq 1 ]; then
 /usr/sbin/l2tpd 
echo "Process $? now running"
fi


I want this scrip to run every minute, so if the daemon is not detected (its been crashing) restart it.  I made a new entry in the crontab as:

root@here:/tmp# crontab -e
no crontab for root - using an empty one

* * * * * /tmp/crontest.sh

Good, so I check the table as root again (process needs root permission to run):

root@here:/tmp# crontab -l
* * * * * /tmp/crontest.sh

Yep, its there 

Next, I check to see the process is running, so I kill it and sit back and wait. 
Nothing happens.
I call the script by
sh -x /tmp/crontest.sh
grep for the process and its there after execution

What did I do wrong?  Do I need to actually execute the script in the cron file (sh -x)?

Any tips are appreciated

---

### Post by luken8r on 2006-11-16
Update;

I got it to restart by adding the shell command to the cron job

* * * * * sh -x /tmp/crontest.sh

But the echo to screen isnt working....yet ;)

---

### Post by streeto on 2006-11-16
See this thread: [http://ubuntuforums.org/showthread.php?t=284895](http://ubuntuforums.org/showthread.php?t=284895)

Output from a cron job is forwarded to your local mail account. You may add a line containing

MAILTO=yourmail@address.com

to override the destination.

---

