---
title: "Log full of error on Asus Skylake"
date: 2016-06-11
forum: General Help
---

### Post by daberbuj on 2016-06-11
Hi, I'm new in Ubuntu. I installed 16.04 on my new Asus laptop but I realized that logs files were full of errors. I've searched in the forum but I couldn't solved my problem.

My configuration is (Asus X556UJ):

[LIST]
[*]Intel Core i5-6200U
[*]Memory 4GB
[*]NVIDIA GeForce 920M 2GB DDR3 VRAM
[/LIST]


[ATTACH=CONFIG]269519[/ATTACH]


Also, I've tried changing kernel boot options but nothing happens. Do you know what can be?

Thanks!

---

### Post by mc4man on 2016-06-11
They are pretty much harmless but does spam logs & make using a tty difficult at best. To make go away - 
```
sudo -H gedit /etc/default/grub
```
On the  GRUB_CMDLINE_LINUX_DEFAULT= line add this option - 
pci=noaer
So it may be something like this, 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pci=noaer "
Then run,
sudo update-grub 


Here I don't use quiet splash so line is like in screen shot
There is a lingering bug report on this in launchpad somewhere..

---

### Post by daberbuj on 2016-06-11
Thank you, it seems that it's ok but now the keys that modify the brightness are not working :S

---

### Post by mc4man on 2016-06-11
Doesn't affect my brightness keys. You could remove the option & see if they come back.

edit: bug report - [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1521173](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1521173)

A _much_ older one with a different boot option that was reported to help (comment 4
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/671979](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/671979)

---

### Post by daberbuj on 2016-06-11
Thank you, I solved it adding "acpi_osi=".

---

