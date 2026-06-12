---
title: "Can't run appimage"
date: 2019-05-28
forum: General Help
---

### Post by lparka on 2019-05-28
I have been tying to solve this for a long time. Earlier attempts to run an .appimage file resulted in a massage saying that FUSE is required. I removed and reinstalled fuse.


Attempt to run appimage:
-----------------------------


**par@par:~/KDENLIVE$ sudo ./kdenlive-18.12.1b-x86_64\ \(1\).appimage **
**dlopen(): error loading libfuse.so.2**

**AppImages require FUSE to run. **
**You might still be able to extract the contents of this AppImage **
**if you run it with the --appimage-extract option. **
**See [https://github.com/AppImage/AppImageKit/wiki/FUSE](https://github.com/AppImage/AppImageKit/wiki/FUSE) **
**for more information**

Attempt to install libfuse2:
-----------------------------

**par@par:~/KDENLIVE$ sudo apt install libfuse2**
**Reading package lists... Done**
**Building dependency tree       **
**Reading state information... Done**
**libfuse2 is already the newest version (2.9.7-1ubuntu1).**
The following packages were automatically installed and are no longer required:
  libflatpak0 libntfs-3g88 libostree-1-1
Use 'sudo apt autoremove' to remove them**.**
**0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.**
[B]par@par:~/KDENLIVE$ 

[/B]Why  libfuse.so.2 cannot be loaded?On another computer with the same version of Ubuntu (18.04)  I can run this appimage.


Any help is appreciated.

---

