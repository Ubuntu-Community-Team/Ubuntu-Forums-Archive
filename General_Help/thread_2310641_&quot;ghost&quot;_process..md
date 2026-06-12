---
title: "&quot;ghost&quot; process."
date: 2016-01-20
forum: General Help
---

### Post by rfeala on 2016-01-20
Hello,

I'm not sure what exactly to call the condition of this process but ghost is the best description I can think of.

I was editing a text file in nano as root when I had to leave the computer for a few minutes - long enough for it to go to sleep. I resumed and went to try to reopen the file with nano and I get the message.

```
File /etc/proxpn/login.conf is being edited (by root with nano 2.4.2, PID 11179); continue?
```

I can not find the file anywhere in the file system and the process id does not show up in htop or ps aux. Kill does not work and rebooting did not help. 

Any ideas?

---

### Post by rfeala on 2016-01-21
Unlocked root and was able to start nano and save the file. Not sure why but sudo was not allowing me to edit.

---

