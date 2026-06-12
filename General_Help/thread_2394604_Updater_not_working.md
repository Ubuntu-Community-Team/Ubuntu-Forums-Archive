---
title: "Updater not working"
date: 2018-06-19
forum: General Help
---

### Post by robelli on 2018-06-19
I am running Ubuntu 18.04 Mate and when it tells me that there updates available it does not do the update when I select it to install . I have read a lot of posts about it but it has lead to confusion . Has this been a common occurence with this distro and if so how do I get it working properly .

---

### Post by Impavidus on 2018-06-19
Maybe a one-time glitch? Try to install updates using the terminal:```
sudo apt update
sudo apt upgrade
```
Maybe the problem doesn't come back. If it does come back, come back here – although I haven't got a clue on what may cause this.

---

### Post by ajgreeny on 2018-06-19
The system may be updating itself already in the background using the unattended-upgrade process, which is the default, and means the it will then not allow anything else to use apt/dpkg etc etc. to install or update any packages.

---

