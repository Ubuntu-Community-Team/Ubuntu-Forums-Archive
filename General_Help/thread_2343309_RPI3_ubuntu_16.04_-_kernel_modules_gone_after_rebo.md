---
title: "RPI3 ubuntu 16.04 - kernel modules gone after reboot"
date: 2016-11-15
forum: General Help
---

### Post by cmisip on 2016-11-15
I installed ubuntu 16.04 on a raspberry pi 3.  It works well until I reboot.  I noticed that after a reboot, ufw is not working so I started ufw and it complained of missing iptables modules.  And in fact they are missing.
If I reinstall the latest kernel, the modules are back where they should be but when I reboot, they are missing again.
I pretty much have to reinstall the kernel each time I reboot to get the modules back.
I have been playing around with overlayroot but I turned it off for the moment to see if I can fix this problem first.

Anybody have a clue as to what is happening?
Thanks
Chris

---

