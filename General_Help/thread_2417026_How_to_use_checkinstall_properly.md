---
title: "How to use checkinstall properly"
date: 2019-04-19
forum: General Help
---

### Post by muqor77 on 2019-04-19
My short question: How do I use checkinstall properly? 

All I know to build deb package using checkinstall, I have to use sudo permission. Is it safe to use sudo permission when building deb package. 
Because when I use Centos , I should not use sudo permission to create rpm package.

TIA.

---

### Post by deadflowr on 2019-04-19
*Thread moved to **General Help***

checkinstall has an rc configuration file at /etc/checkinstallrc which defines how it should run.
Different distributions set it differently.
On Ubuntu it's set to build the package and directly install it, so sudo would be required.
You are free to change that setting in the config file to not do that if you want.

---

### Post by muqor77 on 2019-04-24
If in some way I build deb package using checkinstall inside chroot env, then I install the package. Is that a correct way to do?

TIA

---

