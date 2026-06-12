---
title: "How to safely break off hung program installation - Tellico"
date: 2017-06-16
forum: General Help
---

### Post by JamButty on 2017-06-16
Having problems with the media collector package Tellico. After a wipe/reinstall (16.04) it hung on installation (via standard unity Ubuntu Software option). No further installations could proceed, so I rebooted. This left me with a raft of dependency problems and a critical system bit left in a "half-installed" state, permanently preventing further installs.  I found no solution to this, so I did another wipe/reinstall. Attempted install of Tellico again after several days of problem-free function. Gee, guess what happened? Prior issue post -https://ubuntuforums.org/showthread.php?t=2363643

So rather than reboot and risk borking my system once again - how do I safely break off this hung installation? I have found no reports of this kind of problem with Tellico here or on its own site.

---

### Post by deadflowr on 2017-06-16
What shows you for
```
dpkg -l tellico
```
or
```
dpkg -l | grep tellico
```
post back output, if any.

---

### Post by JamButty on 2017-06-16
tried capitalized and not - same answer
> dpkg-query: no packages found matching tellico



---

### Post by JamButty on 2017-06-17
command line attempt at install failed, predictably.> sudo apt update && sudo apt install tellico
[sudo] password for max: 
Reading package lists... Done
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/

---

### Post by deadflowr on 2017-06-17
It means that apt is already running, somewhere, somehow, on the system.
What version of Ubuntu is it?

---

### Post by JamButty on 2017-06-17
16.04 yes, I have not rebooted yet so it is still running.

---

### Post by JamButty on 2017-06-17
determined pids locking file and issued kill commands to no effect, but 
> sudo pkill aptd
cleared the lock. gui install of another app worked, then command line install of tellico worked.
Why libqt5script5 got stuck in a half-installed state requiring a wipe and reload previously remains a mystery, but all looks kosher now.

---

