---
title: "Installation hitch"
date: 2012-10-26
forum: General Help
---

### Post by Hiuhu on 2012-10-26
I installed ubuntu 12.04 alongside windows 7 and installed it properly but when I restart the computer only windows boots and shows up. What could be the problem ? The partition where ubuntu was installed exists but it is not booting. I am using a lenovo G580

---

### Post by dino99 on 2012-10-26
i suppose you have not set grub while installing. Boot on the live image, then open a terminal and run:

sudo grub-install /dev/sda

and reboot

---

### Post by Hiuhu on 2012-10-26
Ok let me try it out

---

### Post by Hiuhu on 2012-10-26
Its still not working this is what it shows me :

root@root: sudo grub-install /dev/sda
/usr/sbin/grub-probe : error : cannot find a device for /boot/grub (is /dev monted ?).

---

