---
title: "vmware server install in dapper"
date: 2006-11-03
forum: General Help
---

### Post by Chancellor on 2006-11-03
I would like to run VMWare Server on my Dapper (6.06LTS) install of Ubuntu.  I believe I have installed the software correctly, however, running the command: 
```
/usr/bin/vmware
```

results in Permission Denied unless I run as root.

Is it possible to run VMWare as a regular user?

Running ```
sudo /usr/bin/vmware 
``` works okay, but I would rather not run my virtual machines with root permissions.

---

### Post by Chancellor on 2006-11-03
Turns out this held the clue:

[http://www.vmware.com/community/thread.jspa?messageID=472299&#472299](http://www.vmware.com/community/thread.jspa?messageID=472299&#472299)

---

