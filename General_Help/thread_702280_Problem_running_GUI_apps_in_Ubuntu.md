---
title: "Problem running GUI apps in Ubuntu"
date: 2008-02-20
forum: General Help
---

### Post by PVS on 2008-02-20
When launching GUI Java apps a blank window with only a title appears and nothing more happens.

```
pvs@pvs-laptop:~$ uname -a
Linux pvs-laptop 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686 GNU/Linux
pvs@pvs-laptop:~$ java -version
java version "1.5.0_14"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_14-b03)
Java HotSpot(TM) Server VM (build 1.5.0_14-b03, mixed mode)
```

---

### Post by erginemr on 2008-02-20
Assuming that you are using Gutsy, there is a new version of Java in the repositories. Uninstalling the one in your system and installing version 1.6 may solve your problem.

---

### Post by PVS on 2008-02-20
Is it the only way you see? Not really good, I should stay with 1.5 due to some reasons. But if it's the only pissibility to solve the problem I will update Java..

---

### Post by jespdj on 2008-02-20
Do you have desktop effects (Compiz Fusion) switched on? Try switching it off to see if that helps.

---

### Post by dje on 2008-02-20
Yes i had that problem running java apps with compiz fusion running (and i was using xgl)

dje

---

### Post by PVS on 2008-02-20
Thank you all, turning off all effects solved the problem )

---

### Post by erginemr on 2008-02-20
> **PVS said:**
> Is it the only way you see? Not really good, I should stay with 1.5 due to some reasons. But if it's the only pissibility to solve the problem I will update Java..

Then you should hold off the update for some time, maybe another forum user will come up with a better idea...

---

