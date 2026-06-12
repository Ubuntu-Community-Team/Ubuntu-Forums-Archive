---
title: "Purging bootchart leaves stuff behind"
date: 2007-02-28
forum: General Help
---

### Post by duns0014 on 2007-02-28
So I installed bootchart so I could check my boot times when I was tweaking my system.  I decided I didn't need it anymore so I purged it.  Unfortunately, it left a little of itself behind.  After I boot up now, I get these guys:

root       834  0.0  0.0   1064   200 ?        S    10:44   0:01 /bin/busybox sh /bin/bootchart bottom
root       839  0.0  0.0   1064   196 ?        S    10:44   0:00 /bin/busybox sh /bin/bootchart bottom
root       844  0.1  0.0   1064   236 ?        S    10:44   0:08 /bin/busybox sh /bin/bootchart bottom
root     10872  0.0  0.0    168    32 ?        S    12:30   0:00 /bin/sleep 0.2
root     10876  0.0  0.0    168    32 ?        S    12:30   0:00 /bin/sleep 0.2
root     10880  0.0  0.0    168    32 ?        S    12:30   0:00 /bin/sleep 0.2

Those first guys are up near the top, snuggled in between some kernel stuff in [brackets], the last three always end up at the bottom for some reason.  I looked at the description under aptitude and it said something about bootchart adding some script to initramfs.  So I'm suspecting that's where it's coming from, but I'm not sure.  Any help?

---

### Post by duns0014 on 2007-03-02
No one?

---

### Post by duns0014 on 2007-03-05
I fixed this myself: [https://launchpad.net/ubuntu/+source/bootchart/+bug/89258](https://launchpad.net/ubuntu/+source/bootchart/+bug/89258)

---

