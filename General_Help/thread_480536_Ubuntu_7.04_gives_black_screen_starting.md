---
title: "Ubuntu 7.04 gives black screen starting"
date: 2007-06-21
forum: General Help
---

### Post by ChaQ on 2007-06-21
I updated to lastest kernel version but when i try to start ubuntu from "the group" it crashes in a second and black screen appears.
Only in recovery mode i can start ubuntu and X :(
i have amd64 and ati x850xt. I 've installed the ati driver config my refreshrate too but problem is still alive.

Any ideas? thanks

---

### Post by Crafty Kisses on 2007-06-21
> **ChaQ said:**
> I updated to lastest kernel version but when i try to start ubuntu from "the group" it crashes in a second and black screen appears.
Only in recovery mode i can start ubuntu and X :(
i have amd64 and ati x850xt. I 've installed the ati driver config my refreshrate too but problem is still alive.

Any ideas? thanks

You should try reconfiguring your X server:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by ChaQ on 2007-06-21
> **Codename said:**
> You should try reconfiguring your X server:
```
sudo dpkg-reconfigure xserver-xorg
```

yes i did it and changed drivers to "ati", "radeon" and "fglrx" but none of them solved my problem..

---

