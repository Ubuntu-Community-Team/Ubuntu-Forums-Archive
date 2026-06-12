---
title: "powernowd and startup issues..."
date: 2007-04-22
forum: General Help
---

### Post by ryantmer on 2007-04-22
I currently have two problems, both of which started after upgrading to Feisty:

1. I can startup fine, but after a few minutes, the system does some sort of reset, and flashes something about "starting powernowd"... it then seems to logout, but when I try to log back in, it freezes and I have to power down.

2. When booting in recovery mode, I get a message that says "mount: special device /dev/hda1 does not exist". The odd thing is, the system can still boot normally, but with the above problem.

---

### Post by ryantmer on 2007-04-22
I googled it, and apparently powernowd is some CPU speed/temp thingy, so I'm guessing that maybe it's overheating? (It has had this problem before, when it still had Windoze...)


Er, meant to click "Edit" there, not new reply...

---

### Post by ryantmer on 2007-04-23
Somewhat pointless post, but I think I fixed it... I checked the system log, and it would do this after 15 minutes of non-activity. By coincidence, this is when my system is supposed to go sleep. So, I stopped it from going to sleep, and that seemed to solve the problem. Also, I uninstalled powernowd, just to be safe (and to get a little bit or wrath/stress relief). ^_^

---

