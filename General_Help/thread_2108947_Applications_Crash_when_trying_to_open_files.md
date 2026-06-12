---
title: "Applications Crash when trying to open files"
date: 2013-01-26
forum: General Help
---

### Post by JayPeeJay on 2013-01-26
After upgrade to 12.04 a few of my applications crash whenever I try to open files.

I seem to be able to open recent files, but not when I go to the directory to try to select any.

This happens in Scribus and LMMS.

Someone suguested changing qt4 settings, but i guess I don't know what to set them to because I still have the issues.

---

### Post by JayPeeJay on 2013-01-26
Solution:

sudo apt-get remove qt-ap-spi

this is known bug and fixed both my problems in LMMS and Scribus.

---

