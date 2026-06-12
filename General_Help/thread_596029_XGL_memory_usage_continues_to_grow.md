---
title: "XGL memory usage continues to grow"
date: 2007-10-29
forum: General Help
---

### Post by -Zeus- on 2007-10-29
My system was running slow yesterday so I looked at my processes and between XGL and emerald 5GB of RAM was used!!! so I restarted X and it was OK... This morning I come and see XGL is using 600MB ram and 15%CPU... it was never like this before.  I installed and ATi AIXGL drivers, could that be it?

---

### Post by hollaburoo on 2007-10-29
The whole point of using AIGLX is that you no longer need XGL.  Assuming you did the installation of the new driver right, then ```
apt-get remove xserver-xgl
``` should be enough to fix your memory problems.  You may want to disable compiz/beryl/compiz-fusion before removing XGL though, just incase you didn't set up AIGLX right.

---

### Post by sevenearths on 2008-03-22
> **hollaburoo said:**
> The whole point of using AIGLX is that you no longer need XGL.  Assuming you did the installation of the new driver right, then ```
apt-get remove xserver-xgl
``` should be enough to fix your memory problems.  You may want to disable compiz/beryl/compiz-fusion before removing XGL though, just incase you didn't set up AIGLX right.

what happens if you xorg.cong references fglrx as the driver. Would there be a problem?

---

