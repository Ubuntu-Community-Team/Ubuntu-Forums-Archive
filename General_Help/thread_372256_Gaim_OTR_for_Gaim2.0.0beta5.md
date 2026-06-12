---
title: "Gaim OTR for Gaim2.0.0beta5"
date: 2007-02-28
forum: General Help
---

### Post by tns on 2007-02-28
I'm running Edgy, and I'm trying to get gaim-otr working. I downloaded and built litotr-3.0.0 from source. Then, I downloaded the otr source along with the patch gaim2b2-otr.diff. I opened the patch and changed gtkstock.h to gaimstock.h and then ran it. *patch -p0 < gaim2b2-otr.diff* Then I scattered the OTR library files all over the place trying to get Gaim to see the plugin.

The OTR plugin still doesn't show up in Gaim, and when I run *gaim -d* from terminal, I found this line 
> 
plugins: probing /usr/lib/gaim/libotr.so
plugins: /usr/lib/gaim/libotr.so is not usable because the 'gaim_init_plugin' symbol could not be found.  Does the plugin call the GAIM_INIT_PLUGIN() macro?


Now I'm stumped... Has anybody got Gaim-OTR working in Gaim2.0.0beta5?

---

### Post by energiya on 2007-02-28
> **tns said:**
> ... the patch gaim2b2-otr.diff.....Gaim2.0.0beta5?
Excuse me, but doesn't gaim2b2 come from Gaim2.0.0beta2 ? If you want to patch try the same version. Otherwise the the possibility of it to work is quite small.

---

### Post by zanglang on 2007-02-28
You can use this repository for Gaim plugin debs:
> deb [http://www.excentral.org/ubuntu/edgy](http://www.excentral.org/ubuntu/edgy) ./

---

