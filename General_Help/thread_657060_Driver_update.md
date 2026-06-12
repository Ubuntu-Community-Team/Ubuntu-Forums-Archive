---
title: "Driver update"
date: 2008-01-03
forum: General Help
---

### Post by abnegnejs on 2008-01-03
I hope this question makes it clear that I'm a complete newb at this stuff.  So, I've noticed that my system seems to render many things pretty slow, and I thought this might be a driver issue. But I haven't found any Linux drivers for my ATI 3D Rage Pro AGP, does anyone know a workaround/solution? Any help is greatly appreciated.

P. S. I suppose it could be because I have an old card...:lolflag:

---

### Post by erfahren on 2008-01-03
you *should* have pretty good support with the open-source driver.  

the wiki page on it might provide some tips; [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by abnegnejs on 2008-01-03
OK, thanks for the quick response.

---

### Post by me4oslav on 2008-01-03
You can also check Envy,it recognise you ATi/nVidia Video Card and install the newest driver:
[http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")
Just install it(it is gonna want some other packages,too),install dkms,run envy -g(Gnome),envy(KDE),check the box Install ATi Driver,click apply and wait.After a while it would ask you if you want to configure xorg.conf with your new driver.You should click YES and it will reboot your PC.Than you are ready.

---

### Post by erfahren on 2008-01-03
> **me4oslav said:**
> You can also check Envy,it recognise you ATi/nVidia Video Card and install the newest driver:
[http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")
Just install it(it is gonna want some other packages,too),install dkms,run envy -g(Gnome),envy(KDE),check the box Install ATi Driver,click apply and wait.After a while it would ask you if you want to configure xorg.conf with your new driver.You should click YES and it will reboot your PC.Than you are ready.
maybe --- but the OP has an older card though, so may actually get better support with the open-source driver than the ATI proprietary driver. 

("fglrx" is a four-letter word around here! - lol)

---

### Post by me4oslav on 2008-01-04
I was having ATI Rage Fury and it worked fine,with the official ATi driver installed from Envy,that why i have wrote about it.

---

