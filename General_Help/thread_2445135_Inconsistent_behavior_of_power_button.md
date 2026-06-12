---
title: "Inconsistent behavior of power button"
date: 2020-06-09
forum: General Help
---

### Post by 4-ubugtu-5 on 2020-06-09
I have configured the power button to shut down without asking in Preferences...Power Manager.  What I see is that about half the time it will shut down without asking, and the other half I get the "Logout Lubuntu" options pop up.  Switching preferences back and forth didn't help.

This bug: [https://bugs.launchpad.net/ubuntu/+source/lubuntu-default-settings/+bug/1319134/comments/24](https://bugs.launchpad.net/ubuntu/+source/lubuntu-default-settings/+bug/1319134/comments/24)
seemed the same, and 18.04 has the same rc.xml, so I followed the suggestion there (removing the shutdown key binding) with no change in behavior.

Lubuntu 18.04, all updates installed

---

### Post by TheFu on 2020-06-11
Do the settings in /etc/systemd/logind.conf conflict in any way?

---

### Post by guiverc on 2020-06-11
That bug was old, and related to an EOL release, so I've just tagged it incomplete (*countdown for closure*), so if you believe it's a bug, you should report it a new bug (please reference that bug as similar or possibly connected to your new bug).  [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

