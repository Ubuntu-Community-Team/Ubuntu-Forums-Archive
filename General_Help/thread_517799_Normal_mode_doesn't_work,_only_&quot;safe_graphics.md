---
title: "Normal mode doesn't work, only &quot;safe graphics mode&quot;"
date: 2007-08-05
forum: General Help
---

### Post by Squee3 on 2007-08-05
I'm still using the Ubuntu Live CD, but before I install Ubuntu, I would like to know why I can't start Ubuntu normally.  When I try to start Ubuntu normally, it says that sever X (graphical interface) won't load.  I can only get Ubuntu to run in safe graphics mode.  Is that because the live CD isn't using the linux driver for my video card that I installed?  Or is it something else?

---

### Post by nitro_n2o on 2007-08-05
maybe you are missing drivers
what is your graphics card? 
try ```
sudo dpkg-reconfigure xserver-xorg
```

---

