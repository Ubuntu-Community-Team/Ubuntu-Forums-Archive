---
title: "Borked my bluetooth"
date: 2007-08-29
forum: General Help
---

### Post by Rebel Dragon on 2007-08-29
I deleted my /etc/init.d/bluetooth. 	](*,)    Anyone know how to reinstall it? 

I've tried reinstalling bluez and the kdebluetooth framework via adept, and apt-get to no avail. 

:confused:

Running Feisty on a Dell Inspiron 9200.

---

### Post by ruibernardo on 2007-08-29
Hi Rebel Dragon,

try to remove and purge bluez-utils package and then reinstall it. 

NOTE: this will remove all configuration files. If you want to save something from them, make a backup of /etc/bluetooth/hcid.conf and /etc/bluetooth/rfcomm.conf (or others).

```
sudo /etc/init.d/bluetooth stop
sudo apt-get remove --purge bluez-utils
sudo apt-get install bluez-utils
```This should work.

---

### Post by Rebel Dragon on 2007-08-29
> **epimeteo said:**
> Hi Rebel Dragon,

try to remove and purge bluez-utils package and then reinstall it. 

NOTE: this will remove all configuration files. If you want to save something from them, make a backup of /etc/bluetooth/hcid.conf and /etc/bluetooth/rfcomm.conf (or others).

```
sudo /etc/init.d/bluetooth stop
sudo apt-get remove --purge bluez-utils
sudo apt-get install bluez-utils
```This should work.

Hallalujah! That did the trick - thanks much! 

:guitar:

---

