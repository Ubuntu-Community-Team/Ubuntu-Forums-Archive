---
title: "virtualbox error"
date: 2007-06-11
forum: General Help
---

### Post by lahook on 2007-06-11
after a kernel upgrade i get this error:
PIIX3 cannot attach drive to the Secondary Master
VBox status code: -102 (VERR_FILE_NOT_FOUND)

I've tried
sudo /etc/init.d/vboxdrv setup
 sudo dpkg-reconfigure virtualbox
sudo apt-get install virtualbox
 sudo apt-get install linux-headers-$(uname -r)
and booting the previous kernel
any ideas? 
any help will be appreciated
vboxlog is attached

---

