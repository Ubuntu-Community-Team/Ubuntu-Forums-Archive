---
title: "ubuntu no forward"
date: 2008-03-08
forum: General Help
---

### Post by radsqd on 2008-03-08
I tried to install ubuntu 8.04 alpha 6 intel 86 desktop iso. Mounted the iso and tried installing with wubi
The installation goes fine and when i reboot and ubuntu installtion starts

it goes directly to step 6 of 7 on migration settings, it asks me to either click and allow migration of windows xp profile or skip it by pressing forward.  Either way ** I can only hit cancel, the forward button is not clickable.**I have tried every option including verbose mode and same result. 

Any help would be appreciated to remedy the situation

Iam running win xp on amd 64 processor and 512 mb ram

---

### Post by ago on 2008-03-09
That is a known bug, you can track it here: [https://bugs.launchpad.net/wubi/+bug/195905](https://bugs.launchpad.net/wubi/+bug/195905)
It will be addressed in coming releases

---

### Post by switchfrenzy5 on 2008-03-18
Any ideas when this will be? Thanks.

---

### Post by ago on 2008-03-18
Evand takes care of that, but it would help if we had full logs from you...

---

### Post by ago on 2008-03-18
For the logs:

1 Uninstall and reninstall (using wubi 455 and latest daily ISO)
2 Press esc at boot after selecting ubuntu
3 Select verbose mode
4 When you get to the point where you see the m-a dialog, press ctrl+alt+f2 to get to a console. Run

sudo zip -r /host/ubuntu/installation-logs.zip /var/log

5 c:\ubuntu\installation-logs.zip should now be available under windows. Attach it here or to the bug report.
6 thanks

---

