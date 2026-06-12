---
title: "Okular - Ability to select Print Tray"
date: 2018-05-02
forum: General Help
---

### Post by Onesimus on 2018-05-02
I am using Okular to look and print PDF documents (it is slightly better than Evince as it is able to open multiple documents in Tabs rather than in separate windows).  However, when I try to print a PDF document from Okular I am unable to select a Print Tray as the Paper Source.  Is there any way to select the Paper Source ?

Additionally, does anyone know if there is a PDF reader than can print a PDF document as a booklet, in the same way that LibreOffice can ?

---

### Post by SeijiSensei on 2018-05-02
This is a problem that has plagued KDE since it went to Qt5.  Qt5's native printer functions do not include options like paper trays.  In 2015, the relevant developer wrote he had little support for fixing this problem: [http://lists.qt-project.org/pipermail/interest/2015-September/018694.html](http://lists.qt-project.org/pipermail/interest/2015-September/018694.html)  I've been on a mailing list for a related bug since 2009.

Can you change the settings if you use the CUPS interface by pointing a browser at [http://localhost:631/](http://localhost:631/) ?

---

