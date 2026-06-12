---
title: "Some daemons won't startup on Edgy"
date: 2006-11-16
forum: General Help
---

### Post by druhboruch on 2006-11-16
I have problems with loading daemons on Edgy.

apcupsd - installed from repositories.  All the startup scripts are in place but daemon desn't start.  I have to manually 

```
sudo /etc/init.d/apcupsd start
```

Same problem with bacula fd on my laptop.  It probably starts before network-manager and hungs since there is no network.

How can I ensure that daemons start in the right order?

---

