---
title: "Windows partition borked and invusuble to Ubuntu"
date: 2007-10-05
forum: General Help
---

### Post by lolwhites on 2007-10-05
I've got a dual boot XP/7.04 system, and yesterday Windows started freezing on startup. I tried System restore but that made things worse - now it doesn't progress further than the blue startup screen.

Rebooted in Ubuntu, it took a long time as it said Ubuntu contained a filing system with errors. It starts OK in Ubuntu but can no longer see the Windows partition; when I try to mount it I get */dev/sda1 does not exist*. I want to get hold of the data so I can copy it somewhere before doing anything else. Any suggestions?

---

### Post by thirddeep on 2007-10-05
First see what drives / partitions exists with 
```
sudo fdisk -l
```

---

### Post by por100pre1 on 2007-10-05
> **thirddeep said:**
> First see what drives / partitions exists with 
```
sudo fdisk -l
```

Yes, do as ThirdDeep posted and post the results here.

---

### Post by lolwhites on 2007-10-05
In the end I managed to get Windows to start in Safe Mode, and solved the problem by reinstalling the antivirus. Ubuntu now sees the Windows partition as before.
Anotehr reason to have an OS that doesn't need an antivirus :)

---

### Post by por100pre1 on 2007-10-05
Which anti virus were you using?

---

### Post by lolwhites on 2007-10-05
Avast

---

