---
title: "Are all application uninstall in Synaptics clean?"
date: 2007-08-24
forum: General Help
---

### Post by sarc on 2007-08-24
Before I try things I would like to know if repeated install-uninstall of many applications thru Synaptics can lead to gradual system degradation (the way it can happen in Windoze Registry mayhem).  
So is there any reason not to try a bunch of apps and just uninstalling if I don't need them?

---

### Post by jim_p on 2007-08-24
In Synaptic, when you click something for uninstall, there is also an option that says "Mark for COMPLETE uninstall". This removes the program and all the configuration files that it has along.

Also, though Synaptic, you can find which apps you have removed in the past but their settings are still on the pc. Just in case you want them removed now

---

### Post by capink on 2007-08-24
To purge ( i.e clean residual files) all removed pakcages:

```
sudo aptitude purge '~c'
```

---

