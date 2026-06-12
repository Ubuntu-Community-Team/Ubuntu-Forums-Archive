---
title: "Xubuntu automatic suspend doesn't work"
date: 2015-05-17
forum: General Help
---

### Post by dzizs2 on 2015-05-17
I have an Asus Eee PC 1015 BX and Ubuntu 14.04. When I set it to suspend after 15 minutes, after that time I get a "Power Manager not authorized" notification and it doesn't suspend. How to make it suspend automatically? I tried running ```
aptitude purge light-locker light-locker-settings
``` and then ```
aptitude install light-locker light-locker-settings
``` but that didn't help.

(I don't know if this is related to this problem but suspending tends to  mess up my booting, i.e. sometimes I can't boot normally after computer  has been suspended, I have to boot with Super Grub Disk and then run  install-grub.)

---

