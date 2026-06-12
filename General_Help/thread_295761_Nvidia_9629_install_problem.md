---
title: "Nvidia 9629 install problem"
date: 2006-11-08
forum: General Help
---

### Post by zpon on 2006-11-08
Hello
I got some problems when i tried to installing the new drives from nvidia. I followed this guide [http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy), when i first install the drives, they works just fine, but when i try to reboot, they are all gone again, apparently it is because there is an older driver installed which conflicts with the new driver when rebooted.
How can i solve this problem?

---

### Post by kinematic on 2006-11-08
wich method from the guide did you actually use?

---

### Post by zpon on 2006-11-08
Oh i'm sorry, I used number 2, but i have tried number one as well (I do know that number one isn't using the new driver)

---

### Post by zpon on 2006-11-09
I got it working using this method [http://albertomilone.com/driver_edgy.html](http://albertomilone.com/driver_edgy.html)

---

### Post by imagineit on 2006-11-09
You don't have to un-install linux-restricted-modules to get the latest nvidia drivers to play nice with the ones in the repositories.  I have to keep the restricted modules for my Intel wireless card.  To ensure that the version in LRM does not conflict with the version you compiled from the nvidia sources, you need to edit the default settings file:

```
sudo vi /etc/default/linux-restricted-modules-common
```and change the following line:

```
DISABLED_MODULES="nv"
```Good Luck!

---

