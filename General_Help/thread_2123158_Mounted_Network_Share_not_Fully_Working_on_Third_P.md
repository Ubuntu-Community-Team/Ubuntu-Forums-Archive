---
title: "Mounted Network Share not Fully Working on Third Party Machines"
date: 2013-03-07
forum: General Help
---

### Post by Alan5127 on 2013-03-07
Hi,

I have an interesting thing going on.  It isn't a practical issue, since I can get around it, but I would be interested to know what is causing it.

Setup:

1) External USB Drive attached to WinXP Pro SP3 machine.  The drive is used for backups, and is shared as \\Lenovo\E

2) \\Lenovo\E is mounted on an Ubuntu 11.04 machine as /Data2/Shared/Backups.  /Data2/Shared is actually the shared folder for a VBox VM (Win XP Pro SP3), but this issue is present irrespective of whether the VM (or even VBox itself) is running, so I am doubting that is a factor (but mentioning just in case!)

3) If I do run the WinXP Pro SP3 VM in VBox, it sees the /Backups directory perfectly.

4) From a third WinXP Pro SP2 (not SP3) machine, I can see /Data2/Shared fine.  I can also see the /Backups directory in there, and the files in /Backups.  However, the directories inside /Backups appear as files of size zero on the WinXP Pro SP2 machine.


Why would that be?

I realise I am effectively trying to bounce through multiple connections / links / mounts etc, so perhaps even seeing the files is a wonder at all, but I am intrigued as to why the directories don't show as directories.

As I said above, it is not a practical issue, since I can just connect from the WinXP Pro SP2 machine directly to \\Lenovo\E and it works perfectly as you'd expect.

Just curious :-)

Thanks,

Alan.

---

