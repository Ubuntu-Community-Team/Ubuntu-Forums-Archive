---
title: "100% CPU Usage - Nautilus"
date: 2007-12-17
forum: General Help
---

### Post by md5hash on 2007-12-17
Nautilus is eating all my ram.. whenever i kill the process it keeps coming back.. my system is really slow..

---

### Post by Lostincyberspace on 2007-12-17
Run this and see if it helps.
```
sudo apt-get clean
```

---

### Post by FuturePilot on 2007-12-17
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/bugs/150471](https://bugs.launchpad.net/bugs/150471) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				There wouldn't happen to be a nautilus-debug-log.txt in your home folder would there be?

---

### Post by md5hash on 2007-12-18
i tried the workaround in launchpad.. but its but working.

---

### Post by md5hash on 2007-12-19
bump

---

### Post by cegpope on 2008-01-06
I'm having this problem too, and no it is not the same one as described in the bug, because Nautilus keeps using 100% of the CPU without logging out and back in again.

If I open the home folder, or browse any folders for that matter, and close the window, Nautilus continues to run in the processes at 100% and to the best of my ability to tell, it happens randomly.

---

