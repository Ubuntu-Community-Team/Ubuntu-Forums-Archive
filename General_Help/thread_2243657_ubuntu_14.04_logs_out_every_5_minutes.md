---
title: "ubuntu 14.04 logs out every 5 minutes"
date: 2014-09-10
forum: General Help
---

### Post by hinaimran-mehr on 2014-09-10
[COLOR=#333333][FONT=UbuntuRegular]I have Ubuntu 14.04. Today suddenly it started to log out abruptly every 5 minutes. It was running fine before. but now I cannot even read the error messages.. what should I do..
Edit: I noticed that it happens when i run applications like firefox or CompizConfig settings manager.
My graphics card driver is Nvidia binary driver- version 331.89 from NVIDIA-331, graphic cards on my system are Intel Corporation 4th Gen Core Processor Integrated Graphics Controller and Nvidia GEFORCE 750M. Currently I am using intel


[/FONT][/COLOR]

---

### Post by ian-weisser on 2014-09-11
An abrupt logout, losing all unsaved data, is usually a X server crash.
Take a look in /var/log/syslog and /var/log/Xorg* for useful error messages after a crash. If you find any, post them here.

---

