---
title: "ubuntu 16.04 server network manager"
date: 2016-07-30
forum: General Help
---

### Post by hezy2 on 2016-07-30
Hello,
how can re-install network manager after uninstalling it? thanks,
hezy.

---

### Post by &amp;KyT$0P# on 2016-07-30
If your server has a GUI, run this command:
```
sudo apt-get install network-manager
```

Otherwise, run this command, then manually install only the specific recommended packages you want:
```
sudo apt-get --no-install-recommends install network-manager
```

---

