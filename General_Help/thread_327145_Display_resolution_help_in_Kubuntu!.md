---
title: "Display resolution help in Kubuntu!"
date: 2006-12-28
forum: General Help
---

### Post by Bllizzd on 2006-12-28
I have just install kubuntu, and my resolution only goes up to 800 by 600, when i use windows, my resolution goes up to 1024 by 764, and ubuntu will go up to 1024 by 764.

How do i get my resolution to go up to 1024 by 764 in kubuntu?

---

### Post by slimdog360 on 2006-12-28
whack this into a terminal
```
sudo dpkg-reconfigure xserver-xorg
```

You may have to know the specifications of your monitor (in you manual or internet) if it cant configure your monitor properly.
then when your done press ctrl-alt-backspace

---

