---
title: "Encrypt a partition in Ubuntu 12.10"
date: 2013-02-01
forum: General Help
---

### Post by bob-linux-user on 2013-02-01
How do I encrypt a partition in Ubuntu [COLOR="Red"]12.10[/COLOR]? 
Please see

[http://www.liberiangeek.net/2012/04/encrypt-your-external-usb-drives-in-ubuntu-12-04-precise-pangolin/](http://www.liberiangeek.net/2012/04/encrypt-your-external-usb-drives-in-ubuntu-12-04-precise-pangolin/)

This used to work ok for Ubuntu 12.04 but I cannot see how to do it in 12.10?

---

### Post by bob-linux-user on 2013-02-02
Any takers please?

There is a gnome-disks utility but it does not seem to have all the same functionality with encrypting partitions that the version in Ubuntu 12.04 had?

---

### Post by bob-linux-user on 2013-02-05
Am the only one who encrypts partitions this way? It seems very simple and straightforward. Has someone got a way which is easier please?

---

### Post by bob-linux-user on 2013-02-13
Am I the only one who encrypted partitions on my hard drive in this way? 

It seems this very useful functionality (see link in original post) was deleted, for no obvious reason, from Ubuntu 12.10 but is on Ubuntu 12.04.

Is there some other simple way of doing this please?

At the moment it is certainly putting me off upgrading to 12.10.

---

### Post by Bufeu on 2013-02-13
> **bob-linux-user said:**
> Am I the only one who encrypted partitions on my hard drive in this way? 

It seems this very useful functionality (see link in original post) was deleted, for no obvious reason, from Ubuntu 12.10 but is on Ubuntu 12.04.

Is there some other simple way of doing this please?

At the moment it is certainly putting me off upgrading to 12.10.[https://wiki.archlinux.org/index.php/Dm-crypt_with_LUKS](https://wiki.archlinux.org/index.php/Dm-crypt_with_LUKS)

---

### Post by LewisTM on 2013-02-13
The gnome-disks utility in 12.10 lets you format partitions but the options have been moved. Select the desired partition, unmount it if mounted, then click the gears button. Pick format and select type "Encrypted, compatible with Linux system (LUKS+Ext4)". That's it. 

Cheers!

---

### Post by bob-linux-user on 2013-02-13
Thanks Bufeu and LewisTM for your replies. It is now working. I was clicking on the cogwheels at the top right when I should have been clicking on the cogwheels lower down where there are more options.

---

