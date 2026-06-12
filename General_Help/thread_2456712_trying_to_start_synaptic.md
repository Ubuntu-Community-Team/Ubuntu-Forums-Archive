---
title: "trying to start synaptic"
date: 2021-01-17
forum: General Help
---

### Post by jgw on 2021-01-17
I am trying to start synaptic.  When I do I get an error which says:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

This occurs when I try to run "dpkg --configure -a"   dpkg is not running, synaptic is not running.  I think this all has to do with flash and pepper flash.  I thought I would just delete both of those and start over.  (I know, there are problems with flash).  Anyway, when I tried to delete/purge either one they are not found.  I then checked for files with "pepperflash", "flash", "adobe flash", etc.  I got lots of those.  Then I decided I would try and just delete the files.  Can't seem to do that either, even when running as a superuser.  

I have a mess and have no idea how to proceed.  Oh, I did reboot my system to see if that helped, it didn't.  

Thoughts?

---

### Post by kansasnoob on 2021-01-18
What is the full output of:

```
sudo dpkg --configure -a
```

---

### Post by jgw on 2021-01-18
I get this in a box:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report.

---

### Post by CelticWarrior on 2021-02-11
So, what happens exactly when you run the command the error message tells you to run? The same question as before...

---

### Post by jgw on 2021-02-11
Oh, sorry, it fixed the problem and I set this to solved without telling anybody - sorry..................

---

