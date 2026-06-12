---
title: "vim highlight"
date: 2017-11-24
forum: General Help
---

### Post by jtodd.fr on 2017-11-24
My Unbuntu 16.04 LTS vim doesn't display search highlight even after manually typing ```
:set hlsearch
``` in vim. 


How can I fix this?  (Any places I can check setting that might go wrong?) 

VI version 7.4 with patch 1-1689 and extra patches 8.0.0056 

Thanks

---

### Post by jtodd.fr on 2017-11-24
I guess I know what goes wrong. The default vim version installed by Ubuntu is vim-tiny. After installing vim via ```
apt-get install vim
```, the problem is fixed. Thanks. 

> **jtodd.fr said:**
> My Unbuntu 16.04 LTS vim doesn't display search highlight even after manually typing ```
:set hlsearch
``` in vim. 


How can I fix this?  (Any places I can check setting that might go wrong?) 

VI version 7.4 with patch 1-1689 and extra patches 8.0.0056 

Thanks

---

