---
title: "Ubuntu 18.04 Grub menu won't hide"
date: 2018-08-01
forum: General Help
---

### Post by korinek.marta on 2018-08-01
Hello,
I am quite new to linux, but managed to get all set up fine, only thing is, that I cant get to hide the grub menu on strutup. I was running dualboot, but recently i deleted Windows 10 partition and merged it with ubuntu partition, after that it was not needed to show grub menu, i want to go straight to the login screen. I tried several tutorials how to do it with editing /etc/defaul/grub but nothing works, also i tried to instal Grub Customizer and ticked off the settings to show grub menu. What to try next? Below is my curent state of /etc/default/grub

```

GRUB_DEFAULT="0"
GRUB_HIDDEN_TIMEOUT="0"
GRUB_DISABLE_OS_PROBER="true"
#GRUB_TIMEOUT_STYLE="hidden"
#GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash resume=UUID=383d2d00-88c8-4f1d-ab78-dd03f1a69229"
GRUB_CMDLINE_LINUX="resume=/dev/sda4"

```

Any advice would be appriciated.

---

