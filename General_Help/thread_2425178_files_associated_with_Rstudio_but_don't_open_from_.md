---
title: "files associated with Rstudio but don't open from nautilus"
date: 2019-08-21
forum: General Help
---

### Post by firthu on 2019-08-21
Hi, my .R files are associated with Rstudio (showing icon correctly) but double-click on them does not work - Rstudio does not open them - . What could it be. Every time I have to manually open Rstudio and go to the folder manually.

---

### Post by #&amp;thj^% on 2019-08-21
Using R inside RStudio is the recommended choice. 
More info found here: [http://www.sthda.com/english/wiki/running-rstudio-and-setting-up-your-working-directory-easy-r-programming](http://www.sthda.com/english/wiki/running-rstudio-and-setting-up-your-working-directory-easy-r-programming)

---

### Post by firthu on 2019-08-21
I use Rstudio. of course. double-click does not open them in Rstudio. that is the problem. same problem with all rstudio files, i.e. .rmd

---

### Post by #&amp;thj^% on 2019-08-21
Still lacking anything useful to help you here, 
How are you using it?
Example: **"nautilus ~/.rstudio-desktop"**
I have to go to work now, I'll check back later. Good Luck.

---

### Post by firthu on 2019-08-21
I dont understand the question. As with any file, when I double-click it (in nautilus), I expect them to open in an associated software.

---

### Post by dragonfly41 on 2019-08-21
Have you tried Thunar file manager instead of Nautilus? Same results?

---

### Post by mc4man on 2019-08-21
> **firthu said:**
> Hi, my .R files are associated with Rstudio (showing icon correctly) but double-click on them does not work - Rstudio does not open them - . What could it be. Every time I have to manually open Rstudio and go to the folder manually.
What release of Ubuntu?
Works fine here in 18.04 with either nemo (default fm)or nautilus, both from d. click or r. click > Open With RStudio

---

### Post by firthu on 2019-08-21
same result

---

### Post by mc4man on 2019-08-21
In addition to query in post 7, how did you install RStudio.
Does this work or provide any message if not? 

> xdg-open  /path/to/whatever.R

---

### Post by firthu on 2019-08-21
Well, I uinstalled and reinstalled Rstudio. but then, didn't open at all, with dmesg error:
rstudio[29785]: segfault at 8 ip 00007febe20aca99 sp 00007ffed912d990 error 4 in libQt5XcbQpa.so.5.9.5[7febe2050000+fb000]

So this answer solved:
[https://askubuntu.com/questions/1041588/virtualbox-not-launching-on-ubuntu-18-04-qt-lib-problem](https://askubuntu.com/questions/1041588/virtualbox-not-launching-on-ubuntu-18-04-qt-lib-problem)

---

### Post by firthu on 2019-09-23
Problem reappeared after installing software that uses qt5. Even in ubuntu 19.04

---

### Post by mc4man on 2019-09-23
> **firthu said:**
> Problem reappeared after installing software that uses qt5. Even in ubuntu 19.04

What do you mean by "Problem reappeared"? Which problem..

Where are you getting rstudio from?  The .debs from here include qt5 libs that rstudio uses so the system libqt5core5a shouldn't matter.

[https://www.rstudio.com/products/rstudio/download/#download](https://www.rstudio.com/products/rstudio/download/#download)
For 18.04 use the Ubuntu18 .deb.

The rstudio binary is installed in /usr/lib/rstudio/bin , libs in /usr/lib/rstudio/lib,
This should come up with no Not Founds - 
```
ldd  /usr/lib/rstudio/bin/rstudio
```

---

### Post by firthu on 2019-09-24
Hi, problem is associated files don't open with nautilus or xdg-open. I got Rstudio from there. I run ```
ldd ....
``` and seems ok. I updated recently to 19.04 because in 18.04 I had segmentation fault in Rstudio. Now I get this with xdg-open: 

```
qt.qpa.plugin: Could not load the Qt platform plugin "xcb" in "" even though it was found.This application failed to start because no Qt platform plugin could be initialized. Reinstalling the application may fix this problem.


Available platform plugins are: eglfs, linuxfb, minimal, minimalegl, offscreen, vnc, wayland-egl, wayland, wayland-xcomposite-egl, wayland-xcomposite-glx, xcb.
```

---

### Post by #&amp;thj^% on 2019-09-24
Sometimes a simple re-install helps:
```
sudo apt install --reinstall libx11-xcb1
```
And:
```
sudo apt install --reinstall libxcb
```

---

### Post by firthu on 2020-02-27
I posted an answer to this here:
[https://askubuntu.com/questions/675223/rstudio-does-not-launch-after-installation/1213490#1213490](https://askubuntu.com/questions/675223/rstudio-does-not-launch-after-installation/1213490#1213490)

---

