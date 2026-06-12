---
title: "mount problems"
date: 2013-08-11
forum: General Help
---

### Post by buffchick on 2013-08-11
So, I made some changes to my raid arrays. I added more disks to one array and removed a whole second array. Now I'm getting some errors when I try to mountall and I'm not sure what they mean. Googling has yielded little. I'm thinking that the swap is because I moved where the drive to a different position on the sata card. (When I went to install, it will only install from position 4 on the card but will only boot from position 1. After hours of trying to figure it out it was just easier to install on one and move it when I was done.) I'm not to sure about that gvfs thing. I'm running 11.10 with xfce. Hoping someone can help point me in the right direction.

```
test@mediaserver:~$ sudo mountall
/bin/sh: gvfs-fuse-daemon: not found
mountall: mount /home/test/.gvfs [2555] terminated with status 127
swapon: /dev/disk/by-uuid/322fcc57-bacb-4f34-b555-cd0c36782f57: swapon failed: Device or resource busy
mountall: swapon /dev/disk/by-uuid/322fbb57-bacb-4f34-b545-cd0c36782f57 [2598] terminated with status 255
mountall: Problem activating swap: /dev/disk/by-uuid/322fbb57-bacb-4f34-b545-cd0c36782f57
test@mediaserver:~$
```

---

### Post by buffchick on 2013-08-12
24h bump...

---

