---
title: "Memory Management Techniques..."
date: 2007-11-30
forum: General Help
---

### Post by Ranhiru on 2007-11-30
Can somebody tell me what are the memory management techniques in Ubuntu?? Or rather the Linux Kernel?? Any e-books or websites???

---

### Post by navaburo on 2007-12-01
You can set the swappiness for starters.

For example, I use:
```
sudo echo 80 > /proc/sys/vm/swappiness
```

For more info:
[http://kerneltrap.org/node/3000](http://kerneltrap.org/node/3000)

---

