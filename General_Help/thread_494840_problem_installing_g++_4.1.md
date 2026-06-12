---
title: "problem installing g++ 4.1"
date: 2007-07-07
forum: General Help
---

### Post by fireworld2406 on 2007-07-07
hi
i have been trying to ocmpileot martian driver so hopefully my modem will work in ubuntu 6.10 so ive been downloading the required packages anyways one of them is g++ 4.1 and one of its dependencies is libstdc++6
when i go to install the libstdc++6 package it says that it requires g++ 4.1 and when i go to install g++ 4.1 it says it requires libstdc++6 how can i get them to install?

---

### Post by taurus on 2007-07-07
Build-essential package is on the CD so if you want to compile something from source, you need to install it.  Insert the installer CD into a drive and run

```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential
gcc -v
```

---

