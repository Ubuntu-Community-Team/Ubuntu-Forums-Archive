---
title: "ubuntu not booting"
date: 2006-10-22
forum: General Help
---

### Post by loserkid_1 on 2006-10-22
i installed ubuntu last night, set the default gateway device to my wireless adapter to try and configure it, then installed some updates (i was connected to the net through a wired connection) i then had to restart. now when ubuntu boots it gets to configuring network interfaces and then just stops on that. the only way i can get it to boot is by taking out my wireless card, but i need to configure it so i can connect through it. how can i boot up with the wireless card in so that i can install the correct drivers for it?

---

### Post by metalheart on 2006-10-22
Try booting into safe mode. Remove incorrect drivers

```
modprobe -r *driver_module*
```

---

