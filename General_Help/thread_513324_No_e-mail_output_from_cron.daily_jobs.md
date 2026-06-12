---
title: "No e-mail output from cron.daily jobs"
date: 2007-07-30
forum: General Help
---

### Post by volumen1 on 2007-07-30
Getting cronjobs to e-mail their output in Ubuntu has been a real hassle so far.  I have 2 machines with identical installs and one is working and the other isn't.  To get both of them working I had to add this line to /etc/crontab

MAILTO=root

Now, on one of the machines.  I wrote a simple test script called 1emailtest


$ ls -al 1emailtest
-rwxr-xr-x 1 root root 72 Jul 23 12:55 1emailtest

$ cat 1emailtest
#!/bin/bash

echo "This is a test of cron output e-mail with /bin/bash"

I get no output mailed to me from this script.   However (get this) when I move th is script into /etc/cron.hourly it works fantastically.  I get e-mail output that looks like this:

/etc/cron.hourly/1emailtest:
This is a test of cron output e-mail with /bin/bash

Does anyone have any ideas?

Also, I should mention that I get e-mail from my daily cron-apt jobs without any problems.  But that runs out of /etc/cron.d so maybe that's why.

---

