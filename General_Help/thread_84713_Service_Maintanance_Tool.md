---
title: "Service Maintanance Tool"
date: 2005-10-31
forum: General Help
---

### Post by twelvegates on 2005-10-31
There is *update-rc.d* to manage a specific service. But it cannot list all *available*/*active* services.
Is there a tool that can list all available and all active services? (It might be gui or command line.)

---

### Post by Xian on 2005-11-01
Try installing & using sysv-rc-conf.

```
$ sudo apt-cache policy sysv-rc-conf
sysv-rc-conf:
  Installed: 0.99-1
  Candidate: 0.99-1
  Version table:
 *** 0.99-1 0
        500 http://us.archive.ubuntu.com breezy/universe Packages
        100 /var/lib/dpkg/status
```

---

