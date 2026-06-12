---
title: "Apache crashed - can't restart because of missing directories"
date: 2014-10-09
forum: General Help
---

### Post by peter.h.m.brooks on 2014-10-09
Here's an odd little problem. I may well not have looked hard enough, but I can't find a reference to it.

It's a fairly hard problem as two separate servers have experienced the same thing. I've not managed to do a full RCA, but I thought I'd ask here to see if anybody has seen something similar.

There are no users on the machines. They are only web servers for mediawiki. 

The symptom is that they start refusing web connections. Apache isn't running.

To fix it:

#service apache2 restart

but this fails because there's no directory

/var/log/apache2

so it can't create a log file. So:

#mkdir /var/log/apache2
#chgrp www-data /var/log/apache2
#service apache2 restart

but this fails because there's no directory

/var/run/apache2

so it can't create a PID file. So:

#mkdir /var/run/apache2
#chgrp www-data /var/run/apache2
#service apache2 restart

... and all is well.

The questions are:

1. Why would apache crash?
2. Why would /var/log/apache2 not be there? What could be deleting it?
3. Why would /var/run/apache2 not be there? What could be deleting it?

It's obviously a bit more difficult to work out what's going on without the apache log files - I've not yet been able to go through all the syslog files to see what's there.

Any suggestions gratefully received.

---

### Post by bashiergui on 2014-10-11
Does this happen upon reboot? If so Maybe you mounted /var/log as tmpfs. Check your /etc/fstab file for a line like:
```
tmpfs /var/log
```
Another possibility is that you're using "disk cleanup" software or have a cronjob that purges the directory on boot.

---

### Post by SeijiSensei on 2014-10-12
I'd remove and reinstall Apache.  It should set up all those directories during installation unless you are doing something unusual like what bashiergui suggests.  I would never assign anything to tmpfs myself, particularly not things as important as /var and its subdirectories.

---

### Post by peter.h.m.brooks on 2014-10-13
Thank you for your suggestions.

---

