---
title: "Cleaning /var/run on shutdown?"
date: 2007-05-29
forum: General Help
---

### Post by jordanm on 2007-05-29
I've been having a wireless network problem, where my wireless was working and now stopped working. I have tracked it down to a problem with /var/run/*.pid not being deleted and as a result certain services think they are already running and do not start.

When I remove /var/run/* before reboot, it solves the problem, but what I am wondering is if there is a certain script that should be doing this automatically. My bootup scripts are not set to the default so i am wondering if I accidently disabled something that is supposed to remove these files. I looked around at /etc/init.d/bootclean and some other scripts that call on it, yet I can't find it in there.

Worst case scenario, I can add 'rm -f /var/run/*' script to init 6 and 0, but I'd prefer not to have to do that if there is already something built in to do the job.

Jordan

---

### Post by jordanm on 2007-05-29
I'm using Feisty-Desktop-i386, by the way.

---

### Post by jordanm on 2007-05-29
Bump

---

