---
title: "LibreOffice menu bar corruption"
date: 2014-11-27
forum: General Help
---

### Post by timgood on 2014-11-27
Running LibreOffice on Ubuntu 14.10 64bit I am getting corruption on the menu bar - see attached image. I'm getting this regardless of theme used. Any ideas as to what might be causing it and how I can make it go away?

---

### Post by flaymond on 2014-11-27
It's happen sometimes and related to video graphic card. I think you using your computer for too long without regularly reboot.

---

### Post by philinux on 2014-11-27
> **timgood said:**
> Running LibreOffice on Ubuntu 14.10 64bit I am getting corruption on the menu bar - see attached image. I'm getting this regardless of theme used. Any ideas as to what might be causing it and how I can make it go away?

I get that now and then. From a net search there is this bug report. [https://bugs.freedesktop.org/show_bug.cgi?id=62480](https://bugs.freedesktop.org/show_bug.cgi?id=62480)

What graphics card have you and which driver installed?

Forgot this link. [http://ask.libreoffice.org/en/question/8055/how-do-i-fix-ui-display-corruption/](http://ask.libreoffice.org/en/question/8055/how-do-i-fix-ui-display-corruption/)

---

### Post by timgood on 2014-11-27
Interesting. The bug report seems to indicate this is a problem with Nvidia cards, but I am running the stock Intel video driver.

---

### Post by philinux on 2014-11-27
> **timgood said:**
> Interesting. The bug report seems to indicate this is a problem with Nvidia cards, but I am running the stock Intel video driver.

One thing to try is to use the Intel Graphics Installer. Scroll down for link. [http://www.omgubuntu.co.uk/2014/11/useful-tools-for-ubuntu-do-you-use-them?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG!+Ubuntu!%29](http://www.omgubuntu.co.uk/2014/11/useful-tools-for-ubuntu-do-you-use-them?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG!+Ubuntu!%29)

The other would be to install the libreoffice ppa for the latest stable version.
[http://linuxg.net/how-to-install-libreoffice-4-3-4-on-ubuntu-14-10-ubuntu-14-04-ubuntu-12-04-and-derivative-systems-via-ppa/](http://linuxg.net/how-to-install-libreoffice-4-3-4-on-ubuntu-14-10-ubuntu-14-04-ubuntu-12-04-and-derivative-systems-via-ppa/)

Both the above are reversible.

---

### Post by timgood on 2014-11-27
Intel Graphics Installer only works on 14.04 and won't install drivers on 14.10 -  I have updated to LibreOffice 4.3.4.1 but the problem remains. Guess I will have to wait for updated Intel driver. Pity.

---

