---
title: "Update Failure"
date: 2013-01-01
forum: General Help
---

### Post by ProxyCyber on 2013-01-01
So I installed ecryptfs-utils. Using sudo apt-get ecryptfs-utils. Didn't   install but the next time I did sudo apt-get update, it said 

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

How can I UNINSTALL  ecryptfs-utils using terminal or some other way? What's the issue?

---

### Post by d4rk0wl on 2013-01-01
That error does not seem to be an issue with ecrytptfs-utils, it seems there is another process using the apt program. 
Do you have the GUI software update running?

Does this happen after a reboot?

Regards,
- D4rk0wl

---

### Post by ProxyCyber on 2013-01-01
Great. Thanks. Solved post-reboot.

---

### Post by lisati on 2013-01-02
Thread closed: duplicate of [http://ubuntuforums.org/showthread.php?t=2100442](http://ubuntuforums.org/showthread.php?t=2100442)

Starting duplicate threads dilutes the community's ability to help.

If you disagree with the earlier decision to move your other thread to "Other OS talk", you are welcome to use the [Resolution Centre]("http://ubuntuforums.org/forumdisplay.php?f=123") to politely state your case.

---

