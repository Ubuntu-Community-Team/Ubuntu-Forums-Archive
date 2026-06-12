---
title: "Version discrepancies of installed libraries"
date: 2013-02-22
forum: General Help
---

### Post by niranjan_rao on 2013-02-22
I am curious when/if libraries get updated when I update using sudo apt-get update/upgrade.

I have two machines saying they are uptodate in updates. However I am seeing different versions of libwebkitgtk on every machine. I don't know if these versions should be same if the patches are uptodate, or what needs to be done so that all the machines are on same version.

Machine 1: Ubuntu 12.04.2 LTS, libwebkitgtk 1.8.3-0ubuntu0.12.04.1
Machine 2: Ubuntu 12.10, libwebkitgtk 1.10.0-0ubuntu1.1

What should I do bring 12.04 machine to same webkit patch level as 12.10? As far as I know none of machines are configured to use any custom repository paths? Or is it going to be case because 12.04 is older, it will not latest webkit releases?

---

### Post by x64Architecture on 2013-02-22
The update policy is for security updates and critical bug fixes only. New upstream releases are not part of that. 

Refrences:
[https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates)
[https://wiki.ubuntu.com/SecurityTeam/UpdateProcedures](https://wiki.ubuntu.com/SecurityTeam/UpdateProcedures)

---

### Post by niranjan_rao on 2013-02-22
Thanks for the response. If I want to update the libraries to same version on every machine, what should we do?

We are notcing some difference in behavior on both platforms in my application and while it's entirely possible that the actual problem is in our code, we want to make sure other variables are exactly same.

---

### Post by snowpine on 2013-02-22
The easiest solution would be to use an identical 12.04 LTS install on all machines.

---

