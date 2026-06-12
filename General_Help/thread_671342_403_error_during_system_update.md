---
title: "403 error during system update"
date: 2008-01-18
forum: General Help
---

### Post by explainer on 2008-01-18
It would appear that there is something broken in the system update today.  I on the lit update icon on my taskbar, and 15 of 16 packages installed, but not this one:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.3.0.0.dfsg-12ubuntu8.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.3.0.0.dfsg-12ubuntu8.1_amd64.deb)
  403 Forbidden

Somebody set the security level incorrectly, it would appear.

---

### Post by atoponce on 2008-01-18
This update is breaking systems, so it's been held back until fixed.  Or so I hear.

---

### Post by fyo on 2008-01-18
For more information see [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/183969](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/183969)

Short version: If you're getting the 403 error, don't sweat it. That'll be fixed soon (apparently) and if that means you didn't download the update while it was available, good for you!

---

