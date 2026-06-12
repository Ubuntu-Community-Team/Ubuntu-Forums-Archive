---
title: "gksudo not recognized"
date: 2007-02-24
forum: General Help
---

### Post by laurentdebacker on 2007-02-24
I'm trying to upgrade dapper to edgy in the way described here:

Method A ( official ):
Just do
Code:

sudo aptitude update && sudo aptitude upgrade

now that your update manager is up to date do :
Code:

gksudo "update-manager -c -d"

the first command worked like a charm but the terminak doesn't recognize gksudo to run the second.
any suggestions?

thx!

---

### Post by aysiu on 2007-02-24
Do you happen to be using Kubuntu?

---

### Post by laurentdebacker on 2007-02-24
yes I am

---

### Post by aysiu on 2007-02-24
That would explain it. Assuming Kubuntu has an update-manager, I'd imagine the command would be ```
kdesu "update-manager -c -d"
``` I've never used that method, though, so I can't vouch for it.

I've always done the changing of the sources.list and the dist-upgrade.

---

