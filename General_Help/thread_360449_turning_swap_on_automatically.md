---
title: "turning swap on automatically"
date: 2007-02-13
forum: General Help
---

### Post by Lukeg on 2007-02-13
When I upgraded to Edgy, my swap partition was messed up and I had to reformat it with gparted.  Now however every time I restart my system I have to manually turn it on with gparted.  How can I make it turn on upon startup?

Any help would be appreciated, thanks.

---

### Post by Ramses de Norre on 2007-02-13
Add a line like this in /etc/fstab: ```
UUID=a5e6da58-1cf9-462b-96e9-96db0c22d6e4 none            swap    sw              0       0
```
You can find out the UUID with **sudo vol_id -u /dev/????**, fill in the correct dev node for your swap partition.

---

