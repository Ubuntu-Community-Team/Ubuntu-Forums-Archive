---
title: "[SOLVED] Removing a .deb package"
date: 2008-06-18
forum: General Help
---

### Post by dstein on 2008-06-18
I installed Acrobat Reader a few months ago. I did not install it from an online repository. I downloaded the .deb package from adobe.com and I believe I typed $ dpkg --install AcrobatReader___, which installed everything fine. How can I remove this package?

Also, for future reference, is there any way to use Aptitude to install a downloaded .deb file? I use Aptitude for all package management. I like how it handles installation/uninstallation and dependencies. It would be great if I knew a way to use this program to install .deb files rather than using dpkg.

Lastly, I sometimes get an icon on my panel to upgrade my packages. I click it and upgrade. Is there any reason that I should not do this, instead using $ sudo aptitude update && sudo aptitude upgrade  ?  Does the graphic upgrade interfere in any way with Aptitudes package handling?

Thanks.

---

### Post by tespio on 2008-06-18
You can find it in synaptic package manager...
It's located under System>Administration>Synaptic Package Manager

---

### Post by bodhi.zazen on 2008-06-18
```
sudo dpkg -r adobereader
```

When installing with dpkg you use the full name of the .deb

ie sudo dpkg -i adobereader-zxy.deb

when removing you use just the application name (without the version information of .deb)

---

### Post by DanM718 on 2008-12-11
Wow thanks for this, worked great!

Dan

---

