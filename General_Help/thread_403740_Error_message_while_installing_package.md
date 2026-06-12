---
title: "Error message while installing package"
date: 2007-04-07
forum: General Help
---

### Post by mmmpancakes on 2007-04-07
I'm trying to install the ndiswrapper in Ubuntu via Synaptic. However, during the installation process I get an error box with the following message:

> 
E: cpio: subprocess post-installation script returned error exit status 2
E: ubuntu-standard: dependency problems - leaving unconfigured
E: ubuntu-base: dependency problems - leaving unconfigured

Any advice you have would be greatly appreciated.

---

### Post by zvacet on 2007-04-07
```
sudo aptitude update && sudo aptitude upgrade
```

If this doesn´t work try

```
sudo aptitude ndiswrapper
```

---

