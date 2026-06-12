---
title: "PM-UTILS Question (Saucy)"
date: 2014-07-18
forum: General Help
---

### Post by diego-rivera on 2014-07-18
Hello, all!

I'm currently plagued by a problem that happens whenever the system attempts to suspend from idle, but a background process was writing information to a CIFS share (i.e. a backup, for instance). The result is that the computer fails to suspend, and makes no attempt to fix the situation, so it just kind of "sits there", still alive (I can use it), with no networking (I can restart it by restarting network-manager, but when I do, the suspend process then resumes and completes normally).

My solution to the problem was creating a script that could be run from /etc/pm/sleep.d, and that would check to make sure no such shares were being accessed at the time of the suspend attempt, and aborting the suspend if that was the case.

All well and good, in theory.

In practice, however, it appears that networking is taken down before the PM hooks are run, and thus if I try to check who is using the mounts, the result is a hung process (since networking is down), and thus the suspend attempt also hangs because the hooks were not run successfully (in particular, the "file use checker" that I added is hung, and thus pm-suspend is hung with it).

I've been looking through all those scripts and I've not found the explicit, specific area where networking is taken down. The hope would be to enable hooks to be run prior to that, and thus meet my objective.

Can someone help out here? I've been looking through the pm-utils documentation but nothing stands out as useful.

Any help is appreciated.

Thanks!

PS/ while this is on Saucy, I suspect the same issue will be present when I upgrade to Trusty later this month.

---

