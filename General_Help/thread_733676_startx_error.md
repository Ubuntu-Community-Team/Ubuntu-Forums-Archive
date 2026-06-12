---
title: "startx error"
date: 2008-03-24
forum: General Help
---

### Post by rohit2412 on 2008-03-24
hi- new to ubuntu and having problems....
i have ultimate edition 1.7 (32 bit)
amd turion 64X2 processor,nvidia geforce 7150m graphics card.................

the problem is that it does not recognise graphics card and takes me in safe graphics mode.......
i tried to install driver after that(after removing that kubuntu-docs error)
i have installed driver several times from restricted driver manager and also reinstalled
from package manager but whenever i reboot it always takes me in safe graphics mode saying that xserver failed to start..."Cannot start x server (your graphical interface)"
i tried sudo-reconfigure xserver-xorg but the driver is always set to nv and i change it to vesa everytime but to no avail...
hope someone can help me....
currently using envy..hoping it solves the problem...

---

### Post by dcstar on 2008-03-24
> **rohit2412 said:**
> hi- new to ubuntu and having problems....
i have ultimate edition 1.7 (32 bit)
amd turion 64X2 processor,nvidia geforce 7150m graphics card.................

the problem is that it does not recognise graphics card and takes me in safe graphics mode.......
**i tried to install driver after that(after removing that kubuntu-docs error)**
i have installed driver several times from restricted driver manager and also reinstalled
from package manager but whenever i reboot it always takes me in safe graphics mode saying that xserver failed to start..."Cannot start x server (your graphical interface)"
i tried sudo-reconfigure xserver-xorg but the driver is always set to nv and i change it to vesa everytime but to no avail...
hope someone can help me....
currently using envy..hoping it solves the problem...

What driver, there are different choices for Nvidia?

---

### Post by rohit2412 on 2008-03-24
thanks,,

nvidia-glx-new was installed by restricted drivers manager
right now envy is running....cant understand wat it is doing....

---

### Post by rohit2412 on 2008-03-24
hi  got it working dont know how.......
thanks anyway.......

---

### Post by dcstar on 2008-03-24
> **rohit2412 said:**
> hi  got it working dont know how.......
thanks anyway.......

You will probably find the Envy script created a correct xorg.conf file - you can look at it but don't touch........            ;-)

---

