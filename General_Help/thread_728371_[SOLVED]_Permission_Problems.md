---
title: "[SOLVED] Permission Problems"
date: 2008-03-18
forum: General Help
---

### Post by M4rotku on 2008-03-18
Hi, I am trying to play a game and it needs to have a cache directory in my root directory.  I managed to use sudo to create the directory, but I need to enable it for being read and written by the game.

How do I change that directories permissions?  Is it possible to log in as root?

Thanks

Enclosed: the screen from the game explaining the directory needed.

---

### Post by pointone on 2008-03-18
```
sudo mkdir /rscache
sudo chmod a+rw /rscache
```

---

### Post by M4rotku on 2008-03-18
I changed the directory permissions successfully, but the game still displays the same error when I try to play.  Does anyone know what may be causing this?

---

