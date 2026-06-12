---
title: "Need Help Bad!!!"
date: 2007-05-18
forum: General Help
---

### Post by azidtripz on 2007-05-18
Hi there, this problem is driving me nuts

i have installed the latest nvidia driver 9755 from nvidia.com
after installation i can log into x, however after reboot i am unable to,
so i checked in lsmod and nvidia is not loaded so i modprobe -i nvidia
and that does the trick, all the fixes i can find for this prolem are
to put "nvidia" into /etc/modules and that i have done but it still doesnt load it
anyone have any sugestions ?
is it posible that /etc/modules isnt being read at boot ?

---

### Post by amd-64 on 2007-05-18
Install the new restricted-manager 
```
sudo install restricted-manager

sudo restricted-manager
```

You can enable the module there. Also make sure you do not have an older version of the nvidia driver that gets loaded first

---

### Post by azidtripz on 2007-05-18
ahhh thank you ver much,
i will try that..

---

