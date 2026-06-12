---
title: "Can't install mysql 4.1.22 from source on Gutsy"
date: 2007-10-24
forum: General Help
---

### Post by dmjones500 on 2007-10-24
I have been installing MySQL from source (so as to match the version - 4.x - used by my web host).

Following the instructions from lamphowto.com, I have successfully completed the old configure/make/make install.  However, I've noticed that when I include the MySQL libs into the ld.so.conf file:

```
echo "/usr/local/mysql/lib/mysql" >> /etc/ld.so.conf
ldconfig
```

it causes my system to hang while booting.  It hangs just prior to showing the username and password boxes.

I'm certain that ldconfig has ruined things, since I can remove the line from ld.so.conf and run ldconfig again, which results in no hang.

Any ideas why this may be happening, and how on earth it could be affecting my boot-up?

---

### Post by dmjones500 on 2007-10-25
I haven't resolved this bizarre situation, however I don't think the ldconfig step is necessary (all the usual binaries I use seem to work without it having been run).  So, I've simply ignored this step.

Consider this... ignored :-)

---

