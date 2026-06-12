---
title: "installed amd catalyst now wont show desktop"
date: 2013-11-03
forum: General Help
---

### Post by hunterkasy on 2013-11-03
I installed the amd catalyst from amd site and installed it and rebooted and the computer lets me log in and then it goes to a black screen and I can see and move the mouse pointer how can I fix this please

---

### Post by hunterkasy on 2013-11-03
I fixed it by running these 2 commands

sudo sh /usr/share/ati/fglrx-uninstall.sh 
sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev*

---

