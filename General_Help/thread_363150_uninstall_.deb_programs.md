---
title: "uninstall .deb programs"
date: 2007-02-16
forum: General Help
---

### Post by TomFumb on 2007-02-16
I installed the oracle personal edition lately from a .deb installer, and now I can't get rid of it!

The program runs horribly slow on my home computer, so I can't work with it, but because I didn't use synaptic to get it on there I don't know how to get rid of it. There's no option in the oracle menu or in add/remove programs.

Can anybody help? do I need to download the installer again and find a remove option?

---

### Post by taurus on 2007-02-16
```
sudo dpkg -r **package_name**
```

---

### Post by TomFumb on 2007-02-17
Thanks!

that worked a treat

---

