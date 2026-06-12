---
title: "System Settings Logs Me Out in Ubuntu 18.04"
date: 2020-05-06
forum: General Help
---

### Post by facosta on 2020-05-06
[ATTACH=CONFIG]285770[/ATTACH] System  settings logs me out when I click on icon in Ubuntu 18.04. What is the fix?

---

### Post by facosta on 2020-05-06
[COLOR=#242729][FONT=Arial]Fixed issue by switching from Nouveau driver to NVIDIA driver in Software Updater > Settings > Additional Drivers
Then completed the following:[/FONT][/COLOR]
sudo ubuntu-drivers devices
[COLOR=#242729][FONT=Arial]which showed that the nvidia driver was recommended. driver   : nvidia-driver-390 - distro non-free recommendeddriver   : xserver-xorg-video-nouveau - distro free builtin[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]So I then ran[/FONT][/COLOR]
sudo ubuntu-drivers autoinstall
[COLOR=#242729][FONT=Arial]which installed and used the Nvidia driver. After rebooting sudo shutdown -r now it worked![/FONT][/COLOR]

---

### Post by CelticWarrior on 2020-05-06
Using the Additional Drivers would have been enough. Autoinstall didn't nothing because it was already installed.

---

