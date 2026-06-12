---
title: "remove kernel 4.15?"
date: 2019-12-06
forum: General Help
---

### Post by wagibson290454 on 2019-12-06
I am running on kernel 5.0.36, but I still have 4.15.72 on the list of available versions. Can I remove this since I seem to be  established on kernel 5?

---

### Post by CatKiller on 2019-12-06
Yes.

When you install a new kernel it keeps the old version too, just in case. When you've got a few of them, you'll be prompted to autoremove the oldest ones.

When you install a new kernel branch it will keep the old one and you'd only be prompted to autoremove enough so that you have a few of each branch. Each kernel branch is a different package, rather than an upgraded version of the same package.

So if you're happy with the new branch, by all means remove the old branch.

In this specific case, 4.15 was the kernel branch that came with the initial 18.04 release and the point releases (18.04.2, and so on) used the Hardware Enablement Stack, which uses the kernel version from the next version of Ubuntu to allow you to use newer hardware. So 4.15 came with 18.04, 4.18 came with 18.10 and 18.04.2, 5.0 came with 19.04 and 18.04.3, and 5.3 came with 19.10 and will probably be in 18.04.4 in February.

---

### Post by Dennis N on 2019-12-06
If you would enable unattended upgrades, your system will automatically keep just the two most recent kernels. No manual autoremove needed. 

Reference system: Ubuntu 18.04.

---

### Post by mörgæs on 2019-12-08
If you want to remove it the command is ```
sudo apt autoremove
```

---

