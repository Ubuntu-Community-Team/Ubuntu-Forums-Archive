---
title: "uninstalled x.org"
date: 2008-03-08
forum: General Help
---

### Post by cabal2000 on 2008-03-08
Please help. I un installed x.server in error an now at boot I just get a black screen

---

### Post by astoltz on 2008-03-08
At the "black screen" there should be a login prompt, yes?  If not, try pressing ctrl-alt-F1 to get a prompt.  Login with your username and password, then enter the command: ```
sudo apt-get install xserver-xorg
```

---

### Post by IcemanV9 on 2008-03-08
Reinstall xorg in the terminal [ctrl+alt+f1] ...

```
sudo aptitude install xserver-xorg
```

---

