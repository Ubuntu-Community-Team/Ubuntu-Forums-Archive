---
title: "compiz extras"
date: 2015-03-09
forum: General Help
---

### Post by Pedroski55 on 2015-03-09
compiz extras are not available in the 64 bit 14.04 repos. I really love wobbly windows. Where can I get them?? If I put compiz-plugins in the software centre, there is nothing of that name.

---

### Post by deadflowr on 2015-03-09
```
sudo apt-get install compiz-plugins
```
they dropped the "extras".

If you cannot see the package in the software center, make sure you have the univerase reposity enabled.
compiz and compiz-core are in the main repository, but the compiz-plugins (extras) are in universe.

---

### Post by Bucky Ball on 2015-03-09
*Thread moved to **General Help**.*

***Installation & Upgrades*** is for installing/upgrading the OS. ;)

---

### Post by Pedroski55 on 2015-03-09
Thanks! I went to system settings>Software and Updates and ticked Canonical Partners.

That seemed to do the trick. After that the software centre found compiz-plugins.

---

### Post by monkeybrain20122 on 2015-03-09
It shouldn't have anything to do with Canonical's Partners.

---

### Post by deadflowr on 2015-03-09
> **monkeybrain20122 said:**
> It shouldn't have anything to do with Canonical's Partners.

I wonder if it is less about enabling the partner repos and more of the repos getting refreshed/reloaded.
The repos probably weren't being refreshed properly. Enabling the partner repos auto-reloads/refreshes them.

Anyway if the OP found the issue [solved then mark this thread as such]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads"), please.

---

### Post by dino99 on 2015-03-09
Take care that , except the default installed compiz packages, most of the exotic/extra plugins are the best way to get heavy troubles with your system: they are mostly non maintained, buggy and abandonned since a while.

---

