---
title: "Partition bootup"
date: 2008-03-04
forum: General Help
---

### Post by Dakillakan on 2008-03-04
Could anyone explain to me how to make it so a partition automatically mounts upon boot?

---

### Post by LuisGMarine on 2008-03-04
This guide here might help you.  I don't want to confuse you, read this guide and if you are still having trouble, post back.  Good Luck!

[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

---

### Post by Dakillakan on 2008-03-05
Thanks, but that did not seem to work.  The script was for mounting a windows partition and it did not show how to mount it upon bootup automatically.

---

### Post by murataht on 2008-03-05
You should add an entry corresponding to the partition to the fstab. check:
```
>cat /etc/fstab
```

this should show your mounted partitions. at the end of the file you should start a new line and indicate what partition to which mount point, and other options. check "man mount" for information about mount options.

good luck.

PS: if you can't figure it out, maybe you should provide as much details as you can, so that others can help you with little difficulty.

---

### Post by cszikszoy on 2008-03-05
Search for PySDM in apt or in add/remove programs.  It will allow you to set partitions to mount on startup.

---

### Post by jken146 on 2008-03-05
[www.psychocats.net/ubuntu/mountlinux](www.psychocats.net/ubuntu/mountlinux)

[www.psychocats.net/ubuntu/mountwindows](www.psychocats.net/ubuntu/mountwindows)

---

