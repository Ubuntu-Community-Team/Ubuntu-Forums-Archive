---
title: "Grub's messed up, can't boot to live cd, help!"
date: 2007-12-06
forum: General Help
---

### Post by smartboyathome on 2007-12-06
Ok, so I messed up grub once again, but now my motherboard broke (cant boot to live*) and I can only boot to Ubuntu 7.04 (which has only 500 MBs of space left). :( Anyway, I would like to know how to find out what my gutsy partition's UUID is. Please help. :)

---

### Post by LaRoza on 2007-12-06
```

blkid

```

```

ls /dev/disk/by-uuid

```

---

### Post by smartboyathome on 2007-12-06
Thanks LaRoza, I will try this ASAP.

---

