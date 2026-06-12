---
title: "Stop Checkinstall From Overwriting Files From Other Packages"
date: 2007-03-26
forum: General Help
---

### Post by SavantEdge on 2007-03-26
Here's the error I'm getting:
```
(Reading database ... 200784 files and directories currently installed.)
Unpacking mail-notification (from .../mail-notification_4.0-1_i386.deb) ...
dpkg: error processing /home/neil/Desktop/mail-notification-4.0/mail-notification_4.0-1_i386.deb (--install):
 trying to overwrite `/usr/lib/libgconf2-4/2/libgconfbackend-xml.so', which is also in package libgconf2-4
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /home/neil/Desktop/mail-notification-4.0/mail-notification_4.0-1_i386.deb
/var/tmp/YXDOVHKHZjEAPQPTreBjb/dpkginstall.log (END) 
```

I don't have the normal mail-notification from the repos.  I wanted to compile my own so that it'd have SSL support.

---

