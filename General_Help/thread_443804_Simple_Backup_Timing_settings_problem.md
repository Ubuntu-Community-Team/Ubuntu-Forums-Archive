---
title: "Simple Backup: Timing settings problem"
date: 2007-05-14
forum: General Help
---

### Post by dryder on 2007-05-14
Hi,

In Administration>Simple Backup Config>Time I want full backups only, to occur at 0500 on Sunday, Wednesday and Friday.

I have set Time to:
0 05 * * Sun,Wed,Fri
Do a full backup at least once every: 1 days

I have also tried:
0 05 0 0 0,3,5
Do a full backup at least once every: 1 days

but the backups do not occur.

Any help please? (I have read man 5 crontab)

MTIA,
David

---

