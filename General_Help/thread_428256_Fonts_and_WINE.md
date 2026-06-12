---
title: "Fonts and WINE"
date: 2007-04-30
forum: General Help
---

### Post by legioneubr on 2007-04-30
Hello all,

I installed band in a box by using WINE, I run it as soon as the installation ended ....without any problem. Since the second time I have opened the application all the fonts have been changed. Everything now seems to be written in aramaic thus making it unusable.... is there a way to fix this problem?

thanks

Marco

---

### Post by hamil on 2007-04-30
Do you have the msttcorefonts installed? Probably uses one of those fonts.

Edit. A quick search at the wine page, came up with this solution:
cp $HOME/.wine/drive_c/windows/system/[pP]*ttf $HOME/drive_c/windows/fonts/

---

### Post by mts280 on 2008-05-15
Hi,

I have the same problem but copying the fonts over to the font directory did not work for me.. any further suggestions?

---

### Post by dagnabit dang doohickey on 2008-05-15
Unless things have changed since my ies4linux installation, ies4linux installs each version of IE into separate drive_c directories.

```
~/.ies4linux/ie5/drive_c/
~/.ies4linux/ie55/drive_c/
~/.ies4linux/ie6/drive_c/
```

So, you may want to copy your fonts into the fonts directories located in each of those drive_c directories.

```
~/.ies4linux/ie5/drive_c/windows/fonts/
~/.ies4linux/ie55/drive_c/windows/fonts/
~/.ies4linux/ie6/drive_c/windows/fonts/

```

---

