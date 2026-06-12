---
title: "fix /dev/sda1 was not cleanly unmounted"
date: 2012-11-04
forum: General Help
---

### Post by pjalegria on 2012-11-04
After upgrade Lubuntu i'm getting force check disk every boot, on boot log i have "/dev/sda1 was not cleanly unmounted"... How can i fix this???

Thanks

---

### Post by dino99 on 2012-11-04
There are a few reports about that issue since a while, often due to modemmanager reloading its drivers list at shutdown. Remove "splash" from /etc/default/grub, then run: sudo update-grub. That will get you know about usefull comments via the verbose mode.

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1066484](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1066484)
[https://bugs.launchpad.net/ubuntu/precise/+source/libnih/+bug/740390](https://bugs.launchpad.net/ubuntu/precise/+source/libnih/+bug/740390)

---

### Post by pjalegria on 2012-11-04
Yeh, it seems that is modemmanager related, i made the test, if i turn off internet connection before logout, the next boot its ok without the error... No fix yet???

---

