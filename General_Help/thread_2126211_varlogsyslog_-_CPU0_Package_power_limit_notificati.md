---
title: "/var/log/syslog - CPU0: Package power limit notification"
date: 2013-03-16
forum: General Help
---

### Post by layolayo on 2013-03-16
[FONT=arial]Hi, running a System76 Lemur 3 with an i7 sandybridge. Latest 12.10 kernel 3.5.0-26 been getting this message:
 
[COLOR=#000000]Mar 14 16:49:49 lemur kernel: [13871.223190] CPU6: Package power limit notification (total events = 2385)[/COLOR]
[COLOR=#000000]Mar 14 16:49:49 lemur kernel: [13871.223193] CPU4: Package power limit notification (total events = 2387)[/COLOR]
[COLOR=#000000]Mar 14 16:49:49 lemur kernel: [13871.223196] CPU5: Package power limit notification (total events = 2386)[/COLOR]
[COLOR=#000000]Mar 14 16:49:49 lemur kernel: [13871.223199] CPU1: Package power limit notification (total events = 2386)[/COLOR]
[COLOR=#000000]Mar 14 16:49:49 lemur kernel: [13871.223201] CPU0: Package power limit notification (total events = 2385)[/COLOR]
[COLOR=#000000]Mar 14 16:49:49 lemur kernel: [13871.223202] CPU2: Package power limit notification (total events = 2385)[/COLOR]
[COLOR=#000000]Mar 14 16:49:49 lemur kernel: [13871.223205] CPU3: Package power limit notification (total events = 2384)[/COLOR]
[COLOR=#000000]Mar 14 16:49:49 lemur kernel: [13871.223207] CPU7: Package power limit notification (total events = 2385)[/COLOR]
[COLOR=#000000]Mar 14 16:49:49 lemur kernel: [13871.224183] CPU4: Package power limit normal[/COLOR]
[COLOR=#000000]Mar 14 16:49:49 lemur kernel: [13871.224185] CPU6: Package power limit normal[/COLOR]
[COLOR=#000000]Mar 14 16:49:49 lemur kernel: [13871.224186] CPU5: Package power limit normal[/COLOR]
[COLOR=#000000]Mar 14 16:49:49 lemur kernel: [13871.224188] CPU1: Package power limit normal[/COLOR]
[COLOR=#000000]Mar 14 16:49:49 lemur kernel: [13871.224189] CPU0: Package power limit normal[/COLOR]
[COLOR=#000000]Mar 14 16:49:49 lemur kernel: [13871.224190] CPU2: Package power limit normal[/COLOR]
[COLOR=#000000]Mar 14 16:49:49 lemur kernel: [13871.224198] CPU7: Package power limit normal[/COLOR]
[COLOR=#000000]Mar 14 16:49:49 lemur kernel: [13871.224199] CPU3: Package power limit normal[/COLOR]

in my syslog for weeks. Thought it was related to an apport issue, but have now disabled apport and issue is still there. It begins at boot up and repeatedly occurs every 2-5 mins, even when laptop is idle.

[/FONT]
[FONT=arial]Any ideas?[/FONT]

---

### Post by Doug S on 2013-03-16
I have seen reports like this before, but have not seen a good solution.
See also: [http://ubuntuforums.org/showthread.php?t=1785211&highlight=power+limit+notification](http://ubuntuforums.org/showthread.php?t=1785211&highlight=power+limit+notification) , particularly post #13
and : [https://bugzilla.kernel.org/show_bug.cgi?id=36182](https://bugzilla.kernel.org/show_bug.cgi?id=36182)

---

