---
title: "Major Problems with Apache and PHP"
date: 2007-01-25
forum: General Help
---

### Post by gavinjb on 2007-01-25
Hi,

I just tried to install an app on my machine and didn't realise until it was too late that it was installing php4 as well (I already had php5 installed), this caused problems with several php scripts on this machine, I have since uninstalled php4 and the app, but now when I try to access any php scripts (through apache server), I am asked where I want to save the file, as apache is now not recognising the php files and processing them, can someone please help me to get this working again.

Thanks,



Gavin,

---

### Post by gavinjb on 2007-01-25
well, I have just tried uninstalling php and apache and then re-installing, but now when I run ./etc/init.d/apache2 restart, nothing happens

---

### Post by lamego on 2007-01-25
Install apache2 and the remove it with the purge option.
The "purge" will make sure the conf is deleted, it should resolve your problem.
apt-get --purge -y remove

---

### Post by gavinjb on 2007-01-26
Thanks, was still having problems though, so I did a clean install on the machine, and ran my install script (installas all my apps with apt-get) and now everything is working fine, it also took me less time than I had previously spent trying to fix the problem

---

