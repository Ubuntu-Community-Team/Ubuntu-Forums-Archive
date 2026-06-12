---
title: "Splash screen"
date: 2008-01-29
forum: General Help
---

### Post by karthik_jce on 2008-01-29
Hi,

I am new to Ubuntu and I hope the screen which i refer here is the splash screen, i.e the one which shows up with a status bar when ubuntu bootsup,

I was using Ubuntu7.04 and installed few packages from Ubuntu 7.10, and after rebooting i find that the screen shows me as "ebuntu" Whereas earlier it was "ubuntu", some package should have modified this and am not sure which one and how to change it back (or with some other image).

Regards
Karthik

---

### Post by danwood76 on 2008-01-29
You probably have 2 splash screens installed now.
To change it to the normal ubuntu one I think you do this in terminal:
```

sudo update-alternatives --config usplash-artwork.so
sudo update-initramfs -u

```

to install different ubuntu splash screens type this in terminal to get a list of them:
```

aptitude search usplash
```
and then choose the one of your choice, for example xubutnu
```

sudo apt-get install xubuntu-artwork-usplash

```

then do the first 2 instructions again to choose and update.

regards,
Danny

---

