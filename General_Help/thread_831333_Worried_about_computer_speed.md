---
title: "Worried about computer speed"
date: 2008-06-16
forum: General Help
---

### Post by sponsoredwalk on 2008-06-16
I am on ubuntu 7.10 but the computer lags and gets very annoying, 256mb ram.
I installed the xfe desktop via the terminal under the assumption that it would speed up the computer (which is supposedly slowed down by the "bulkiness" of gnome???) but it did not. 

Well whatever the cause i made a Xubuntu 7.10 disc and am wondering would my computer be faster than it is using plain old - U - buntu 7.10 if i installed Xubuntu 7.10 as an entirely seperate entity i.e. put the disc in and wait the hour or so for it to install?

---

### Post by Zorael on 2008-06-16
Xfce has a smaller memory-print than Gnome and KDE (which are comparatively fairly even); ergo, it will swap less. However, it does not magically make all your running applications and services take up less memory, so you may want to track down those memory-hogs and replace them with lighter alternatives, much like you just did with Gnome -> Xfce. Perhaps Epiphany/Konqueror/Opera instead of Firefox, disable that Compiz, disable services that you don't use, etc.

Pure processor-heavy tasks, such as compressing files or compiling stuff, will still be as fast/slow.

For desktop environment memory-print numbers, see [http://ktown.kde.org/~seli/memory/desktop_benchmark.html](http://ktown.kde.org/~seli/memory/desktop_benchmark.html).

---

### Post by sponsoredwalk on 2008-06-16
i see, well is there any way to make the computer use MORE of the swap memory and less of the cpu 256mb ram as i have an unnecessarily high swap partition  (8gb:))from an eventful installation...???

---

