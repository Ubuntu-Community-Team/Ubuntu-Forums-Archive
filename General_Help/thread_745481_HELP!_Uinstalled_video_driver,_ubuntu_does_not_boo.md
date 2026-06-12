---
title: "HELP! Uinstalled video driver, ubuntu does not boot correctly, video/graphics error!"
date: 2008-04-04
forum: General Help
---

### Post by abhishekrd on 2008-04-04
OK so im running ubuntu dual booted with vista, with ubuntu on the 2nd partition. Ubuntu is set as the primary os, and i have a video error on it. This is when i installed envy, for my very old radeon 9200se card. After booting onto ubuntu i disliked how the video driver functioned and made a huge mistake to uninstall the video drivers and boot up. When i do boot up, i get a very distorted screen, looks kinda like trying to watch satelite tv during a storm. I did however try recovery mode, but i need some help getting my drivers installed because i only see a huge terminal that comes up during recovery mode. PLEASE I NEED HELP!:confused::(

---

### Post by zvacet on 2008-04-04
In recoveriy mode 

```
dpkg-reconfigure xserver-xorg
```

Select** vesa** driver and after you finish you will have basic graphic.Then search for your video card driver.

---

### Post by abhishekrd on 2008-04-04
> **zvacet said:**
> In recoveriy mode 

```
dpkg-reconfigure xserver-xorg
```

Select** vesa** driver and after you finish you will have basic graphic.Then search for your video card driver.

thanks going to try right now

---

### Post by abhishekrd on 2008-04-04
ok now it says i have all my video drivers installed but compiz isnt working anymore??? neither the emerald theme manager, or my avant window manager...

how can i get them working?

---

### Post by abhishekrd on 2008-04-05
> **zvacet said:**
> In recoveriy mode 

```
dpkg-reconfigure xserver-xorg
```

Select** vesa** driver and after you finish you will have basic graphic.Then search for your video card driver.

i reinstall ubuntu, i got too frustrated, and now i cant get simple ubuntu effects to start working....omg...it worked 100% before all of this but it get me mad that it cant work now

---

### Post by zvacet on 2008-04-05
You don´t use windows anymore,so you don´t need to reinstall when you have problems.On this subforum you solved your video problem,but you want compiz to work.Look in [this](http://ubuntuforums.org/forumdisplay.php?f=223) subforum and I´m sure you will find answer or help faster then here.

---

