---
title: "What am i doing wrong with m cp command?"
date: 2007-06-10
forum: General Help
---

### Post by Gizim on 2007-06-10
gizim@Spartan:/$ cp /media/IPOD/Backup/My\ Music/ /storage/
cp: omitting directory `/media/IPOD/Backup/My Music/'
gizim@Spartan:/$


argh

---

### Post by EndPerform on 2007-06-10
Are you trying to copy the directory?  Try this:

```

cp -r /media/IPOD/Backup/My\ Music/ /storage/

```

---

### Post by Gizim on 2007-06-10
> **EndPerform said:**
> Are you trying to copy the directory?  Try this:

```

cp -r /media/IPOD/Backup/My\ Music/ /storage/

```

eh im such a noob.. thanks

---

