---
title: "Can't Remove vmware or install updates/programs becuz of corrupted vmware install"
date: 2007-02-06
forum: General Help
---

### Post by bfob on 2007-02-06
I get the following error because of corrupted vmware install, when trying to uninstall i get the following error. 
---------------------------------------------------------------------------------------------------------------------------------
E: vmware-player: subprocess pre-removal script returned error exit status 1

---

### Post by CRCarl on 2007-02-07
I have not seen that before - but this might help. 

Make sure you don't have any VM's you want to keep in that directory first. 

```
rm -rf /usr/bin/vmware
```

---

