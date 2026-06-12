---
title: "synaptic error"
date: 2008-03-15
forum: General Help
---

### Post by SpikeyMike on 2008-03-15
Hi, I recently installed mysql but now whenever I install or uninstall anything using synaptic package manager I get the following error:

[COLOR="Red"]E: mysql-server-5.0: subprocess post-installation script returned error
exit status 1

E: mysql-server: dependency problems - leaving unconfigured[/COLOR]

can anyone advise me about this?

Spikey

---

### Post by mssever on 2008-03-15
Try reinstalling mysql-server or doing a ```
sudo dpkg-reconfigure mysql-server
```

---

### Post by zvacet on 2008-03-15
system>admin>software sources>check all under Ubuntu software and updates tab.Reload.Try to install again.

---

