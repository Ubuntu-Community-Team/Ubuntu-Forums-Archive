---
title: "apt broken - failed VMWare install"
date: 2008-05-07
forum: General Help
---

### Post by ryanferreri on 2008-05-07
Hi All,

I tried to install VMWare 2.0 beta using the RPM from VMWare's site. I converted the RPM to .deb using alien. The install failed. I tried to remove the package using apt (package vmware-server) but it failed too. Now when I try to run apt-get install -f it tries to uninstall VMWare again but fails, and if I try to remove the package through Synaptic it returns 

> E: vmware-server: subprocess post-removal script returned error exit status 2

Since the failed removal, I did install VMWare using the .tar.gz binaries and it works great. But now I can't install updates on my computer at all. 

Is there a way for me to purge out this failed install so apt doesn't try to remove the package every time it starts?

(Ubuntu 8.04 x64)

---

