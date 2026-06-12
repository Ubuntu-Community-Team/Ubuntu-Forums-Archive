---
title: "Changing startup screen"
date: 2006-08-07
forum: General Help
---

### Post by kernco on 2006-08-07
I originally installed Ubuntu 6.06 from the CD, but I recently wanted to try out the Kubuntu desktop, so I did "apt-get install kubuntu-desktop".  I like having the option to use KDE, but now when Ubuntu boots it shows the Kubuntu loading screen instead of the Ubuntu one.  Is there any way to get it back to using the original Ubuntu loading screen?

---

### Post by Ramses de Norre on 2006-08-07
```
sudo update-alternatives --config usplash-artwork.so
sudo dpkg-reconfigure linux-image-`uname -r`
```

---

