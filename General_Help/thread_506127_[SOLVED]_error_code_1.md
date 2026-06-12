---
title: "[SOLVED] error code 1"
date: 2007-07-21
forum: General Help
---

### Post by upthelum on 2007-07-21
Can anyone PLEASE tell me what this error message means, and how i can fix the problem. I am trying to install various software including compiz but keep getting this message. This is so frustrating, i have been trying to fix this all week and dont know what to do now except re-installing the os, which i am reluctant to do as i am starting to get it looking just how i want.
Running Xubuntu server, athlon 64, gig ram, 250gb hdd. 

Please help im about to start pulling out what little hair i have...

Errors were encountered while processing:
 backuppc
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by upthelum on 2007-07-21
Any takers!!!

---

### Post by geraldm on 2007-07-21
error 1 would be a permissions error.  The sub-process did not have 
proper permissions at that point in the install / backuppc ? 
If it is instead a return code, and not an error code, then it just means
EXIT_FAILURE

Gerald

---

