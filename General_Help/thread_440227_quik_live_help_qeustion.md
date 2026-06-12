---
title: "quik live help qeustion"
date: 2007-05-11
forum: General Help
---

### Post by gr3nad3 on 2007-05-11
can some post a code get to Ubuntu start from the live cd, i have to change the resolution setting to get my Ubuntu to work right now. its mounted on / or w/e . thats all i need to know

---

### Post by taurus on 2007-05-11
_Assuming_ you have mounted it to **/mnt/ubuntu**, open a terminal and do

Applications -> Accessories -> Terminal
```
gksudo gedit **/mnt/ubuntu**/etc/X11/xorg.conf
```

---

