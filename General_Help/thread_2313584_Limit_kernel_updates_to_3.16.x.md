---
title: "Limit kernel updates to 3.16.x"
date: 2016-02-13
forum: General Help
---

### Post by MACscr on 2016-02-13
I am using Ubuntu 14.04 LTS and I need limit my kernel updates to only 3.16.x and below as my current backup solution (r1soft) doesnts support the 3.19.x kernel. Is there a proper way to keep things updated with apt-get, but limited the kernel to 3.16.x kernel updates?

---

### Post by v3.xx on 2016-02-13
You could remove these packages to stop kernel upgrades.

[ATTACH=CONFIG]267293[/ATTACH]

---

### Post by MACscr on 2016-02-13
But i dont want to stop kernel upgrades, I just want to stay within within 3.16. Even though 3.19.x is the newest, updates still come out for 3.13.x and 3.16.x. This is also a headless system, so I do everything at the cli.

---

### Post by v3.xx on 2016-02-13
Removing those packages will stop version upgrades, in your case it will stop offering the 3.19 and should still offer updates to the installed kernels.

```
sudo apt-get remove linux-generic linux-image-generic linux-headers-generic
```

This assumes you have the generic kernel installed.

---

