---
title: "dependencies"
date: 2007-06-24
forum: General Help
---

### Post by phizikal on 2007-06-24
Ok, I have been trying to get some programs and such. But everyone of them says it has a missing dependencies. How can I get all of them. 

The program I am trying to get is basic-256.

PLEASE AND THANKS YOUS!

---

### Post by tgm4883 on 2007-06-24
sudo apt-get install *name of dependency*

---

### Post by phizikal on 2007-06-24
```

root@admin:/home/admin# sudo apt-get install libc6
Reading package lists... Done
Building dependency tree... Done
libc6 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```
and i am still getting the error. =/

---

### Post by tgm4883 on 2007-06-24
How are you trying to install the program, and can you post the output when you try to install it?

---

### Post by phizikal on 2007-06-24
I am downloading it from getdeb and it auto installs.

---

### Post by tgm4883 on 2007-06-24
from terminal, use I think sudo dpkg -i *packagename*.deb  Look up the usage of dpkg to be sure

---

