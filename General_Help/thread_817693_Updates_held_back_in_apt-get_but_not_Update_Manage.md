---
title: "Updates held back in apt-get but not Update Manager"
date: 2008-06-03
forum: General Help
---

### Post by brendonbrewer on 2008-06-03
Today I did an update (with hardy-proposed and hardy-backports enabled) using apt-get and here's what happened.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic
  linux-restricted-modules-generic
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.

However, the GUI update manager is telling me to install these updates. I'm guessing that would be a bad idea, but it worries me that the two programs are disagreeing with each other. I thought one was just a gui front end to the other.

What's going on here?

---

### Post by Xiong Chiamiov on 2008-06-05
They're actually both front-ends to apt, just like Synaptic, Adept, and Aptitude.  There have been some interesting things going on recently for some people with the update managers not updating certain packages; I'm not sure if it has something to do with the fact that kernel updates can break a lot of things or what.  Theoretically, the people in charge have made sure that nothing will break with a new kernel, but sometimes...

---

### Post by Nepherte on 2008-06-05
If you want to install the updates that were held back, you can install them by doing:
```
sudo apt-get install dist-upgrade
```

---

### Post by mrMango on 2008-06-05
I believe you mean

```
sudo apt-get dist-upgrade
```

---

