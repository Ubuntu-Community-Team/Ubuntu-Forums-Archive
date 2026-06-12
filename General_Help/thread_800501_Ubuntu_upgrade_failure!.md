---
title: "Ubuntu upgrade failure!"
date: 2008-05-19
forum: General Help
---

### Post by mrwasabi on 2008-05-19
Hey folks I need help! I tried to do the 8.04 LTS upgrade via the updater and it locked up my box forcing a hard reboot, now my box will not boot back to the desktop! I tried running:
**sudo dpgk-reconfigure xserver-xorg**
This generated an error saying that it wasn't installed or was broken. How do I repair this? TIA!

---

### Post by Anduu on 2008-05-19
try restarting the upgrade process again.

sudo apt-get update && sudo apt-get dist-upgrade

---

### Post by Cap'n Skyler on 2008-05-19
i posted this elsewhere,i did upgrade too,but it was quirky so i just whipped up a new 8.04 cd and re installed from that and then updated and it is working pretty good now.
ya might try that.:popcorn:

---

