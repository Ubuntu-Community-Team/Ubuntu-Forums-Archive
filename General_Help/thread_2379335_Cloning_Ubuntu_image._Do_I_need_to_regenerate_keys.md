---
title: "Cloning Ubuntu image. Do I need to regenerate keys for SSH?"
date: 2017-12-04
forum: General Help
---

### Post by gingerpower121 on 2017-12-04
As the tile explains I am cloning my image of Ubuntu which has openssh-server installed. My question is do I need to regenerate keys and if so how?I already have a working python script that that I plan on running that takes care of most duplicate network settings so running any commands for each clone copy isn't that big of a deal.

---

### Post by gingerpower121 on 2017-12-04
In case anyone looks at this in the future the following commands seem to do what I'm looking for:
sudo rm /etc/ssh/ssh_host_*
sudo /usr/sbin/dpkg-reconfigure openssh-server

---

