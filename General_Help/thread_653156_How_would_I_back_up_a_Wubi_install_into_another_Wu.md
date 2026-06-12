---
title: "How would I back up a Wubi install into another Wubi install?"
date: 2007-12-29
forum: General Help
---

### Post by Planets on 2007-12-29
Just in case some change in future upgrades happen that doesn't allow a Wubi install to upgrade to the next version, how would I back up my preferences, information, etc., and import them into a new Wubi install? Would the only way be to convert it to a partition install?

---

### Post by flamelab on 2007-12-30
You back-up your /home somewhere and then you paste it in the new one after the upgrade .

---

### Post by Planets on 2007-12-30
Home.disk?

---

### Post by ago on 2007-12-30
Yes all of your /home is in home.disk, so copy it somewhere and then mount it from within the new installation

mount -o loop /host/path/to/home.disk.old /new/mountpoint

---

### Post by Planets on 2007-12-31
Thanks, ago. =)

---

