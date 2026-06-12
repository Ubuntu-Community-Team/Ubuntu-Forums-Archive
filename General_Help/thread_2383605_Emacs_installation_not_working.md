---
title: "Emacs installation not working"
date: 2018-01-27
forum: General Help
---

### Post by thesneakingwolf on 2018-01-27
So I've recently reinstalled Ubuntu, version 17.10, and everything is working great, except one thing: I can't install emacs.

When I first tried to install emacs, I got an error saying the file libotf.so.0 was missing. After looking around on the Internet I managed to solve that, by removing a package called "openmpi-bin"(don't know if I should have done that though). Now when I try to install emacs, I get an error saying:

"error while loading shared libraries: libm17n-core.so.0: cannot open shared object file: No such file or directory"

I have been able to install emacs25-nox, but I cannot find a way to install the GUI version.

(I am running GNOME Xorg with Nvidia drivers)

---

### Post by managerceo1 on 2018-01-27
Maybe it was a 32 bit version, but you have a 64 bit operating system?

---

### Post by Impavidus on 2018-01-28
So you can't install emacs using the package manager with```
sudo apt install emacs25
```or using any of the GUI interfaces to the package manager?

Just trying to confirm you tried via the package manager, not by downloading stuff from the internet and manually installing it. Using the package manager you should always get the right version. Missing libraries are almost unheard of when installing this way.

---

### Post by thesneakingwolf on 2018-01-28
Yes, I have tried installing emacs using apt install, both the 'emacs' and 'emacs25' package, but both has raised the same error. I very surprised, too, when this happened, because errors like these rarely happen, and when they do, it's often because of some common problem, and the solution is often easy to find. That doesn't seem to be the case here, though.

---

### Post by Impavidus on 2018-01-29
emacs25 depends on the packages **libotf0** and **libm17n-0**, which contain the files /usr/lib/x86_64-linux-gnu/libotf.so.0 and /usr/lib/x86_64-linux-gnu/libm17n-core.so.0. The libraries should have been installed automatically. Maybe reinstalling those packages helps.

---

### Post by thesneakingwolf on 2018-01-29
That seems indeed to be the solution. I thought I had already reinstalled **libm17n-0**, but I must have done so while emacs was still installed, before I purged it. Thanks a lot!

---

