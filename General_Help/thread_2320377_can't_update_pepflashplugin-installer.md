---
title: "can't update pepflashplugin-installer"
date: 2016-04-13
forum: General Help
---

### Post by marchello_lippi2 on 2016-04-13
Hi all, 

Can't update pepflashplugin-installer using apt-get update. The pop-up window appears and it has option to "try update now" which opens new console window that tries to update package, but it closes in a moment without the result. 

How do I solve it? 
Thanks ahead. 

$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 14.04.4 LTS
Release:        14.04
Codename:       trusty

---

### Post by howefield on 2016-04-13
Perhaps the ppa that you are using is down ?

As an alternative you could purge pepflashplugin-installer, enable the Ubuntu partners repository and install adobe-flashplugin.

---

