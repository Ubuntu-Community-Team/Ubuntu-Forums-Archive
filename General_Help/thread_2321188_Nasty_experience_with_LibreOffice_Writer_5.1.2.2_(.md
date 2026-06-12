---
title: "Nasty experience with LibreOffice Writer 5.1.2.2 (gtk3)"
date: 2016-04-21
forum: General Help
---

### Post by vasa1 on 2016-04-21
I keep my Linux notes as a Writer document. The files is about 29 pages long (33.3 KiB).

I had no problems with an earlier version of LibreOffice Writer, but with the current version from the software center in 16.04, whenever I opened this file, my laptop's temperature and CPU usage shot up to 60 degrees Celsius and 60% and stayed there for about 2-3 min. The program was unusable during this time. After things cooled down it was usable: I could enter text or highlight stuff.

After several tries, I noticed that the pages shown in the left corner of the status bar *decreased* to just one during the madness. I then saw that I had *Web* rather than *Normal* selected in the *View* menu. This never caused problems previously. Switching to *Normal* fixed things. I don't know why.

---

### Post by miksar on 2016-04-23
I'm having the same problem, but I haven't found any solution yet.

---

### Post by miksar on 2016-04-23
OK, I found a solution: removing the package libreoffice-gtk seems to help a lot.

---

### Post by vasa1 on 2016-05-02
> **miksar said:**
> OK, I found a solution: removing the package libreoffice-gtk seems to help a lot.

I don't understand why that should work on 1_6_.04. libreoffice-gtk is meant to facilitate integration of gtk_2_ apps. In 1_6_.04, LibreOffice 5.1.2.2 defaults to using gtk_3_ and *libreoffice-gtk* isn't present by default in flavors such as Lubuntu.

Anyway, the workaround I'm using is to drop back to gtk_2_ for LibreOffice.

See [http://ubuntuforums.org/showthread.php?t=2322879&p=13482332#post13482332](http://ubuntuforums.org/showthread.php?t=2322879&p=13482332#post13482332)

For the gtk2 mode to look decent, I installed *libreoffice-gtk*.

Now, even if I have "Web" selected under View, there isn't any problem. Maybe my laptop doesn't have the horsepower to handle the gtk3 version of LibreOffice.

---

