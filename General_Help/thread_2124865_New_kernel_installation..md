---
title: "New kernel installation."
date: 2013-03-12
forum: General Help
---

### Post by Stormlord on 2013-03-12
Hi,

As we all know, all ubuntu 12.04.2 based distros ship with kernel 3.5 instead of 3.2, 12.04 and 12.04.1 were shipped with.  I had installed Xubuntu 12.04 when it was first released and I am doing all the necessary updates up to now and everything gets updated except for the kernel.  Since I must update it manually, what exactly is the correct way?  Should I just select all three 3.5 kernel related packages (linux-image, linux-headers) and install them using Synaptic or do I have to do anything other than that please?

Thank you.

---

### Post by Cheesemill on 2013-03-12
You don't have to do anything manually, you can upgrade your machine to a full 12.04.2 system by doing the following...
```
sudo apt-get install linux-generic-lts-quantal xserver-xorg-lts-quantal
```

Be aware that some graphics hardware won't work using the closed-source drivers with the new xorg subsystem (specifically ATI 2/3/4xxx series cards) so if you are unsure you may want to only install the kernel package (linux-generic-lts-quantal).

For more information see this page...
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

---

### Post by Stormlord on 2013-03-12
Thank you Cheesemill.  ;)

---

