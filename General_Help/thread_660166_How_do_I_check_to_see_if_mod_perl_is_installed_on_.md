---
title: "How do I check to see if mod_perl is installed on Apache?"
date: 2008-01-06
forum: General Help
---

### Post by DouglasAWh on 2008-01-06
How do I check to see if mod_perl is installed on my Apache?  Additionally, does anyone know if XAMPP from Apache Friends plays nicely with pre-existing versions?  I already have MySQL installed, so I don't want what I've done there to get blown away if I install XAMPP.

Thanks!

---

### Post by rubicon on 2008-01-06
To see if you have mod_perl installed, go to Synaptic and find libapache2-mod-perl2 (I believe that's it).

To be sure, you may run 'apache2ctl -M' to see which modules are enabled and then, if needed, enable mod_perl (by 'a2enmod').

---

