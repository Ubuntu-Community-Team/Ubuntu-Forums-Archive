---
title: "widescreen lcd need new resoution"
date: 2007-05-27
forum: General Help
---

### Post by Tucatts on 2007-05-27
Just bought a new widescreen LCD and need to change the resolution to 1440x900. My nividia drivers are installed and I am running Feisty fawn. Do I use the following? 
sudo dpkg-reconfigure xserver-xorg or is there something else I should do?
Thanks

---

### Post by aidanr on 2007-05-27
yes you can do it that way or add the new resolution to /etc/X11/xorg.conf

gksudo gedit /etc/X11/xorg.conf

---

