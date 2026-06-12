---
title: "Does Xubuntu 12.04 support Matrox G200 VGA chipset?"
date: 2013-09-24
forum: General Help
---

### Post by Azdour on 2013-09-24
Hi,

I have a machine that has on-board graphics - Matrix G200 and was wondering if I will hit problems if I install Xubuntu 12.04 on it.  I've never had this graphic manufacturer before, I usually have Intel or nVidia.

---

### Post by ibjsb4 on 2013-09-24
Can't tell you the model number off the top of my head, but I have another box with a dual head Matrox card working fine with ubuntu generic drivers on 12o4.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Matrox+G200&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Matrox+G200&sa=Search&cof=FORID:9)

---

### Post by JKyleOKC on 2013-09-24
The quickest way to find out is to boot from the Live CD that you would be using to do the installation, and choose the "Try" option rather than just installing. This will load Xubuntu without making any changes to your system; if the display works properly in this case, you can be reasonably confident that it will do so after installation as well.

---

### Post by Azdour on 2013-09-24
Hi,

Thanks for the replies.  I do not have the machine yet but I am encouraged from ibjsb4's post that it should be fine.

---

### Post by ibjsb4 on 2013-09-24
You may/may not need this package, just wanted to make you aware of it :)

[https://apps.ubuntu.com/cat/applications/precise/matroxset/](https://apps.ubuntu.com/cat/applications/precise/matroxset/)

---

### Post by kostkon on 2013-09-25
Matrox Gxxx cards should work fine with the MGA driver (which, if I remember correctly, the latest MESA has since removed, but it's still available in Ubuntu), fully with OpenGL 3D support that is (primitive for todays standards and obviously not enough to run Unity).

---

### Post by Azdour on 2013-10-29
Thanks to everyone who replied.  The Matrix G200 works well on the PC under Xubuntu.

---

