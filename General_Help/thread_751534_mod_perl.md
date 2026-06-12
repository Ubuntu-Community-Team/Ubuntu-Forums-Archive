---
title: "mod_perl"
date: 2008-04-10
forum: General Help
---

### Post by k0rn on 2008-04-10
I'm having trouble installing mod_perl with Apache2. On Ubuntu 7.10 AMD 64 X2. It asks me for apxs path. If its installed which it is not. Then it asks for the apache dir and i enter /etc/apache2 . But it says cant find ap_release.h .And when i do a locate ap_release.h it comes up empty. And i cant find the httpd executable either. The apache server is running its just when i go to a url that has one of my perl scripts it pops up with a download box. Thats why i need mod_perl.If anyone could help that would be great.

---

### Post by Netwrork Unit on 2008-06-25
Same problem here ! I try to install mod_perl for running Bubzilla on ubuntu.

---

### Post by paulpc on 2008-07-01
Use aptitude to install mod_perl. Select the package 'libapache2-mod-perl2'

Cheers,

---

