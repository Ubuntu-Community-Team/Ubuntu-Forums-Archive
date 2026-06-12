---
title: "Upstart with Bash Script"
date: 2013-06-18
forum: General Help
---

### Post by sslx on 2013-06-18
I have a script that starts and stops its service.
Also, the script takes an arguement like.
./seafile.sh start
./seafile.sh stop
How can I attach this to the upstart?
I assume I can't use exec or script since starting and stopping needs different commands?
Can I just use pre-start script and pre-stop script with no exec and empty regular script?
Thanks,

---

### Post by Cheesehead on 2013-06-18
Split any appropriate elements into "pre-start script" and "pre-stop script" elements for Upstart.
The actual /path/to/service should be on the "exec" line

Exec does more than start the service. Upstart uses that line to track the service's PID for later stopping.
So you should not need an explicit line to stop the service.

---

