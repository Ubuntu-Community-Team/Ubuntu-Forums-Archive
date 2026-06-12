---
title: "Error installing nvidia-331 on Ubuntu 14.04 (Acer Aspire Z370, NVIDIA GeForce GT 620)"
date: 2015-06-28
forum: General Help
---

### Post by temmokan on 2015-06-28
Hello,

OS: Ubunto 14.04 x86_64, all last updates applied.

I am trying to install nvidia-331 package (to acquire OpenGL 4.x support) on Acer Aspire Z370 monoblock, equipped with NVIDIA GeForce GT 620 card.

The below message I see when trying to install nvidia-331 package gives me no hint on where to look for the origin of problem:

```
[COLOR=#111111][FONT=Consolas]Preparing to unpack .../nvidia-331_331.113-0ubuntu0.0.4_amd64.deb ...[/FONT][/COLOR]
Unpacking nvidia-331 (331.113-0ubuntu0.0.4) ...
dpkg: error processing archive /var/cache/apt/archives/nvidia-331_331.113-0ubuntu0.0.4_amd64.deb (--unpack):
 [COLOR=#111111][FONT=Consolas]unable to open '/usr/lib32/nvidia-331/libnvidia-ifr.so.331.113.dpkg-new': No such file or directory[/FONT][/COLOR]
```

I would appreciate hints in how to handle the above error. Purging nvidia* packages, autocleaning etc did not help.

---

### Post by temmokan on 2015-07-05
Not a single reply during a week. Nothing much helpful on Google, too. I can't believe I am the only one who encountered that problem.

---

### Post by dino99 on 2015-07-05
is that nvidia-331 picked up from the ubuntu archive ? or installed from an other source ?
erase the packages (sudo rm /var/cache/apt/archives/*) then update again and see if you get better luck to upgrade

---

