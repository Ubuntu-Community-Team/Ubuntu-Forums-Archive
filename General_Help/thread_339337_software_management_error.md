---
title: "software management error"
date: 2007-01-15
forum: General Help
---

### Post by deaddylan123 on 2007-01-15
Hey,
well everytime i try to run or install an update, i get that 'only one software management tool is allowed to run at the same time' error. ive restarted my computer many times and i doesnt go away, so i cant update or run any installers.

help is appreciated - thaks
deaddylan123

---

### Post by leona on 2007-01-19
Yep getting the same here.  Checked system, this application is NOT running anywhere, so I'm assuming a lock file hasn't been cleaned out, where is it and what's it called so I can kill it please, thank you

Arr just ran this

sudo dpkg --configure -a

Which cleared the problem

---

### Post by Littleweseth on 2007-01-19
one lockfile is /var/lib/dkpg/lock; and the other is /var/lib/aptitude/lock,

do 'sudo rm /var/lib/dpkg lock' and 'sudo rm /var/lib/aptitude/lock' at a terminal.

---

