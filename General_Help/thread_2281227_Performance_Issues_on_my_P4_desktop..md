---
title: "Performance Issues on my P4 desktop."
date: 2015-06-05
forum: General Help
---

### Post by k-d-bhaumik2012 on 2015-06-05
Hello,
Recently I have resurrected my old P4 desktop and tried running 14.04 LTS on it.
I prefer this distro as I have been using Ubuntu since the launch of 12.04 LTS. But this PC randomly runs slow at times. Specially when browsing the net on chrome.

PC Specs.
Core : Intel® Pentium(R) 4 CPU 3.06GHz × 2 
Motherboard: P5GD2-TVM-GB-SI, 1MB Cache.
Graphics: Intel® 915G x86/MMX/SSE2
RAM: 2GB DDR2

I know, trying a different flavor like Xubuntu or Lubuntu will help, as my graphics specs are low. But Is there anyway I can tweak Unity or any other aspect of the OS to make it run faster?

---

### Post by dino99 on 2015-06-05
chrome (chromium) is a heavy app, better to use 'midori' on such low hardware

---

### Post by tgalati4 on 2015-06-05
2 GB of RAM will fill up quickly with firefox or chrome and lots of tabs.  Check your usage by opening a terminal:

```
free
```

---

### Post by v3.xx on 2015-06-05
And like you said, it could be your graphics.  Unity is demanding.

Try a different desktop/window manager, just for a comparison.  Flashback with the metacity window manager is easy to install and lighter than your current set-up.
```
sudo apt-get install gnome-panel
```
Reboot and choose your desktop at the login screen by clicking on the icon.

Edit
Further research indicated that Unity will fall back to llvmpipe with a weak graphics card.  This would come at a performance cost.

If I understand the code correctly ..
```
glxinfo | grep OpenGL
```
Will tell you if this is the case.

I have now exhausted my Unity knowledge base :) good luck

---

