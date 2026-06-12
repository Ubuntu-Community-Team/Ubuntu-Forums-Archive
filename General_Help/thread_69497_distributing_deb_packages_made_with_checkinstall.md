---
title: "distributing deb packages made with checkinstall"
date: 2005-09-27
forum: General Help
---

### Post by 23meg on 2005-09-27
i use [checkinstall]("http://asic-linux.com.mx/~izto/checkinstall/") every time i compile something from source. it's an invaluable tool for keeping track of what you've compiled and easily uninstalling and reinstalling it later on. but i'm wondering how safe it is to distribute packages made with it. do they inherit the build dependencies so that while installing the deb package on another system apt will indicate them, and not install the package if they are not found? other than this, i reckon it must be safe as long as the correct cpu architecture is indicated while distributing. is it?

---

