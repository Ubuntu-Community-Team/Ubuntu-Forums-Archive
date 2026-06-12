---
title: "I want to change the boot screen."
date: 2024-10-18
forum: General Help
---

### Post by rupo2024 on 2024-10-18
I'm currently running Ubuntu Server 24.04.
Boot screen displayed 

Ubuntu
. . . . .

in ASCII. (The dots are animated.)

Previously, dmesg was shown.
I don't know if it happened after upgrading from 22.04 to 24.04 and/or after using the boot-repair tool.
I would like dmesg to be displayed on the boot screen.


Please tell me how to change the settings.

---

### Post by rupo2024 on 2024-10-18
Self res...

I succeeded edit grab.

(1)Open config...
sudo vi /etc/default/grub

(2)Edit...
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to
GRUB_CMDLINE_LINUX_DEFAULT=""

(3)Update grub...
sudo update-grub

thanks.

---

