---
title: "how exactly surface-fixing &quot;chkdsk /F /R c:&quot; at every single boot for linux?"
date: 2008-05-03
forum: General Help
---

### Post by frenchn00b on 2008-05-03
Hello,
I would like that at every single boot, the linux box does cluster per cluster the typical wonderful windows :
```
chkdsk /F /R /dev/hda1 
```
 
it takes ages, but I boot/start once every 2 days only. For me, I need a daily fixed EXT3 harddrives.
  
Man tune2fs is too complicated

---

### Post by RealPSL on 2008-05-04
While I am not agreeing with this approach the solution is not complex.
```
tune2fs -c 2 /dev/sda6
``` for example will force an fsck after the /dev/sda6 file system is mounted more than 2 times. You can adjust it accordingly to make sure it meets your requirements. This is also a one time change.

---

