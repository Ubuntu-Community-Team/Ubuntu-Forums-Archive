---
title: "need to reset graphic configuration"
date: 2014-05-23
forum: General Help
---

### Post by Djalmahal on 2014-05-23
I tried to install the official nvidia driver. Now after the login it hangs up and I never reach unity.

All I have is the recovery mode and I want to reset so it falls back to whatever it used before (nouveau?).

When I try. To run sudo apt-get install something it says

Not using locking for read only lock file /var/lob/dpkg/lock
Unable to write to /var/cache/apt/
The package lists or status file could not be parsed or locked


Thanks

---

### Post by hyperreal on 2014-05-24
Enter into recovery mode and at the prompt run the following:  nvidia-xconfig

Reboot and see if you are able to login to a normal session.  If not, post your /var/log/Xorg.0.log.

---

