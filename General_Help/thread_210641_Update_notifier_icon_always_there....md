---
title: "Update notifier icon always there..."
date: 2006-07-07
forum: General Help
---

### Post by patrickfromspain on 2006-07-07
Hi there!

I have some kind of problem with the update notifier icon: it's always there, although there aren't any updates. It also shows an error, saying something about not being able to read the sources.list file and I should go to synaptic to solve the problem.

Anyone has similiar issues?

---

### Post by falcon15500 on 2006-07-07
Can you post your /etc/apt/sources.list ?

falc

---

### Post by Mike-97470 on 2006-07-08
I had the same problem after installing 6.0.6.  The file /etc/apt/sources.list had only root permissions.  I changed the Read permissions to "all" and that fixed it.  Apparently the update notifier only has user privleges.

---

