---
title: "Blank Screen"
date: 2008-04-01
forum: General Help
---

### Post by sureshd2008 on 2008-04-01
I have loaded Kubuntu on my Compaq Pressariio Laptop. It worked fine after installation.
However, now, after reboot, the screen is blank and I am unbale to recover from it

Please help with suggestions.

Thanks,
Suresh

---

### Post by zvacet on 2008-04-02
In recovery mode type 

```
dpkg-reconfigure xserver-xorg
```

when you come to the driver stage select **vesa** and continue to the end.Reboot and you should hace basic graphic.Loo for your video driver under restricted divers manager (or something similar).

---

