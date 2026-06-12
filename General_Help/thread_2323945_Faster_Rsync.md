---
title: "Faster Rsync"
date: 2016-05-09
forum: General Help
---

### Post by dannymichel on 2016-05-09
Is there maybe an rsync cache or something like that? A way to speed up rsync for a directory you frequently do rsync to?

---

### Post by Habitual on 2016-05-09
I take it the destination is a remote host?

---

### Post by dannymichel on 2016-05-09
Not necessarily. Same location, but network drives wireless

---

### Post by nerdtron on 2016-05-09
I'm looking for solutions too but I find wireless + rysnc on remote drives is slow. Since rsync also uses ssh encryption overhead will also consume bandwidth. In my experience, samba shares perform better if you have network drives.

---

### Post by dannymichel on 2016-05-09
> **nerdtron said:**
> I'm looking for solutions too but I find wireless + rysnc on remote drives is slow. Since rsync also uses ssh encryption overhead will also consume bandwidth. In my experience, samba shares perform better if you have network drives.

Unfortunately cant SMB
This is a time capsule and drive connected via time capsule

---

