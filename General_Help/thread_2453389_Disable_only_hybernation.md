---
title: "Disable only hybernation"
date: 2020-11-09
forum: General Help
---

### Post by miel13 on 2020-11-09
Hello :)

How can I disable only the hybernation please (and keep suspend to ram) ?
I want not write the ram memory to the disk.
My swap is disabled (32go ddr).

1/ Method 1 :
[HTML]Edit : /etc/systemd/sleep.conf

AllowSuspend=yes
AllowHibernation=no
AllowSuspendThenHibernate=no
AllowHybridSleep=no
#SuspendMode=
SuspendState=mem standby freeze[/HTML]

2/ Method 2 :

[HTML]sudo systemctl unmask sleep.target suspend.target
sudo systemctl mask hibernate.target hybrid-sleep.target suspend-then-hibernate.target[/HTML]

Are both methods safe?

Thx !

---

### Post by CelticWarrior on 2020-11-09
Welcome.

Suspension is enabled and hibernation is disabled, both by default.

---

