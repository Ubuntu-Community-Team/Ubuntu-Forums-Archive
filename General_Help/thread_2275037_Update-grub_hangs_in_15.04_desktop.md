---
title: "Update-grub hangs in 15.04 desktop"
date: 2015-04-23
forum: General Help
---

### Post by nlee2 on 2015-04-23
On fresh install of 15.04 desktop 64-bit, update-grub just hangs. I need to add video=hyperv_fb:1920x1080 to GRUB_CMDLINE_LINUX_DEFAULT. How done?

Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.19.0-15-generic
Found initrd image: /boot/initrd.img-3.19.0-15-generic

---

### Post by dino99 on 2015-04-23
check that gksu is installed, if not 'sudo apt-get install gksu' (without the quotes)

gksu gedit /etc/default/grub
then add ' add video=hyperv_fb:1920x1080' and save before quiting
and finally run again 'sudo update-grub'

---

### Post by dino99 on 2015-04-23
check that gksu is installed, if not 'sudo apt-get install gksu' (without the quotes)

gksu gedit /etc/default/grub
then add ' add video=hyperv_fb:1920x1080' and save before quiting
and finally run again 'sudo update-grub'

---

### Post by nlee2 on 2015-04-23
Thank you for your help to get update-grub working in 15.04.

It does not seem to matter whether I edit  /etc/default/grub with gedit or nano. When I run sudo update-grub, it just hangs.

---

### Post by Bucky Ball on 2015-04-24
Yea, you don't need gedit. nano is fine.

---

### Post by nlee2 on 2015-04-24
update-grub hangs on a 15.04 hyper-v gen 2 vm install but it did create /boot/grub/grub.cfg.new properly. Needed to manually rename it to replace grub.cfg to make it work.

---

