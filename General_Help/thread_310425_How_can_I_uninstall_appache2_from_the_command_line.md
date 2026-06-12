---
title: "How can I uninstall appache2 from the command line"
date: 2006-12-01
forum: General Help
---

### Post by Bill007 on 2006-12-01
OOPS

How can I uninstall appache2 from the command line 

what is the command:-k 

Regards Bill

---

### Post by cronholio on 2006-12-01
```
sudo aptitude remove apache2
```

or

```
sudo aptitude purge apache2
```

The latter will remove all Apache 2 config files as well.

---

