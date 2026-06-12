---
title: "Edgy -&gt; Feisty upgrade frozen: now what?"
date: 2007-07-25
forum: General Help
---

### Post by doundounba on 2007-07-25
Hi all,

I've finally gotten around to trying to upgrade my main rig from (Kubuntu) Edgy to Feisty.  I did this upgrade on another computer a while (months) ago and it worked fine.  But not this time.

I believe everything downloaded...  But I can't tell because the Distribution Upgrade window is now blank.  Two other windows have popped up entitled "Error" and "Error <2>".  Both are also blank.  I'm a little reluctant to just kill the adept processes...


```
$ ps -elf | grep adept
1 S me    5514     1  0  75   0 -  8419 -      Jul15 ?        00:01:35 adept_notifier
1 S root     18494 18456  0  75   0 -  6410 -      11:45 ?        00:00:00 kio_file [kdeinit] file /tmp/ksocket-root/klauncherR8jVuc.slave-socket /tmp/ksocket-root/adept_managerfqeUgb.slave-socket
4 S root     22686     1  0  75   0 - 121075 1     17:06 ?        00:00:27 python /tmp/kde-root/adept_managerluM4Ib.tmp-extract/dist-upgrade.py --frontend DistUpgradeViewKDE
1 S root     22795 22686  0  75   0 - 121251 write_ 18:07 ?       00:00:00 python /tmp/kde-root/adept_managerluM4Ib.tmp-extract/dist-upgrade.py --frontend DistUpgradeViewKDE
0 S me   23644 23578  0  77   0 -   692 pipe_w 18:28 pts/1    00:00:00 grep adept
$
```

What would be the best way to proceed?

Thanks for any advice.

---

### Post by doundounba on 2007-07-26
Well, I finally "kill -TERM"ed the python processes.  After much hammering of "sudo aptitude dist-upgrade" and Adept's "Full Upgrade" (what choked one up seemed to be handled by the other one) as well as a "sudo dpkg --configure -a" and a "sudo apt-get autoremove", I seem to be running Feisty. (EDIT: Oh yeah, there was a "sudo apt-get -f install" in there, too.)

I'm a little worried about my system, but other than some monitor refresh rate problems, things seem to be functional...

---

