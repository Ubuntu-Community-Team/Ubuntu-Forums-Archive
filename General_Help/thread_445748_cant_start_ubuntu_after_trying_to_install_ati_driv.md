---
title: "cant start ubuntu after trying to install ati drivers"
date: 2007-05-16
forum: General Help
---

### Post by normva on 2007-05-16
I tryed to install ATI drivers using this thread [http://ubuntuforums.org/showthread.php?t=438008&highlight=ati+drivers+guide](http://ubuntuforums.org/showthread.php?t=438008&highlight=ati+drivers+guide).
Mayby i did something wrong, but cant start ubuntu anymore. It loads fine and after loading it shows an error thet i dont remenber anymore (something about xorg.conf). need help!!!!!!!

---

### Post by DeathStar on 2007-05-16
Hi Normva,

I had the same issue (and am still battling with it at the moment).

The error you're getting seems to relate to the XServer failing to start becauseyour xorg.conf is not correct.

If you can access the promt, try the following...

```
cd /etx/X11

sudo mv xorg.conf xorg.conf.bak

sudo dpkg-reconfigure xserver-xorg
```

This will allow you to reconfigure your xserver from scratch and you should be able to set it up as it was originally. That way, you can at leat access the login screen.

Let me know how you get on.

DS

---

