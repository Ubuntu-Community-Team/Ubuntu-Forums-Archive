---
title: "K3B Issue"
date: 2005-09-21
forum: General Help
---

### Post by Breaks on 2005-09-21
When loading K3B i get the following:

> Unable to find cdrdao executable
K3b uses cdrdao to actually write CDs.
Solution: Install the cdrdao package.

So i load up kynaptic to see if cdrdao is there but its not.. how do i go about fixing this? :s... thanks in advance for any help.

---

### Post by aysiu on 2005-09-21
You need to enable extra repositories. Follow [these directions](http://www.frankandjacq.com/ubuntuguide/5.04/index.html#extrarepositories), then type this into a terminal ```
sudo apt-get update
sudo apt-get install cdrdao
```

---

