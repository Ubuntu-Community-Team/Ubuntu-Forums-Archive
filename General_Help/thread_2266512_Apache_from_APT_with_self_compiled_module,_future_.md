---
title: "Apache from APT with self compiled module, future issues with upgrades?"
date: 2015-02-23
forum: General Help
---

### Post by evil32 on 2015-02-23
Hi Guys

We have several webservers running Unbuntu 14.04 with Apache 2.4x,  we needed an Apache module (remoteip) which unfortunately is not available via an APT repository (that I could find), so we've had to compile this ourselves.

Is this likely to cause issues with future Apache upgrades? (i.e. as the module is compiled against our current Apache version)

Will we need to recompile these each time Apache gets upgraded via "apt-get update"?

If so, can anybody recommend a strategy for handling this? 

I'm not a fan of forcing the system to maintain the current release as we could end up missing critical updates.

Thanks

---

### Post by Ruben_van_Smirren on 2015-02-24
If you install the software in de root directory of apache2 it's probably not needed to do this everytime.

---

### Post by evil32 on 2015-02-24
Thanks for replying Ruben. I think for now, we'll just patch 1 host and see what effect it has, then roll out to the others.

---

