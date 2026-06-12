---
title: "scim-launcher is consuming all of my memory"
date: 2007-01-08
forum: General Help
---

### Post by ]grimm[ on 2007-01-08
I've recently run into a problem where scim-launcher eats up all of my memory and repeatedly respawns until I kill X and change my input method to "default" or "none" instead of scim.  

I can't recall any major changes to my system in recent past at all, let alone anything that would have interfered with scim.  I've been using scim for input ever since I installed Edgy.

Does anyone know what the problem might be?  I tried reinstalling scim and some related components, but to no avail.

---

### Post by twjo on 2007-01-15
well it seems i'm having the same problem, scim-launcher consuming all my memories after bootup. I have to kill the process to release the memory. Is there some memory leak bugs for scim?

---

### Post by cisforcojo on 2008-01-10
Same problem here. I'm currently studying Chinese and tests are next week so this is extremely opportune. Any help you can give me would be GREATLY appreciated!!!

---

### Post by cisforcojo on 2008-01-10
Think I've solved it.

]grimm[, I think you almost had it but you probably didn't delete the .scim folder in your home directory.

```

sudo apt-get remove scim
rm -rf ~/.scim
sudo apt-get install scim scim-chinese scim-modules-socket scim-gtk2-immodule xfonts-intl-chinese ttf-arphic-gbsn00lp ttf-arphic-gkai00mp ttf-arphic-bkai00mp ttf-arphic-bsmi00lp im-switch scim-bridge
```

---

