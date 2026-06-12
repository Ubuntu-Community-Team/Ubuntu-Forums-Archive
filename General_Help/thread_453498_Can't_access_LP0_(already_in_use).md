---
title: "Can't access LP0 (already in use)"
date: 2007-05-24
forum: General Help
---

### Post by richas on 2007-05-24
I have an application that uses the printer port (/dev/lp0).  It reports that it is already in use.  
How do I find out what is holding the port?  I have no other applications running.

Thanks

rich

---

### Post by mbradlcu on 2007-05-25
check out lsof and fuser, here's some a good links
[http://www.uwsg.iu.edu/UAU/advcomm/lsof.html](http://www.uwsg.iu.edu/UAU/advcomm/lsof.html)
[http://sial.org/howto/debug/unix/lsof/](http://sial.org/howto/debug/unix/lsof/)
```
sudo fuser -m /dev/lp0
```

---

