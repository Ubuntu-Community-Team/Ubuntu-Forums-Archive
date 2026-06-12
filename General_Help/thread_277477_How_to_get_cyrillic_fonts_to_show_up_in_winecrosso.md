---
title: "How to get cyrillic fonts to show up in wine/crossover"
date: 2006-10-14
forum: General Help
---

### Post by makhand on 2006-10-14
I've installed "ABBYY Lingvo 11 Russian-English Dictionary" using the latest crossover beta (6.0.0 beta2). I tried installing it 5.0.3 and couldn't get all  of the components (dictionaries) to install. 6.0.0 seems to be working nearly flawlessly, except that almost none of the Russian fonts are showing up. I have haven't had much luck in finding even a starting place to remedy this problem. Can anyone help? Most of the Cyrillic letters (except sometimes italicized ones) show up as boxes. 

thanks,
makhand

---

### Post by josys36 on 2006-10-18
If you find an answer to this let me know. I am working on a simular issue with another product.

Jason

---

### Post by cap_gemo on 2007-09-24
Normally you only have UTF russian locales in Ubuntu, but Lingvo seems to support only one-byte-coding (it's just a thought, don't know, if it really is so). That's why first you need to generate a Windows russian locale. Enter the following command in a terminal:

  sudo locale-gen ru_RU.CP1251

  Then open the gnome menu editor to edit the properties of the launcher. In the command, that is used to launch the programm, add the following right at the beginning:

  LANG=ru_RU.CP1251

  so if you had something like this

  WINEPREFIX=/home/yourname/.wine wine C:\\Program Files\\ABBYY Lingvo\\Lingvo.exe

  it should look like

  LANG=ru_RU.CP1251 WINEPREFIX=/home/yourname/.wine wine C:\\Program Files\\ABBYY Lingvo\\Lingvo.exe

  Try it. Also try playing with other Russian locales.

---

### Post by Clarke on 2007-12-22
If u are interested particulary in Lingvo, its possible to use it's dictionaries with Stardict.
[The guide]("http://brutalblog.wordpress.com/2007/12/20/1/")
Hope it will help.

---

